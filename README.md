# Low-Light Image Enhancement using CNN

This repository contains a Convolutional Neural Network (CNN) model designed from scratch to enhance low-light images—with an architecture resembling a simplified encoder-decoder (similar to U-Net) and custom training strategies.

---

## Project Overview & Motivation

I built this pipeline entirely from scratch to deeply understand how deep learning techniques are applied to real-world image enhancement tasks. Starting from a basic CNN, I incrementally developed encoder-decoder blocks with skip-like connections to better preserve spatial information.

To ensure effective training, I implemented:

* **Early stopping** — to prevent overfitting
* **Adaptive learning rate scheduling** — to help the model converge efficiently

Throughout, I continuously visualized training metrics (loss curves, learning rate changes) and output images to monitor progress and guide debugging.

---

## Repository Structure

* **`CNN.ipynb`**: The main notebook covering:

  1. **Data loading/preprocessing** — reads paired low-light and normal-light images
  2. **Model definition** — builds convolutional encoder-decoder blocks
  3. **Training loop** spans:

     * Loss and validation metrics
     * Early stopping based on validation loss
     * Adaptive learning rate scheduler
     * **Visualization callbacks** plotting:

       * Training vs. validation loss curves over epochs
       * Change in learning rate
       * Snapshot image outputs at selected epochs to track visual improvement
  4. **Evaluation** — test-time examples compared side-by-side with ground truth
  5. **Visualization summary graphs** — shows how the model’s predictions gradually match the test data

---

## Dataset

The dataset used for training is available on Kaggle:

👉 **[Train3 – Low-Light Image Dataset by aditidatta26](https://www.kaggle.com/datasets/aditidatta26/train3)**

Contains paired folders:

* `low_light/` — dim input images
* `normal_light/` — corresponding bright ground truths

> Ensure consistent filenames and dimensions across both folders.

---

## How to Run

1. **Clone the repo:**

   ```bash
   git clone https://github.com/Adi26Datta/LowLightImageEnhancement.git
   cd LowLightImageEnhancement
   ```

2. **Download the dataset:**

   ```bash
   kaggle datasets download -d aditidatta26/train3
   unzip train3.zip -d dataset
   ```

3. **Install dependencies:**

   ```bash
   pip install -r requirements.txt
   ```

4. **Launch the notebook:**

   ```bash
   jupyter notebook CNN.ipynb
   ```

5. **Run all cells** to reproduce data loading, model training, metric visualization, and final enhancement results.

---

## Model Architecture & Training Highlights

* **Encoder-decoder** CNN blocks, inspired by U-Net

* **Skip-like connections** to maintain image details

* **Training setup**:

  * Loss: Mean Squared Error (MSE)
  * Optimizer: Adam
  * Early stopping based on validation loss
  * Adaptive learning rate (e.g. ReduceLROnPlateau)

* **Visualization**:

  * **Loss curves** (training vs. validation)
  * **Learning rate schedule** plot
  * **Output snapshots** every few epochs to visually track improvements

These visualizations helped confirm that the model gradually learns to match low-light inputs to their well-lit counterparts.

---

## Results

* **Quantitative**: Final loss values and validation trajectories plotted
* **Qualitative**: Side-by-side comparisons (input → predicted → ground truth) show the model transforming dark scenes into visually accurate bright images, nearly matching the test data.

All visualization panels and comparison figures are available in the notebook for inspection and analysis.

---

## Future Work

* Expand to deeper U-Net or ResNet-style backbones
* Apply to diverse real-world low-light datasets (night photography, security footage)
