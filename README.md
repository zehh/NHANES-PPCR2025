# Data Analysis NHANES PPCR 2025 Project - Dataset Creation

This repository contains the code and data workflow for merging NHANES 2017-2018 datasets for the PPCR 2025 Data Project by Group 7.

## 📂 Repository structure

- `Scripts/` — contains the R Markdown file (`Creating Dataset with Labels.Rmd`) that reads, merges, selects variables, and exports datasets.
- `Input/` — contains:
  - raw NHANES `.xpt` files downloaded from the [NHANES website](https://wwwn.cdc.gov/nchs/nhanes/continuousnhanes/default.aspx?BeginYear=2017),
  - as well as the text files listing the variables to keep for each dataset.
- `Output/` — stores the final merged datasets in `.xlsx`, `.dta`, and `.rds` formats.

## 🔍 How to add or change variables in the datasets

The variables to be included in each final dataset are stored in separate external text files inside the `Input/` folder. This design makes it easy to update or expand the analysis by simply editing these files, without modifying the R code. 

### Current variable lists

- `Input/variable_list.txt`:  
  Contains the **default set of variables**, focused on the primary exposure, outcome, and essential covariates.

- `Input/variable_list_fregni_plus_students.txt`:  
  Contains an **extended set of variables**, combining the list proposed by Professor Fregni (as outlined in [this document](https://docs.google.com/spreadsheets/d/1R2-H-GNjgzqN-QrE5ATa5aSI6Wi5duCdthr5S92D6WY/edit?gid=1983944501#gid=1983944501)) with additional suggestions made by the students.

### To include new variables:

1. Open the appropriate text file in the `Input/` folder (for example, `variable_list.txt` or `variable_list_fregni_plus_students.txt`).
2. Add the new variable names on separate lines.
3. Ensure that the corresponding NHANES `.xpt` file containing these variables is downloaded and placed in the same `Input/` folder.
4. Knit or run the R Markdown script again to regenerate the datasets.

⚠️ The script will automatically check if all requested variables are present. If any are missing, it will issue a warning listing exactly which ones are absent, so you can correct the names or download the required NHANES file.

## 🚀 How to run

Open `Scripts/Creating Dataset with Labels.Rmd` in RStudio and run all chunks, or knit the document. This will:

- Read and merge all `.xpt` files by `SEQN`.
- Create two sets of datasets:
  - One using variables from `Input/variable_list.txt` (default set).
  - Another using variables from `Input/variable_list_fregni_plus_students.txt` (extended set).
- Write each dataset to the `Output/` folder in `.xlsx`, `.dta`, and `.rds` formats.

## 📊 How to read the dataset into Stata

Each merged dataset is exported as a Stata `.dta` file in the `Output/` folder.

For example, to load the **default dataset**, run in Stata:

```stata
use "Output/merged_dataset.dta", clear
````

To load the **extended dataset (Fregni + students)**, run:

```stata
use "Output/merged_dataset_fregni_plus_students.dta", clear
```

Make sure your working directory in Stata is set to the project root, or provide the full path to the file instead.

---

✅ That’s it — you can now perform your analyses directly in Stata or any other statistical software using these prepared NHANES datasets.

---

## 🔗 Resources

* [NHANES 2017-2018 Data Files](https://wwwn.cdc.gov/nchs/nhanes/continuousnhanes/default.aspx?BeginYear=2017)


