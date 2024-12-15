# Udacity_Rohlik_Sales_Forecasting

This is the Final Project in the Data Scientist Nanodegree program. You can check the project here: https://github.com/TranDat24318791998/Udacity_Rohlik_Sales_Forecasting
For this project, I selected the task of forecasting sales for Rohlik's products as the final project. This project is also part of an ongoing Kaggle competition. You can check the competition details at the following link:  
[https://www.kaggle.com/competitions/rohlik-sales-forecasting-challenge-v2/overview](https://www.kaggle.com/competitions/rohlik-sales-forecasting-challenge-v2/overview).

---

## 1. Overview of the Project

Rohlik Group has a core problem of forecasting the sales of various products across their warehouses, based on historical sales data and product attributes such as holidays, inventory characteristics, and other time-related features.  

### Data Used for the Task:
The dataset consists of the following files:
- `sales_train.parquet`: Historical sales data for individual products on a daily basis.
- `calendar.csv`: Information about calendar-specific events like holidays.
- `inventory.csv`: Data related to product inventories.
- `sales_test.csv`: Data used for predicting sales in the final submission.
- `test_weights`: Weights assigned to each product for computing the evaluation score.

---

## 2. Libraries and Tools Used

The following libraries are required to run the project:

- `lightgbm==4.5.0`
- `matplotlib==3.8.4`
- `numpy==2.0.0`
- `pandas==2.2.3`
- `scikit-learn==1.4.2`
- `seaborn==0.13.2`
- `tqdm==4.66.4`

---

## 3. Problem-Solving Approach

To solve this task, I used tree-based models implemented via the **LightGBM framework**. In addition, I applied advanced techniques such as **cross-validation** and **ensembling** to ensure robust and reliable predictions. Below are the details of the methodology:

### **3.1. Splitting Training and Validation Data**
- To ensure that the model generalizes well, I divided the training and validation data based on time. Specifically, the last two weeks of the dataset are used for validation, while the remaining data before this period is used for training.
- **Cross-validation setup**: 
  - I used a time-based cross-validation method with `k=5` folds. In each fold:
    - **Fold 1**: The last two weeks are used as the validation set, and the preceding data is used as the training set.
    - **Fold 2**: The second-to-last two weeks are used as the validation set, and the corresponding training data is adjusted accordingly.
    - This process continues until the folds cover the entire dataset.

> **Note:** The reason for this setup is to mimic the real-world scenario where the model must predict future sales using only past data. This ensures that there is no data leakage during validation.

### **3.2. Ensembling Method**
- I used a simple ensemble technique where the final prediction is the average of the outputs from five models trained on different folds.

---

## 4. Setup Instructions

To ensure all dependencies are correctly installed, run the following command:
```bash
pip install -r requirements.txt
```
After installing the dependencies, open and execute the notebook end_to_end_flow.ipynb to review the analysis, training, and predictions.

## 5. Acknowledgments
I would like to thank Udacity and Kaggle for providing such an engaging environment for learners in the field of data science.
