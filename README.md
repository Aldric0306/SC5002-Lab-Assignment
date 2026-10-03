# SC5002 Artificial Intelligence Fundamentals & Applications
## Lab Assignment - Classical Search and Regularized Regression

This repository contains the Google Colab notebook for the SC5002 lab assignment. The work covers two main areas:

1. Classical search concepts, including Breadth-First Search (BFS), A* Search, admissible heuristics, and an 8-puzzle problem.
2. Applied machine learning using the California Housing dataset, Linear Regression, Ridge Regression, feature scaling, 5-fold cross-validation, and alpha tuning.

The accompanying submitted report contains the detailed Part 1 calculations and the required Learn-with-AI prompt logs. This repository focuses on the executable Part 2 notebook required for submission.

## Repository Contents

- `SC5002_Lab_Assignment.ipynb` - Google Colab notebook containing the supplied low-code machine-learning workflow.
- `README.md` - project overview, execution instructions, and result summary.
- `requirements.txt` - Python package requirements for local execution outside Google Colab.

## Part 2 Workflow

### Task 2.1 - Dataset Setup and Feature Analysis

The notebook loads the California Housing dataset using `fetch_california_housing(as_frame=True)` and samples 1,000 records using `random_state=42` for reproducibility.

The target variable is `MedHouseVal`. The eight input features are:

- `MedInc`
- `HouseAge`
- `AveRooms`
- `AveBedrms`
- `Population`
- `AveOccup`
- `Latitude`
- `Longitude`

All predictors are standardized using `StandardScaler` before model training.

### Task 2.2 - Model Training and Alpha Tuning

The notebook evaluates:

| Model | Hyperparameter | Mean 5-Fold CV R² |
|---|---:|---:|
| Linear Regression | None | 0.6457 |
| Ridge Regression | α = 0.1 | 0.6457 |
| Ridge Regression | α = 10.0 | 0.6443 |
| Ridge Regression | α = 1000.0 | 0.3574 |

The results show that weak-to-moderate Ridge regularization produces performance close to ordinary Linear Regression, while an extremely large penalty causes substantial underfitting.

### Task 2.3 - Visual Analysis

The notebook generates a bar chart comparing the mean 5-fold cross-validation R² score for Linear Regression and the three Ridge Regression settings.

The most visible result is the sharp performance decrease at `alpha = 1000`, illustrating the effect of excessive coefficient shrinkage.

## How to Run in Google Colab

1. Open `SC5002_Lab_Assignment.ipynb` in Google Colab.
2. Select **Runtime -> Run all**.
3. Allow the California Housing dataset to download if prompted.
4. Confirm that the final comparison chart is displayed.
5. Save the executed notebook so the runtime outputs remain embedded.

No manual dataset upload is required because the notebook obtains the dataset through scikit-learn.

## Local Execution

If running locally instead of in Colab:

```bash
pip install -r requirements.txt
jupyter notebook SC5002_Lab_Assignment.ipynb
```

Internet access is required the first time `fetch_california_housing` downloads the dataset.

## Reproducibility

The notebook follows the assignment template and uses the specified random seeds:

- dataset sample: `random_state=42`
- train/test split: `random_state=42`
- cross-validation: 5 folds

Using the same package versions and dataset should produce the same or very similar reported scores.

## Use of Generative AI

Generative AI was used as a learning assistant in accordance with the assignment requirements. It was used to clarify concepts such as admissible heuristics, verify A* node-selection calculations, explain feature scaling and Ridge regularization, and interpret cross-validation results. The exact prompts and reflections are documented in the submitted PDF report.

## Submission Checklist

Before submitting the GitHub link, verify that:

- the repository is set to **Public**;
- `SC5002_Lab_Assignment.ipynb` opens correctly;
- the notebook has been executed and saved with its outputs visible;
- the comparison chart appears in the notebook;
- `README.md` renders correctly on the repository front page;
- there are no private credentials, tokens, or unrelated files in the repository.
