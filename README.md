# NTUT-UTL PCB Coil Generator

**English** | [繁體中文](./README.zh-TW.md)

Interactive browser-based tool for designing planar PCB spiral coils with live preview, mm/mil unit support, and DXF export.

**Online tool:**  
https://long-jun.github.io/PCB_Coil_Web_Designer/

Originally developed for the UTL Lab at National Taipei University of Technology (NTUT).

---

## Features

- Real-time planar spiral coil preview using HTML5 Canvas
- Automatic scaling and centered preview
- Inner diameter, trace width, and spacing controls
- mm / mil unit support
- CW / CCW winding direction
- Start angle, end angle, and turn-count controls
- Automatic outer-diameter and approximate trace-length calculation
- DXF export for CAD / ECAD workflows
- Pure HTML / CSS / JavaScript
- Fully static and usable through GitHub Pages or locally

---

## Quick Start

### Online

Open the web tool directly:

https://long-jun.github.io/PCB_Coil_Web_Designer/

No installation is required.

### Local

```bash
git clone https://github.com/Long-Jun/PCB_Coil_Web_Designer.git
cd PCB_Coil_Web_Designer
```

Then open `index.html` in Chrome, Edge, Firefox, or another modern browser.

---

## Design Parameters

### Inner Diameter

Defines the inner diameter of the planar spiral coil.

Supported units:

- mm
- mil

### Trace Width

Defines the PCB conductor width.

Supported units:

- mm
- mil

### Spacing

Defines the gap between adjacent turns.

Supported units:

- mm
- mil

### Rotation Direction

- `CW` — clockwise
- `CCW` — counter-clockwise

### Start Angle / End Angle / Turns

The basic relationship is:

```text
turns = (endAngle - startAngle) / 360
```

Changing the number of turns updates the end angle, and changing the end angle updates the calculated turn count.

The geometry uses an Archimedean spiral approximation:

```text
pitch = trace width + spacing
```

---

## Design Summary

The tool automatically reports:

- Outer diameter
- Total number of turns
- Approximate total trace length

These values are intended for rapid PCB-coil design and preliminary engineering estimates.

---

## DXF Export

The generated DXF can be imported into common CAD / ECAD software.

Key characteristics:

- Coordinates are exported in millimeters
- Trace width is stored in the polyline width
- Suitable for further PCB-layout or mechanical-CAD processing

If the imported geometry appears at the wrong scale, verify that the destination software interprets the DXF coordinates as millimeters.

---

## Project Structure

```text
PCB_Coil_Web_Designer/
├── index.html
├── README.md
├── README.zh-TW.md
└── LICENSE
```

The main interface, styling, and JavaScript logic are contained in `index.html`.

---

## Limitations

The current version is primarily intended for single-layer planar spiral coils.

Current limitations include:

- No multilayer or stacked-coil generator
- No segment-wise variable trace width
- No built-in inductance, Q-factor, or DC-resistance solver
- Start and end pads are not generated as complete PCB pad geometries

---

## GitHub Pages

This repository can be deployed directly as a static website.

1. Open **Settings → Pages**
2. Select **Deploy from a branch**
3. Select the `main` branch
4. Select `/ (root)`
5. Save the configuration

The project will then be available at:

https://long-jun.github.io/PCB_Coil_Web_Designer/

---

## License

This project is licensed under the **Apache License 2.0**.

See [LICENSE](./LICENSE) for details.

---

## Acknowledgements

Originally developed for PCB coil design and experimental work in the **UTL Lab, National Taipei University of Technology (NTUT)**.

Feedback, issues, and improvements are welcome through GitHub Issues.
