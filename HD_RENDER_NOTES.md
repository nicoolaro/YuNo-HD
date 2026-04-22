# HD Render Notes

## Current Asset Policy

The HD renderer now treats assets in three categories inside `src/gfx.c`:

- `HD_ASSET_REPLACE`
  - Replace the original draw with the HD PNG.
  - After injection, clear the corresponding SD region so the original image does not show through.

- `HD_ASSET_REPLACE_KEEP_SD`
  - Replace the final on-screen image with the HD PNG.
  - Keep the original SD pixels on the surface because later engine UI/composition logic may still need them.
  - Current practical use: full-screen `640x400` assets such as background images.

- `HD_ASSET_SD_ONLY`
  - Do not inject HD directly.
  - Let the original engine path render the asset in SD.
  - Current known examples: `mnwaku`, `item`, and `swaku2`, which appear to be menu/UI construction assets rather than final display images.

## Why This Exists

The engine does not treat every graphic as a final image. Some assets are used as source material for later copy/compose operations.

Two important examples discovered during debugging:

- `kabe1`
  - Safe to use as an HD background.
  - The SD surface should remain available for later UI composition.

- `mnwaku`
  - Not a normal display asset.
  - Raw HD injection shows the helper/template graphic directly and breaks the menu.
  - For now it must stay on the original SD path.

- `item`
  - UI/menu construction asset, not a normal standalone HD display image.
  - Should remain on the original SD path for now.

- `swaku2`
  - Likely another UI/helper asset based on prior testing and removal history.
  - Should remain on the original SD path for now.

## Changes Made In This Pass

- Extracted the HD-vs-SD decision into a named helper in `src/gfx.c`.
- Replaced inline special-case logic with an asset policy enum.
- Kept current working behavior:
  - `mnwaku`, `item`, and `swaku2` remain SD-only
  - full-screen HD assets keep the SD surface intact
  - same-path dedup remains enabled for HD layers

## Next Cleanup Candidates

- Expand asset classification beyond hardcoded one-offs.
- Add a small whitelist/blacklist or table-driven asset policy list.
- Reduce repeated PNG reloads when redrawing `hd_canvas`.
- Separate HD presentation logic from original engine source-surface logic.
