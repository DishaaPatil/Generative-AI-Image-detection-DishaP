# Generative-AI-Image-detection-DishaP
**Brief problem statement:**

Hi! I've made this project for bitgrit's [Generative AI](https://bitgrit.net/competition/18#) competition. It requires us to classify images as real (label '0') or AI generated(label '1'). All the images in the datasets are 20 x 20 x 3 (channels). The underlying data is all processed, so it cannot be converted back to the original images. The goal of this competition is to predict the ‘labels’ column using the data provided.

***Classifiers and techniques used***
1. **PCA**(*Principal Component Analysis*)
2. **Naive Bayes Classifier**
3. **Decision Tree Classifier**
4. **Softmax Classifier**
5. **Support Vector Classifier**
6. **Adaboost**
7. **GradBoosting**
8. **Random Forest**
9. **Voting Classifier**


## Procedure
1. Preprocessed the data after loading it, using **MinMaxScaler**, to change all features in the range of 0-1.
2. Split the training data into test & train sets (ratio 1:4).
3. Applied 4 different classifiers on the data and checked the accuracy.
   1)  **Naive Bayes Classifier**:
   The accuracy was **62.1904761904762%**
   ![Nb accuracy](https://github.com/DishaaPatil/Generative-AI-Image-detection-DishaP/assets/102872725/a5af5a17-49ea-4ede-adaf-35d1c157b63c)


   2)  **Decision Tree Classifier**
   The accuracy was **78.95238095238095%**
   ![dt acc](https://github.com/DishaaPatil/Generative-AI-Image-detection-DishaP/assets/102872725/973df742-12a3-49dc-b3f6-00f79d182989)


   3)  **Softmax Classifier**
   The accuracy was **80.85714285714286%**
   ![softmax acc](https://github.com/DishaaPatil/Generative-AI-Image-detection-DishaP/assets/102872725/af98426c-c880-41f1-9761-39e3ad87ac44)


   4)  **Support Vector Classifier**(with linear kernel)
   The accuracy was **80.95238095238095%**
   ![svc acc](https://github.com/DishaaPatil/Generative-AI-Image-detection-DishaP/assets/102872725/4257d12a-2797-480a-9353-7872ecb2da75)


   5) **Support Vector Classifier** (with Gaussian kernel)
   The accuracy was **86.47619047619047%**
   ![svm g acc](https://github.com/DishaaPatil/Generative-AI-Image-detection-DishaP/assets/102872725/928b190b-7c13-4007-a0bf-c9fb38411304)


4. After this, I tried applying PCA to the data and then check its accuracy with the above classifiers. The following result was obtained:
   ![pca acc 150](https://github.com/DishaaPatil/Generative-AI-Image-detection-DishaP/assets/102872725/03277cb8-a4d4-447e-869e-8db1558fd6f0)

   ![pca acc 160-250](https://github.com/DishaaPatil/Generative-AI-Image-detection-DishaP/assets/102872725/bdffadef-988a-4faf-8bd6-38fa3347d7cd)
5. As visible, SVC gave the best results. So by fine tuning the number of components, I found the prediction accuracy to be **86.47619047619047%** for Linear Kernel when number of components were 208
   ![pca svc l f](https://github.com/DishaaPatil/Generative-AI-Image-detection-DishaP/assets/102872725/71adb2fa-4fea-4cbe-b0f6-938aae7babe1)

and **87.04761904761905%** for Gaussian Kernel, with number of components 207.
![pca svc g](https://github.com/DishaaPatil/Generative-AI-Image-detection-DishaP/assets/102872725/3ddd94a1-e9f1-4da7-b762-2218132deaf0)

6. So I did 2 submissions, PCA+SVC Linear and PCA+SVC Gaussian, out of which PCA+SVC Linear performed pretty well, with a f1 score of **0.7968** and PCA+SVC Gaussian performed poorly with accuracy of 0.68672566.
7. Later I tried more advanced techniques, of bagging, boosting, etc. to try to increase the accuracy.
8. First I tried Bagging, which got a f1 score of **0.85588235**.
  
![bagging heatmap](https://github.com/DishaaPatil/Generative-AI-Image-detection-DishaP/assets/102872725/8a5c1eae-d601-45a3-a373-2097de9471a5)

9. Then I tried GradBoosting, but at lower learning rates, it didn't give good accuracy and at higher learning rates, the validation set had a very poor accuracy as compared to testing set, meaning the model had overfitted. So I didn't consider this for final submission.  
![gb bars final](https://github.com/DishaaPatil/Generative-AI-Image-detection-DishaP/assets/102872725/a31bc8dc-b286-4b45-8f9d-3dc4ec27eee2)
10. Finally I tried AdaBoosting with SVC as base classifier, as it had given highest accuracy in previous cases. It gave the highest accuracy till now, with an f1 score of **0.87572254**.
 
![ab heatmap](https://github.com/DishaaPatil/Generative-AI-Image-detection-DishaP/assets/102872725/ee113567-bf81-461e-9fd0-10bab9a50568)

    


