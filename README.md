# NeoRacer Hardware Files

This repository holds the open hardware for the NeoRacer, the 1/10 scale autonomous racing car built by the Neobotics Foundation. Everything you need to understand, modify, or print the car lives here: the master CAD project, neutral exchange formats for any CAD tool, a 2D drawing, the parts that you print yourself, and the open electrical documents for the OSCORE power and control board.

If you just want to print the parts, jump to [3d-printed-parts](3d-printed-parts/). If you want to open the whole car and change it, start with the FreeCAD project in [full-vehicle](full-vehicle/). If you want the electronics, the schematic and hardware manual are in [oscore-board](oscore-board/).

## Before you clone

The CAD files are large, so they are stored with [Git LFS](https://git-lfs.com). Install it once before cloning or the big files will come down as small text pointers instead of real geometry:

```bash
git lfs install
git clone https://github.com/Neobotics-Foundation-Inc/neoracer-hardware-files.git
```

If you already cloned without LFS, run `git lfs pull` inside the repo to fetch the real files.

## What is in here

The files are split into three folders. `full-vehicle` is the complete car. `3d-printed-parts` is the subset you fabricate yourself. `oscore-board` is the custom electronics, the OSCORE power and control board. Every file name starts with `neoracer-` so it still tells you what it is after you download it on its own.

### full-vehicle/ (the whole NeoRacer)

| File | Format | Size | What it is |
| --- | --- | --- | --- |
| `neoracer-full-vehicle.FCStd` | FreeCAD project | 154 MB | The master source. This is the editable, parametric model with the full feature tree. Open it in [FreeCAD](https://www.freecad.org) to change dimensions, regenerate exports, or branch a new revision. Treat this as the single source of truth. |
| `neoracer-full-vehicle.step` | STEP (ISO 10303) | 96 MB | The full assembly in a neutral CAD format. STEP keeps solid geometry, so it opens cleanly in Fusion 360, SolidWorks, Onshape, Inventor, and most other tools. Use this if you do not run FreeCAD. |
| `neoracer-full-vehicle.stl` | STL mesh | 99 MB | The current triangle mesh of the full car. Good for quick viewing, renders, and visual reference. It is geometry only, not a parametric model, so you cannot edit features in it. |
| `neoracer-full-vehicle-2025-11.stl` | STL mesh | 99 MB | An earlier mesh export from November 2025, kept for reference. If this and the current mesh disagree, trust `neoracer-full-vehicle.stl`. |
| `neoracer-full-vehicle-drawing.dwg` | DWG drawing | 36 MB | The 2D drawing set with dimensions and layout. Open it in AutoCAD, LibreCAD, or any DWG viewer when you need measured 2D views rather than the 3D model. |

### 3d-printed-parts/ (what you print)

| File | Format | Size | What it is |
| --- | --- | --- | --- |
| `neoracer-printed-parts.step` | STEP (ISO 10303) | 3.6 MB | Every printable part of the NeoRacer collected in one STEP assembly. Import it into your slicer or CAD tool, separate the bodies, and arrange them on your print bed. This is the starting point for a full set of printed parts. |
| `neoracer-battery-cap.stl` | STL mesh | 0.4 MB | The battery cap, exported on its own and ready to drop straight into a slicer. A small standalone print, useful as a first test or a quick replacement. |

### oscore-board/ (the power and control board)

The OSCORE board is the NeoRacer's custom electronics, a power-distribution and control PCB built around an ESP32-S3. These are its open electrical documents at revision RevA (June 2026).

| File | Format | Size | What it is |
| --- | --- | --- | --- |
| `neoracer-oscore-schematic.pdf` | PDF | 0.7 MB | The full schematic. Start here to see how the board is wired, from the power rails through the ESP32-S3 to every connector. |
| `neoracer-oscore-hardware-manual.pdf` | PDF | 3.7 MB | The hardware manual: power system, the MCU, the onboard IMU, every interface, and the electrical limits. The reference for using or modifying the board. |
| `neoracer-oscore-reference-designators.pdf` | PDF | 2.0 MB | The reference-designator map. Use it to find any component from the schematic on the physical board. |
| `neoracer-oscore-board.step` | STEP (ISO 10303) | 56 MB | The board's 3D model in a neutral CAD format, for fit checks and enclosure design. Opens in any CAD tool. |
| `neoracer-oscore-board-front.png` | PNG | 0.7 MB | A render of the front of the board. |
| `neoracer-oscore-board-back.png` | PNG | 0.9 MB | A render of the back of the board. |
| `neoracer-oscore-board-interface.png` | PNG | 1.3 MB | The annotated interface map: every connector and what it is for. |

## Picking the right file

- You want to redesign the car: open `neoracer-full-vehicle.FCStd`.
- You use a different CAD tool: open `neoracer-full-vehicle.step`.
- You want to print parts: start with `3d-printed-parts/neoracer-printed-parts.step`, or grab `neoracer-battery-cap.stl` for a single part.
- You want a 3D view without CAD: open `neoracer-full-vehicle.stl` in any mesh viewer.
- You need 2D dimensions: open `neoracer-full-vehicle-drawing.dwg`.
- You want to understand the electronics: open `oscore-board/neoracer-oscore-schematic.pdf`, then the `oscore-board/neoracer-oscore-hardware-manual.pdf`.
- You are designing an enclosure or checking fit around the board: open `oscore-board/neoracer-oscore-board.step`.

## A note on versions

`neoracer-full-vehicle.stl` is the current mesh and `neoracer-full-vehicle.step` is the neutral export that goes with it. `neoracer-full-vehicle-2025-11.stl` is an older mesh from November 2025, kept only for reference. The FreeCAD project is the live source that all of these are exported from. When you regenerate exports, please keep these names so the history stays readable, and add a dated name like `neoracer-full-vehicle-2026-06.stl` only when you are deliberately archiving an old export.

## Contributing

Improvements are welcome: better tolerances, easier prints, lighter parts, new revisions. Edit the FreeCAD project, regenerate the STEP and STL exports so every format stays in sync, and open a pull request that explains what changed and why. By contributing you agree to license your work under the same terms as the rest of the repository.

## License

The hardware in this repository is released under the CERN Open Hardware Licence Version 2, Strongly Reciprocal (CERN-OHL-S-2.0). In short, you are free to use, study, modify, and distribute these designs, including making physical products from them. In return, if you distribute a product or a modified design, you have to share your complete source under the same license and keep the notices intact. The full text is in [LICENSE](LICENSE).
