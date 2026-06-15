# FluxDash v1.0.0 — Teaching-Oriented Eddy Covariance Workflow App

FluxDash is a Windows Electron desktop app designed for students and early-career professionals learning eddy covariance data workflows. It brings data viewing, `.ghg` extraction, optional EddyPro processing, pre-filtering, REddyProc gap filling and partitioning, footprint diagnostics, interactive result exploration, workflow logging, and project save/reload into one interface.

## Author and creator

FluxDash was inspired and created by Ife Familusi, Research Associate, Kentucky State University. Contact: ife.familsui@kysu.edu. All rights reserved.

## Main features in v1.0.0

- Built-in `.ghg` processor/extractor for SmartFlux/EddyPro outputs.
- Raw covariance fallback for older `.ghg` files that contain high-frequency `.data` and biomet files.
- Optional EddyPro engine for advanced users.
- Pre-filtering before gap filling for missing-value codes and realistic NEE/CO2, LE, H, and radiation ranges.
- REddyProc u* threshold filtering, MDS gap filling, and nighttime/daytime partitioning.
- Interactive Results Explorer with cumulative NEE/GPP/Reco, source/sink budgets, unit conversion, ET, CUE/WUE, Bowen ratio, EBC, gap-filling diagnostics, light-response curves, Q10, VPD response, seasonal/diel patterns, and footprint visualization.
- Light-response and temperature-response plots now report fitted equations and parameters.
- Analysis-level outlier handling for response plots: IQR filtering, percentile trimming, manual x/y ranges, and repeated x-spike removal.
- Dark, light, and system theme options.
- Save project and open/reload project.
- Exportable workflow log with methods choices and supporting references.
- FLUXNET/AmeriFlux CSV support for FULLSET and ERA5 products at half-hourly, daily, weekly, monthly, and yearly resolution.
- Help menu with About and bundled software documentation.

## Requirements

### Required for building the app

1. Install Node.js LTS from https://nodejs.org.
2. Extract this folder.
3. Double-click `build.bat`.

The first build downloads Electron, Chart.js, and build dependencies through npm.

### Required for the Process tab

Install Python 3 from https://python.org/downloads and check **Add Python to PATH** during installation.

EddyPro is optional. Use it only from the Process tab's engine selector if you specifically want external EddyPro reprocessing.

### Required for partitioning

The Partition tab requires R and the R package `REddyProc`. Use the **Setup R** button in the app, or install R manually and then allow FluxDash to install/check `REddyProc`.

## Build

Run:

```bat
build.bat
```

or manually:

```bat
npm install
npm run check
npm start
npm run build
```

The Windows installer will be created in:

```text
dist\FluxDash Setup 1.0.0.exe
```

## Recommended student workflow

1. Install Python 3 and R.
2. Install FluxDash with the Windows installer.
3. Open a folder containing `.ghg` or EP-Summary files, and FLUXNET/AmeriFlux CSV datasets.
4. Use **Scan folder**.
5. In **Process**, choose **Built-in .ghg processor / extractor** for `.ghg` files, or **FLUXNET/AmeriFlux CSV normalizer** for FLUXNET/AmeriFlux CSV folders.
6. Review pre-filtering rules and start processing.
7. Run **Partition** with the desired REddyProc method and u* option.
8. Explore and export results from the **Results** tab.
9. Export the workflow log for manuscript methods or lab-report documentation.

## Notes

- EP-Summary files remain the fastest input for raw EC outputs; FLUXNET FULLSET files are preferred for standardized, already gap-filled/partitioned products.
- For REddyProc, confirm that NEE/co2_flux/FC, u*, air temperature, radiation, and either VPD or RH are available.
- The raw covariance fallback is for teaching and exploratory use. For publication-grade processing, validate against EddyPro and site-specific metadata/correction settings.
- Documentation is bundled under **Help > Open Software Documentation**.


## FLUXNET/AmeriFlux CSV support

FluxDash v1.0.0 can scan folders containing AmeriFlux/FLUXNET CSV files such as `FULLSET_HH`, `FULLSET_DD`, `FULLSET_MM`, `FULLSET_WW`, `FULLSET_YY`, and ERA5 meteorological products. When a FULLSET file is available, FluxDash normalizes common columns such as `NEE_VUT_REF`, `GPP_NT_VUT_REF`, `GPP_DT_VUT_REF`, `RECO_NT_VUT_REF`, `RECO_DT_VUT_REF`, `LE_F_MDS`, `H_F_MDS`, `SW_IN_F_MDS`, `TA_F_MDS`, `VPD_F_MDS`, and `USTAR` into the internal FluxDash names used by the Results Explorer. Because FLUXNET FULLSET files already include gap-filled and partitioned products, the Partition tab uses those columns directly rather than rerunning REddyProc.
