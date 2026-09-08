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
Video -> MediaPipe Pose -> Pose Landmark -> Extraction Feature Engineering -> Sliding Window -> 
CNN-LSTM -> Exercise Classification -> Real-Time Prediction

## Video/Dataset
This project uses video data from two publicly available human action recognition datasets:

## UCF101
UCF101 is a human action recognition dataset developed by the Center for Research in Computer Vision (CRCV) at the University of Central Florida.
The dataset contains 13,320 videos across 101 action categories. It includes a wide range of realistic human actions with variations in camera motion, viewpoint, background, illumination, and body pose.
Several action categories relevant to this project are available in UCF101, including:
- Body Weight Squats
- Jumping Jack
- Lunges
- Push Ups

Official dataset:
[UCF101 – Action Recognition Dataset](https://www.crcv.ucf.edu/data/UCF101.php)

## HMDB51
HMDB51 (Human Motion Database) is a human action recognition dataset developed by researchers from Brown University and collaborators.
The dataset contains 51 action categories and thousands of short video clips collected from movies and web videos. It provides diverse variations in viewpoint, camera motion, video quality, illumination, and human movement.
The dataset includes action categories relevant to this project, such as:
- Push Up
- Sit Up

Official dataset:
[HMDB51 – Human Motion Database](https://serre.lab.brown.edu/hmdb51.html)

## Dataset Usage in This Project
This project does not use the complete UCF101 and HMDB51 datasets. Instead, a subset of videos from the relevant action categories was selected for the classification task.
The selected videos were processed through the MediaPipe Pose feature extraction pipeline and transformed into temporal feature sequences for CNN-LSTM model training.

The five target exercise classes in this project are:

- Jumping Jack
- Lunges
- Push-up
- Squat
- Sit-up

The Sit-up class was supplemented with manually collected video data to provide the required class for the classification task.
The original datasets are not included in this repository due to dataset size and storage considerations. Users interested in reproducing the project can obtain the datasets from their respective official sources above.

### Dataset References
If you use these datasets, please refer to their original publications:
- Soomro, K., Zamir, A. R., & Shah, M. (2012). *UCF101: A Dataset of 101 Human Actions Classes From Videos in The Wild.*
- Kuehne, H., Jhuang, H., Garrote, E., Poggio, T., & Serre, T. (2011). *HMDB: A Large Video Database for Human Motion Recognition.*


## Feature Extraction
Human body pose information is extracted from video frames using MediaPipe Pose. The extracted features consist of three main groups:
### 1. Spatial Features
Spatial features represent the pose information of the human body at each frame.
### 2. Velocity Features
Velocity features describe the change in spatial features between consecutive frames.
### 3. Acceleration Features
Acceleration features describe the change in velocity over time.

The final feature representation consists of:
- 45 spatial features
- 45 velocity features
- 45 acceleration features
**Total: 135 features per frame**

## Temporal Sequence

The frame-level features are organized into temporal sequences using a sliding window approach.

The model input consists of:

**30 frames × 135 features**

The sequence length corresponds to approximately one second of video when using a 30 FPS reference.

## Model Architecture

The project uses a hybrid **Convolutional Neural Network (CNN) and Long Short-Term Memory (LSTM)** architecture.

### 1D Convolutional Neural Network

The 1D CNN is used to extract local patterns from the temporal feature sequence.

### Long Short-Term Memory

The LSTM is used to learn temporal dependencies and movement patterns across consecutive frames.

The combination of CNN and LSTM allows the model to capture both local feature patterns and temporal characteristics of human movement.

The overall model structure can be summarized as:

**Input Sequence (30 × 135) → 1D CNN → LSTM → Classification Layer → Exercise Class**

## Data Augmentation

Several data augmentation techniques were used during model development to improve the robustness of the model:

- Horizontal Flip
- Time Warping
- Gaussian Noise

These techniques introduce variations in body orientation, movement timing, and feature values during training.

## Model Training

The model training process includes:

- Data preparation
- Feature preprocessing
- Feature engineering
- Temporal sequence generation
- Data augmentation
- CNN-only model
- LSTM-only model
- CNN-LSTM model
- Model training
- Validation
- Ablation study
- Temporal ensemble analysis

Different model configurations were evaluated to compare their performance and identify the final CNN-LSTM configuration.

## Model Evaluation

The model is evaluated using several classification metrics, including:

- Accuracy
- Precision
- Recall
- F1-score
- Confusion Matrix

The reported model performance is:

| Metric | Result |
|---|---:|
| Test Accuracy | **91.79%** |
| Validation Accuracy | **94.96%** |

The evaluation process also includes temporal prediction analysis to examine the effect of temporal ensemble and smoothing on classification performance.

## Real-Time Implementation

The trained model is integrated into a real-time webcam application using:

- OpenCV
- MediaPipe Pose
- TensorFlow / Keras

The real-time system performs the following steps:

**Webcam Frame → MediaPipe Pose → Pose Landmark Extraction → Feature Engineering → Sequence Buffering → CNN-LSTM Inference → Temporal Smoothing → Exercise Prediction**

The implementation also performs real-time monitoring and logging of system performance and prediction results.

## Project Structure

    Bodyweight-Exercise-Classification-Using-CNN-LSTM/
    │
    ├── README.md
    ├── requirements.txt
    │
    └── notebooks/
        ├── 01_feature_extraction.ipynb
        ├── 02_model_training.ipynb
        ├── 03_model_evaluation.ipynb
        └── 04_realtime_implementation.ipynb

## Notebook Description

| Notebook | Description |
|---|---|
| `01_feature_extraction.ipynb` | Extracts human pose landmarks from video using MediaPipe Pose and performs feature engineering. |
| `02_model_training.ipynb` | Prepares temporal sequences, trains CNN, LSTM, and CNN-LSTM models, and performs model experiments and ablation studies. |
| `03_model_evaluation.ipynb` | Evaluates the trained model using classification metrics, confusion matrix, and temporal prediction analysis. |
| `04_realtime_implementation.ipynb` | Implements real-time exercise classification using a webcam, MediaPipe Pose, and the trained CNN-LSTM model. |

## Technologies

- Python
- TensorFlow / Keras
- MediaPipe
- OpenCV
- NumPy
- Pandas
- Scikit-learn
- Matplotlib
- Jupyter Notebook


Environment Note: This project was developed and tested using MediaPipe 0.10.20. Reproducing the exact environment may require using a compatible Python version and package configuration.
