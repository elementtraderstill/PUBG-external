# dx11-overlay

DX11 overlay project. External process, user-mode only, no injection.

<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/1b3d8026-a410-4e9a-98db-53b5f4265b20" />

<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/337a3f3f-1613-40ee-9cfb-4c9618e1eba7" />


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

