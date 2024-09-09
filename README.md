---

# Credit Card Fraud Detection Analysis

This project performs exploratory data analysis (EDA) on credit card transaction data to identify fraudulent transactions. It includes data visualization and preprocessing to better understand the distribution and patterns of fraud in the dataset.

## Table of Contents

- [Introduction](#introduction)
- [Requirements](#requirements)
- [Data](#data)
- [Usage](#usage)
- [Results](#results)
- [Contributing](#contributing)
- [License](#license)

## Introduction

Credit card fraud detection is a critical task in the financial industry. This project utilizes various Python libraries to visualize and analyze credit card transaction data, helping to uncover patterns that may indicate fraudulent activity.

## Requirements

To run this project, you will need:

- Python 3.x
- pandas
- numpy
- matplotlib
- seaborn
- imbalanced-learn
- scikit-learn

You can install the required libraries using pip:

```bash
pip install pandas numpy matplotlib seaborn imbalanced-learn scikit-learn
```

## Data

The analysis uses a dataset named `cc_fraud`, which contains the following columns:

- `Time`: Timestamp of the transaction
- `Amount`: Amount of the transaction
- `Class`: Class label indicating whether the transaction is fraudulent or valid

## Usage

1. **Import Libraries**: Start by importing necessary libraries for data manipulation and visualization.

    ```python
    import os
    import pandas as pd
    import numpy as np
    import matplotlib.pyplot as plt
    import seaborn as sns
    from imblearn.over_sampling import RandomOverSampler, SMOTE
    import datetime
    ```

2. **Load Data**: Load your credit card fraud dataset into a pandas DataFrame named `cc_fraud`.

    ```python
    cc_fraud = pd.read_csv('path_to_your_data.csv')
    ```

3. **Visualizations**: Generate various plots to explore the data:

    - **Class Distribution**: Shows the proportion of valid vs. fraudulent transactions.

        ```python
        plt.figure()
        sns.countplot(x='Class', data=cc_fraud)
        plt.title("Class Distribution")
        plt.show()
        ```

    - **Transaction Amount Distribution**: Compares the distribution of transaction amounts between valid and fraudulent transactions.

        ```python
        plt.figure()
        sns.boxplot(data=cc_fraud, x='Class', y='Amount')
        plt.title("Distribution of Transaction Amount")
        plt.yscale('log')
        plt.show()
        ```

    - **Fraudulent Transactions by Hour**: Analyzes the frequency of fraudulent transactions by hour of the day.

        ```python
        plt.figure()
        sns.countplot(data=cc_fraud[cc_fraud['Class'] == 'Fraud'], x='hour', color='red')
        plt.title("Fraudulent Transactions by Hour")
        plt.show()
        ```

4. **Preprocessing**: Convert timestamps to hours and handle missing values.

    ```python
    def convert_time(sec):
        return datetime.datetime.fromtimestamp(sec)
    
    cc_fraud_time = cc_fraud[['Time', 'Amount', 'Class']].copy()
    cc_fraud_time['time'] = cc_fraud_time['Time'].apply(convert_time)
    ```

## Results

The visualizations and preprocessing steps reveal insights into the dataset:

- The class distribution shows a significant imbalance between valid and fraudulent transactions.
- The distribution of transaction amounts suggests that fraudulent transactions tend to be larger.
- Analyzing the hour of the day reveals patterns in the timing of fraudulent transactions.

## Contributing

If you want to contribute to this project, please fork the repository and submit a pull request with your changes. Make sure to update the README file accordingly.

---

Feel free to adjust or add any details specific to your project or dataset.
