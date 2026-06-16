# Literature Review Matrix

**Topic:** Automated E-Commerce Product Categorization and Tagging System Using Convolutional Neural Networks  
**Course:** SWR302 — Research Writing  
**Papers Reviewed:** 5

---

## 1. Comparative Summary Matrix

| No. | Title & Author | Problem Addressed | Method / Approach | Dataset | Evaluation Metrics | Key Results | Relevance to Our Topic |
|-----|----------------|-------------------|-------------------|---------|-------------------|-------------|------------------------|
| P01 | E-Commerce Product Categorization Using ML and Deep Learning — Surve (2022) | Manual classification is time-consuming; unclear which CNN model performs best for e-commerce categorization. | Compared 5 models: CNN (from scratch), VGG19, InceptionV3, ResNet50, MobileNet via Transfer Learning on Flipkart product images. | Flipkart (Kaggle): 16,679 images, 15 categories. Augmented from 7,755 originals. 70/30 train-test split. | Accuracy, Precision, Recall, F1-Score, Prediction time per image. | InceptionV3 and MobileNet both achieved 85% accuracy. MobileNet fastest at 0.101s/image. CNN baseline: 51%. Transfer learning improved accuracy by +34%. | Directly relevant — same CNN and Transfer Learning approach for e-commerce categorization. Confirms MobileNet/InceptionV3 as optimal model choices. |
| P02 | E-Commerce Product Image Classification using Transfer Learning — Jha et al. (2021) | Explosive growth of product images makes manual classification impractical; traditional CNN training is computationally costly and prone to overfitting. | Applied Transfer Learning using VGG-19 and InceptionV3 pre-trained on ImageNet. Froze convolutional layers; fine-tuned fully connected layers. | Fashion MNIST (Kaggle): 70,000 grayscale images, 28x28px, 10 fashion categories. 85% train / 15% validation split. | Training and Validation Accuracy, Loss Value (cross-entropy) tracked across epochs. | Both VGG-19 and InceptionV3 converged faster with stable validation accuracy. InceptionV3 demonstrated superior multi-scale feature extraction and loss minimization. | Validates Transfer Learning superiority over training from scratch. Supports selection of lightweight architectures (MobileNetV3) for real-time classification in our system. |
| P03 | Fine-Grained Classification of Product Images Based on CNNs — Liu et al. (2018) | Traditional keyword and attribute methods fail to capture rich visual features; deep CNNs are resource-intensive to train. | Designed Deep CNN (7x7, 5x5, 3x3x3 conv layers) and Shallow CNN with 50% Dropout. 5x data augmentation via flipping and rotation. Softmax output layer. | Caltech256 (100 train / 50 test per class) and self-collected from T-mall, JD, Amazon: 20,000 images, 20 categories, 256x256px. | Classification Accuracy compared against SVM baseline. | Deep CNN: 92.1%. Shallow CNN: 90.6%. SVM baseline: 76.3–86.2%. Shallow CNN achieves near-equal accuracy with significantly fewer computational resources. | Supports lightweight Shallow CNN architecture for resource-efficient deployment. Data augmentation strategy directly applicable to our preprocessing pipeline. |
| P04 | Optimizing E-Commerce Product Classification Using Transfer Learning — Khanuja (2019) | Text-based classification inaccurate due to inconsistent merchant labeling; training CNN from scratch is costly and risks overfitting. | VGG-16 pre-trained on ImageNet. Froze convolutional blocks, added Dense (ReLU) -> Dropout (0.5) -> Dense (Sigmoid). One-vs-All binary classification per category. | Self-crawled via Selenium and BeautifulSoup: approximately 17,500 product images, 5 macro-categories, approximately 900 test images per category. | Train/Validation Accuracy, Binary Cross-entropy Loss, Training time comparison vs. traditional CNN. | Traditional CNN: 79%, over 3 hours training. Transfer Learning (multi-class): 85%, approximately 17 minutes. One-vs-All strategy: 89% accuracy. | Demonstrates One-vs-All strategy for improved per-category accuracy. VGG-16 feature vectors reusable for similarity-based product recommendation in our system. |
| P05 | An Image-based Transfer Learning Framework for Classification of E-Commerce Products — Surve et al. (2022, ICDLT) | Manual classification of millions of products is unsustainable; misclassified images degrade search experience and user retention. | Benchmarked Traditional CNN against VGG-19, InceptionV3, ResNet50, and MobileNet using pre-trained ImageNet weights with Softmax classification layer. | ImageNet (pre-training weights) and self-scraped Dataset-2: 15,000 product images from multiple e-commerce platforms under diverse real-world conditions. | Accuracy, Precision, Recall, F1-Score, Prediction time per image (seconds). | InceptionV3 achieved best overall performance: 85% accuracy, 0.10s per image. All Transfer Learning models outperformed the CNN baseline on both accuracy and inference speed. | Provides concrete benchmark (0.10s inference) justifying real-time integration with Java backend via JDBC. Validates MobileNet/InceptionV3 selection for our categorization module. |

---

## 2. Limitations and Research Gaps

| No. | Key Limitations |
|-----|-----------------|
| P01 | Image-only input with no textual metadata; relatively small dataset (16,679 images); results not validated on platforms beyond Flipkart; hyperparameters not systematically optimized. |
| P02 | 28x28 grayscale images are unrealistic for real-world product photographs; VGG-19 and InceptionV3 are too computationally heavy for mobile or edge deployment; evaluation limited to fashion domain only. |
| P03 | Fixed 256x256 input resolution is inflexible for real-world image uploads of varying sizes; scope limited to 20 product categories; no integration of textual product metadata. |
| P04 | Classification tested only at macro-category level (5 categories) without sub-category granularity; One-vs-All strategy requires training and maintaining N separate models, which is unscalable at enterprise level. |
| P05 | An 85% accuracy rate implies a 15% error rate which becomes significant at platform scale; scraped training data may not adequately represent real-world noise such as motion blur, occlusion, or multi-product frames. |

---

## 3. Synthesis of Common Themes

### Theme 1: Transfer Learning Consistently Outperforms Training from Scratch

All five reviewed papers demonstrate that Transfer Learning, using weights pre-trained on ImageNet, achieves higher classification accuracy, faster convergence, and reduced overfitting risk compared to CNN models trained from scratch. Accuracy improvements range from +34 percentage points (P01: CNN 51% vs. MobileNet 85%) to over +10 percentage points across other studies.

### Theme 2: MobileNet and InceptionV3 Are Identified as Optimal Architectures

Papers P01 and P05 independently identify InceptionV3 and MobileNet as top-performing architectures, both achieving 85% accuracy. MobileNet additionally provides the fastest inference time at 0.101 seconds per image, making it suitable for real-time deployment. Paper P04 further confirms that even VGG-16 achieves 89% accuracy when combined with a One-vs-All classification strategy.

### Theme 3: Data Augmentation Is Essential When Training Data Is Limited

Papers P01 and P03 both apply augmentation techniques — including horizontal and vertical flipping, rotation, and brightness adjustment — to substantially expand training sets (P01: 7,755 to 16,679 images; P03: 4,000 to 20,000 images). This practice is essential for improving generalization when collecting large-scale real-world product imagery is not feasible.

### Theme 4: The Absence of Multimodal Input Is a Shared Limitation

No paper in this review combines visual features with textual product metadata such as titles, descriptions, or brand names. This multimodal gap is the most frequently cited direction for future research across all five studies and represents a key opportunity for improvement in our proposed system through CNN and BERT fusion.

### Theme 5: Scalability to Real-World Category Breadth Remains Unaddressed

The majority of studies evaluate on 5 to 20 product categories, which falls far short of the hundreds or thousands of categories present on real e-commerce platforms. The One-vs-All approach in P04 becomes operationally unscalable as category count increases. Hierarchical classification and multi-label approaches are suggested across papers but not implemented in any of the reviewed works.

---

## References

| No. | Full Citation |
|-----|---------------|
| P01 | Surve, V. A. (2022). *E-Commerce Product Categorization Using Machine Learning and Deep Learning Techniques*. MSc Research Project, National College of Ireland. https://norma.ncirl.ie/6322/ |
| P02 | Jha, B. K., Sivasankari, G. G., & Venugopal, K. R. (2021). E-Commerce Product Image Classification using Transfer Learning. *Proceedings of the 2021 5th International Conference on Computing Methodologies and Communication (ICCMC)*. https://doi.org/10.1109/ICCMC51019.2021.9418371 |
| P03 | Liu, T., Wang, R., Chen, J., Han, S., & Yang, J. (2018). Fine-Grained Classification of Product Images Based on Convolutional Neural Networks. *Advances in Molecular Imaging, 8*(4). https://doi.org/10.4236/ami.2018.84007 |
| P04 | Khanuja, R. K. (2019). *Optimizing E-Commerce Product Classification Using Transfer Learning*. Master's Project, San Jose State University. https://doi.org/10.31979/etd.egyw-ktc5 |
| P05 | Surve, V. A., Pathak, P., Hasanuzzaman, M., Haque, R., & Stynes, P. (2022). An Image-based Transfer Learning Framework for Classification of E-Commerce Products. *Proceedings of the 2022 6th International Conference on Deep Learning Technologies (ICDLT '22)*. https://doi.org/10.1145/3556677.3556689 |
