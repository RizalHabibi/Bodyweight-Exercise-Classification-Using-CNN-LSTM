# Bodyweight-Exercise-Classification-Using-CNN-LSTM

A computer vision and deep learning project for real-time classification
of bodyweight exercises using MediaPipe Pose and a CNN-LSTM architecture.

## Overview

This project implements a human activity recognition system that classifies
five bodyweight exercises:

- Jumping Jack
- Lunges
- Push-up
- Squat
- Sit-up

The system uses MediaPipe Pose to extract human body landmarks from video frames. The extracted pose data transformed into spatial, velocity, and acceleration features and processed as temporal sequences using a CNN-LSTM model.

## Objective
The project was developed as part of an undergraduate thesis in Electrical Engineering.
The main objective of this project is to develop a deep learning-based system capable of recognizing bodyweight exercises from human pose information and supporting real-time exercise classification.

The project focuses on:
- Human pose-based feature extraction
- Temporal sequence modeling
- CNN-LSTM architecture for activity classification
- Model evaluation and performance analysis
- Real-time inference using a webcam

## Pipeline
The overall processing pipeline is:
Video
  ↓
MediaPipe Pose
  ↓
Pose Landmark Extraction
  ↓
Feature Engineering
  ↓
Sliding Window
  ↓
CNN-LSTM
  ↓
Exercise Classification
  ↓
Real-Time Prediction

## Model

The model combines:

- 1D Convolutional Neural Network (CNN)
- Long Short-Term Memory (LSTM)

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
