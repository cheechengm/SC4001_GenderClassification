# Automatic Gender Classification using Deep Learning

This project explores various deep learning architectures to perform automatic gender classification from facial images. The study utilizes the **Adience dataset**, which is known for its real-world challenges, including variations in lighting, pose, and occlusion.

---

### ## Project Overview
The goal is to move beyond traditional hand-crafted features by implementing and comparing modern neural network architectures. We explored three distinct methodologies to optimize performance:
* **Baseline Enhancement:** Pretraining a standard CNN on the large-scale **CelebA** dataset.
* **Transfer Learning:** Fine-tuning a pre-trained **EfficientNetB5** backbone.
* **Architectural Innovation:** Developing a **DilatedResNet** that incorporates multi-scale dilated convolutions to expand the receptive field.

---

### ## Model Architectures & Methods

#### 1. Pretraining with CelebA
* Uses the Levi and Hassner CNN architecture as a baseline.
* Pretrained on the CelebA dataset to enhance the model's generalization capacity before training on Adience.
* Input images are standardized to **100x100 pixels**.

#### 2. EfficientNetB5 (Transfer Learning)
* Leverages **EfficientNetB5** pre-trained on ImageNet.
* Initial pre-trained weights were frozen to retain learned features.
* Custom top layers added: Global Average Pooling, Dense (1024, ReLU), Dropout (0.5), and Dense (512, ReLU).
* Final classification performed via a Sigmoid activation layer.

#### 3. DilatedResNet with Multi-Scale Dilated Convolutions
* Integrates a **ResNet-18** backbone with custom **Multi-Scale Dilated Convolution Blocks**.
* Each block uses parallel convolutional layers with dilation rates of **1, 2, 4, and 8**.
* Outputs are concatenated and processed with Batch Normalization and ReLU to capture diverse spatial contextual information.

---

### ## Experiments and Results

The models were evaluated on the Adience test split, with **EfficientNetB5** emerging as the superior architecture.

| Model Architecture | Test Accuracy |
| :--- | :--- |
| **Baseline (Adience Only)** | 0.8931 |
| **CelebA Pretrained Baseline** | 0.8967 |
| **DilatedResNet (Multi-Scale)** | 0.8984 |
| **EfficientNetB5 (Fine-tuned)** | **0.9099** |

---

### ## Tech Stack
* **Languages:** Python
* **Libraries:** TensorFlow/Keras (EfficientNet & Baseline), PyTorch (DilatedResNet)
* **Datasets:** Adience, CelebA, ImageNet
