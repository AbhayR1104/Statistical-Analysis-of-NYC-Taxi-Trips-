# Statistical Analysis of NYC Taxi Trips 🚕

This repository contains a comprehensive statistical analysis of New York City taxi trip data from February and March 2022. The project explores various statistical methods to clean, analyze, and model the dataset, covering everything from data preprocessing to hypothesis testing and predictive modeling. This was originally completed as a final project for a Probability and Statistics course.

## 📋 Table of Contents
1. [Project Overview](#-project-overview)
2. [Key Analyses Performed](#-key-analyses-performed)
3. [Tech Stack](#-tech-stack)
4. [Setup and Installation](#-setup-and-installation)
5. [Summary of Results](#-summary-of-results)

---

## 📖 Project Overview

The goal of this project was to apply a wide range of statistical techniques to a real-world dataset.The dataset contains information about taxi trips, including distance, duration, fare amounts, and passenger counts.This project follows a structured approach to answer several statistical questions about the data.

### Data Preprocessing

**Dataset Cleaning**: Removed trips with zero distance and handled negative or zero values in key columns by marking them as `NaN` for imputation. 
**Outlier Detection**: Applied Tukey's rule ($\alpha=1.5$) to detect and handle outliers in `passenger_count`, `trip_duration`, and `fare_amount`. 
**Linear Interpolation**: Filled missing values by performing linear interpolation sorted by pickup time, scaled by trip distance to ensure realistic estimates.

---

## 📈 Key Analyses Performed

A series of statistical tests and models were built to analyze the data:

**Hypothesis Testing (t-test, Z-test, Wald's test)**: Conducted tests to determine if there was a statistically significant difference in the mean `trip_distance` and `fare_amount` between February and March.
**Distribution Comparison (K-S & Permutation Tests)**: Used 1-sample and 2-sample K-S tests, as well as a permutation test, to check if `trip_duration` and `fare_amount` follow the same distribution.
**Linear Regression**: Built regression models to predict `total_amount` using `trip_distance` and `trip_duration`, both separately and together, evaluating the models with SSE and MAPE.
**Time Series Analysis**: Predicted the median `total_amount` for the final day of the dataset using AR(2), AR(3), EWMA, and SMA models on the daily median trip amounts. [cite: 76, 77, 79]
**Chi-Square Test**: Investigated the dependency between `tip_amount` and `passenger_count` by categorizing them as "high" or "low" based on their median values. [cite: 86, 87]
**Bayesian Inference**: Modeled the `trip_distance` using Bayesian methods, starting with a Normal prior for the mean and updating it to find the posterior distribution after observing data from two consecutive months.

---

## 🛠️ Tech Stack

* **Language**: Python
* **Core Libraries**: Pandas, NumPy, Scipy
* **Environment**: Jupyter Notebook / Google Colab

---

## 🚀 Setup and Installation

To reproduce this analysis, follow these steps:

1.  **Clone the repository:**
    ```sh
    git clone [https://github.com/](https://github.com/)[YOUR_USERNAME]/[YOUR_REPO_NAME].git
    cd [YOUR_REPO_NAME]
    ```
2.  **Create a virtual environment (recommended):**
    ```sh
    python3 -m venv venv
    source venv/bin/activate
    ```
3.  **Install dependencies:**
    ```sh
    pip install -r requirements.txt
    ```
4.  **Add Data**: Download the `2022-02.csv` and `2022-03.csv` files and place them in the root directory.
5.  **Run the analysis**: Open and run the `Probstats_FinalProject_notebook.ipynb` in a Jupyter environment.

---

## 📊 Summary of Results

* **Outlier Detection**: A total of **17,987** outliers were detected for `passenger_count`, **7,686** for `trip_duration`, and **8,782** for `fare_amount`.
* **Hypothesis Testing**: Wald's test indicated a significant difference in means for both trip distance and fare amount between the two months, while the Z-test and t-test did not.
* **Linear Regression**: The model combining both `trip_duration` and `trip_distance` provided a better fit for predicting `total_amount`, with a lower SSE (6.67e12) and MAPE (340.63).
* **Time Series**: The AR(3) model was the most accurate for predicting the final day's median trip amount, with the lowest MAPE of 3.23.
* **Chi-Square Test**: The test revealed a statistically significant dependency between the amount of tip given and the number of passengers in a trip.
