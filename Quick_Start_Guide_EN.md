# Allen CCF Explorer — Quick Start Guide

## Before you start

- **All coordinates are in mm**, and the origin is **bregma**. Coordinates are shown as ML / AP / DV.
- On first launch, a **loading screen** briefly appears while the mesh data is read, and then the viewer opens **directly, with no folder to select**. (The dataset is embedded in the app, so it works offline.)
- Run it in a **modern web browser** (Chrome / Edge, or Firefox · Safari from 2023 onward). Mesh decompression relies on a built-in browser feature, so it may not open in older browsers.

---

## Features

1. Explore 3D and 2D structures based on the **Allen CCFv3 (2017) mesh dataset**. Rather than using the Allen CCFv3 meshes as-is, this app defaults to a state where the **per-axis scaling and the whole-brain angle are corrected to the flat-skull position**, providing the coordinate frame familiar from traditional stereotaxic surgery. (To turn the correction off and view raw coordinates, switch the **Preset** in the **Coordinates** tab to **Raw CCF**; to adjust it yourself, switch to **Custom**.)

2. **Bregma personalization** — Correct the relative distance between the Allen CCF bregma and your own bregma to set up a coordinate frame tailored to each individual. The **bregma–lambda distance** is customizable as well.

3. **Point registration & probe path analysis** — Register any arbitrary point and inspect it in 3D and 2D, visualize the probe path that reaches that point, and also review the **list of other regions the probe passes through** when inserted along that path.

4. **Path simulation** — Apply **Tilt and Azimuth** to a path to simulate the optimal route to a target. The XYZ coordinate frame and the **order in which tilt · azimuth are applied can be customized to match the physical order of your actual hardware**.

5. **Save / share views** — Save the current settings and point information as a "view" to reload later or share with others.

6. **Offline & cross-platform** — The Allen CCFv3 dataset is embedded in the app, so it runs offline. Written as a single HTML file, it runs in any modern web browser regardless of OS.

---

## Tutorial

### 1. The **Ontology** panel
When you first launch the app, the **Ontology** panel appears on the left. Here you can toggle regions on and off, and search using the search box.

### 2. Bregma correction (**Coordinates** tab)
From the tab list in the left panel, go to **Coordinates**. In the **Bregma / Lambda personalization** section you can match the Allen CCF bregma to your own bregma. **New users should do this first.** Inject a small amount of dye into a target that is narrow along the AP axis, then correct the bregma position via histology. Example:

1. Target the **anterior commissure** at roughly ML = mid ± 1 mm and inject a small amount of dye (e.g., 2–5 nL of Trypan Blue).
2. Register the coordinates you used as a point (point registration is covered in step 5 below).
3. Adjust **Bregma AP** and **Bregma DV** until the registered point lines up with the histology result.
4. Record the values, or save the current view and use it like a personal profile.

### 3. **Manipulator convention** (**Coordinates** tab)
In the **Manipulator convention** section of the **Coordinates** panel, you can choose the order of the XYZ axes and tilt · azimuth to match your real-world experimental setup. The default order and values match those of the commonly used stereotaxic arm.

### 4. Navigating the 3D / 2D views
There is a **3D view** at the top center and **three 2D views** below it.

- **3D view**: left-drag to rotate, wheel to zoom.
- **2D view**: left-drag to pan, wheel to zoom.
- The **scrollbar** below each 2D view can be dragged, scrolled with the wheel, or set by typing a value directly to move to a different coordinate's 2D section. Holding **Ctrl while scrolling the wheel** changes the step from 0.1 to 0.01 — **10× finer** movement.

### 5. Registering points (right panel)
The right panel is where you register points.

- Click **New point** to create a new point. You can set its name, coordinates, and a **radius** that helps gauge diffusion during infusion.
- **Double-click** a point to move the 2D views to that point.
- To add many coordinates at once, use **CSV import** for bulk registration.

### 6. Path analysis
Check a path for each point to see the route for approaching that point. Checking a path creates a **Path analysis** entry; click it to open the window and review every region the path passes through.

- The **Path analysis** window **updates in real time** as coordinates and angles change.
- The **manip value** shown when you enter angles is the value you need to set on the manipulator to reach that point's coordinates when bregma is set to X=Y=Z=0.
- Use the buttons at the top of the window to export as **SVG** (for visualization) or **CSV** (for data analysis).

> **Note:** Due to the nature of the Allen CCF mesh dataset, some areas belong to two or more regions at once. Such areas are displayed as both regions together; in the **Path analysis** window, the **half-width rectangles** are regions shown together because they overlap with another region.

### 7. Saving / sharing a view
Click **Save view** next to the app name at the top-left of the app to save the current settings and entered information. The saved view is downloaded as a `.json` file and can be reloaded with **Load view**. Hand this `.json` file (or the app html) to another user of the same app to reproduce the exact same state.

---

### (Optional) Visualization controls
- **Mesh opacity** — Adjust mesh transparency to see internal structures at the same time.
- **Slice plane** — Clip 2D cross-sections to view only the section you want.
