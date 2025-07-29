# Mobile Device User Behavior Analysis Notebook

A comprehensive R notebook that cleans, explores, and models the **Mobile Device Usage & User Behavior** dataset. The project demonstrates end-to-end data-science workflow—data wrangling, visualization, regression, and multi-class classification—using only open-source R packages.

## Table of Contents
1. [Project Overview](#project-overview)  
2. [Folder Structure](#folder-structure)  
3. [Prerequisites](#prerequisites)  
4. [Installation & Setup](#installation--setup)  
5. [Notebook Walk-through](#notebook-walk-through)  
6. [Key Results](#key-results)  
7. [Re-running the Analysis](#re-running-the-analysis)  
8. [Troubleshooting](#troubleshooting)  
9. [Roadmap](#roadmap)  
10. [License](#license)  
11. [Author](#author)

## Project Overview
This repository contains **`mobile_dataset.ipynb`**, an interactive R Markdown notebook that:

- **Cleans and scales** raw usage data (`user_behavior_dataset.csv`)  
- **Explores** distributions, outliers, and correlations with `summarytools`, `skimr`, and base R functions  
- **Builds predictive models**  
  - *Linear Regression* → predicts daily app-usage time  
  - *Logistic Regression* → classifies user gender (binary)  
  - *Multinomial Logistic Regression* → predicts handset model classes  
- **Evaluates** models with RMSE, R², accuracy, precision, and recall  
- **Exports** the cleaned dataset to `cleaned_user_behavior_dataset.csv` for downstream work

The notebook is aimed at students and practitioners who want a quick, reproducible template for behavioral analytics with R.

## Folder Structure
```
.
├── mobile_dataset.ipynb          # Main R notebook
├── user_behavior_dataset.csv     # Original raw data (11 columns, 700 rows)
├── cleaned_user_behavior_dataset.csv
├── README.md
└── LICENSE
```

## Prerequisites
| Tool / Library | Tested Version | Purpose |
| -------------- | ------------- | ------- |
| R | ≥ 4.2 | Core language |
| **tidyverse** | 2.0 | Data manipulation |
| **dplyr, tidyr** | 1.1 | Cleaning & wrangling |
| **caret** | 6.0 | Data splits & metrics |
| **Metrics** | 0.1 | RMSE calculation |
| **nnet** | 7.3 | Multinomial regression |
| **caTools** | 1.18 | Train / test split (alt.) |
| **skimr** (optional) | 2.2 | Quick data skim |
| **summarytools** (optional) | 1.0 | Detailed summary tables |

> ⚠️ `summarytools` and `magick` can fail to compile on minimal systems. If installation breaks, comment out those cells or use Docker.

## Installation & Setup
1. **Clone**
   ```bash
   git clone https://github.com//.git
   cd 
   ```

2. **Launch RStudio or VS Code** with the R extension.

3. **Install packages** (first run only)
   ```R
   install.packages(c(
     "tidyverse", "dplyr", "tidyr", "caret", "Metrics",
     "nnet", "caTools", "skimr"        # optional: "summarytools"
   ))
   ```

4. **Open** `mobile_dataset.ipynb` and execute cells sequentially, or knit it to HTML/PDF.

## Notebook Walk-through
| Section | Description |
| ------- | ----------- |
| **1 🌱 Setup & Packages** | Installs/loads all needed libraries. |
| **2 🧹 Data Cleaning** | Removes `NA`s and duplicates, scales numeric fields, saves cleaned CSV. |
| **3 🔍 EDA** | Uses `str()`, `summary()`, `skim()` and plots to understand distributions. |
| **4 📈 Linear Regression** | Predicts `App.Usage.Time..min.day.` → RMSE ≈ 41.9, R² ≈ 0.94. |
| **5 ⚖️ Binary Logistic Regression** | Classifies `Gender` (Male/Female) with ~ X % accuracy (see output). |
| **6 🎯 Multinomial Regression** | Predicts `Device.Model`; shows convergence logs & confusion matrix. |
| **7 🗂️ Export** | Writes the cleaned dataset for reuse. |
| **8 📝 Session Info** | Captures package versions for reproducibility. |

## Key Results
| Task | Metric | Score |
| ---- | ------ | ----- |
| **App-usage time (mins/day)** | RMSE | **41.87** |
|  | R² | **0.94** |
| **Gender classification** | Accuracy | *varies* (see cell output) |
| **Device model prediction** | Accuracy | ~ 18% (baseline-plus but leaves room for improvement) |

*Interpretation*: App-usage time is strongly explained by screen-on time, battery drain, data usage, and behavior class. Classification tasks show moderate to low performance, suggesting additional features or models (e.g., random forest) may help.

## Re-running the Analysis
```R
# Clean & model in one go
source("run_analysis.R")   # (provided script wraps notebook steps)
```
Or execute each notebook cell interactively—ideal for learning and tweaking parameters.

## Troubleshooting
| Symptom | Fix |
| ------- | --- |
| **`magick` compilation error** | Omit `summarytools` cells or install system libs (`libmagick++-dev`). |
| **Package XYZ not found** | `install.packages("XYZ")` inside the notebook. |
| **`ERROR: object ... not found`** | Ensure previous cells executed successfully, or restart the kernel and run all. |

## Roadmap
- [ ] Add cross-validation using `caret::train`  
- [ ] Compare tree-based models (random forest, XGBoost)  
- [ ] Deploy as Shiny dashboard  
- [ ] Dockerfile for one-command reproducibility  

Contributions & feature requests are welcome—see [CONTRIBUTING](CONTRIBUTING.md).

## License
Distributed under the **MIT License**. See `LICENSE` for more information.

## Author
**Sudev Samuel**  
[sudevsamuel7@gmail.com](mailto:sudevsamuel7@gmail.com)  

Feel free to reach out with questions, suggestions, or collaboration ideas!

[1] https://ppl-ai-file-upload.s3.amazonaws.com/web/direct-files/attachments/76186047/ff9f480c-557a-40db-9cb4-410620c4d130/mobile_dataset.ipynb
