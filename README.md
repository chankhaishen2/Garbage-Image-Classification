# Garbage classification based on image
1. This repository contains the file for a side project, which investigates the accuracy and inference time of three lightweight image classifiers on garbage classification.
2. The sole purpose of this side project is to select a garbage image classifier to be deployed on my portfolio website (which is a static website).
3. The three image classifier compared are MobileNetV3-Small, MobileNetV2 and EfficientNet-B0.
4. The garbage image dataset originates from https://www.kaggle.com/datasets/asdasdasasdas/garbage-classification?select=Garbage+classification. The dataset contains 2527 images from 6 classes, namely cardboard, glass, metal, paper, plastic and trash.

# Description
1. The dataset is randomly shuffled and split into train set, validation set and test set with ratio of 8:1:1.
2. To reduce overfitting, during training, the images are flipped horizontally and vertically, randomly rotated for 15 degrees, and adjusted the colour contrast and normalised using the mean and standard deviation of ImageNet dataset. 
3. Optuna is used for hyperparameter tuning for MobileNetV3-Small, MobileNetV2 and EfficientNet-B0. Unfreezing percentage of 0.1, 0.2, 0.3 and 0.4, learning rate of 0.00001 and 0.0001, and optimizer of AdamW and SGD are explored.
4. For MobileNetV3-Small, MobileNetV2 and EfficientNet-B0, seeds of 0, 198, 473, 5784 and 96312 are used to fine tune the model. The accuracy and the inference time across all seeds are averaged.
5. The accuracy of MobileNetV3-Small, MobileNetV2 and EfficientNet-Bo are 0.8550, 0.8669 and 0.8661 respectively, whereas the inference time of MobileNetV3-Small, MobileNetV2 and EfficientNet-B0 are 2.271 milliseconds, 2.180 milliseconds and 2.773 milliseconds respectively.
5. Quantization is attempted for MobileNetV3-Small but the accuracy of the quantized model is extremely low. So, quantization is not attempted for subsequent models, namely MobileNetV2 and EfficientNet-B0.
6. Based on the average accuracy and average inference time across five seeds, it can be said that MobileNetV2 is the model with the highest accuracy and the shortest inference time. So, MobileNetV2 is selected as the garbage image classifier to be deployed in my portfolio website.


# Files
1. "main.ipynb" file is the code to conduct the experiments.
2. "MobileNetV3-Small-results.csv", "MobileNetV2-results.csv" and "EfficientNet-B0-results.csv" are the results of the experiments on MobileNetV3-Small, MobileNetV2 and EfficientNet-B0 respectively. "all-results.xlsx" is the aggregated results for all three models.
3. "MobileNetV2.onnx" is the fine-tuned MobileNetV2 model using seed 0, which will be deployed on my portfolio website.
