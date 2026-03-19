# Mask2Rep: Self-Supervised Image Representation Learning

**Mask2Rep** is a custom-built Masked Autoencoder (MAE) trained entirely from scratch using PyTorch. The model leverages the power of Self-Supervised Learning (SSL) to reconstruct high-fidelity spatial and semantic representations from heavily occluded images (75% masked).

📖 **Read the Full Technical Deep-Dive on Medium:** [Mask2Rep Article](https://medium.com/@hjethani20/demystifying-self-supervised-learning-building-a-masked-autoencoder-mae-from-scratch-8f82b146f78f)  
⚙️ **Try the Live Interactive Demo:** [Hugging Face Space](https://huggingface.co/spaces/haresh8765/Mask2Rep-Self-Supervised-Image-Representation-Learning)

---

## Architecture Highlights

At the core of Mask2Rep is an **Asymmetric Vision Transformer (ViT)**. The architecture is designed for maximum computational efficiency while learning deep semantic boundaries.

* **Patch Tokenization & Extreme Masking:** Input images are divided into non-overlapping 16x16 patches. We apply an aggressive **75% masking ratio**, dropping out a large majority of the visual context.
* **Heavyweight Encoder:** The deep ViT encoder processes *only* the visible 25% of unmasked patches. This significantly reduces computational overhead and memory allocation during training.
* **Lightweight Decoder:** A decoupled, shallow decoder integrates the encoded latent vectors with learnable mask tokens and positional embeddings to hallucinate and reconstruct the missing 75% of the image.
* **Loss Function:** The model is optimized strictly by minimizing the Mean Squared Error (MSE) across the masked patches, forcing it to learn a holistic understanding of object shapes rather than memorizing local pixels.

---

## Model Training Details

* **Framework:** PyTorch
* **Hardware:** Nvidia Tesla T4 GPUs (Kaggle)
* **Mask Ratio:** 0.75
* **Loss Function:** MSE (Computed on masked patches only)
* **Model Size:** 1.29 GB (Weights separated via decoupled registry architecture for deployment)

---

## How to Run Locally

### 1. Clone the Repository
```bash
git clone [https://github.com/Hareshjethani/Mask2Rep-Self-Supervised-Image-Representation-Learning.git](https://github.com/Hareshjethani/Mask2Rep-Self-Supervised-Image-Representation-Learning.git)
cd Mask2Rep-Self-Supervised-Image-Representation-Learning
2. Install Dependencies
Bash
pip install -r requirements.txt
3. Run Inference
You can run the inference script by providing an input image:

Bash
python inference.py --image_path ./sample_images/test.jpg --mask_ratio 0.75
(Note: Ensure you download the pre-trained weights from Hugging Face before running inference.)
```
Team
This project was built and deployed collaboratively by:

Haresh Kumar

License
This project is licensed under the MIT License. Feel free to use, modify, and distribute the code as per the license terms
