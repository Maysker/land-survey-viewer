<h1>
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="assets/logo-64.png">
    <img src="assets/logo-light-64.png" alt="" width="40" height="40">
  </picture>
  Land Survey Viewer
</h1>

**Windows Technical Preview · 0.1.1-preview**

Land Survey Viewer opens a land surveyor's deliverables — DWG/DXF drawings and TXT/CSV point files — and shows them on a 2D map and in a 3D site view, exactly as delivered. No AutoCAD, no GIS software, and your files never leave your computer.

🌐 **Website:** https://maysker.github.io/land-survey-viewer/
⬇️ **Download:** [Latest release](https://github.com/Maysker/land-survey-viewer/releases/latest)

> **Built for one specific workflow.** Land Survey Viewer was developed around one user's survey deliverables and working process in Belgium, and tested on a small set of real files. It is not a universal viewer. DWG and DXF files differ widely between surveyors, software and versions, so drawings that differ from what it was built for may open only partly, or not at all.

> This repository holds the website, release notes and the installer downloads. The application source code is kept in a separate private repository.

---

## What it does

- **Read DWG, DXF and point files.** DWG is converted locally by the bundled converter, without AutoCAD. Support is built around the drawings the app was made for; other files may come through incomplete.
- **Map View.** Parcel, buildings, height points, contours and other layers, optionally over official Belgian aerial imagery.
- **3D Site View.** The existing terrain (3DFACE surface) with overlays, an approximate building volume and an optional orthophoto drape.
- **Inspect.** Click any element to see its layer and coordinates at full source precision; copy or export them.
- **Plan Mode.** Sketch ideas on the site and get area and volume summaries.

## What it deliberately does not do

Land Survey Viewer **shows the survey as delivered**. It does not guess units, coordinate systems, heights or point codes, it does not triangulate points into terrain, and it does not correct or certify anything. It is a viewer, not a CAD, GIS or engineering tool.

## Scope

This preview was built for a specific Belgian survey workflow and does not try to be complete. What it was built and tested for:

- **Tested with:** Belgian survey drawings (DWG/DXF) in Lambert 72 using the Flemish GM-BT layer convention, and simple TXT/CSV point lists.

- **Coordinate system:** Belgian Lambert 72 (EPSG:31370) is recognised and placed on the map. Drawings in any other system open as a local plan without imagery.
- **Layer conventions:** the Flemish GM-BT layer convention is recognised automatically; other drawings can be classified by hand in Map View.
- **Imagery:** official orthophoto services of Flanders, Wallonia and the Brussels-Capital Region only.
- **Not read:** Civil 3D objects, proxy objects, solids, meshes, dimensions, images and paper space. They are listed in the import report.

## Requirements

- Windows 10 or 11, 64-bit
- Microsoft Edge WebView2 Runtime (included in current Windows; the installer adds it if missing — needs internet once)
- .NET Framework 4.8 (included in current Windows 10 and 11)

Python and everything else the app needs are bundled.

## Install

**Installer (recommended):** download `LandSurveyViewer-<version>-setup.exe` from the [latest release](https://github.com/Maysker/land-survey-viewer/releases/latest) and run it. No administrator rights are needed; it installs for the current user and adds one Start Menu entry.

**Portable ZIP:** download `LandSurveyViewer-<version>-win64.zip`, extract it anywhere and run `Land Survey Viewer.exe`.

### "Windows protected your PC"

Preview builds are not yet code-signed, so Microsoft Defender SmartScreen may warn on first run. Check the download first (see below), then click **More info → Run anyway**.

### Verify your download

Each release lists the SHA-256 checksum of every file. In PowerShell:

```powershell
Get-FileHash .\LandSurveyViewer-0.1.1-preview-setup.exe -Algorithm SHA256
```

The result must match the checksum in the release notes.

## Privacy

- The app runs entirely on your computer. Its internal server listens on `127.0.0.1` only.
- Survey files are copied into the app's local data folder and are never uploaded.
- No analytics, no telemetry, no account.
- The only network traffic is **optional** aerial imagery from the official regional services. It is requested only after you allow it, and only for surveys confirmed to be in Lambert 72. Downloaded imagery is kept locally until you clear it under **Privacy**.

## Uninstall

Use **Settings → Apps** (or *Add or remove programs*). Your surveys and settings in `%LOCALAPPDATA%\GeoSurveyViewer` are kept; delete that folder to remove them too.

## Feedback

This is a technical preview. Please report problems or suggestions through [Issues](https://github.com/Maysker/land-survey-viewer/issues). Never attach survey files that you are not allowed to share.

## Data sources and licences

- Aerial imagery: Digitaal Vlaanderen (Flanders), Service public de Wallonie (Wallonia), paradigm.brussels / UrbIS (Brussels-Capital Region), under their respective terms.
- Regional boundaries: SPF Finances / AGDP open data.
- Third-party software (Python, ezdxf, NumPy, Shapely, Pillow, Three.js, OpenLayers, ACadSharp, Microsoft WebView2): see `THIRD_PARTY_NOTICES.md` shipped with the application.

© 2026 Adam Gazdiev. Land Survey Viewer is provided as is, without warranty of any kind.
