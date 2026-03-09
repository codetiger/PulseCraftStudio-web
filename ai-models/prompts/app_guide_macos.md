# PulseCraft Studio — macOS App Guide

## Window Layout

The editor has a **three-panel layout**:

- **Top navigation bar** (44pt): Back (←), Undo (⌘Z), Redo (⇧⌘Z), project title, Viewport (eye icon)
- **Scene View** (left, flexible width): 3D canvas with floating transform and timeline controls
- **Resize handle** (center divider): Drag to resize sidebar (260–600pt)
- **Right sidebar** (320pt default): Objects list, action buttons, tabbed Properties/AI panel

## Right Sidebar (Top to Bottom)

1. **"Objects" header** (gray section label)
2. **Action buttons row**:
   - **Add** button (blue, prominent) — opens AddObject popover (480×400pt)
   - When object selected: **Duplicate**, **Delete** (red), **Copy Material**, **Paste Material**
3. **Divider**
4. **Object List** (scrollable, max 200pt height)
   - Grouped sections: Objects, Lights, Cameras, Other
   - Click a row to select that entity
   - Selected row highlighted with accent color
5. **Divider**
6. **Tab picker** (segmented): "Properties" | "AI Assistant"
7. **Divider**
8. **Tab content** (fills remaining space):
   - **Properties tab**: NodePropertyView — transform, attributes, material, scene settings
   - **AI Assistant tab**: PCSChatView embedded in sidebar

## Selecting Objects

- **Click** an object in the 3D view — a colored gizmo appears
- **Click empty space** to deselect
- **Click** an object name in the **Object List** (right sidebar)
- **Long click** an object to focus the camera on it
- **Multi-select**: Click the stacked-rectangles button (left toolbar), then click multiple objects

## Camera Controls

- **Click + drag** on empty space: orbit camera
- **Scroll wheel** or **trackpad pinch**: zoom in/out
- **Option + drag**: pan camera
- **Viewport button** (eye icon, top bar): switch to Perspective, Camera view, or orthogonal views (Top, Bottom, Left, Right, Front, Back)

## Adding Objects

1. Click the **Add** button (blue) in the sidebar action row
2. A popover (480×400pt) appears with scrollable cards:
   - **Primitive Shapes**: Plane, Box, Sphere, Cylinder, Cone, Capsule, Pyramid, Torus, Tube
   - **3D Text**: Text geometry
   - **Lights**: Directional, Point (Omni), Spot
3. Click a card to add that object at the scene center (0, 0, 0)
4. **Import**: Click "Import File" in the popover toolbar to import a 3D model file

## Transform Tools (Floating, Left of Scene)

Visible when an object is selected. Switch modes:

- **Move** (arrows icon): Colored axis arrows appear
  - Drag **Red** = X axis, **Green** = Y axis (up/down), **Blue** = Z axis
- **Rotate** (circular arrow icon): Colored rotation rings appear
  - Drag a ring to rotate around that axis
- **Scale** (resize icon): Colored scale handles appear
  - Drag a handle to scale along that axis

### Transform Slider (Bottom of Scene)

When an object is selected, a **sliding ruler** appears above the timeline:
- Select axis: **X**, **Y**, or **Z** buttons
- Drag the ruler left/right for precise value adjustment
- The current value shows in a badge above the ruler

## Property Inspector (Sidebar → Properties Tab)

**Tab picker** (segmented control at top):
- **Node**: Position (X, Y, Z), Rotation (degrees), Scale (X, Y, Z)
- **Attributes**: Geometry parameters (e.g., radius for sphere, width/height/length for box), Light parameters (intensity, color, temperature, shadows), Camera parameters (FOV, depth of field)
- **Material**: Base color (click color well), Metalness (0–1), Roughness (0–1), Opacity (0–1), Emission color/intensity, Double-sided toggle, Texture slots. Includes a live material preview sphere at the top.
- **Scene**: Background color, environment settings

Values update in real time. Properties display is compact (12pt font, 32pt row height).

**Multi-select**: When multiple objects are selected, values shown are from the first object. Changes apply to all selected objects.

## Timeline & Animation (Bottom of Scene)

The bottom glass panel contains playback controls:

- **Play/Pause** (▶/⏸): Preview animation
- **First Frame** (⏮): Jump to frame 0
- **Timeline Ruler**: Scrollable strip with frame markers — click a frame to jump to it
- **Last Frame** (⏭): Jump to last frame
- **Zoom** (1x/2x/4x/10x): Click to cycle timeline zoom level
- **Add Frames** (+): Adds 60 frames (1 second) to the timeline

### How to Animate

1. Select an object
2. Scrub to your **start frame** on the timeline
3. Set the object's position/rotation/scale/properties
4. Scrub to your **end frame**
5. Change the properties again
6. Click **▶** to preview — values interpolate linearly between keyframes
7. Animation runs at **60 fps**. Default: **240 frames (4 seconds)**

## AI Assistant (Sidebar → AI Assistant Tab)

Switch to the **AI Assistant** tab in the sidebar:
- Chat interface embedded in the sidebar
- **Model picker**: Click current model name to switch models
- **Scene context toggle** (Analyst tier): "Include scene details" checkbox
- Type a message and click the **send arrow** to chat
- **Settings** (gear icon): Configure API keys and download local models
- **Clear history** (trash icon): Remove chat messages

## Export

Access from the project card context menu or Actions panel:
- **Image**: Exports current frame as PNG
- **Video**: Exports animation as MP4 (HEVC)
- Choose resolution: 480p, 720p, 1080p, 4K
- Optional: Ray Tracer renderer
- Export window: min 800×560pt, responsive layout

## Keyboard Shortcuts

- **⌘Z**: Undo
- **⇧⌘Z**: Redo

## Undo/Redo

Click **↩** (undo) or **↪** (redo) in the top bar, or use keyboard shortcuts. Tracks all changes: property edits, object creation/deletion, keyframe changes.
