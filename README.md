# Hill vs. Valley SVM Classifier

## Project Overview
This project aims to automatically classify sequences of points as either a "valley" (1) or a "hill" (0) using a Support Vector Machine (SVM) algorithm. The project explores the impact of data noise on model performance and generalization.

## Dataset
The dataset is sourced from the **UCI Machine Learning Repository**. It contains instances characterized by 100 numeric attributes and a single binary label.
The data is analyzed in two variations:
* **Without noise:** Smooth transitions between points. Contains 606 training instances and 121 testing instances.
* **With noise:** Irregular variations. Contains 606 training instances and 121 testing instances.

## Technologies Used
* **Python** * **Pandas & NumPy** - Data manipulation and preprocessing.
* **Scikit-learn** - SVM model training, evaluation, and data scaling (`StandardScaler`).
* **Matplotlib** - Visualizing results and confusion matrices.

## Methodology & Hyperparameter Tuning
To achieve the best accuracy, an exhaustive grid search approach was implemented using `itertools.product` to test combinations of SVM hyperparameters:
* **C (Error penalty/Cost):** Values ranging from 2^-5 to 2^7.
* **Gamma (Point influence):** Values ranging from 2^-15 to 2^3.

## Results
The model was evaluated using accuracy scores and confusion matrices for both datasets.

### 1. Noisy Data Performance
* **Best Accuracy:** 0.6221 (with C=128, gamma=0.03125).
* **Observations:** The model correctly identified 262 "hill" examples and 115 "valley" examples. It achieved a high recall (88%) for Class 0 (hill) but struggled with Class 1 (valley), misclassifying nearly two-thirds of them. 

### 2. Clean Data (Without Noise) Performance
* **Best Accuracy:** 0.6040 (with C=128, gamma=8).
* **Observations:** The model correctly identified 267 "hill" examples and 99 "valley" examples[cite: 45, 46]. The recall for Class 0 remained high (91%), while Class 1 detection remained poor (32%).

## Key Takeaways & Conclusions
* **Classification Bias:** In both scenarios, the model exhibited a strong bias towards predicting Class 0 (hills), resulting in a high recall for hills but a poor detection rate for valleys.
* **The Impact of Noise:** Counterintuitively, the SVM model achieved slightly better overall accuracy on the noisy dataset[cite: 51]. This suggests that the noise forces the model to learn a more generalized decision boundary, preventing it from excessively relying on fine details or perfect transitions present in the clean data[cite: 52].
