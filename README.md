# Uber Analysis (Power BI)

## Overview

This repository contains a Power BI report and its semantic model for the "Uber Analysis" project. The workspace includes the Power BI packaged file, the extracted report definition, static resources, and the semantic model artifacts used to build and deploy the dataset.

## Contents

- `uber_Analysis.pbip` — Power BI project/package file (open with Power BI Desktop).
- `uber_Analysis.Report/` — Extracted report definition and page/visual assets (JSON structure).
- `uber_Analysis.SemanticModel/` — Semantic model artifacts and `definition.pbism` (Tabular Model files, TMDL definitions).

Key files inside the workspace:

- `uber_Analysis.Report/definition/report.json` — report JSON for visuals and pages.
- `uber_Analysis.SemanticModel/definition.pbism` — packaged semantic model (dataset) file.
- `uber_Analysis.SemanticModel/definition/model.tmdl` — model TMDL describing tables, measures, and relationships.

## Prerequisites

- Power BI Desktop (recommended latest stable release) to open `.pbip` and explore the report.
- Optionally, Tabular Editor or Analysis Services tools to inspect `.pbism` / `.tmdl` files.

## How to open the project

1. Open Power BI Desktop.
2. Use `File → Open` and select `uber_Analysis.pbip` to load the report and dataset.
3. Alternatively, inspect the extracted report at `uber_Analysis.Report/` to review pages and visual JSON definitions.
4. To inspect or edit the semantic model, open `uber_Analysis.SemanticModel/definition.pbism` with Tabular Editor or import the `.tmdl` files into a compatible tool.

## Development & Versioning Notes

- The repository stores extracted report artifacts (JSON, visuals) for source control and review.
- When modifying visuals or the semantic model, prefer editing in Power BI Desktop, then re-export or repackage the `.pbip` to keep artifacts consistent.

## Troubleshooting

- If Git reports a "detected dubious ownership" error on Windows (filesystem not recording ownership), resolve by adding the directory to Git's safe list:

  ```powershell
  git config --global --add safe.directory "F:/power bi/uber_analysis"
  ```

- If files are on a network share or non-NTFS volume, consider moving the repository to a local NTFS folder or run Git as the same user who created the files.

## Contact

If you need help reproducing an error, please paste the full error message and the steps you ran (commands, Power BI action, or build/deploy steps).

---
Generated README for the workspace contents. Update as project evolves.
