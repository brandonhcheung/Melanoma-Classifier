# Melanoma Classification Using CNN and EfficientNet

#### - For a more detailed analysis of model performance, evaluation metrics, and medical considerations, see **Melanoma Classifer Report (PDF)** in this repository.
**Members:** Brandon Cheung · Kareem Hamideh · Karim Grar · Kyungdon Baik  
---

## Overview
This project builds a deep learning system to classify dermatologic images as **benign** or **malignant melanoma**. Early detection of melanoma is critical, and image-based machine learning models can help support early screening and medical triage.

We compare three models:
- A custom Convolutional Neural Network (CNN)
- EfficientNetB0 with transfer learning
- EfficientNetB3 with transfer learning

---

## Dataset
- **Source:** Kaggle – Melanoma Cancer Image Dataset
- https://www.kaggle.com/datasets/bhaveshmittal/melanoma-cancer-dataset/data

---

## Models & Training
- **CNN:** Built from scratch with convolutional blocks, batch normalization, dropout, and ReLU activations
- **EfficientNetB0 & B3:** ImageNet pretrained models using two-phase fine-tuning
- **Techniques:** Data augmentation, early stopping, learning rate scheduling, Adam/AdamW optimizers

---
## Results Summary

The results highlight how model architecture and complexity affect melanoma classification performance. The custom CNN established a functional baseline and showed that a model trained from scratch can learn useful visual features. However, its limited representational capacity led to weaker performance across accuracy, AUC, and recall for malignant lesions. This was most evident in a higher rate of false negatives, which is especially problematic in medical settings where missed melanoma cases can delay diagnosis and treatment.

Transfer learning with EfficientNet substantially improved results. EfficientNetB0 benefited from pretrained ImageNet features, allowing it to capture finer texture, color variation, and lesion irregularities than the CNN. These improvements were consistent across accuracy, ROC curves, confusion matrices, and recall for the malignant class. The two-phase fine-tuning strategy further stabilized training and improved generalization without introducing significant overfitting.

EfficientNetB3 achieved the strongest overall performance, benefiting from higher input resolution and a deeper, more expressive architecture. It produced the highest accuracy and AUC and demonstrated the best separation between benign and malignant cases across decision thresholds. Higher recall for malignant lesions suggests improved sensitivity to subtle visual cues important for early melanoma detection.

Despite these gains, important limitations remain. Class imbalance in the dataset likely made learning the malignant class more difficult, particularly for the CNN. Resizing images to fixed resolutions may have removed subtle diagnostic details. Although EfficientNet models reduced false negatives, some malignant cases were still misclassified, posing risk in real clinical settings. False positives, while less dangerous, can lead to unnecessary biopsies and patient anxiety. Additionally, EfficientNetB3 required substantially more computational resources, limiting its practicality under hardware constraints.

Overall, while EfficientNetB3 delivered the highest performance, EfficientNetB0 provides the best balance between accuracy, efficiency, and deployment feasibility. These results emphasize that medical image classification systems must be evaluated not only by accuracy, but also by error types, computational cost, and real-world clinical impact.

