# EPL Match Winner Prediction

[![Python](https://img.shields.io/badge/Python-3.8%2B-blue)](https://www.python.org/)
[![License](https://img.shields.io/badge/License-MIT-green)](./LICENSE)

Predict the outcome of English Premier League matches using machine learning and historical match data. This project leverages web scraping, data cleaning, feature engineering, and Random Forest classification to make informed predictions.

---

## Table of Contents

- [EPL Match Winner Prediction](#epl-match-winner-prediction)
  - [Table of Contents](#table-of-contents)
  - [Project Overview](#project-overview)
    - [data\_scrape.ipynb](#data_scrapeipynb)
    - [ml\_predictions.ipynb](#ml_predictionsipynb)
  - [Technologies Used](#technologies-used)
  - [Repository Structure](#repository-structure)
  - [Installation and Setup](#installation-and-setup)
  - [Model Evaluation](#model-evaluation)
  - [Credits / Acknowledgment](#credits--acknowledgment)

---

## Project Overview

The project is divided into two main parts: **Scraping** and **Prediction**.

### data_scrape.ipynb

We scrape match results from the EPL to build a dataset for predicting match winners. The notebook uses the `requests` library to download data and Beautiful Soup to parse HTML, extracting the relevant tables. The data is then loaded into pandas for cleaning and preparation for the machine learning model.

**Workflow recap:**

- Start with the standings_url for the Premier League
- Scrape the table data from the HTML page
- Access each team's individual page
- Scrape scores and fixtures for each match of that team
- Scrape shooting stats for each match of that team
- Combine the data frames for each team
- Loop through each season and selected teams to consolidate into a single data frame
- Merge everything and perform minor data cleanup

### ml_predictions.ipynb

This notebook predicts winners for EPL matches using the scraped dataset.

**Steps included:**

- Load match data into pandas and clean it
- Apply a Random Forest machine learning model to predict match outcomes
- Measure the algorithm's performance and improve model accuracy
- Continue iteratively improving the model

**Summary of the Prediction process:**

- Scraped data about Premier League matches
- Cleaned the data and prepared it for the ML model
- Created a simple ML model with a few predictors and a target
- Trained a Random Forest model
- Computed accuracy and precision scores
- Improved accuracy by generating more predictors using rolling averages
- Enhanced precision by analyzing both sides of the matches of team A and team B
- Achieved a final model precision of 67.5 percent

**Possible next steps:**

- Scrape more seasons, ideally 10 to 20, to improve predictions
- Use additional columns in the dataset to generate more features for the model

---

## Technologies Used

- Python 3.8+
- Pandas for data manipulation and analysis
- Scikit-learn for machine learning
- Requests for web scraping
- Beautiful Soup for HTML parsing
- Jupyter Notebook for interactive development

---

## Repository Structure

epl-ml-match-winner-prediction/<br>
│<br>
├── data_scrape.ipynb # Notebook to scrape EPL match data<br>
├── ml_predictions.ipynb # Notebook for ML model training and evaluation<br>
├── matches_data.csv # Raw match data collected<br>
├── requirements.txt # Python dependencies<br>
└── LICENSE # Project license<br>

---

## Installation and Setup

1. Clone the repository

```bash
git clone https://github.com/andreyestevam/epl-ml-match-winner-prediction.git
cd epl-ml-match-winner-prediction
```

2. Install required packages
```bash
pip install -r requirements.txt
```

3. Run Jupyter Notebooks<br>
You can either: Scrape the data (can be slightly different than the one collected in this repository due to possible website changes):
```bash
jupyter notebook data_scrape.ipynb
```
Or: Train and Evaluate the ML model:
```bash
jupyter notebook ml_predictions.ipynb
```

## Model Evaluation
The Random Forest model is evaluated using accuracy and precision metrics. Initial models are simple, but precision improves significantly by adding rolling averages, using more predictors, and considering both teams' historical performance. The final precision achieved, with the existing data in this repository, is 67.5 percent.

## Credits / Acknowledgment

This project was inspired by a project-based learning approach. All data cleaning, feature engineering, and machine learning modeling were implemented independently, reflecting hands-on experimentation and practical learning with Python, Pandas, Beautiful Soup, and scikit-learn.