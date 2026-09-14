# ARCADE RETRO RACER — GameMaker Studio 2.3+ Edition
Super Scaler pseudo-3D engine. Dynamic weather. 6 classic cars. Browser/desktop playable via GameMaker's HTML5 export.

## CONTROLS
Up/W accelerate · Down/S brake · Left/Right steer · Space/Shift nitro · Enter confirm · P pause · M mute

## HOW THE SUPER SCALER ENGINE WORKS (see obj_game_Draw.gml)
- SPRITE SCALING: every world item is a flat 2D sprite (tree, coin, traffic car).
  Each item stores a depth z. Per frame:  scale = CAM_DEPTH / (z + CAM_DEPTH).
  z shrinks with speed, so sprites grow rapidly as they approach.
- VANISHING POINT: screenX = VP_X + worldX * ROAD_HALF * scale + curve * (1 - scale)
  screenY = HORIZON_Y + GROUND_Y * scale
  Items are anchored to the vanishing point at the horizon center and move
  OUTWARD from it as they scale up -> the classic Super Scaler rush.
- PARALLAX BACKGROUNDS: sky(0.05x), far mountains(0.15x), near mountains(0.35x),
  snowfield(0.6x), roadside posts/ground(1.0x) scroll at different speeds.
- All sprites are generated at runtime on surfaces (no asset downloads needed).
  Replace spr_* generation with your own art later if desired.
