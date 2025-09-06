## End to ENd ML project
Perfect! Let’s make a **more detailed, modular README** that highlights everything you’ve done, including the ML pipeline, modular coding approach, and libraries used.

  Watch the working at : https://youtu.be/dLlDznzrWlU (AWS Codepipeline issues wrt to CD so had to host it locally)
---

# Student Exam Performance Prediction

A **Flask web application** to predict student math scores based on demographic and academic features using a **modular machine learning pipeline**. This project demonstrates **end-to-end ML workflow**: data ingestion, preprocessing, model training, evaluation, and deployment on **AWS Elastic Beanstalk**.

---

## Table of Contents

* Project Overview
* Libraries and Technologies
* Project Structure
* Features
* Installation
* Usage
* Machine Learning Pipeline
* Deployment on AWS Elastic Beanstalk
* Author

---

## Project Overview

This project predicts a student's **math score** using the following features:

* Gender
* Race/Ethnicity
* Parental Level of Education
* Lunch Type
* Test Preparation Course
* Reading Score
* Writing Score

The ML workflow is **modular**, allowing easy updates and retraining of models.

---

## Libraries and Technologies Used

**Python Libraries**:

* `pandas`, `numpy` – Data manipulation and numerical computations
* `scikit-learn` – Preprocessing, pipelines, model evaluation
* `catboost`, `xgboost` – Gradient boosting models
* `matplotlib`, `seaborn` – Data visualization
* `flask` – Web application framework
* `dill` – Serialization of models and preprocessing objects

**Other Tools**:

* AWS Elastic Beanstalk – Deployment
* Git & GitHub – Version control
* HTML/CSS – Frontend templates

---

## Project Structure

```
mlproject/
│
├── src/
│   ├── components/
│   │   ├── data_ingestion.py        # Load and split dataset
│   │   ├── data_transformation.py   # Preprocessing pipelines
│   │   └── model_trainer.py         # Train and evaluate ML models
│   ├── pipeline/
│   │   └── predict_pipeline.py      # Inference pipeline
│   ├── utils.py                     # Utility functions (save/load models)
│   ├── exception.py                 # Custom exceptions
│   └── logger.py                    # Logging configuration
│
├── templates/
│   ├── home.html                     # Prediction form
│   └── index.html                    # Landing page
│
├── artifacts/                        # Saved models, preprocessors, datasets
├── requirements.txt                  # Python dependencies
├── .gitignore
├── application.py                    # Flask app entry point
├── setup.py                          # Package installation
└── README.md
```

---

## Features

* **Web Interface:** Submit student data and get predicted math score.
* **Modular ML Pipeline:** Separate modules for data ingestion, preprocessing, and model training.
* **Multiple Models:** RandomForest, GradientBoosting, XGBoost, CatBoost, DecisionTree, LinearRegression, KNeighbors, AdaBoost.
* **Model Selection:** Automatically selects the best performing model based on R² score.
* **Preprocessing Serialization:** Saves preprocessing pipeline (`preprocessor.pkl`) for inference.
* **Logging:** Logs all operations and exceptions for easy debugging.
* **AWS Deployment Ready:** Configured for Elastic Beanstalk deployment.

---

## Installation

1. Clone the repository:

```bash
git clone https://github.com/<your-username>/mlproject.git
cd mlproject
```

2. Create a **Python 3.9 virtual environment**:

```bash
python -m venv venv
source venv/bin/activate   # Linux/Mac
venv\Scripts\activate      # Windows
```

3. Install dependencies:

```bash
pip install -r requirements.txt
```

---

## Usage

1. Run the Flask app locally:

```bash
python application.py
```

2. Open the browser at `http://127.0.0.1:5000/`.
3. Fill in the student details and submit the form.
4. View the predicted math score.

---

## Machine Learning Pipeline

1. **Data Ingestion (`data_ingestion.py`)**

   * Loads the dataset (`stud.csv`).
   * Splits into train/test (80/20).
   * Saves raw, train, and test CSVs in `artifacts/`.

2. **Data Transformation (`data_transformation.py`)**

   * Preprocessing pipelines for categorical and numerical columns.
   * Categorical: OneHotEncoder + StandardScaler
   * Numerical: SimpleImputer + StandardScaler
   * Saves preprocessor as `preprocessor.pkl`.

3. **Model Training (`model_trainer.py`)**

   * Trains multiple regressors: RandomForest, GradientBoosting, XGBoost, CatBoost, DecisionTree, LinearRegression, KNeighbors, AdaBoost.
   * Performs GridSearchCV to find best hyperparameters.
   * Selects **best model** based on test R² score.
   * Saves best model as `model.pkl`.

4. **Prediction Pipeline (`predict_pipeline.py`)**

   * Loads `preprocessor.pkl` and `model.pkl`.
   * Accepts user input and outputs predicted math score.

5. **Custom Logging & Exceptions**

   * `logger.py` logs key operations.
   * `exception.py` handles and formats exceptions for debugging.

---

## Deployment on AWS Elastic Beanstalk

1. Install **EB CLI**:

```bash
pip install awsebcli
```

2. Initialize Elastic Beanstalk:

```bash
eb init -p python-3.9 mlproject --region <your-region>
```

3. Create an environment:

```bash
eb create mlproject-env
```

4. Deploy your app:

```bash
eb deploy
```

5. Open your deployed app:

```bash
eb open
```

**WSGI Configuration (`.ebextensions/option_settings.config`):**

```yaml
aws:elasticbeanstalk:container:python:
  WSGIPath: application:application
```

---

## Author

**Akshaykumar Garur**
Email: [akshaygarur5305@gmail.com](mailto:akshaygarur5305@gmail.com)

---

If you want, I can **also create a short diagram for the ML pipeline and folder structure** that you can include in the README—it makes it look very professional for GitHub.

Do you want me to create that diagram?

