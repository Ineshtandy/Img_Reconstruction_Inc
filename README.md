# 🧠 Image Inpainting

This project implements **Context Encoders** for semantic image inpainting, based on the work by Pathak et al. (CVPR 2016). The goal is to predict missing regions in an image using a deep convolutional encoder-decoder pipeline, enhanced with adversarial training. The dataset is built using **masked images from the VOC2012 dataset** with central blocks, random regions, and semantic cutouts.

## 🔍 Project Overview

* **Dataset**: PASCAL VOC2012 images with synthetically masked regions (over 34,000 samples)
* **Architecture**: AlexNet-based encoder, convolutional layer implementing channel wise fully connected layer behavior, and multi-stage decoder
* **Loss Functions**:

  * **Masked L2 loss** for pixel-level reconstruction
  * **Adversarial loss** using a custom discriminator (GAN)
* **Training**: Conducted on Apple M2 8 GPU cores with batches of size 64 for 50 epochs

## 📂 Directory Structure

```
├── dataset_creation.ipynb
├── model_exploration.ipynb
└── README.md
```

## 🚀 Getting Started

### Clone the Repository

```bash
git clone https://github.com/Ineshtandy/context-encoder-inpainting.git
cd context-encoder-inpainting
```

## 📈 Results

Sample output after 50 epochs with adversarial training (λ\_adv = 0.05):

![L2_GAN_Result](https://github.com/user-attachments/assets/c7edd660-2f4a-4391-af7e-6dead7bfd3b6)

While these results show promising structure and color placement, the outputs still lack texture and appear blurry. This is largely due to computational limitations, which limited time under training, complexity of models and loss functions that could be used.

## 🧪 Future Work

* Longer Training time with increased λ\_adv
* Integrate perceptual (VGG-based) loss
* Explore larger datasets (e.g., COCO or Places2)

## 📝 Citation

Based on:

> Pathak, D., Krähhenbühl, P., Donahue, J., Darrell, T., & Efros, A. A. (2016). [Context Encoders: Feature Learning by Inpainting](https://arxiv.org/abs/1604.07379). *CVPR 2016*.
