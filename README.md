# 🚢 Titanic Survival Prediction

![Titanic Banner](https://upload.wikimedia.org/wikipedia/commons/f/fd/RMS_Titanic_3.jpg)

## 📌 Project Overview
This project predicts **survival of passengers on the Titanic** using different machine learning models.  
Initially, a Logistic Regression model gave around **81% accuracy**, but through **balancing techniques, ensemble methods, and stacking**, I worked on improving performance further.  

The dataset used has **5 features** and was **imbalanced** with class counts:
- **0 (Did not survive): 549**
- **1 (Survived): 342**

---

## ⚙️ Models and Results

### 1️⃣ On Imbalanced Data
- **Logistic Regression (LR):** 0.79 accuracy | ![Confusion Matrix 1]
- (<img width="640" height="547" alt="33-1" src="https://github.com/user-attachments/assets/a84e3482-c3ac-4c83-8548-875c19b5b135" />
)  
- **SVC (Linear):** 0.65 accuracy, 56 FN, 6 FP  
- **Decision Tree (DT):** 0.77 accuracy, 18 FN, 23 FP  
- **Random Forest (RF):** 0.79 accuracy, 20 FN, 16 FP | ![CM 2]
- <img width="640" height="547" alt="33-2" src="https://github.com/user-attachments/assets/379adfd1-f0fb-4ef8-bb64-79a7b894b556" />

- **AdaBoost:** 0.79 accuracy, 20 FN, 16 FP |
- <img width="640" height="547" alt="33-3" src="https://github.com/user-attachments/assets/16bb4681-4bf8-44d1-a61f-c45f944b0e61" />

- **Gradient Boosting (GB):** **0.82 accuracy**, 19 FN, 12 FP | ![CM 4]
- <img width="640" height="547" alt="33-4" src="https://github.com/user-attachments/assets/29f12b54-2351-4998-bb23-bb5fa20b516d" />


---

### 2️⃣ Using Class Weights (`class_weight={0:1,1:2}`)
- **Logistic Regression:** 0.79 acc, 10 FN, 26 FP  
- **SVC:** 0.70 acc, 34 FN, 18 FP  
- **Decision Tree:** 0.76 acc, 20 FN, 22 FP  
- **Random Forest:** **0.8212 acc**, 19 FN, 13 FP | ![CM 5]
- <img width="640" height="547" alt="33-5" src="https://github.com/user-attachments/assets/05778308-fbb0-428a-80c6-893a309d7a59" />

- **BalancedRandomForest (imblearn):** 0.80 acc, 14 FN, 21 FP | ![CM 6]
- <img width="640" height="547" alt="33-6" src="https://github.com/user-attachments/assets/f97de38a-34ad-4445-b0ca-f36e85fc6d41" />


---

### 3️⃣ Down Sampling
- **Logistic Regression:** **0.81 acc**, 10 FN, 24 FP | ![CM 7]
- <img width="640" height="547" alt="33-7" src="https://github.com/user-attachments/assets/a84d1f64-d893-4f65-947a-562b8ce28bd2" />

- **SVC:** 0.709 acc, 24 FN, 28 FP  
- **Decision Tree:** 0.77 acc, 14 FN, 27 FP  
- **Random Forest:** 0.78 acc, 15 FN, 24 FP  
- **Gradient Boosting:** 0.79 acc, 18 FN, 18 FP  

#### 🔗 Stacking (Base: RF, GB, SVC, DT, LR | Meta: LR)
- **Accuracy:** **0.849** 🎉 | 11 FN, 16 FP | ![CM 8]
- <img width="640" height="547" alt="33-8" src="https://github.com/user-attachments/assets/26141239-5be8-4da0-9d6c-244644ed9fff" />

- Another stacking with KNN + Naive Bayes + Ridge as meta → did not perform well  

---

### 4️⃣ SMOTE (Synthetic Minority Oversampling)
- **Logistic Regression:** 0.80 acc, 14 FN, 21 FP  
- **SVC:** 0.71 acc, 22 FN, 29 FP  
- **Random Forest:** 0.79 acc, 16 FN, 21 FP | ![CM 9]
- <img width="640" height="547" alt="33-9" src="https://github.com/user-attachments/assets/bfd32543-aeb3-44bb-a96f-16f25d3054ef" />

- **Decision Tree:** 0.759 acc, 22 FN, 21 FP  
- **AdaBoost:** 0.78 acc, 17 FN, 21 FP  
- **Gradient Boosting:** **0.82 acc**, 20 FN, 12 FP | ![CM 10]
- <img width="640" height="547" alt="33-10" src="https://github.com/user-attachments/assets/49e5fd47-64ec-4184-8223-ba995e719f26" />


#### 🔗 Stacking
- **Stack 1 (same base as before):** 0.82 acc, 18 FN, 14 FP | ![CM 11]
- <img width="640" height="547" alt="33-11" src="https://github.com/user-attachments/assets/eca6bb33-3ca8-4407-b1a2-0799f78097c2" />

- **Stack 2 (with KNN + NB):** 0.81 acc, 21 FN, 12 FP  

---

### 5️⃣ Up Sampling
- **Logistic Regression:** **0.82 acc**, 10 FN, 21 FP 
- **SVC:** 0.72 acc, 21 FN, 28 FP  
- **Decision Tree:** 0.76 acc, 20 FN, 22 FP  
- **Random Forest:** 0.78 acc, 17 FN, 22 FP  
- **AdaBoost:** 0.75 acc, 15 FN, 28 FP  
- **Gradient Boosting:** 0.79 acc, 18 FN, 18 FP  
- **Stack 1:** 0.79 acc, 19 FN, 18 FP  

---

## 📊 Key Takeaways
- **Gradient Boosting** consistently gave one of the best individual performances (~82%).  
- **Class weighting** and **sampling (SMOTE, downsampling, upsampling)** helped balance survival prediction.  
- **Stacking with ensemble models** (RF, GB, SVC, DT, LR as base + LR as meta) gave the **best result: 0.849 accuracy**.  
- **SVC struggled** with imbalanced data and didn’t improve much even with balancing.  

---

## 🏁 Final Best Model
✨ **Stacking Classifier (RF + GB + SVC + DT + LR as base, LR as meta)** → **0.849 Accuracy**  

---

## 📸 Visuals
Confusion matrices and decision boundaries are attached in this repo for better understanding:
- **CM for Logistic Regression, Random Forest, Gradient Boosting, and Stacking**
- **Plots showing effect of imbalance handling**

---

## 🙌 Conclusion
The project shows how:
- Handling **imbalanced data** is crucial in classification tasks.  
- **Ensemble methods (Boosting, Stacking)** outperform single models.  
- Model performance can be pushed further with **class weights, SMOTE, and resampling techniques**.  

This is not just about accuracy—it’s about **making the model fairer and more reliable in predicting survival chances**. 🚢⚖️  

---
