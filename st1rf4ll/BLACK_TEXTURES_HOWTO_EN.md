# Making Rivals surfaces black through Fleasion's Modifications tab

Notes from getting this working on macOS, August 2026. Everything below was tested in
game, and the negative results are included on purpose — they are the expensive part.

## What this is, and what it is not

Surface colour in Rivals is **not** reachable through replacement rules in the config.
It comes from the material texture files that ship *inside the Roblox client*, and those
are never requested over the network, so a proxy never sees them. Fleasion handles them
in a completely separate place: the **Modifications** tab, which writes files into the
Roblox install directly, stashes the originals, and puts them back when you reset or quit.

Things that were tried by ID and do **not** touch the map:

| tried | result |
|---|---|
| 384 TexturePack slot IDs (`<id>:0`) + bare `<color>` IDs | painted the skin's arms and the AR, map untouched |
| 14 direct material colour assets | nothing |
| 11 TexturePacks found by diffing the asset cache around an arena-only session | nothing |

The map only responded once a client material file was replaced.

## The one rule that explains everything: these textures multiply

`studs.dds` and the material `diffuse.dds` files are multiplied onto each part's own
colour, and — this is the part that costs people a day — **the engine takes only their
brightness. Hue is discarded.**

Proof, two installs, both with the replacement config fully disabled so nothing else
could interfere:

| file | mean brightness | result in game |
|---|---|---|
| purple, brightness 0.27 | 0.27 | world went nearly black |
| purple, brightness 0.49 (stock level) | 0.49 | looked completely stock |

The second file differs from stock **only** in colour. The game did not notice. Same test
with full magenta at stock brightness, on both `studs.dds` and `plastic/diffuse.dds`: no
change either.

So: **you can darken, you cannot tint.** If you have seen a "dark textures" pack, this is
why it is dark rather than coloured — black is the only thing this route gives you. It is
a property of the method, not an art choice.

The same applies to the arena texture asset `7658055825`: it is a brightness map, so a
black file works and a coloured one just dims things.

## Making the file

Do not decode → tint → re-encode with Pillow. It reads DXT1/DXT5 but writes only
**uncompressed** DDS, which drops the whole mip chain and inflates the file about 6x.

Recolour **in compressed space instead**. A DXT1 block is 8 bytes: two RGB565 endpoint
colours, then 4 bytes of 2-bit per-pixel indices. Scale only the two endpoints and leave
the indices alone — the image darkens while header, dimensions, format, mip chain and
file size stay byte-for-byte identical in structure.

One trap: DXT1 picks its mode from the **order** of the two endpoints. `c0 > c1` is the
opaque 4-colour mode; `c0 <= c1` is 3 colours plus 1-bit transparency. RGB565 packing is
not monotonic in brightness, so scaling can flip that comparison and silently turn opaque
blocks transparent. Where it flips, swap the endpoints back and remap the indices
(`0<->1`, and `2<->3` in 4-colour blocks).

That trap is not theoretical. A darkened `studs.dds` from a ready-made pack measured:

* **67.7% of blocks** in the transparent mode (stock: 1.4%)
* **40.6% of pixels actually transparent** (stock: 0%)
* **0 mip levels** (stock: 12)

It reads as "black" in game, but the blackness is largely holes punched through the
texture, and the missing mips shimmer at distance. Worth checking any file you inherit.

Script used here: `tint_dds.py`.

```bash
# neutral darkening, mips and block modes preserved
python3 tint_dds.py <stock studs.dds> studs_dark.dds --strength 0 --gain 0.55
```

`--gain` is the brightness multiplier — 0.55 is a moderate dusk, 0.30 is properly dark.

## Installing it

1. **Quit Roblox.** Files are written into the app itself; a running client will not
   re-read them.
2. Fleasion → **Modifications** tab.
3. For `studs.dds` use the ready-made **Low Quality Studs** row → **Browse...** → your file.
4. For anything else use **Custom Modifications → + Add Modification** and type the target
   path explicitly, for example `PlatformContent/pc/textures/plastic/diffuse.dds`.
   Avoid the **High Quality Studs** row unless you mean it — it covers three targets at
   once, including the normal maps.
5. Launch and look at any plastic surface.

Undo is **Reset to original** in the same row. Fleasion keeps the untouched file in
`ModOriginals/` and restores it on exit as well.

Change one file per run. Installing several at once and reasoning backwards from the
result is how you end up with a confident wrong conclusion.

## Pitfalls worth knowing

**Never tint the normal maps.** `plastic/normal.dds` and `plastic/normaldetail.dds` encode
surface direction, not colour — stock mean RGB is around (255, 128, 0). Colour-tinting
pipelines happily process them anyway; one pack's versions measured (166, 138, 198), which
means the relief data is gone. Installing those breaks lighting and speculars on every
plastic surface.

**Rebuild from the stash, not from the client.** Once a modification is applied, the file
in the Roblox folder *is your file*. Re-tinting it compounds the effect. The untouched
original lives in Fleasion's `ModOriginals/` mirror of the same relative path.

**Fleasion copies the file when you apply it.** Editing your source file on disk afterwards
changes nothing in game — re-apply the row (Browse to the same path again).

**Check the target's dimensions before assuming a file fits.** Material sets are usually
built against the Windows client, and the two clients do not always agree.
`plastic/diffuse.dds` is 128x2048 in the macOS client, while a typical painted set ships it
at 560x560 — the single most important colour file in the set, and it simply does not
match.

## Platform differences

Roblox resource root:

* **Windows** — `%LOCALAPPDATA%\Roblox\Versions\<version>\`
* **macOS** — `/Applications/Roblox.app/Contents/Resources/`

Material textures live under `PlatformContent/pc/textures/` on both.

The Windows client ships a folder per material (`wood/`, `grass/`, `brick/`, `marble/`,
`ice/`, `slate/`, `sand/`, `concrete/`, `granite/`, `rust/`, `aluminum/`, `glass/`,
`pebble/`, `cobblestone/`, `diamondplate/`, `woodplanks/`, ...). **macOS ships almost none
of them** — only `studs.dds`, `wangIndex.dds`, `brdfLUT.dds`, `plastic/`, `sky/`, `water/`
and `ui/`. On macOS the rest arrive as TexturePack assets instead. So a 98-file Windows
material pack has a counterpart for 43 files on a Mac, and only 36 of those match by
dimensions.

Fleasion writes new files where the client has none (marking them `.fleasion_new` so it can
remove them on reset), but the macOS client will not read them, so those entries do nothing.
