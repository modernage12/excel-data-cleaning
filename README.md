# Excel Data Cleaning Project: US Presidents Dataset

## Overview

This repository showcases a practical data cleaning pipeline executed entirely in **Microsoft Excel**. The project demonstrates how to transform a raw, inconsistent, and messy dataset into a standardized, structured, and database-ready format.

While many practitioners default to SQL or Python for data preprocessing, executing these steps in Excel remains highly efficient for smaller datasets before they are ingested into analytical databases or visualization tools like Tableau.

---

## Repository Structure

* `us_presidents_raw.csv`: The initial, unmodified dataset containing formatting errors, duplicates, inconsistencies, and redundant columns.
* `us_presidents_cleaned.csv`: The finalized, clean dataset ready for data analysis, pivot tables, or database ingestion.

---

## Data Cleaning Workflow and Methodology

The cleaning process followed a strict data integrity workflow to ensure no raw data was permanently overwritten or lost.

### 1. Data Preservation and Safety

* **Rule Baseline:** Always work on a copy of the initial file. Never modify the raw file directly to ensure reproducible comparisons.

### 2. Deduplication

* **Action:** Navigated to the "Data" tab and selected "Remove Duplicates" across all columns.
* **Impact:** Identified and eliminated redundant rows (such as duplicate entries for specific records), ensuring each row represents a unique observation.

### 3. Text Standardization and Case Alignment

* **Action:** Applied text transformation formulas to clean up erratic casing where names appeared in all caps or all lowercase.
* **Formulas Used:**
* `=PROPER(cell)`: To standardize names to title case (e.g., converting "james monroe" to "James Monroe").
* `=UPPER(cell)`: Used where full capitalization was required for structural consistency.



### 4. Whitespace Removal

* **Action:** Cleaned trailing, leading, and excess middle spaces that often cause syntax or join errors during SQL or Python ingestion.
* **Formula Used:** `=TRIM(cell)`

### 5. Categorical Consistency via Advanced Filtering

* **Action:** Deployed Excel **Filters** on categorical columns (such as `Party`) to run a structural audit.
* **Impact:** * Spotted and merged hidden spelling variances (e.g., mapping variations like "republicans" or corrupted strings back to the standardized "republican").
* Evaluated `BLANK` or empty values to decide whether to impute or drop them based on context.



### 6. Data Type Casting and Reformatting

* **Numerical Data:** Converted financial data or salaries saved as text into clean numeric values by removing unnecessary currency symbols and decimals, making the fields instantly calculable.
* **Date Fields:** Standardized disparate date strings into a unified **Short Date** format to ensure chronological calculations function seamlessly.

### 7. Formula Freezing (Paste as Values)

* **Action:** Before finalizing the columns, all dynamic formulas (`TRIM`, `PROPER`) were frozen using **Paste Special > Values**. This breaks the dependency on the formula engine and locks the raw string data.

### 8. Dimensionality Reduction (Dropping Redundant Columns)

* **Action:** Removed columns deemed entirely useless or redundant for downstream analytical purposes, such as heavily corrupted text columns or duplicate unique identifiers.

---

## Key Takeaways and Best Practices

* **Know Your Ingestion Targets:** Formatting choices (like stripping currency symbols or trimming trailing spaces) are critical if the data is bound for an SQL database, where non-numeric characters or invisible spaces break data schemas.
* **Context Matters:** Data cleaning is not a one-size-fits-all process. Modifying variables must always align with the ultimate business logic and the specific analytical objective of the project.

---

**TL;DR:** This repository contains a complete Excel data cleaning project that transforms a messy dataset of US Presidents into a structured format. The repository includes both the raw and cleaned CSV files for direct comparison, documenting a workflow that covers deduplication, text normalization (using TRIM and PROPER), categorical correction via filters, data type casting, and the removal of redundant columns.
