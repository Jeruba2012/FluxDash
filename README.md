# FluxDash v1.0.0 — Teaching-Oriented Eddy Covariance Workflow App

FluxDash is a Windows desktop application designed for students, early-career professionals, instructors, and researchers learning and applying eddy covariance data workflows. It brings data viewing, `.ghg` extraction, optional EddyPro processing, pre-filtering, REddyProc gap filling and partitioning, footprint diagnostics, interactive result exploration, workflow logging, and project save/reload into one interface.

[Download FluxDash](https://github.com/Jeruba2012/FluxDash/releases/latest)

## Author and creator

FluxDash was inspired and created by **Ife Familusi**, Research Associate, Kentucky State University. Contact: [ife.familusi@kysu.edu](mailto:ife.familusi@kysu.edu). All rights reserved.

## Main features in v1.0.0

- Built-in `.ghg` processor/extractor for SmartFlux/EddyPro outputs.
- Raw covariance fallback for older `.ghg` files that contain high-frequency `.data` and biomet files.
- Optional EddyPro engine for advanced users.
- FLUXNET/AmeriFlux CSV support for FULLSET and ERA5 products at half-hourly, daily, weekly, monthly, and yearly resolution.
- QC flag acceptance presets: strict, moderate, permissive, all, and custom.
- Variable-specific QC application: `qc_co2_flux` affects NEE/CO2 flux only, `qc_H` affects H only, and `qc_LE` affects LE only.
- Optical/signal diagnostic screening using AGC/RSSI-style columns where present.
- Expanded plausibility limits for NEE, LE, H, Rn, Rg, u*, Tair, VPD, and RH.
- Slow-driver cleaning, including negative radiation drift handling, RH saturation capping, and VPD normalization.
- Optional MAD-based meteorological-driver outlier flagging.
- Optional nighttime low-u* NEE-only mask.
- Preservation of original variables alongside cleaned, gap-filled, and partitioned outputs.
- REddyProc u* threshold filtering, MDS gap filling, and nighttime/daytime partitioning.
- Interactive Results Explorer with cumulative NEE/GPP/Reco, source/sink budgets, unit conversion, ET, CUE/WUE, Bowen ratio, energy balance closure, gap-filling diagnostics, light-response curves, Q10, VPD response, seasonal/diel patterns, and footprint visualization.
- Light-response plots for NEE or GPP against SW/Rg, PAR, or PPFD, with binned means, fitted equations, and robust-envelope fitting options.
- Energy balance closure analysis with available-energy and turbulent-energy diagnostics.
- Analysis-level outlier handling for response plots.
- Dark, light, and system theme options.
- Save project and open/reload project.
- Exportable workflow log with methods choices and supporting references.
- Help menu with About and bundled software documentation.

## Download and installation

The current Windows installer is available from the Releases page:

[Download the latest FluxDash release](https://github.com/Jeruba2012/FluxDash/releases/latest)

For direct installer download:

[Download FluxDash for Windows](https://github.com/Jeruba2012/FluxDash/releases/latest/download/FluxDash-Windows-Setup.exe)

Install the application using the Windows installer. Some workflows require supporting software:

- **Python 3**: required for the built-in `.ghg` extractor and raw fallback processor.
- **R** and **REddyProc**: required for REddyProc gap filling and partitioning.
- **EddyPro**: optional; use only when external EddyPro reprocessing is desired.

## Recommended student workflow

1. Install FluxDash using the Windows installer.
2. Install Python 3 and R if processing/partitioning workflows require them.
3. Open a folder containing `.ghg`, EP-Summary, FLUXNET/AmeriFlux, or CSV datasets.
4. Use **Scan folder**.
5. In **Process**, choose **Built-in .ghg processor / extractor** for `.ghg` files, or **FLUXNET/AmeriFlux CSV normalizer** for standardized CSV products.
6. Review QC, missing-value, and pre-filtering rules before processing.
7. Run **Process** and inspect filter counts and warnings.
8. Run **Partition** with the desired REddyProc method and u* option.
9. Explore and export results from the **Results** tab.
10. Export the workflow log for methods documentation.

## Scientific use notice

FluxDash is intended for teaching, exploratory analysis, workflow support, and environmental research. Users are responsible for reviewing processing choices, QC thresholds, variable units, sign conventions, instrument metadata, gap-filling performance, partitioning results, and exported values before using outputs in a thesis, report, publication, or management decision.

The built-in raw covariance fallback is primarily for teaching and exploratory use. Publication-grade raw-data processing should be validated against EddyPro or another established eddy covariance processing system.

## Documentation

The complete software documentation is available here:

[FluxDash Software Documentation](docs/FluxDash_Software_Documentation_v1_0.pdf)

## Related publications by the software creator

Familusi, I., Gebremedhin, M., Gyawali, B., Chiluwal, A., & Brotzge, J. (2025). A deciduous forest's CO2 exchange within the mixed-humid climate of Kentucky, USA. *Forests, 16*(4), 562. https://doi.org/10.3390/f16040562

Familusi, I., Gebremedhin, M., Ries, I., Brown, J., & Gyawali, B. (2024). The productivity and carbon exchange of an intensively managed pasture in Central Kentucky. *Atmosphere, 15*(3), 348. https://doi.org/10.3390/atmos15030348

## Suggested citation

Familusi, I. (2026). *FluxDash* (Version 1.0.0) [Computer software]. Kentucky State University.

## Terms

FluxDash is proprietary software distributed in compiled form for educational, research, and authorized noncommercial professional use. The source code is not publicly distributed through this repository. See [TERMS_OF_USE.txt](TERMS_OF_USE.txt).

Copyright © 2026 Ife Familusi. All rights reserved.
