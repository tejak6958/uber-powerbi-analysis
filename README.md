
# Uber Analysis (Power BI)

## Project Summary

This workspace contains a Power BI report (`uber_Analysis.pbip`) plus the extracted report and semantic model artifacts used for development, review, and source control. The report analyzes Uber trip data and relies on local Excel tables included in the repository.

## Top-level files (present in this repo)

- `uber_Analysis.pbip` — Power BI project/package (open in Power BI Desktop).
- `uber_Analysis.Report/` — Extracted report definition and page/visual JSON (see `definition/report.json`).
- `uber_Analysis.SemanticModel/` — Semantic model files and TMDL definitions (model, tables, and relationships).
- `Location Table.xlsx`, `Uber Trip Details.xlsx` — Excel data sources used by the report.
- `Data Modeling.png` — Diagram of the data model.
- `Problem Statement.docx` — Project brief and objectives.

## Key artifacts

- Report definition: `uber_Analysis.Report/definition/report.json` — contains theme, resource images, and report-level settings.
- Semantic model: `uber_Analysis.SemanticModel/definition/model.tmdl` — references tables including:
  - `Trip Details`
  - `Location Table`
  - `Calendar Table`
  - several `LocalDateTable_*` helper tables

The model enables time-intelligence annotations and includes a `Dynamic Measure` table.

## How to open and inspect

1. Open Power BI Desktop and select `File → Open` then choose `uber_Analysis.pbip`.
2. To inspect the extracted report JSON (pages, visuals, resources), open `uber_Analysis.Report/definition/report.json` in a text editor.
3. To examine the semantic model with tooling, open `uber_Analysis.SemanticModel/definition.pbism` in Tabular Editor or load the `.tmdl` into a compatible tabular model editor.
4. Data refresh: the report references the included Excel files. If you move files, update data source paths in Power BI Desktop before refreshing.

## Local development workflow

- Edit visuals/measures in Power BI Desktop, verify, then export or repackage to update the `.pbip` and the extracted `uber_Analysis.Report/` and `uber_Analysis.SemanticModel/` artifacts for source control.
- Use Tabular Editor for advanced measure and model editing; when saving changes, export the `.tmdl` back into the `uber_Analysis.SemanticModel/definition/` folder.

## Troubleshooting

- Git "dubious ownership" error on Windows (filesystem lacks ownership metadata): add the repo to Git safe list:

  ```powershell
  git config --global --add safe.directory "F:/power bi/uber_analysis"
  ```

- If the Excel data sources moved or are missing, open Power BI Desktop, go to `Transform data → Data source settings`, and update the file path.
- If visuals render incorrectly after changes, verify the report theme in `uber_Analysis.Report/definition/report.json` and ensure referenced images under `uber_Analysis.Report/StaticResources/RegisteredResources/` exist.

## Notes & Next steps

- This README was updated to reflect the repository contents (report JSON, semantic model, and included Excel sources). If you want, I can:
  - Add a `CONTRIBUTING.md` with the exact workflow for updating the model and report,
  - Add a `Makefile` or scripts to automate export/import of `.pbip` and `.pbism`, or
  - Document the key DAX measures and visuals in a separate file.

If you want any of those, tell me which and I'll add them.

