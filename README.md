# Using Ensemble Techniques to Classify Deepfake Images
**By Surya Rathee**

---

## Abstract
> Deepfakes are an emerging threat within the digital media environment by allowing the production of hyper-realistic manipulated videos and images. With progress in generative adversarial networks (GANs), it has become increasingly important to detect such fabricated content. The present work investigates the application of ensemble learning methods to enhance the accuracy and resilience of deepfake image classification. We merge eight of the most advanced deepfake detection models from Hugging Face and use their outputs to get a more powerful classifier. Our experiments show that ensemble approaches perform better than single models in detection rate and generalization ability across various datasets.

---

## Introduction
Deepfake technology leverages AI-driven methods, specifically GANs, to generate realistic fake media. Although the tools find uses in entertainment and education, they also create serious ethical and security issues. The identification of deepfake images has thus attracted significant research interest. Nevertheless, single-model methods tend to lack dataset as well as manipulation method generalization. Ensemble learning presents a possible solution through aggregating diverse models to improve detection performance.

---

## Related Work
Numerous deepfake detection models have been developed in recent years, including:
* Multiple Huggingface Models
* CNN-based models
* Vision Transformer (ViT)-based architectures
* Forensic-inspired models

Our ensemble integrates the following publicly available models from Hugging Face:
1.  `dima806/deepfake_vs_real_image_detection`
2.  `prithivMLmods/Deep-Fake-Detector-Model`
3.  `DaMsTaR/Detecto-DeepFake_Image_Detector`
4.  `DarkVision/Deepfake_detection_image`
5.  `Wvolf/ViT_Deepfake_Detection`
6.  `thembululwa/deepfake_detection`
7.  `prithivMLmods/Deep-Fake-Detector-v2-Model-ONNX`

---

## Methodology

### Preprocessing
All images were resized and normalized to conform with the input requirements of each model. A unified preprocessing pipeline was used to ensure consistency.

### Individual Model Predictions
Each model provides a binary or probabilistic output. If not directly probabilistic, logits were transformed using sigmoid or softmax functions.

### Ensemble Strategy
We tested the following ensemble techniques:
* **Majority Voting:** Final label is the most common prediction.
* **Averaging Probabilities:** Outputs are averaged, and thresholding determines the final label.
* **Weighted Averaging:** Models are weighted according to their standalone validation accuracy.

### Training and Evaluation
A curated dataset of real and deepfake images was used. Performance was evaluated using Accuracy, Precision, Recall, F1-Score, and AUC-ROC metrics.

| **Model Name** | **Accuracy** | **Precision (Macro)** | **Recall (Macro)** | **F1-Score (Macro)** |
|:---------------------------------------------------|:------------:|:--------------------:|:------------------:|:--------------------:|
| `dima806/deepfake_vs_real_image_detection`         |     0.92     |         0.92         |        0.92        |         0.92         |
| `prithivMLmods/Deep-Fake-Detector-Model`           |     0.49     |         0.25         |        0.49        |         0.33         |
| `DaMsTaR/Detecto-DeepFake_Image_Detector`          |     0.92     |         0.92         |        0.92        |         0.92         |
| `DarkVision/Deepfake_detection_image`              |     0.92     |         0.92         |        0.92        |         0.92         |
| `Wvolf/ViT_Deepfake_Detection`                     |     0.92     |         0.92         |        0.92        |         0.92         |
| `thembululwa/deepfake_detection`                   |     0.77     |         0.84         |        0.77        |         0.76         |
| `prithivMLmods/Deep-Fake-Detector-v2-Model-ONNX`   |     0.91     |         0.91         |        0.91        |         0.91         |
| **Ensemble Model** |   **0.94** |       **0.94** |      **0.94** |       **0.94** |

*Table 1: Performance Comparison of Deepfake Detection Models*

---

## Results
Our experiments show ensemble techniques surpass individual model performance:

* Majority Voting achieved 94% accuracy.
* Averaging Probabilities reached 94% accuracy.
* Weighted Averaging yielded the best result with 94% accuracy and 0.94 AUC.

---

## Discussion
The ensemble models significantly outperform any single model due to the diversity in architectures and detection strategies. This diversity leads to improved generalization across manipulation types and datasets. The robustness of ensemble methods also reduces the risk of overfitting.

---

## Conclusion
Ensemble techniques significantly improve the detection of deepfake images. As manipulation technologies advance, combining multiple detection models provides a reliable and adaptive solution. Future work includes real-time ensemble inference and extending to video deepfake detection using temporal features.

---

## References
1.  Tolosana et al., "DeepFakes and Beyond: A Survey of Face Manipulation and Fake Detection", *Information Fusion*, 2020.
2.  Mirsky and Lee, "The Creation and Detection of Deepfakes: A Survey", *ACM Computing Surveys*, 2021.
3.  Hugging Face model repositories (as cited in Section 2).
4.  [Tiny Dataset for Deepfake Classifiers on Kaggle](https://www.kaggle.com/datasets/suryarathee/tiny-dataset-for-deepfake-classifiers)
5.  [GitHub repository by Surya Rathee](https://github.com/suryarathee/deepfake-detection)
