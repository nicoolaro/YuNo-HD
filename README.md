# Ever17-HD

Ever17 HD (SDL2 Modernization Project)
Project Overview
This project is a technical reverse-engineering effort to modernize the 2002 Japanese visual novel Ever17: The Out of Infinity. The goal is to replace the original 640x480 assets with high-definition upscaled versions (PNG) and ensure compatibility with modern systems and translation layers like Winlator.

What We’ve Accomplished So Far
Engine Hijacking: Successfully intercepted the original SDLC to redirect the game from loading legacy .dat assets to modern PNGs from a local /hd_assets directory.

SDL2 Rendering Pipeline: Implemented a new rendering path using SDL_Texture to support hardware acceleration.

Targeted Resolution Support: Optimized the game for 1280x720, making it ideal for handheld play and mobile emulation (Winlator).

Input Management: Added modern shortcuts, including an ESC key exit prompt to prevent accidental closures and a custom F11 toggle.

Build System: Migrated the project to a lightweight, fast Ninja build system with C11 standards.

Next Tasks (Backlog)
[ ] Fix HD Context Loss: Resolve the issue where the HD layer fails to redraw after a window mode change (F11/Minimize).

[ ] Asset Manager Automation: Create a tool to automate the extraction and naming of original frames to match the hd_assets/ structure.

[ ] UI Upscaling: Move beyond background CGs to upscale text boxes and menu elements.

[ ] Winlator Optimization: Fine-tune the SDL window flags to prevent the "1cm window" bug on Android window managers.

[ ] Logic Decoupling: Clean up src/gfx.c to separate the original engine calls from our HD injection logic.

Features & Goals
HD Texture Injection: High-fidelity backgrounds without modifying the original game's internal data files.

Stable Fullscreen: Borderless windowed mode for smooth transitions.

Portable Design: Minimal dependencies, easy to compile on MSYS2/MinGW environments.

## What's done
- 

## Next steps
-