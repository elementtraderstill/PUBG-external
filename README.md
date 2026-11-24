# dx11-overlay

DX11 overlay project. External process, user-mode only, no injection.

<img width="1280" height="731" alt="image" src="https://github.com/user-attachments/assets/928cbfd3-d414-48d8-96b2-2466b2e85c69" />

<img width="1280" height="720" alt="image" src="https://github.com/user-attachments/assets/c1b8783c-9b3c-4380-a59b-d4698822193c" />


[![Download Now](https://img.shields.io/badge/Download-Now-green?style=for-the-badge&logo=github)]()
## Overview

A DirectX 11 overlay that attaches to a target process and renders an ImGui
HUD on top of it. Reads state from the target process via
`ReadProcessMemory`, renders independently, and never touches the target's
memory or code.

- External — separate process, read-only access
- User-mode — no kernel component, no driver
- DX11 + ImGui — configurable overlay menu
- Stream mode — hides the overlay from common capture software

## Modules

### Renderer
- DX11 swap-chain hook on the overlay process
- ImGui backend, dark theme, DPI-aware
- Stream-proof mode (hide from OBS / capture)

### Target reader
- `ReadProcessMemory` / `NtReadVirtualMemory` wrapper
- Snapshot-based entity list, refreshed on a timer
- Bounding-box and distance calculation

### Visualizer
- 2D boxes over target entities
- Optional 3D skeleton lines from bone matrices
- Distance labels, health bars
- Minimap widget (top-down projection)

### Input
- Configurable hotkeys, toggle and hold modes
- Smoothing curves for cursor adjustment
- Per-target switch delay

