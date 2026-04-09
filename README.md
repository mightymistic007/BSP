# VitalBeat: Multi-Modal Arrhythmia Classification Engine

VitalBeat is a sophisticated biometric framework designed to tackle the challenge of automated cardiac arrhythmia detection. By integrating **Electrocardiogram (ECG)** and **Photoplethysmogram (PPG)** data, the system leverages the electrical and mechanical signatures of the heart to provide a dual-verification diagnostic model.

## 🚀 Key Features & Technical Innovation

* **Multi-Sensor Data Fusion**: VitalBeat addresses the "False Alarm" problem in clinical monitoring by cross-referencing ECG electrical peaks (R-peaks) with PPG pulse waves (Systolic peaks).
* **Deep Signal Denoising**: Employs a multi-stage filtering pipeline including a **Butterworth Bandpass Filter** to isolate cardiac frequencies ($0.5\text{Hz} - 40\text{Hz}$) and a **Notch Filter** to eliminate $50/60\text{Hz}$ powerline interference.
* **Dynamic Peak Analysis**: Utilizes adaptive thresholding for robust peak detection, even in the presence of baseline wander or motion artifacts commonly found in mobile PPG data.
* **Multi-Class Arrhythmia Intelligence**: The engine is trained to differentiate between Sinus Rhythm, Tachycardia (abnormally fast), Bradycardia (abnormally slow), and irregular rhythms like Atrial Fibrillation.

## 🛠️ Tech Stack & Implementation Details

* **Language**: Python 3.x.
* **Signal Processing**: `SciPy.signal` for digital filter design and convolution-based smoothing.
* **Feature Engineering**: Custom algorithms to calculate **RR-Intervals** (ECG) and **PP-Intervals** (PPG), alongside standard deviation of normal-to-normal intervals (SDNN).
* **Machine Learning**: `Scikit-learn` implementation of ensemble classifiers (e.g., Random Forest or SVM) optimized via GridSearch for maximum F1-score.

## 🧪 Detailed Methodology

### 1. Pre-Processing & Artifact Removal
Raw biometric data is often corrupted by "Baseline Wander" (breathing) and "Muscle Noise" (EMG interference). VitalBeat cleans these signals using:
* **Zero-phase filtering** to prevent phase distortion of the QRS complex.
* **Moving Average Smoothing** to sharpen PPG pulse contours for better peak identification.

### 2. Feature Extraction (The "Cardiac Signature")
From each heartbeat, the following features are distilled:
* **Temporal Features**: Heart Rate (BPM), Pulse Arrival Time (PAT), and Peak-to-Peak intervals.
* **Morphological Features**: Pulse width, slope ratio of the PPG dicrotic notch, and QRS duration from ECG.

### 3. Classification & Evaluation
The model is evaluated using a 70/30 train-test split with k-fold cross-validation. Performance is measured through:
* **Confusion Matrices**: To track specific misclassifications between similar arrhythmias.
* **ROC-AUC Curves**: To measure the model's ability to distinguish between healthy and pathological states.

## 📂 Project Structure

```text
/BSP-main
├── BSP_FINAL.ipynb       # Python Notebook: Pre-processing, EDA, and ML Pipeline
├── BSP_PPT.pptx          # Technical Presentation: Visualizing results and logic
├── PPG_Dataset.7z        # Raw Biometric Repository (ECG & PPG time-series)
├── README.md             # Documentation (This file)
└── Research_Report.pdf   # Theoretical background and Arrhythmia Case Study
