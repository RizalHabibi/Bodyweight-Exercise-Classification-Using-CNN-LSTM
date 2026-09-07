# Bodyweight-Exercise-Classification-Using-CNN-LSTM
 Bodyweight Exercise Classification Using CNN-LSTM

# Bodyweight Exercise Classification Using CNN-BiLSTM

A computer vision and deep learning project for real-time classification
of bodyweight exercises using MediaPipe Pose and a CNN-BiLSTM architecture.

## Overview

This project implements a human activity recognition system that classifies
five bodyweight exercises:

- Jumping Jack
- Lunges
- Push-up
- Squat
- Sit-up

The system extracts human pose landmarks using MediaPipe Pose and uses
spatial, velocity, and acceleration features as input to a CNN-BiLSTM model.

## Pipeline

Video
→ MediaPipe Pose
→ Feature Extraction
→ Feature Engineering
→ Sliding Window
→ CNN-BiLSTM
→ Classification
→ Real-Time Prediction

## Model

The model combines:

- 1D Convolutional Neural Network (CNN)
- Bidirectional Long Short-Term Memory (Bi-LSTM)

The input sequence consists of 30 frames with 135 features per frame.

## Features

The model uses three groups of features:

- Spatial features
- Velocity features
- Acceleration features

These features are derived from MediaPipe Pose landmarks.

## Results

| Metric | Result |
|---|---:|
| Test Accuracy | **91.79%** |
| Validation Accuracy | **94.96%** |

## Technologies

- Python
- MediaPipe
- TensorFlow / Keras
- Scikit-learn
- NumPy
- Pandas
- OpenCV
- Matplotlib

## Project Structure

```text
notebooks/
├── 01_mediapipe_feature_extraction.ipynb
├── 02_model_training.ipynb
├── 03_model_evaluation.ipynb
└── 04_realtime_implementation.ipynb
