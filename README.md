# 🛡️ **FaceGuard: AI‑Based Facial Recognition Access Control System**

A deep‑learning–powered facial recognition system designed to secure high‑sensitivity environments by verifying employee identity before granting access. Built as part of the ELE8100 CyberAI coursework at Queen’s University Belfast, this project demonstrates how convolutional neural networks can be applied to real‑world cybersecurity challenges.
---

## **Project Overview**

FaceGuard is an access‑control system that identifies individuals from 64×64 grayscale facial images and determines whether they are authorised to enter a secure server room.  
Only the following employees are granted access:
- **Employee ID 0 — CEO**  
- **Employee ID 5 — CTO**  
- **Employee ID 10 — System Administrator**
All other IDs (1–4, 6–9, 11–39) are denied access.

The system is trained on the **Augmented Olivetti Faces Dataset** (2000 images, 40 classes) and achieves **98–99% test accuracy**.
---

## **Model Architecture**

A custom CNN built using PyTorch:

- **Conv Block 1:**  
  - Conv2D (1 → 32 filters, 3×3)  
  - BatchNorm2D  
  - ReLU  
  - MaxPool (2×2)

- **Conv Block 2:**  
  - Conv2D (32 → 64 filters, 3×3)  
  - BatchNorm2D  
  - ReLU  
  - MaxPool (2×2)

- **Fully Connected Layers:**  
  - Flatten → 256 neurons → ReLU + Dropout  
  - Output layer: 40‑class softmax

- **Regularization:**  
  - Dropout (0.5)  
  - Batch Normalization  

This architecture balances feature extraction, generalization, and computational efficiency for small grayscale images.
---

##**Training & Evaluation**

**Training Setup:**

- Loss: `CrossEntropyLoss`  
- Optimizer: `Adam (lr=0.001)`  
- Scheduler: `ReduceLROnPlateau`  
- Batch size: 32  
- Epochs: 50  
- 80/20 stratified train‑test split  
- Additional 90/10 train‑validation split

**Results:**

- **Test Accuracy:** **98.75%**  
- Strong generalization with minimal overfitting  
- High precision/recall across all 40 classes  
- Confusion matrix confirms reliable identification of authorised IDs (0, 5, 10)

Training curves include:

- Training vs. validation loss  
- Training vs. validation accuracy  

---

##**Access Control Function**

The `check_access()` function:

- Accepts a 64×64 grayscale face image  
- Performs inference using the trained CNN  
- Computes softmax probabilities  
- Determines whether access is **GRANTED** or **DENIED**  
- Displays:
  - Input image  
  - Predicted ID  
  - Confidence score  
  - Access decision (visual + text)

This simulates a real‑world access‑control workflow.
---

##**Demo: Test Cases**

The notebook includes at least 5 test cases:

- ✔️ CEO (ID 0) — Authorized  
- ✔️ CTO (ID 5) — Authorized  
- ✔️ System Administrator (ID 10) — Authorized  
- ❌ Employee 3 (ID 3) — Unauthorized  
- ❌ Employee 15 (ID 15) — Unauthorized  
- ❌ Employee 25 (ID 25) — Unauthorized  

Each test displays a visual decision panel.
---

## **Dataset**

**Augmented Olivetti Faces Dataset**  
- 2000 images  
- 40 individuals  
- 64×64 grayscale  
- Balanced: 50 images per class  
- Normalized to [0, 1]

Dataset sourced via KaggleHub or Canvas.
---

## 🛠️ **Technologies Used**

- Python  
- PyTorch  
- NumPy  
- Matplotlib  
- Scikit‑Learn  
- Seaborn  
- PIL  
---

##**How to Run**

1. Clone the repository  
2. Install dependencies  
3. Download the dataset (KaggleHub or Canvas)  
4. Run the Jupyter Notebook  
5. Load the trained model or train from scratch  
6. Use `check_access()` to test access control
---

## **Project Structure**

```
FaceGuard/
│
├── augmented_faces.npy
├── augmented_labels.npy
├── best_faceguard_model.pth
├── CW1_ShreeyaKangutkar.ipynb
├── README.md
└── images/ (optional screenshots)
```

---

## Academic Context
This project was developed for:

ELE8100 – CyberAI  
MSc Applied Cyber Security  
Queen’s University Belfast  
Academic Year 2025/26
---

## **License**

This project is for academic use.  
If you wish to reuse or extend it, please credit the original author.

 A **viva preparation cheat sheet**  

Just tell me what you want next.
