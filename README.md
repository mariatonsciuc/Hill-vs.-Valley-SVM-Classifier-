# Hill vs. Valley SVM Classifier

## Project Overview
[cite_start]This project aims to automatically classify sequences of points as either a "valley" (1) or a "hill" (0) using a Support Vector Machine (SVM) algorithm[cite: 8, 19, 20]. The project explores the impact of data noise on model performance and generalization.

## Dataset
[cite_start]The dataset is sourced from the **UCI Machine Learning Repository**[cite: 10]. [cite_start]It contains instances characterized by 100 numeric attributes and a single binary label[cite: 18].
The data is analyzed in two variations:
* [cite_start]**Without noise:** Smooth transitions between points[cite: 11, 13]. [cite_start]Contains 606 training instances and 121 testing instances[cite: 12].
* [cite_start]**With noise:** Irregular variations[cite: 14, 17]. [cite_start]Contains 606 training instances and 121 testing instances[cite: 15, 16].

## Technologies Used
* [cite_start]**Python** * **Pandas & NumPy** - Data manipulation and preprocessing[cite: 22].
* [cite_start]**Scikit-learn** - SVM model training, evaluation, and data scaling (`StandardScaler`)[cite: 24].
* [cite_start]**Matplotlib** - Visualizing results and confusion matrices[cite: 23].

## Methodology & Hyperparameter Tuning
[cite_start]To achieve the best accuracy, an exhaustive grid search approach was implemented using `itertools.product` to test combinations of SVM hyperparameters[cite: 25, 27]:
* [cite_start]**C (Error penalty/Cost):** Values ranging from 2^-5 to 2^7[cite: 28].
* [cite_start]**Gamma (Point influence):** Values ranging from 2^-15 to 2^3[cite: 29].

## Results
The model was evaluated using accuracy scores and confusion matrices for both datasets.

### 1. Noisy Data Performance
* [cite_start]**Best Accuracy:** 0.6221 (with C=128, gamma=0.03125)[cite: 32].
* [cite_start]**Observations:** The model correctly identified 262 "hill" examples and 115 "valley" examples[cite: 36, 37]. [cite_start]It achieved a high recall (88%) for Class 0 (hill) but struggled with Class 1 (valley), misclassifying nearly two-thirds of them[cite: 38]. 

### 2. Clean Data (Without Noise) Performance
* [cite_start]**Best Accuracy:** 0.6040 (with C=128, gamma=8)[cite: 41].
* [cite_start]**Observations:** The model correctly identified 267 "hill" examples and 99 "valley" examples[cite: 45, 46]. [cite_start]The recall for Class 0 remained high (91%), while Class 1 detection remained poor (32%)[cite: 47].

## Key Takeaways & Conclusions
* [cite_start]**Classification Bias:** In both scenarios, the model exhibited a strong bias towards predicting Class 0 (hills), resulting in a high recall for hills but a poor detection rate for valleys[cite: 39, 48, 50].
* [cite_start]**The Impact of Noise:** Counterintuitively, the SVM model achieved slightly better overall accuracy on the noisy dataset[cite: 51]. [cite_start]This suggests that the noise forces the model to learn a more generalized decision boundary, preventing it from excessively relying on fine details or perfect transitions present in the clean data[cite: 52].
