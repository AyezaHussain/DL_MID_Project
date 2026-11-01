# Deep Learning Midterm Project

**Student:** Ayeza Hussain  |  **Roll no:** SP24-BBD-033

This repository has the source code and the report for my Deep Learning midterm project. I built two models on two different datasets:

| | Model 1: DNN | Model 2: CNN |
|---|---|---|
| Problem | Predict if a telecom customer will churn | Recognise an American Sign Language letter from an image |
| Dataset | Telco Customer Churn (7,043 customers) | Sign Language MNIST (27,455 train / 7,172 test images, 28x28 grayscale) |
| Model | Dense network 19-128-64-32-1 with dropout (12,929 parameters) | CNN with two convolutional blocks, batch normalization and dropout (1,686,264 parameters) |
| Notebook | [`DNN_Telco_Churn_Final.ipynb`](DNN_Telco_Churn_Final.ipynb) | [`CNN_Sign_Language_MNIST_Final.ipynb`](CNN_Sign_Language_MNIST_Final.ipynb) |

## Datasets (not included, because of their size)

- Telco Customer Churn: https://www.kaggle.com/datasets/blastchar/telco-customer-churn
- Sign Language MNIST: https://www.kaggle.com/datasets/datamunge/sign-language-mnist

## Results (on the test sets)

**DNN (churn)**

| Metric | Logistic Regression (baseline) | DNN |
|---|---|---|
| Accuracy | 0.7395 | 0.7438 |
| Precision (churn) | 0.5059 | 0.5117 |
| Recall (churn) | 0.7968 | 0.7594 |
| F1-score (churn) | 0.6189 | 0.6114 |
| ROC-AUC | 0.8396 | 0.8331 |

The DNN and the logistic regression baseline give almost the same results on this dataset. Class weights were used because only about 27% of the customers churn. The DNN trained for 17 epochs (early stopping) and the test loss was 0.4873.

**CNN (sign language)**

- Test accuracy: **0.9485**, test loss 0.1696, macro F1-score 0.94
- Data split: 21,964 training, 5,491 validation (taken from the training file) and 7,172 test images. The test set was used only for the final evaluation.
- The weakest letters are N (recall 0.71) and R (precision 0.60). Some of the closed-fist signs look very similar at 28x28 pixels.

## Files in this repository

- `DNN_Telco_Churn_Final.ipynb` – Model 1 (DNN), Google Colab notebook with all outputs saved
- `CNN_Sign_Language_MNIST_Final.ipynb` – Model 2 (CNN), Google Colab notebook with all outputs saved
- `Deep_Learning_Midterm_Project_Report.docx` – project report
- `dnn_churn_model.joblib` and `cnn_sign_model.joblib` – the trained models saved with joblib

## How to run

1. Open a notebook in Google Colab (File > Open notebook > GitHub, or upload it).
2. Download the datasets from the Kaggle links above and put the CSV files in the root of your Google Drive (`MyDrive`):
   - `WA_Fn-UseC_-Telco-Customer-Churn.csv` for the DNN notebook
   - `sign_mnist_train.csv` and `sign_mnist_test.csv` for the CNN notebook
3. Run all cells. The notebooks mount Google Drive, so change the file paths in the loading cell if your files are somewhere else.

## Libraries

Python, TensorFlow / Keras, scikit-learn, pandas, NumPy, Matplotlib, Seaborn, joblib.
