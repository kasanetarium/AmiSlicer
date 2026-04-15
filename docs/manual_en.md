# AmiSlicer

> ⚠️ **Alpha Release (v0.01)** — This software is in early development.

---

## Table of Contents

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
  - [5.4 Wave Settings](#54-wave-settings)
- [6. Preview](#6-preview)
- [7. Self-Intersection](#7-self-intersection)
- [8. Export G-code](#8-export-g-code)
- [9. Save / Load Settings](#9-save--load-settings)
- [10. Troubleshooting](#10-troubleshooting)
- [11. Safety Notice](#11-safety-notice)
- [12. License](#12-license)

---

## 1. What is AmiSlicer

AmiSlicer is a desktop application that generates G-code from STL files by applying sinusoidal deformation to perimeters.

It produces unique woven-like surface textures by alternating phase between layers.

### Key Features

- STL slicing (layer-based)
- Sinusoidal perimeter deformation
- Alternating phase (180°) between layers
- Optional Z-direction modulation
- Self-intersection detection and correction
- 2D / 3D preview
- G-code export
- JSON-based settings

---

## 2. Installation

### System Requirements

- macOS / Windows

Download from:
https://github.com/kasanetarium/AmiSlicer

| OS      | File |
|---------|------|
| macOS   | AmiSlicer-macos0.01.zip |
| Windows | AmiSlicer-windows0.01.zip |

Steps:
1. Extract ZIP
2. Launch:
   - Windows: AmiSlicer.exe
   - macOS: AmiSlicer.app (Right-click → Open if needed)

---

## 3. Basic Workflow

1. Open STL  
2. Adjust orientation  
3. Configure printer settings  
4. Configure wave parameters  
5. Preview  
6. Fix intersections if needed  
7. Export G-code  
8. Print  

---

## 4. UI Overview

- Left panel: STL + settings  
- Right panel: 2D / 3D preview  
- Bottom: actions and status  

---

## 5. Detailed Usage

### 5.1 Loading STL

- File → Open STL
- Drag & drop supported
- Displays:
  - Size (X/Y/Z)
  - Faces
  - Manifold status

---

### 5.2 Model Rotation

- Rotate X / Y / Z
- Apply / Reset
- Preview updates automatically

---

### 5.3 Printer Settings

#### Machine

- Bed size
- Nozzle diameter
- Filament diameter
- Start / End G-code

⚠️ Incorrect G-code may damage your printer.

#### Print

- Layer height
- Line width
- Temperature
- Speed
- Flow
- Retraction

---

### 5.4 Wave Settings

Core feature of AmiSlicer.

- Amplitude: wave height
- Wave count: number per layer
- Alternate phase: 180° shift
- Z modulation (optional)

Bottom settings:

- Bottom layers
- Fill pattern
- Optional wave on bottom

---

## 6. Preview

### 2D

- Blue: original
- Red: deformed
- Orange: intersection warning
- Green: fill

### 3D

- Full model visualization
- Rotate / zoom supported

---

## 7. Self-Intersection

May occur in concave shapes.

Fix options:

- Reduce amplitude or wave count
- Fix Self-Intersections
- Fallback to original contour

---

## 8. Export G-code

- Save as .gcode
- Preview before export

---

## 9. Save / Load Settings

- Save settings as JSON
- Load from file or drag & drop
- Default settings supported

---

## 10. Troubleshooting

### Empty preview

- Model may be non-manifold
- Try rotating

### Cannot fix intersections

- Reduce amplitude
- Reduce wave count
- Simplify model

---

## 11. Safety Notice

> ⚠️ **Important**

- This software is an alpha version and may contain unexpected behavior or bugs.
- This software generates G-code that controls 3D printer heaters and motors. Please use it with caution.
- Do not leave your 3D printer unattended while printing.
- When using this software for the first time, perform a test print to confirm that temperature and motion are correct.
- After printing, make sure that the nozzle and heat bed have cooled down properly and that the print has finished safely.
- The author is not responsible for any damage or loss caused by the use of this software.

---

## 12. License

MIT License

---

AmiSlicer v0.01 Alpha  
Author: Yosuke Hori / kasanetarium
