==========================================================
  boy / moon808132 — STANDARD PACK for Rivals (Fleasion)  v1.5
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
             assault rifle. The shoot sound is trimmed to fit inside the
             original clip and brought down to 56% of its volume.
             The two magazine sounds are shipped at FULL length, which is
             longer than the clips they replace — if either one ends up
             cut short or silent in game, say so and I'll ship the
             trimmed versions instead (they're ready).
             The sniper's bolt-back sound is removed — as agreed, this
             also silences it on the sniper itself.

  ANIMS    — equip, sprint, reload and inspect come from the Event
             Horizon set. IDLE and SHOOT are deliberately left stock:
             both were posed for the sniper, and on the rifle the idle
             held the gun up and away from the camera while the shoot
             kicked the barrel far too hard. With the stock idle the
             model sits in the hand the way it should.
             If any of the four still looks off, tell me which and I'll
             switch that single rule back — the others keep working.

  ICONS    — weapon, level and streak icons.
             The game multiplies UI icons by its own tint, so the colour
             is picked for what it becomes on screen, not for how the
             file looks: the level icon is blue (a yellow one came out
             green against the game's blue tint), the streak icon keeps
             the warm gradient.

  Not included in this build (agreed): watermark, skybox, other UI.

----------------------------------------------------------
HOW TO IMPORT (Fleasion)
----------------------------------------------------------
  1. Open Fleasion.
  2. Import / Add config  ->  select the file:
        boy_Standard_V1.5.json
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
