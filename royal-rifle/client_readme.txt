==========================================================
  ROYAL RIFLE — assault rifle model for Rivals (Fleasion)  v1.1
==========================================================

----------------------------------------------------------
WHAT THIS PACK CHANGES
----------------------------------------------------------
  MODEL     — the assault rifle body is replaced with the royal rifle,
              gold with diamond-blue. Every other stock part of the gun
              is removed so nothing pokes through the new model.

  MAGAZINE  — shipped as its own mesh on purpose: the magazine is an
              animated part in Rivals, so it drops out and slots back in
              during the reload instead of staying glued to the body.

  COLOUR    — please read this bit. Rivals guns have no texture of their
              own: the game paints each part a flat colour. The colour is
              baked into the mesh itself and is MULTIPLIED by whatever
              colour the equipped wrap gives the part:
                • light wrap  -> gold and diamond read at full strength
                • black wrap  -> everything multiplies down to a silhouette
              Use a light wrap to see the pack as intended.

  SOUNDS    — the assault rifle borrows the Akey-47 skin's sounds. No
              files are shipped for this: the rules point the stock
              sounds at the game's own Akey-47 ones.
                • shoot  -> Akey-47 shoot (the third of its three)
                • equip  -> Akey-47 equip
                • bolt   -> the extra sound Akey-47 layers into its
                            reload and inspect
              Two notes. The equip and bolt sounds are shared with other
              weapons, so you will hear the new ones there too. And the
              Akey-47 magazine sounds are the same files the stock rifle
              already uses, so those are unchanged by design — the skin
              adds layers on top rather than replacing them, and layers
              cannot be added this way.

  Nothing else is touched: no animations, no UI.

----------------------------------------------------------
HOW TO IMPORT (Fleasion)
----------------------------------------------------------
  1. Open Fleasion.
  2. Import / Add config  ->  select the file:
        royal_rifle_V1.1.json
  3. Make sure the config is ENABLED (toggle on).
  4. Everything streams from the cloud (CDN) — no extra files to place,
     you don't need anything except the .json.

----------------------------------------------------------
IMPORTANT: CLEAR THE ROBLOX CACHE BEFORE TESTING
----------------------------------------------------------
  Roblox caches assets on disk. If you skip this you may still see the
  OLD model and think the pack didn't work.

  1. Fully CLOSE Roblox (quit completely, not just the window).
  2. In Fleasion, remove any older/previous imports of this pack.
  3. Enable "Clear Cache on Launch" (or clear the Roblox cache by hand),
     then launch.
  4. Take the assault rifle and check the model and the reload.

----------------------------------------------------------
HEADS-UP: GAME UPDATES
----------------------------------------------------------
  Rivals sometimes changes the internal IDs of its assets when the game
  updates. If that happens, part of this pack may stop applying. That is
  NOT a broken pack — the IDs just moved. Message me and I'll patch the
  affected IDs quickly.

----------------------------------------------------------
  Enjoy!  — questions / fixes: just reach out.
==========================================================
