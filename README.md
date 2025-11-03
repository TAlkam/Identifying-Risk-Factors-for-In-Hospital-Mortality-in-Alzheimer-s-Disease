# Identifying-Risk-Factors-for-In-Hospital-Mortality-in-Alzheimer-s-Disease

# 🧠 Identifying Risk Factors for In-Hospital Mortality in Alzheimer’s Disease

This repository contains a reproducible pipeline and analysis notebook for identifying high-impact predictors of **in-hospital mortality among patients with Alzheimer’s Disease (AD)** using **dual modeling approaches**: traditional logistic regression and explainable machine learning (XGBoost + SHAP). The project utilizes nationally representative data from the **2017 HCUP Nationwide Inpatient Sample (NIS)** and follows a rigorous methodology suitable for publication and clinical translation.

## 📌 Overview

Older adults with Alzheimer’s disease are at elevated risk of dying during hospitalization. This project aims to:

* Compare **survey-weighted logistic regression** vs. **XGBoost** classifiers.
* Identify top predictors using **odds ratios** and **SHAP values**.
* Evaluate performance through **AUROC**, **AUPRC**, **Brier score**, and **log loss**.
* Perform **sensitivity analysis** by removing end-of-life indicators (palliative care and DNR).
* Provide interpretable visualizations and feature explanations for clinical audiences.

## 📊 Methods

* **Data**: HCUP NIS 2017 subset of patients aged ≥60 years with Alzheimer's Disease.
* **Outcome**: In-hospital mortality (`died`).
* **Features**: Age, sex, comorbidities (from top 20 ICD-10 diagnoses), hospital characteristics, DNR and palliative care flags.
* **Modeling**:

  * Logistic regression (survey-weighted)
  * XGBoost with SHAP-based explainability
* **Sensitivity Analysis**: Models were re-run after excluding `dnr` and `pall` to test generalizability.

## 🚀 Getting Started

### 1. Clone the Repository

```bash
git clone https://github.com/yourusername/ad-mortality-risk.git
cd ad-mortality-risk
```

### 2. Install Dependencies

Run the following inside your Python environment (e.g., Colab or virtualenv):

```bash
pip install -r requirements.txt
```

Or, manually install:

```bash
pip install pandas pyreadstat shap scikit-learn xgboost matplotlib openpyxl
```

### 3. Open Notebook

Launch the notebook in **Google Colab** or Jupyter:

```bash
jupyter notebook Identifying_Risk_Factors_for_In_Hospital_Mortality_in_Alzheimer’s_Disease.ipynb
```

Ensure your `.dta` and `ICD-10` description files are uploaded into your working directory (or mounted to Colab).

## 📁 File Structure

```
├── Identifying_Risk_Factors_for_In_Hospital_Mortality_in_Alzheimer’s_Disease.ipynb
├── section111validicd10-jan2025_0.xlsx        # ICD-10 code descriptions
├── NIS_2017_Core_data_alz_only.dta            # Cleaned Stata file (user-provided)
├── outputs/
│   ├── shap_summary_plot.png
│   ├── shap_bar_plot.png
│   └── model_performance_table.csv
```

> ⚠️ Due to HCUP data restrictions, the dataset is **not included** in this repo. You must obtain access to NIS 2017 data from [HCUP](https://www.hcup-us.ahrq.gov/nisoverview.jsp).

## 📈 Key Results

* **Logistic Regression AUROC**: 0.8789 (Full), 0.8075 (Sensitivity)
* **XGBoost AUROC**: 0.8866 (Full), 0.8950 (Sensitivity)
* Dominant predictors: acute respiratory failure, sepsis, DNR status, palliative care, aspiration pneumonia.
* SHAP plots provided intuitive interpretation of feature importance.

## 📉 Sensitivity Analysis

DNR and palliative care were excluded to simulate non-terminal case modeling. XGBoost maintained robust performance, while logistic regression's AUROC dropped, demonstrating the nonlinear model's ability to detect latent mortality risk.

## 🧠 SHAP Explainability

SHAP (SHapley Additive exPlanations) was used to visualize feature impact:

* `shap.summary_plot()`: Direction and distribution of top predictors
* `shap.bar_plot()`: Global importance ranking

These visualizations bridge statistical modeling with clinical interpretability.

## 📄 Citation

If you use this notebook or findings in your research, please cite:

> Alkam T, et al. Identifying Risk Factors for In-Hospital Mortality in Alzheimer’s Disease: A Dual Approach Using Regression and Explainable Machine Learning. *[Journal Name]*. 2025. (Under Review)

## 🧑‍⚕️ Author

**Dr. Tursun Alkam**
MD, PhD, MBA, MSAAI (c)

## 📜 License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

---

Let me know if you’d like a `requirements.txt` generated or if you'd like a `LICENSE` or `GitHub Actions` CI setup.
