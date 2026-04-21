# YUNO-HD 🌊

**YU-NO HD** is a technical reverse-engineering project dedicated to modernizing the 2002 Japanese visual novel *YU-NO: A Girl Who Chants Love at the Bound of this World*. 

The primary objective is to bypass legacy engine limitations, replacing original 640x480 assets with high-definition upscaled PNGs while ensuring flawless compatibility with modern hardware and translation layers like Winlator.

---

## ✨ Key Features
*   **HD Texture Injection:** High-fidelity backgrounds rendered without modifying internal game data files.
*   **Modern Rendering:** Replaced the legacy pipeline with an `SDL_Texture` based path for hardware acceleration.
*   **Targeted Resolution:** Optimized for 1280x720—perfect for handhelds and mobile emulation.
*   **Enhanced Input:** Added modern shortcuts, including an `ESC` exit prompt and `F11` fullscreen toggle.
*   **Portable Design:** Minimal dependencies, optimized for MSYS2/MinGW environments.

## 🛠 Technical Stack
*   **Language:** C11
*   **Graphics:** SDL2 (Hardware Accelerated)
*   **Build System:** Ninja
*   **Environment:** MSYS2 / MinGW-w64

---

## 📊 Project Status

### Accomplished
- [x] **Engine Hijacking:** Intercepted SDLC to redirect asset loading from `.dat` to `/hd_assets`.
- [x] **SDL2 Pipeline:** Full implementation of hardware-accelerated rendering.
- [x] **Stable Fullscreen:** Borderless windowed mode via `F11`.
- [x] **HD Canvas Fix:** Resolved context loss issues during window resizing/minimizing.
- [x] **HD Backgrounds:** Successfully rendering high-resolution assets.

### Current Focus
- [ ] **Popup Menu Transparency:** Fixing alpha blending issues in the menu system.
- [ ] **UI Boundaries:** Addressing black borders in the left/right UI zones.
- [ ] **Menu Backgrounds:** Implementing HD replacements for system menus.

---

## 🗺 Roadmap & Backlog

### Development
- [ ] **Logic Decoupling:** Refactor `src/gfx.c` to separate original engine calls from HD injection logic.
- [ ] **Winlator Optimization:** Fine-tune SDL window flags to fix the "1cm window" bug on Android.
- [ ] **Toggle System:** Add a real-time switch to toggle between original and HD assets.

### Assets & UI
- [ ] **Asset Manager Automation:** Create a tool to automate extraction/naming of original frames.
- [ ] **UI Upscaling:** Extend support beyond CGs to text boxes and menu elements.
- [ ] **Typography:** Implement modern font support or improve current font rendering.

---

## 🚀 Building
The project uses the Ninja build system for speed and simplicity.
```bash
# Example build command (MSYS2)
ninja
```