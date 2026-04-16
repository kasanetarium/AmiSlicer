# AmiSlicer

> ⚠️ **Alpha Release (v0.01)** — This software is in early development.

---

## Table of Contents

- [AmiSlicer](#amislicer)
  - [Table of Contents](#table-of-contents)
  - [1. What is AmiSlicer](#1-what-is-amislicer)
    - [Key Features](#key-features)
  - [2. Installation](#2-installation)
    - [System Requirements](#system-requirements)
  - [3. Basic Workflow](#3-basic-workflow)
  - [4. UI Overview](#4-ui-overview)
  - [5. Detailed Usage](#5-detailed-usage)
    - [5.1 Loading STL](#51-loading-stl)
    - [5.2 Model Rotation](#52-model-rotation)
    - [5.3 Printer Settings](#53-printer-settings)
      - [5.3.1 Machine Tab](#531-machine-tab)
      - [5.3.2 Print Tab](#532-print-tab)
    - [5.4 Wave Tab](#54-wave-tab)
      - [5.4.1 Wave Settings](#541-wave-settings)
      - [5.4.2 Bottom Settings](#542-bottom-settings)
  - [6. Preview](#6-preview)
    - [6.1 2D Preview](#61-2d-preview)
    - [6.2 3D Preview](#62-3d-preview)
  - [7. Detecting and Fixing Self-Intersections](#7-detecting-and-fixing-self-intersections)
    - [7.1 Detection](#71-detection)
    - [7.2 Fix Procedure](#72-fix-procedure)
    - [7.3 Warning When Saving G-code](#73-warning-when-saving-g-code)
  - [8. Saving G-code](#8-saving-g-code)
  - [9. Saving and Loading Settings](#9-saving-and-loading-settings)
    - [9.1 Save](#91-save)
    - [9.2 Load](#92-load)
    - [9.3 Default Settings](#93-default-settings)
  - [10. G-code Preview](#10-g-code-preview)
  - [11. Keyboard Shortcuts](#11-keyboard-shortcuts)
  - [12. Troubleshooting](#12-troubleshooting)
    - [Empty Preview](#empty-preview)
    - [Cannot Fix Self-Intersections](#cannot-fix-self-intersections)
  - [13. Notes](#13-notes)
  - [14. Safety Notice](#14-safety-notice)
  - [15. License](#15-license)

---

## 1. What is AmiSlicer

AmiSlicer is a desktop application that loads STL files and generates G-code by applying sinusoidal deformation to perimeters. It can create 3D printed objects with a unique woven-like surface texture.

<img src="img/soroban_git.jpg" width="50%" alt="soroban">

### Key Features

* **STL slicing** — Slice STL meshes layer by layer
* **Wave generation** — Generate waves on perimeters with freely adjustable amplitude and wave count
* **Alternating phase inversion** — Invert the phase by 180° between layers to create a woven pattern
* **Z-direction modulation** — Generate waves in the Z direction as well, creating a more three-dimensional wavy surface
* **Self-intersection detection and correction** — Detect overlapping waves (self-intersections) and provide simple correction methods
* **2D / 3D preview** — Real-time preview of the shape; 2D shows the selected layer, and 3D shows the whole object
* **G-code generation** — Export G-code data
* **Save / load settings** — Share settings between projects in JSON format

---

## 2. Installation

### System Requirements

* macOS / Windows

1. Download the latest version from the release page:  
   [https://github.com/kasanetarium/AmiSlicer](https://github.com/kasanetarium/AmiSlicer)

| OS      | File |
| ------- | ---- |
| macOS   | `AmiSlicer-macos0.01.zip` |
| Windows | `AmiSlicer-windows0.0-1.zip` |

2. Extract the ZIP file
3. Double-click the executable to launch
   * **Windows**: `AmiSlicer.exe`
   * **macOS**: `AmiSlicer.app` (on first launch, you may need to right-click and choose **Open**)

---

## 3. Basic Workflow

```text
1. Load STL                → Open STL...
2. Adjust model orientation → Rotate X/Y/Z → Apply Rotation
3. Configure printer basics → Machine / Print tab
4. Configure wave settings  → Wave tab
5. Check preview            → 2D Preview / 3D Preview
6. Fix self-intersections   → Allow SI → Fix Self-Intersections
7. Save G-code              → Save G-code...
8. Print with your 3D printer
```

---

## 4. UI Overview

<img src="img/UI_git.jpg" width="50%" alt="UI">
---

## 5. Detailed Usage

### 5.1 Loading STL

<img src="img/STLUI_git.jpg" width="50%" alt="STLUI">

1. Click **Open STL…** or use **File → Open STL…** (`Ctrl+O`), or drag and drop an STL file into the application window
2. Select a `.stl` file
3. After loading, the following information is displayed:
   * **Size X/Y/Z** — Bounding box size of the model (mm)
   * **Faces** — Number of triangle faces
   * **Manifold** — Yes (closed geometry) / No (non-manifold, which may cause slicing problems)
4. Slicing and preview are generated automatically

---

### 5.2 Model Rotation

Change the orientation of the STL model to adjust the slicing direction.

| Action | Description |
| ------ | ----------- |
| **Rotate X** | Rotate around the X axis (default: 90°) |
| **Rotate Y** | Rotate around the Y axis |
| **Rotate Z** | Rotate around the Z axis |
| **Apply Rotation** | Apply the rotation and update the preview |
| **Reset** | Reset all rotation values to 0° |
| **Mesh 3D Preview** | Display the rotated mesh in 3D |

> 💡 The preview updates automatically when parameters are changed.

---

### 5.3 Printer Settings

#### 5.3.1 Machine Tab

<img src="img/machine_git.jpg" width="50%" alt="machine">

These are the hardware settings of your 3D printer.

Please check the specifications of your printer and the settings you normally use in your slicer.

**⚠️ Start G-code and End G-code include commands related to nozzle and bed heating/cooling. Incorrect values may cause printer failure or accidents. Please enter them carefully, for example by copying them from the slicer you currently use.**

| Setting | Default | Description |
| ------- | ------- | ----------- |
| Bed Size X/Y/Z | 220 / 220 / 250 mm | Printer bed size |
| Nozzle Diameter | 0.4 mm | Nozzle diameter |
| Filament Diameter | 1.75 mm | Filament diameter |
| Start G-code | Homing / heating etc. | Custom G-code inserted at the beginning |
| End G-code | Cooling / parking etc. | Custom G-code inserted at the end |

#### 5.3.2 Print Tab

<img src="img/print_git.jpg" width="50%" alt="print">

These are the print parameters.

Please enter values appropriate for your filament and 3D printer.

| Setting | Default | Description |
| ------- | ------- | ----------- |
| Layer Height | 0.2 mm | Layer height |
| Line Width | 0.4 mm | Line width (recommended: 100–120% of nozzle diameter) |
| Nozzle Temp | 200 °C | Nozzle temperature |
| Bed Temp | 60 °C | Bed temperature (disabled when 0) |
| 1st Layer Speed | 1200 mm/min | First layer print speed |
| Perimeter Speed | 3000 mm/min | Perimeter print speed |
| Travel Speed | 7200 mm/min | Travel speed |
| Flow Multiplier | 1.0 | Extrusion flow multiplier |
| 1st Layer Flow | 1.1 | First layer flow multiplier |
| Retraction Length | 1.0 mm | Retraction distance |
| Retraction Speed | 2700 mm/min | Retraction speed |
| Fan Speed | 100 (0–255) | Fan speed |
| Center on bed | ON | Place the output at the center of the bed |

### 5.4 Wave Tab

<img src="img/wave_git.jpg" width="50%" alt="wave">


These are the wave settings, which are the core feature of AmiSlicer. The Wave tab consists of three groups: **Wave Settings**, **Bottom Settings**, and **Print Settings (synced)**.

> 💡 At the bottom of the Wave tab there is a **Print Settings (synced)** group. **Layer Height**, **Line Width**, **Nozzle Temp**, **Flow Multiplier**, and **Perimeter Speed** can also be viewed and edited from the Wave tab, so you can check them without switching tabs while adjusting waves. These values are synchronized bidirectionally with the Print tab.

#### 5.4.1 Wave Settings

**Basic Parameters**

| Setting | Default | Description |
| ------- | ------- | ----------- |
| **Amplitude** | 1.0 mm | Wave amplitude |
| **Wave Count / Layer** | 20 | Number of waves per layer |
| **Wave Start Layer (from Bottom)** | 0 | Layer where waves start, relative to Bottom Layers |

**Checkboxes**

| Setting | Default | Description |
| ------- | ------- | ----------- |
| **Alternate phase** | ON | Invert phase by 180° between layers |
| **Allow self-intersection in preview** | OFF | Also show waveforms with self-intersections in preview |
| **Move sine in Z direction** | OFF | Apply waves in the Z direction as well |
| **Z Mod Amplitude** | 0.2 mm | Z-direction wave amplitude |
| **Adapt Z phase to taper** | OFF | Adapt Z phase to taper direction |
| **Start loop from min Z** | ON | Start printing from the minimum Z point |

#### 5.4.2 Bottom Settings

This group summarizes settings related to bottom layers.

| Setting | Default | Description |
| ------- | ------- | ----------- |
| **Bottom Layers** | 1 | Number of bottom layers (can be 0; also used as the reference for Wave Start Layer) |

| Setting | Default | Description |
| ------- | ------- | ----------- |
| **Fill bottom** | ON | Enable / disable bottom fill pattern |
| **Apply sine wave to fill lines** | OFF | Apply sine wave to bottom fill lines |
| **Bottom Fill Pitch** | 0.4 mm | Fill line spacing |
| **Bottom Fill Angle** | 0.0 deg | Fill line angle (rotates +90° for each layer) |

**Bottom perimeter wave mode** — Choose one of the following:

| Option | Description |
| ------ | ----------- |
| **Original contour (no wave)** | Use the original contour for bottom-layer perimeters |
| **Apply sine wave (XY only)** | Apply sine wave only in XY |
| **Apply sine wave (XYZ)** | Apply sine wave in XY + Z when Z modulation is enabled |

> 💡 Bottom Layers is always active regardless of whether Fill bottom is ON or OFF. If it is set to 0, no bottom layer is generated. Wave Start Layer is specified relative to Bottom Layers. When Alternate phase is enabled, the phase alternates continuously from bottom layers to wave layers.

---

## 6. Preview

### 6.1 2D Preview

<img src="img/2D_git.jpg" width="50%" alt="2D">


Displays the contour of the selected layer.

| Display Element | Description |
| --------------- | ----------- |
| 🔵 Blue line | Original contour |
| 🔴 Red line | Deformed contour |
| 🟠 Thick orange line | Deformed contour with self-intersection |
| 🟢 Green line | Bottom fill pattern |

### 6.2 3D Preview

<img src="img/3D_git.jpg" width="50%" alt="3D">

Displays all layers stacked in 3D.

You can rotate with mouse drag and zoom with the mouse wheel.

| Display Element | Description |
| --------------- | ----------- |
| 🔴 Red line | Selected layer |
| 🟠 Thick orange line | Deformed contour with self-intersection |

Layer switching:

| Action | Method |
| ------ | ------ |
| Slider | Drag the vertical slider in the right panel |
| Next layer | `→` or `↓` |
| Previous layer | `←` or `↑` |

---

## 7. Detecting and Fixing Self-Intersections

In concave shapes (such as star-like shapes), a large wave amplitude may cause the contour to intersect with itself.

### 7.1 Detection

* Self-intersections are automatically detected for each layer, and layers with self-intersections are shown in orange.

### 7.2 Fix Procedure

First, it is recommended to reduce **Amplitude**, change **Wave Count**, or modify the STL file itself so that self-intersections do not occur. If you still want to print the shape as is, you can forcibly remove self-intersections using one of the following buttons.

| Button | Action |
| ------ | ------ |
| **Fix Self-Intersections** | Locally set amplitude to 0 only for the intersecting wave cycles |
| **Fallback to Original Contour** | Replace self-intersecting layers with the original contour |

1. If **Fix Self-Intersections** is used, the correction algorithm runs.
   * Only the wave cycles that self-intersect are set to amplitude 0
   * Other cycles keep the configured amplitude
   * Neighboring cycles are also tapered gradually (50% → 75% → 0%)
2. The corrected result is reflected in the preview
3. To restore the previous state, click **Restore Self-Intersections**

> 💡 If self-intersections still remain after correction, consider reducing **Amplitude**, changing **Wave Count**, or modifying the STL file.

### 7.3 Warning When Saving G-code

If you attempt to save G-code while self-intersections remain, a confirmation dialog will appear.

---

## 8. Saving G-code

1. Check the shape in the preview
2. Click **Save G-code…**
3. Choose a save location with the `.gcode` extension

> 💡 You can use **Preview G-code…** to inspect the generated G-code before saving.

---

## 9. Saving and Loading Settings

### 9.1 Save

You can save settings.

* Click **Save Settings…** or use **File → Save Settings…** (`Ctrl+S`)
* All Machine / Print / Wave settings are saved in JSON format
* By default, the file name candidate is set to match the STL file name

### 9.2 Load

* Click **Load Settings…** or use **File → Load Settings…** (`Ctrl+Shift+O`)
* You can also load a settings JSON file by dragging and dropping it into the window

### 9.3 Default Settings

It is recommended to save your printer settings as default settings.

| Menu | Action |
| ---- | ------ |
| **File → Save as Default** | Save the current settings as default and load them automatically next time |
| **File → Reset to Default** | Restore the saved default settings |
| **File → Reset to Factory Defaults** | Restore the factory defaults and remove saved defaults |

Default settings are saved to `~/.config/amislicer/default.json`.

---

## 10. G-code Preview

Click **Preview G-code** to inspect the generated G-code as text.

---

## 11. Keyboard Shortcuts

| Shortcut | Function |
| -------- | -------- |
| `Ctrl+O` | Open STL file |
| `Ctrl+S` | Save settings |
| `Ctrl+Shift+O` | Load settings |
| `Ctrl+Q` | Quit the application |
| `←` / `↑` | Previous layer |
| `→` / `↓` | Next layer |

---

## 12. Troubleshooting

### Empty Preview

* If **Manifold** is `No`, slicing may have failed
* Try adjusting the model rotation

### Cannot Fix Self-Intersections

* Reduce Wave Count (make the wavelength longer)
* Reduce Amplitude
* If the model has severe concave / convex features, correction may be limited, so consider modifying the STL file

---

## 13. Notes

* Shapes with branching geometry (shapes whose cross-sections split into multiple contours) are not supported.
* Shapes with internal structures (such as donut-like shapes) are not supported.
* To create woven structures successfully, parameters such as nozzle temperature, print speed, and extrusion amount must be carefully adjusted according to the target geometry, nozzle diameter, filament material, and the environment where the 3D printer is installed.

---

## 14. Safety Notice

> ⚠️ **Important**

* This software is an alpha version and may contain unexpected behavior or bugs.
* This software generates G-code that controls 3D printer heater temperatures and motors. Please use it with caution.
* Do not leave your 3D printer unattended while printing.
* When using this software for the first time, perform a test print to confirm that temperature and motion are correct.
* After printing, make sure that the nozzle and heat bed have cooled down properly and that the print has finished safely.
* The author is not responsible for any damage or loss caused by the use of this software.

---

## 15. License

MIT License

Copyright (c) 2026 Yosuke Hori / kasanetarium

See the [LICENSE](LICENSE) file for details.

---

<p align="center">
<strong>AmiSlicer v0.01 Alpha</strong><br>
Author: Yosuke Hori / kasanetarium
</p>
