# Workflows — macOS

## Create a Metallic Gold Sphere

1. Click the **Add** button (blue) in the sidebar action row
2. In the popover, under **Primitive Shapes**, click the **Sphere** card
3. The sphere appears at center and is auto-selected
4. In the **right sidebar**, ensure the **Properties** tab is selected
5. Switch to the **Material** tab in the segmented picker
6. Click the **Base Color** well → pick gold (#FFD700)
7. Drag **Metalness** slider to **1.0**
8. Drag **Roughness** slider to **0.3**

## Set Up Three-Point Lighting

1. Click **Add** → **Lights** → click **Directional** (key light)
2. In sidebar **Properties** → **Attributes** tab → set **Intensity** to **2000**, enable **Cast Shadows**
3. Switch to **Move** mode (floating left toolbar) → drag the **green arrow** up to Y ≈ 3
4. Switch to **Rotate** mode → tilt light downward by dragging the **red ring**
5. Click **Add** → **Lights** → click **Point** (fill light)
6. In **Attributes** → set **Intensity** to **500**
7. Move it to the opposite side (drag **red arrow** to negative X)
8. Click **Add** → **Lights** → click **Directional** (rim light)
9. Set **Intensity** to **1000**, position behind and above the subject

## Animate an Object Moving Across the Scene

1. Click your object in the 3D view or in the **Object List** to select it
2. In the **bottom timeline**, scrub to **frame 0**
3. Switch to **Move** mode (floating left toolbar) → position the object at the start
4. Scrub to **frame 120** (2 seconds at 60fps)
5. Drag the object to the end position
6. Click **▶** to preview — it moves smoothly between the two positions
7. To add more frames: click **+** next to the timeline zoom button

## Create a Spinning Cube

1. Click **Add** → **Primitive Shapes** → **Box**
2. Scrub timeline to **frame 0**
3. In sidebar **Properties** → **Node** tab → note Rotation Y = 0°
4. Scrub to **frame 120** (2 seconds)
5. Set Rotation **Y** to **360°**
6. Click **▶** — the cube spins a full revolution

## Resize a Shape with Geometry Parameters

1. Select the object (click in scene or Object List)
2. In sidebar **Properties** → switch to **Attributes** tab
3. Adjust the geometry parameters (type values or use sliders):
   - **Box**: width, height, length, chamferRadius
   - **Sphere**: radius
   - **Cylinder**: radius, height
   - **Torus**: ringRadius (donut size), pipeRadius (tube thickness)
   - **Cone**: topRadius, bottomRadius, height
4. Changes apply instantly in the 3D view

## Make Glass-Like Material

1. Select the object → in sidebar **Properties** → **Material** tab
2. The live preview sphere at top shows your material
3. Set **Base Color** to white (#FFFFFF)
4. Drag **Metalness** to **0.0**
5. Drag **Roughness** to **0.0**
6. Drag **Opacity** to **0.3** (partially see-through)
7. For more realism: enable **Double Sided** toggle
8. Watch the preview sphere update in real time

## Add a Spotlight with Shadows

1. Click **Add** → **Lights** → **Spot**
2. Switch to **Move** mode → drag it above your target (green arrow up)
3. Switch to **Rotate** mode → angle the light downward (drag red ring)
4. In sidebar **Properties** → **Attributes** tab:
   - Set **Intensity** to **3000**
   - Set **Outer Angle** to control the cone spread (e.g., 45°)
   - Set **Inner Angle** for the bright center (e.g., 20°)
   - Enable **Cast Shadows**
   - Adjust **Shadow Radius** for soft/hard shadows

## Duplicate and Arrange Objects

1. Select an object in the 3D view or Object List
2. Click the **Duplicate** button (overlapping squares) in the sidebar action row
3. The copy appears at the same position — switch to **Move** mode and drag it
4. Repeat to create arrangements (rows, circles, etc.)

## Use Multi-Select

1. Click the **stacked rectangles** button (top of floating left toolbar) — it highlights when active
2. Click objects one by one to add them to the selection
3. Use transform tools to move/rotate/scale all selected objects together
4. In sidebar **Properties** — changes apply to all selected objects (values shown from first object)
5. Click the multi-select button again to exit multi-select mode

## Resize the Sidebar

- Hover over the **divider** between the scene and sidebar — cursor changes to resize
- **Drag left** to make the sidebar wider (max 600pt)
- **Drag right** to make it narrower (min 260pt)

## Switch Viewport

- Click the **eye icon** in the top navigation bar
- Choose: Perspective (default 3D), Camera (through scene camera), or orthogonal views
- Use **Option + drag** to pan the camera instead of orbiting

## Keyboard Shortcuts

- **⌘Z**: Undo
- **⇧⌘Z**: Redo
