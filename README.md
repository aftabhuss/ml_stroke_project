# Stroke Prediction Using Machine Learning

![Python](https://img.shields.io/badge/python-3.8%2B-blue)
![Pandas](https://img.shields.io/badge/pandas-2.0%2B-green)
![scikit--learn](https://img.shields.io/badge/scikit--learn-orange)
![License](https://img.shields.io/badge/license-MIT-brightgreen)

A binary classification project to predict the likelihood of a patient having a stroke based on health and demographic features.

## Dataset

- **File**: `dataset.csv` (not included in repo – download from Kaggle)
- **Source**: [Stroke Prediction Dataset on Kaggle](https://www.kaggle.com/datasets/fedesoriano/stroke-prediction-dataset)
- **Rows**: 5,110
- **Target**: `stroke` (1 = stroke, 0 = no stroke) – highly imbalanced (~5% positive cases)

### Features
| Column               | Description                                      |
|----------------------|--------------------------------------------------|
| gender               | Male / Female / Other                            |
| age                  | Age in years                                     |
| hypertension         | 0 or 1                                           |
| heart_disease        | 0 or 1                                           |
| ever_married         | Yes / No                                         |
| work_type            | Private / Self-employed / Govt_job / children / Never_worked |
| Residence_type       | Urban / Rural                                    |
| avg_glucose_level    | Average glucose level in blood                   |
| bmi                  | Body mass index (missing values filled with median) |
| smoking_status       | formerly smoked / never smoked / smokes / Unknown |
| stroke               | **Target** – 1 if patient had a stroke           |

## Project Structure
├── project.ipynb          ← Complete Jupyter notebook (data loading → modeling → evaluation)
├── dataset.csv            ← (you need to add this)
├── README.md              ← This file

## Key Steps in the Notebook

1. **Exploratory Data Analysis**  
   - Basic info, shape, missing values
2. **Preprocessing**  
   - Drop unnecessary `id` column  
   - Fill missing `bmi` values with median  
   - Outlier detection (IQR method) on `bmi` and `avg_glucose_level`
3. **Handling Class Imbalance**  
   - Resampling technique applied (e.g., SMOTE or RandomUnderSampler – see notebook)
4. **Model Training**  
   - Model trained on resampled data
5. **Evaluation**  
   - Confusion matrix (heatmap)  
   - Classification report (precision, recall, F1-score)

### Latest Results (on test set)
precision    recall  f1-score   support
0       0.97      0.82      0.89       972
1       0.13      0.52      0.21        50
accuracy                           0.81      1022
macro avg       0.55      0.67      0.55      1022
weighted avg       0.93      0.81      0.86      1022

- Good overall accuracy (~81%)  
- High recall on the minority class (stroke) after resampling  
- Trade-off: lower precision for stroke predictions

## How to Run

```bash
# 1. Clone the repo
git clone https://github.com/your-username/stroke-prediction.git
cd stroke-prediction

# 2. (Recommended) Create a virtual environment
python -m venv venv
source venv/bin/activate    # Linux/Mac
# or
venv\Scripts\activate       # Windows

# 3. Install dependencies
pip install pandas numpy scikit-learn seaborn matplotlib jupyter

# 4. Download the dataset
# Place dataset.csv in the repository root

# 5. Launch Jupyter Notebook
jupyter notebook
