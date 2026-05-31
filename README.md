# NeoRacer Hardware Files

This repository holds the open hardware for the NeoRacer, the 1/10 scale autonomous racing car built by the Neobotics Foundation. Everything you need to understand, modify, or print the chassis lives here: the master CAD project, neutral exchange formats for any CAD tool, a 2D drawing, and the parts that you print yourself.

If you just want to print the parts, jump to [3d-printed-parts](3d-printed-parts/). If you want to open the whole car and change it, start with the FreeCAD project in [full-vehicle](full-vehicle/).

## Before you clone

The CAD files are large, so they are stored with [Git LFS](https://git-lfs.com). Install it once before cloning or the big files will come down as small text pointers instead of real geometry:

```bash
git lfs install
git clone https://github.com/Neobotics-Foundation-Inc/neoracer-hardware-files.git
```

If you already cloned without LFS, run `git lfs pull` inside the repo to fetch the real files.

## What is in here

The files are split into two folders. `full-vehicle` is the complete car. `3d-printed-parts` is the subset you fabricate yourself. Every file name starts with `neoracer-` so it still tells you what it is after you download it on its own.

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

## Picking the right file

- You want to redesign the car: open `neoracer-full-vehicle.FCStd`.
- You use a different CAD tool: open `neoracer-full-vehicle.step`.
- You want to print parts: start with `3d-printed-parts/neoracer-printed-parts.step`, or grab `neoracer-battery-cap.stl` for a single part.
- You want a 3D view without CAD: open `neoracer-full-vehicle.stl` in any mesh viewer.
- You need 2D dimensions: open `neoracer-full-vehicle-drawing.dwg`.

## A note on versions

`neoracer-full-vehicle.stl` is the current mesh and `neoracer-full-vehicle.step` is the neutral export that goes with it. `neoracer-full-vehicle-2025-11.stl` is an older mesh from November 2025, kept only for reference. The FreeCAD project is the live source that all of these are exported from. When you regenerate exports, please keep these names so the history stays readable, and add a dated name like `neoracer-full-vehicle-2026-06.stl` only when you are deliberately archiving an old export.

## Contributing

Improvements are welcome: better tolerances, easier prints, lighter parts, new revisions. Edit the FreeCAD project, regenerate the STEP and STL exports so every format stays in sync, and open a pull request that explains what changed and why. By contributing you agree to license your work under the same terms as the rest of the repository.

## License

The hardware in this repository is released under the CERN Open Hardware Licence Version 2, Strongly Reciprocal (CERN-OHL-S-2.0). In short, you are free to use, study, modify, and distribute these designs, including making physical products from them. In return, if you distribute a product or a modified design, you have to share your complete source under the same license and keep the notices intact. The full text is in [LICENSE](LICENSE).
