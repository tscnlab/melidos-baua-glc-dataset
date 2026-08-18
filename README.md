# MeLiDos BAuA GLC dataset

This repository contains the Dortmund, Germany site data collected by the
Federal Institute for Occupational Safety and Health (BAuA) for the MeLiDos
field study. It is a GLC Schema 3.0.2 Data Package derived from the
[original MeLiDos dataset](https://github.com/MeLiDosProject/BroszioEtAl_Dataset_2025).

The package entry point is `datapackage.json`. Core study, participant,
device, datasheet, dataset, and variable metadata are stored in `data/`.
Participant-level CSV files referenced by `data/datasets.json` are organized
as:

- `data/files/sensor/`: participant-level head, chest, and wrist sensor tables;
- `data/files/longitudinal-reports/`: diaries, experience and wear logs, and
  repeated assessments;
- `data/files/questionnaires/`: screening, baseline, and end-of-study
  questionnaires;
- `data/files/study-timing/`: participant trial-period records.

The source dataset is:

> Broszio, K., Zauner, J., & Spitschan, M. (2025). *Personal light exposure
> dataset for Dortmund, Germany* (Version 1.0.0) [Data set].
> https://doi.org/10.5281/zenodo.18111232

The refactoring converts the imported tabular RData resources to UTF-8 CSV,
separates records by participant, and supplies GLC 3.0.2 metadata without
altering the source measurement values.

## Calibration-date note

The source metadata workbook supplies device delivery dates but no separately
identified calibration dates. For consistency with the current GLC device
requirement, those delivery dates are used provisionally as calibration-date
proxies. They must be checked against the underlying device calibration
records when those records become available.

## Validation

The complete package passes GLC Schema 3.0.2 validation with validator 0.5.2.
Validation reports 0 errors. Its warnings identify empty cells already present
in the source tables, including explicit rows introduced when sensor-stream
gaps were expanded.

Validation also runs automatically through
`.github/workflows/validate-glc-dataset.yml`. Successful runs produce an
attested `validation-report` artifact containing `validation.json` and
`validated-files-manifest.json`.

## License

The dataset is licensed under the Creative Commons Attribution 4.0
International License (CC BY 4.0). See `LICENSE`.
