# SmartCar Price Estimator

**ML-Powered Used Car Price Prediction | Google Colab + Google Drive**

> Predicts used car market prices using 5 regression algorithms trained on a 19,237-row dataset. Built with scikit-learn, deployed via an interactive ipywidgets UI in Google Colab.

---

## Dataset

**Car Prices Dataset** — Sidharth178  
Source: [https://www.kaggle.com/datasets/sidharth178/car-prices-dataset](https://www.kaggle.com/datasets/sidharth178/car-prices-dataset)  
Rows: 19,237 | Format: CSV | Platform: Kaggle

> Download the dataset from the link above and upload `train.csv` to your Google Drive before running the training notebook.

---

## Project Files

| File | Description |
|------|-------------|
| `train.csv` | Dataset — 19,237 rows of used car listings |
| `SmartCar_Training.ipynb` | Model training notebook (5 algorithms, evaluation, charts) |
| `SmartCar_UI.ipynb` | Interactive price estimator UI |

---

## Quick Start

### Step 1 — Prepare Google Drive

1. Open Google Drive → click **New** → **New Folder** → name it `SmartCar`
2. Inside `SmartCar`, create two sub-folders: `models` and `assets`
3. Upload `train.csv` to the `SmartCar` folder
4. Place both `.ipynb` notebooks in the same folder *(optional but recommended)*

Your Drive structure should look like this:

```
MyDrive/
└── SmartCar/
    ├── train.csv
    ├── SmartCar_Training.ipynb
    ├── SmartCar_UI.ipynb
    ├── models/          ← .pkl files will be saved here
    └── assets/          ← charts will be saved here
```

### Step 2 — Run the Training Notebook

1. Open `SmartCar_Training.ipynb` in Google Colab
2. **Cell 1** — Mounts Google Drive; click **Allow** when prompted
3. Run all cells top to bottom (`Runtime → Run all`)
4. On completion, 5 `.pkl` model files and chart images will be saved to Drive

### Step 3 — Run the UI Notebook

1. Open `SmartCar_UI.ipynb` in Google Colab
2. Run all cells
3. An interactive form will appear — fill in the car details and click **Estimate Price**

---

## Dataset Columns

| Column | Type | Description |
|--------|------|-------------|
| `Price` | Target | Car selling price (USD) |
| `Manufacturer` | Categorical | Brand name (Toyota, BMW, etc.) |
| `Prod. year` | Numeric | Year of manufacture |
| `Category` | Categorical | Sedan, Jeep, Hatchback, etc. |
| `Fuel type` | Categorical | Petrol, Diesel, Hybrid, etc. |
| `Engine volume` | Numeric | Engine displacement in litres |
| `Mileage` | Numeric | Distance driven in kilometres |
| `Gear box type` | Categorical | Manual / Automatic / Tiptronic |
| `Cylinders` | Numeric | Number of engine cylinders |
| `Levy` | Numeric | Tax or import levy amount |
| `Leather interior` | Categorical | Yes / No |
| `Drive wheels` | Categorical | Front / Rear / 4x4 |
| `Doors` | Numeric | Number of doors |
| `Airbags` | Numeric | Number of airbags |
| `Color` | Categorical | Exterior car color |

---

## Machine Learning Algorithms

| # | Algorithm | Notes |
|---|-----------|-------|
| 1 | Linear Regression | Baseline model |
| 2 | Decision Tree | Rule-based splits, max depth 10 |
| 3 | Random Forest | 100 estimators — expected best accuracy |
| 4 | Gradient Boosting | Sequential ensemble, 100 estimators |
| 5 | SVR | RBF kernel — requires scaled input |

The best-performing model is automatically selected and saved. All models are evaluated on **R² Score**, **RMSE**, and **MAE**.

---

## Output Files

After training, the following files are saved to `MyDrive/models/` and `MyDrive/assets/`:

**Model Files (`models/`)**

| File | Description |
|------|-------------|
| `best_model.pkl` | Best performing trained model |
| `scaler.pkl` | StandardScaler (used by SVR) |
| `label_encoders.pkl` | LabelEncoders for categorical columns |
| `feature_names.pkl` | Column order for inference |
| `best_model_name.pkl` | Name string of the best model |

**Chart Files (`assets/`)**

| File | Description |
|------|-------------|
| `model_comparison.png` | R², RMSE, MAE bar chart for all 5 models |
| `feature_importance.png` | Random Forest feature importance ranking |
| `correlation_matrix.png` | Heatmap showing correlation between all numeric features |

---

## Troubleshooting

| Issue | Fix |
|-------|-----|
| Drive mount fails | `Runtime → Restart Runtime` → re-run from Cell 1 |
| `DRIVE_PATH` error | Verify exact folder name in Drive — it is case-sensitive |
| Model file not found | Run the Training notebook completely before opening the UI |
| Prediction returns very low value | Check that `Mileage` and `Levy` inputs are in correct units |

---

## Author

**Zara Naeem**

---

*SmartCar Price Estimator — Machine Learning Regression Project*