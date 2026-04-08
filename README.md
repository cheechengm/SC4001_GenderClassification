### Automatic Gender Classification using Deep Learning

[cite_start]This project explores various deep learning architectures to perform automatic gender classification from facial images[cite: 24]. [cite_start]The study utilizes the **Adience dataset**, which is known for its real-world challenges, including variations in lighting, pose, and occlusion[cite: 23, 34].

---

### ## Project Overview
[cite_start]The goal is to move beyond traditional hand-crafted features by implementing and comparing modern neural network architectures[cite: 26, 29]. We explored three distinct methodologies to optimize performance:
* [cite_start]**Baseline Enhancement:** Pretraining a standard CNN on the large-scale **CelebA** dataset[cite: 56].
* [cite_start]**Transfer Learning:** Fine-tuning a pre-trained **EfficientNetB5** backbone[cite: 60].
* [cite_start]**Architectural Innovation:** Developing a **DilatedResNet** that incorporates multi-scale dilated convolutions to expand the receptive field[cite: 64, 65].

---

### ## Model Architectures & Methods

#### 1. Pretraining with CelebA
* [cite_start]Uses the Levi and Hassner CNN architecture as a baseline[cite: 56].
* [cite_start]Pretrained on the CelebA dataset to enhance the model's generalization capacity before training on Adience[cite: 56, 101].
* [cite_start]Input images are standardized to **100x100 pixels**[cite: 71].

#### 2. EfficientNetB5 (Transfer Learning)
* [cite_start]Leverages **EfficientNetB5** pre-trained on ImageNet[cite: 60].
* [cite_start]Initial pre-trained weights were frozen to retain learned features[cite: 61].
* [cite_start]Custom top layers added: Global Average Pooling, Dense (1024, ReLU), Dropout (0.5), and Dense (512, ReLU)[cite: 80, 81].
* [cite_start]Final classification performed via a Sigmoid activation layer[cite: 80].

#### 3. RNN with Multi-Scale Dilated Convolutions
* [cite_start]Integrates a **ResNet-18** backbone with custom **Multi-Scale Dilated Convolution Blocks**[cite: 64].
* [cite_start]Each block uses parallel convolutional layers with dilation rates of **1, 2, 4, and 8**[cite: 65, 88].
* [cite_start]Outputs are concatenated and processed with Batch Normalization and ReLU to capture diverse spatial contextual information[cite: 65, 90].

---

### ## Experiments and Results

[cite_start]The models were evaluated on the Adience test split, with **EfficientNetB5** emerging as the superior architecture[cite: 102].

| Model Architecture | Test Accuracy |
| :--- | :--- |
| **Baseline (Adience Only)** | [cite_start]0.8931 [cite: 73] |
| **CelebA Pretrained Baseline** | [cite_start]0.8967 [cite: 73] |
| **DilatedResNet (Multi-Scale)** | [cite_start]0.8984 [cite: 96] |
| **EfficientNetB5 (Fine-tuned)** | [cite_start]**0.9099** [cite: 83] |

---

### ## Tech Stack
* [cite_start]**Languages:** Python [cite: 67, 85]
* [cite_start]**Libraries:** TensorFlow/Keras (EfficientNet & Baseline), PyTorch (DilatedResNet) [cite: 67, 85]
* [cite_start]**Datasets:** Adience, CelebA, ImageNet [cite: 56, 60]

---

### ## Future Work
* [cite_start]Implementing **Attention-based mechanisms** or **Vision Transformers (ViT)**[cite: 106].
* [cite_start]Exploring **Deformable Convolutions** to improve model flexibility[cite: 106].
* [cite_start]Utilizing facial landmark alignment and advanced data augmentation strategies[cite: 107].
