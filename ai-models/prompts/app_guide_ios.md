# PulseCraft Studio — iOS App Guide

## Screen Layout

The editor is a full-screen 3D canvas with floating glass-panel toolbars:

- **Top bar**: Back (←), Undo (↩), Redo (↪), project title, Help (?), Viewport (eye icon)
- **Scene View**: Full-screen 3D canvas (black background)
- **Left toolbar** (floating, vertical): Multi-select toggle, Move/Rotate/Scale mode buttons
- **Right toolbar** (floating, vertical): Add (+), Object List, Properties, entity action buttons
- **Bottom bar** (floating): Transform slider (when object selected), Timeline transport controls
- **AI button** (floating, bottom-right): Blue-purple circle with sparkles icon

## Selecting Objects

- **Tap** an object in the 3D view — a colored gizmo appears on it
- **Tap empty space** to deselect
- Open **Object List** (list icon in right toolbar) — tap an object name to select it
- **Long press** an object to focus the camera on it
- **Multi-select**: Tap the stacked-rectangles button (top of left toolbar), then tap multiple objects

## Camera Controls

- **1-finger drag** on empty space: orbit camera around the scene center
- **2-finger pinch**: zoom in/out
- **Viewport button** (eye icon, top bar): switch between Perspective, Camera view, or orthogonal views (Top, Bottom, Left, Right, Front, Back)

## Adding Objects

1. Tap the **+** button (top of right toolbar)
2. A popover appears with scrollable cards in sections:
   - **Primitive Shapes**: Plane, Box, Sphere, Cylinder, Cone, Capsule, Pyramid, Torus, Tube
   - **3D Text**: Text geometry
   - **Lights**: Directional, Point (Omni), Spot
3. Tap a card to add that object at the scene center (0, 0, 0)
4. **Import**: Tap "Import File" in the popover toolbar to import a 3D model file

## Transform Tools (Left Toolbar)

Visible when an object is selected. Switch modes:

- **Move** (arrows icon): Colored axis arrows appear
  - Drag **Red** = X axis, **Green** = Y axis (up/down), **Blue** = Z axis
- **Rotate** (circular arrow icon): Colored rotation rings appear
  - Drag a ring to rotate around that axis
- **Scale** (resize icon): Colored scale handles appear
  - Drag a handle to scale along that axis

### Transform Slider (Bottom)

When an object is selected, a **sliding ruler** appears above the timeline:
- Select axis: **X**, **Y**, or **Z** buttons
- Drag the ruler left/right for precise value adjustment
- The current value shows in a badge above the ruler

## Entity Actions (Right Toolbar)

When an object is selected, action buttons appear below the main panel buttons:
- **iPhone** (compact): Single menu button (⋯) containing all actions
- **iPad** (regular): Individual buttons shown:
  - **Duplicate** (overlapping squares icon)
  - **Delete** (trash icon, red) — not available for cameras
  - **Copy Material** (paintbrush icon)
  - **Paste Material** (filled paintbrush icon)

## Property Inspector

Tap the **sliders icon** in the right toolbar to open the property popover:

**Tab picker** (segmented control at top):
- **Node**: Position (X, Y, Z), Rotation (degrees), Scale (X, Y, Z)
- **Attributes**: Geometry-specific parameters (e.g., radius for sphere, width/height/length for box), Light parameters (intensity, color, temperature, shadows), Camera parameters (FOV, depth of field)
- **Material**: Base color (tap color well to pick), Metalness (0–1 slider), Roughness (0–1 slider), Opacity (0–1 slider), Emission color and intensity, Double-sided toggle, Texture slots
- **Scene**: Background color, environment settings

All values update the 3D view in real time as you adjust sliders.

## Timeline & Animation (Bottom Bar)

The bottom glass panel contains playback controls:

- **Play/Pause** (▶/⏸): Preview animation
- **First Frame** (⏮): Jump to frame 0
- **Timeline Ruler**: Scrollable strip with frame markers — tap a frame to jump to it
- **Last Frame** (⏭): Jump to last frame
- **Zoom** (1x/2x/4x/10x): Tap to cycle timeline zoom level
- **Add Frames** (+): Adds 60 frames (1 second) to the timeline

### How to Animate

1. Select an object
2. Scrub to your **start frame** on the timeline
3. Set the object's position/rotation/scale/properties
4. Scrub to your **end frame**
5. Change the properties again
6. Tap **▶** to preview — values interpolate linearly between keyframes
7. Animation runs at **60 fps**. Default: **240 frames (4 seconds)**

## Object List

Tap the **list icon** in the right toolbar:
- Objects grouped by type: **Objects**, **Lights**, **Cameras**, **Other**
- Tap a row to select that entity
- **Swipe right** on a row: Duplicate (blue)
- **Swipe left** on a row: Delete (red) — not available for cameras

## AI Assistant

Tap the **sparkles button** (blue-purple circle, bottom-right corner):
- Chat popover opens with message history
- **Model picker**: Tap current model name to switch models
- **Scene context toggle** (Analyst tier): "Include scene details" checkbox
- Type a message and tap the **send arrow** to chat
- **Settings** (gear icon): Configure API keys and download local models

## Export

Access from project settings:
- **Image**: Exports current frame as PNG
- **Video**: Exports animation as MP4 (HEVC)
- Choose resolution: 480p, 720p, 1080p, 4K
- Optional: Ray Tracer renderer (requires real device, not simulator)

## Undo/Redo

Tap **↩** (undo) or **↪** (redo) in the top bar. Tracks all changes: property edits, object creation/deletion, keyframe changes.
