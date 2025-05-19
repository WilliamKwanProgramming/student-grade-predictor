# Student Performance Indicator

### Dataset Details

Coded through a data science project at UofT in Fall 2024. My contribution extends to the Jupyter Notebooks for EDA and Model Training. Front end (flask, web) is done by my good friend and colleague Frank B.!

This project investigates how factors such as parental background, test preparation, and other variables influence students' performance on math exams.

The dataset includes eight features:

- `gender`: The student’s sex (Male/Female)
- `race/ethnicity`: The student’s ethnic group (A, B, C, D, or E)
- `parental level of education`: The highest level of education achieved by the student’s parent(s) (e.g., high school, associate’s degree, bachelor’s degree, master’s degree)
- `lunch`: Type of lunch provided (standard or free/reduced)
- `test preparation course`: Whether the student completed a prep course before the exam (yes/no)
- `reading score`: The score the student received on the reading section
- `writing score`: The score the student received on the writing section

**Target variable:**

- `math score`: The student’s score on the math exam.

**Dataset Source:**

[Students Performance in Exams on Kaggle](https://www.kaggle.com/datasets/spscientist/students-performance-in-exams?resource=download)

---

## UI Animation

![HomepageUI](./screenshots/stdperformanceindicator.gif)

---

## Project Workflow

1. **Data Ingestion**

   - Load the data from the CSV file.
   - Split the data into training and testing sets and save each as a separate CSV.

2. **Data Transformation**

   - Build a `ColumnTransformer` pipeline:
     - **Numeric features:** Fill missing values with the median (to handle outliers) and apply standard scaling.
     - **Categorical features:** Fill missing values with the most frequent category, perform one-hot encoding, then apply standard scaling.
   - Save the fitted transformer as a `.pkl` file in the `artifacts` folder.

3. **Model Training**

   - Train several regression models and evaluate their performance.
   - Identify Linear Regression as the best model, then perform hyperparameter tuning.
   - Serialize the final model to a pickle file for use in the prediction pipeline.

4. **Prediction Pipeline**

   - Accept new input data, convert it into a DataFrame, load the necessary pickle files (transformer and model), and output the predicted math score.

5. **Flask Web App**

   - Create a Flask application with a user interface that allows users to enter feature values and receive a predicted math score in their browser.

---

## Notebooks

- **Exploratory Data Analysis:** [EDA Notebook](./notebook/eda_on_data.ipynb)
- **Model Training:** [Model Training Notebook](./notebook/model_training.ipynb)

---

## How to Run

1. Create a Conda environment:
   ```bash
   conda create -p std python=3.8 -y
   ```
2. Activate the env:
   ```bash
   conda activate std/
   ```
3. Install deps:
   ```bash
   pip install -r requirements.txt
   ```
4. Start the app!:
   ```bash
   python app.py
   ```
5. Open your browser and go to `https://127.0.0.1:5000/`
