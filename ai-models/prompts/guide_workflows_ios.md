# Workflows — iOS

## Create a Metallic Gold Sphere

1. Tap **+** (top of right toolbar)
2. Under **Primitive Shapes**, tap the **Sphere** card
3. The sphere appears at center and is auto-selected
4. Tap the **sliders icon** (right toolbar) to open Properties
5. Switch to the **Material** tab
6. Tap the **Base Color** well → pick gold (#FFD700)
7. Drag **Metalness** slider to **1.0**
8. Drag **Roughness** slider to **0.3**

## Set Up Three-Point Lighting

1. Tap **+** → **Lights** → tap **Directional** (key light)
2. Tap **sliders icon** → **Attributes** tab → set **Intensity** to **2000**, enable **Cast Shadows**
3. Switch to **Move** mode (left toolbar) → drag the **green arrow** up to Y ≈ 3
4. Switch to **Rotate** mode → tilt light downward by dragging the **red ring**
5. Tap **+** → **Lights** → tap **Point** (fill light)
6. In Properties → **Attributes** → set **Intensity** to **500**
7. Move it to the opposite side of the scene (drag **red arrow** to negative X)
8. Tap **+** → **Lights** → tap **Directional** (rim light)
9. Set **Intensity** to **1000**, position behind and above the subject

## Animate an Object Moving Across the Scene

1. Tap your object in the 3D view to select it
2. In the **bottom timeline**, scrub to **frame 0**
3. Switch to **Move** mode (left toolbar) → position the object at the start
4. Scrub to **frame 120** (2 seconds at 60fps)
5. Drag the object to the end position
6. Tap **▶** to preview — it moves smoothly between the two positions
7. To add more frames: tap **+** next to the timeline zoom button

## Create a Spinning Cube

1. Tap **+** → **Primitive Shapes** → **Box**
2. Scrub timeline to **frame 0**
3. Open Properties → **Node** tab → note Rotation Y = 0°
4. Scrub to **frame 120** (2 seconds)
5. In **Node** tab → set Rotation **Y** to **360°**
6. Tap **▶** — the cube spins a full revolution

## Resize a Shape with Geometry Parameters

1. Select the object
2. Tap **sliders icon** (right toolbar) → switch to **Attributes** tab
3. Adjust the geometry sliders:
   - **Box**: width, height, length, chamferRadius
   - **Sphere**: radius
   - **Cylinder**: radius, height
   - **Torus**: ringRadius (donut size), pipeRadius (tube thickness)
   - **Cone**: topRadius, bottomRadius, height
4. Changes apply instantly in the 3D view

## Make Glass-Like Material

1. Select the object → open Properties → **Material** tab
2. Set **Base Color** to white (#FFFFFF)
3. Drag **Metalness** to **0.0**
4. Drag **Roughness** to **0.0**
5. Drag **Opacity** to **0.3** (partially see-through)
6. For more realism: enable **Double Sided** toggle

## Add a Spotlight with Shadows

1. Tap **+** → **Lights** → **Spot**
2. Switch to **Move** mode → drag it above your target (green arrow up)
3. Switch to **Rotate** mode → angle the light downward (drag red ring)
4. Open Properties → **Attributes** tab:
   - Set **Intensity** to **3000**
   - Set **Outer Angle** to control the cone spread (e.g., 45°)
   - Set **Inner Angle** for the bright center (e.g., 20°)
   - Enable **Cast Shadows**
   - Adjust **Shadow Radius** for soft/hard shadows

## Duplicate and Arrange Objects

1. Select an object
2. **iPhone**: Tap the **⋯** menu (right toolbar) → **Duplicate**
3. **iPad**: Tap the **overlapping squares** button (right toolbar)
4. The copy appears at the same position — switch to **Move** mode and drag it
5. Repeat to create arrangements (rows, circles, etc.)
6. Alternatively: open **Object List**, swipe right on an item, tap **Duplicate**

## Use Multi-Select

1. Tap the **stacked rectangles** button (top of left toolbar) — it highlights when active
2. Tap objects one by one to add them to the selection
3. Use transform tools to move/rotate/scale all selected objects together
4. Open Properties — changes apply to all selected objects
5. Tap the multi-select button again to exit multi-select mode
