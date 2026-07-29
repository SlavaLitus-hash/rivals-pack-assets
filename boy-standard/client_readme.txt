==========================================================
  boy / moon808132 — STANDARD PACK for Rivals (Fleasion)  v1.2
==========================================================

Thanks for your order! This pack re-skins the ASSAULT RIFLE and swaps
two UI icons. Nothing else in the game is touched.

----------------------------------------------------------
WHAT THIS PACK CHANGES
----------------------------------------------------------
  MODEL    — your own mesh replaces the assault rifle body. Every other
             stock part of the gun is removed so only your model shows.
             The mesh ships at the exact bounding box of the part it
             replaces, so the game has nothing to stretch — the gun keeps
             your proportions.

             COLOUR — please read this bit. Rivals guns have no texture
             of their own: the game paints each part a flat colour. So
             the colour is baked into the mesh itself, face by face, from
             your atlas. That colour is MULTIPLIED by whatever colour the
             equipped wrap gives the part:
               • light wrap  -> the lava reads at full strength
               • black wrap  -> everything multiplies down to a silhouette
             Use a light wrap to see the pack as intended. The black areas
             are true 0,0,0 so they swallow as much light as this route
             allows; a highlight can still catch them, because the surface
             material belongs to the game and cannot be swapped.

  SOUNDS   — Event Horizon shoot / magazine out / magazine in on the
             assault rifle. All three are trimmed to fit inside the
             original clip lengths (Rivals cuts or mutes anything
             longer). The shoot sound is also brought down to 56% of the original.
             The sniper's bolt-back sound is removed — as agreed, this
             also silences it on the sniper itself.

  ANIMS    — equip, idle, sprint, reload, inspect and shoot are swapped
             for the Event Horizon set.
             Heads-up: those animations were authored for the sniper,
             whose timings differ from the assault rifle (the AR shot
             is ~0.17 s against a full bolt cycle). Some of them may
             look off or cut short. Tell me which ones and I'll turn
             those single rules off — the rest keep working.

  ICONS    — level and streak icons in the pack's yellow gradient.

  Not included in this build (agreed): watermark, skybox, other UI.

----------------------------------------------------------
HOW TO IMPORT (Fleasion)
----------------------------------------------------------
  1. Open Fleasion.
  2. Import / Add config  ->  select the file:
        boy_Standard_V1.2.json
  3. Make sure the config is ENABLED (toggle on).
  4. Everything streams from the cloud (CDN) — no extra files to place,
     you don't need anything except the .json.

----------------------------------------------------------
IMPORTANT: CLEAR THE ROBLOX CACHE BEFORE TESTING
----------------------------------------------------------
  Roblox caches assets on disk. If you skip this you may still see and
  hear the OLD assets and think the pack didn't work.

  1. Fully CLOSE Roblox (quit completely, not just the window).
  2. In Fleasion, remove any older/previous imports of this pack.
  3. Enable "Clear Cache on Launch" (or clear the Roblox cache by hand),
     then launch.
  4. Take the assault rifle and check the model, sounds and animations.

  "Nothing changed" almost always means a stale cache.

----------------------------------------------------------
HEADS-UP: GAME UPDATES
----------------------------------------------------------
  Rivals sometimes changes the internal IDs of its assets when the game
  updates. If that happens, a part of this pack may stop applying. That
  is NOT a broken pack — the IDs just moved. Message me and I'll patch
  the affected IDs quickly.

----------------------------------------------------------
  Enjoy!  — questions / fixes: just reach out.
==========================================================
