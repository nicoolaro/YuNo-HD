# Session Handoff 2026-04-22

## Stable State Reached

- HD asset policy helper was added in `src/gfx.c`.
- Confirmed `SD_ONLY` assets so far:
  - `mnwaku`
  - `item`
  - `swaku2`
- Confirmed behavior:
  - `mnwaku`, `item`, and `swaku2` should not be used from `hd_assets` for now.
  - `kabe1` is safe to use as an HD background.
  - Full-screen HD background replacement currently keeps the SD surface intact because later UI composition may still depend on it.

## Important Notes

- Original game assets are still loaded from the archive/decode pipeline first.
- `hd_assets` is only a runtime replacement layer on top of the original engine path.
- `meson.build` only enabled PNG loading via `SDL2_image`; it did not replace the original asset system.

## What Was Tried Today

- Menu asset debugging for:
  - `kabe1`
  - `mnwaku`
  - `item`
  - `swaku2`
- Confirmed that some UI/menu helper assets are not final display images and must remain on the SD/original path.
- Added `HD_RENDER_NOTES.md` to track renderer policy and current asset classifications.

## Open Bug For Next Session

- Main menu / talk-choice menu background fill is still transparent.
- White frame and white text render, but the dark interior fill is missing.
- A global compositor change was tested and reverted because it broke normal scene rendering.
- A global `gfx_fill()` near-black workaround was tested and reverted because it changed normal story text box colors and did not fix the menu.

## Best Next Direction

- Do not change global `gfx_update()` transparency behavior first.
- Investigate the exact menu construction path that produces the dark interior fill.
- Focus on the main menu/talk-choice fill path specifically rather than changing shared renderer behavior again.

## Files Changed During This Session

- `src/gfx.c`
- `HD_RENDER_NOTES.md`

## Suggested Commit Message

`Add HD asset policy and keep menu helper assets on SD path`
