# NHANES PPCR 2025 Project

This repository contains the code and data workflow for merging NHANES 2017-2018 datasets for the PPCR 2025 Data Project by Group 7.

## 📂 Repository structure

- `Scripts/` — contains the R Markdown file (`Creating Dataset with Labels.Rmd`) used to read, merge, select variables, and export datasets.
- `Input/` — contains raw NHANES `.xpt` files downloaded from the [NHANES website](https://wwwn.cdc.gov/nchs/nhanes/continuousnhanes/default.aspx?BeginYear=2017).
- `Output/` — stores the final merged datasets in `.xlsx`, `.dta`, and `.rds` formats.

## 🔍 How to add more variables to the dataset

If you want to include additional variables in the final merged dataset:

1. **Edit the `vars_to_keep` vector** inside `Scripts/analysis.Rmd` and add the new variable names. For example:

    ```r
    vars_to_keep <- c(
      "SEQN",
      "DRQSDT1",
      "HSCRP_J",
      "RIDAGEYR",
      "RIAGENDR",
      "RIDRETH1",
      "BMXBMI",
      "SMQ020",
      "PAQ605",
      "PAQ650",
      "SLD012",
      "NEWVAR1",  # example of new variable
      "NEWVAR2"
    )
    ```

2. **Make sure the corresponding NHANES `.xpt` file that contains these variables is downloaded and placed in the `Input/` folder.**

3. Knit or run the R Markdown script again to regenerate the merged dataset with the new variables.

⚠️ The script will automatically check if all requested variables are present. If any are missing, it will issue a warning listing exactly which ones are absent, so you can either correct the variable name or download the appropriate data file.

## 🚀 How to run

Open `Scripts/Creating Dataset with Labels.Rmd` in RStudio and run all chunks or knit the document. This will:

- Read and merge all `.xpt` files by `SEQN`,
- Select only the variables listed in `vars_to_keep`,
- Write the final dataset to the `Output/` folder in `.xlsx`, `.dta`, and `.rds` formats.

## 📊 How to read the dataset into Stata

The final merged dataset is exported as a Stata `.dta` file in the `Output/` folder.

To load it in Stata, open Stata and run:

```stata
use "Output/merged_dataset.dta", clear
```

Make sure your working directory in Stata is set to the project root, or provide the full path to the file instead.

---

✅ That’s it — you can now perform your analyses directly in Stata with all selected NHANES variables already merged and labeled.

---

## 🔗 Resources

- [NHANES 2017-2018 Data Files](https://wwwn.cdc.gov/nchs/nhanes/continuousnhanes/default.aspx?BeginYear=2017)

---
