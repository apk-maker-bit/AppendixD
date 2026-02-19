# Patent owner cleaning & harmonization pipeline
Patent data cleaning and harmonization pipeline used to produce a reproducible script for name cleaning and fuzzy consolidation with regard to cofidentiality
This repository contains the methodology and scripts used for cleaning and harmonizing patent assignee data exported from Lens.org.

## Overview
The pipeline is designed to transform messy patent ownership strings into standardized entity names and categories while maintaining a clear audit trail.


## Workflow Steps
1. **Normalization**: Standardizes Unicode characters and handles Nordic diacritics (e.g., converting 'ae' to 'ä').
2. **Token Cleaning**: Removes legal suffixes (Ltd, Oy, GmbH) and parenthetical information.
3. **Parent Mapping**: Applies regex patterns (defined in `parent_patterns.json`) to group subsidiaries or variations under a single parent entity (e.g., Company A-1 -> Company A).

## Usage
1. Install dependencies: `pip install -r requirements.txt`
2. Place your raw Lens.org export in the `data/` folder as `input_data.xlsx`.
3. Run the pipeline: `python src/cleaning_pipeline.py`
4. The `harmonization_map.csv` is a template to add user's own rules

## Reproducibility & Confidentiality
In accordance with reproducible research standards, the logic and rule-maps are provided here. All sensitive data has been stripped from this public version; users should provide their own `input_data.xlsx` following the standard Lens.org format.
