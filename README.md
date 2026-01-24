# Cocoa Flower and Fruit Detection Using Deep Learning
## Project Overview

This repository presents a deep learning based object detection pipeline for identifying cocoa flowers and cocoa pods in natural field images. The primary objective of the project is to demonstrate the feasibility of applying modern object detection techniques to agricultural monitoring tasks under limited data conditions.

The project focuses on two key aspects. First, a label consistent data augmentation strategy is used to address the challenge of small annotated datasets. Second, a two stage deep learning detector is trained and evaluated to localize cocoa flowers and pods using bounding boxes.

## Key Contributions

Design of a label consistent data augmentation pipeline for object detection

Handling of Pascal VOC XML annotations with bounding box validation

Training of a Faster R CNN based object detection model

IoU based quantitative evaluation using precision, recall, and F1 score

Visualization of ground truth and predicted bounding boxes


## Dataset Description

Data type. RGB field images

Original dataset size. 18 images

Augmented dataset size. 54 images
Total dataset size: 72 images

Object classes

Flower

Cocoa pod

Annotation format. Pascal VOC XML

The images were collected under real field conditions and annotated manually. Due to the limited dataset size, data augmentation plays a critical role in model training.


## Data Augmentation
A comprehensive data augmentation pipeline was implemented to expand the dataset while maintaining annotation consistency.

Augmentation techniques include.

Geometric transformations such as flipping, rotation, scaling, and translation

Color and illumination variations including brightness, contrast, hue, and saturation

Noise and blur effects to simulate real world conditions

Random cropping followed by resizing

Bounding boxes are transformed together with images, and invalid annotations are automatically filtered to ensure data quality.


## Model Architecture

Detection framework. Faster R CNN

Backbone network. ResNet50 with Feature Pyramid Network

Pretrained weights. COCO dataset

Detection head customized for two object classes and background

The two stage architecture was selected to prioritize detection accuracy over inference speed.


## Training Configuration

Deep learning framework. PyTorch and Torchvision

Optimizer. Stochastic Gradient Descent

Learning rate. 0.005

Batch size. 2

Number of epochs. 100

Training environment. Google Colab GPU


## Evaluation Methodology
Model performance is evaluated using an IoU based matching strategy on the validation dataset.

Evaluation details.

Intersection over Union threshold. 0.7

Confidence score threshold. 0.7

Metrics reported

Precision

Recall

F1 score

Due to the small dataset size, standard mean average precision evaluation was not applied. The selected metrics provide an interpretable assessment of detection correctness under strict localization constraints.
## Performance Analysis

To validate the real-world efficiency of the model, a comparative study was conducted between manual human counting and the AI model on a representative field image (Image 2.2).

### 1. Detection Accuracy (Case Study)
| Object Class | Manual Count (Ground Truth) | AI Model Detection | Accuracy vs Manual |
| :--- | :--- | :--- | :--- |
| **Cocoa Flowers** | 19 | 13 | 68.4% |
| **Cocoa Pods** | 40 | 38 | **95.0%** |
| **Total Objects** | **59** | **51** | **86.4%** |

*Observation:* The model achieved high accuracy (95%) on Cocoa Pods, which are the primary yield indicators. Flower detection proved more challenging due to the small size of objects, yet the model still captured the majority of instances.

### 2. Time Efficiency
The most significant advantage of this pipeline is the drastic reduction in processing time.

* **Manual Counting Time:** 2 minutes (120 seconds)
* **AI Processing Time:** 0.11 seconds

> **Result:** The AI model is approximately **1,090x faster** than manual inspection. This demonstrates that the system can process large datasets in seconds, whereas manual counting would require hours of labor.
## Performance Analysis

To validate the real-world efficiency of the model, a comparative study was conducted between manual human counting and the AI model on a representative field image (Image 2.2).

### 1. Detection Accuracy (Case Study)
| Object Class | Manual Count (Ground Truth) | AI Model Detection | Accuracy vs Manual |
| :--- | :--- | :--- | :--- |
| **Cocoa Flowers** | 19 | 13 | 68.4% |
| **Cocoa Pods** | 40 | 38 | **95.0%** |
| **Total Objects** | **59** | **51** | **86.4%** |

### 2. Time Efficiency
* **Manual Counting Time:** 2 minutes (120 seconds)
* **AI Processing Time:** 0.11 seconds

> **Result:** The AI model is approximately **1,090x faster** than manual inspection.

### 3. Visual Proof
Here are the screenshots from our experiment:

| AI Detection Result | Time Computation Log |
| :---: | :---: |
| ![AI Result](Assets/Ai_Result.jpeg) | ![Time Log](Assets/Time_Log.jpeg) |
*Figure 1: Left: AI detecting flowers/pods. Right: Log showing 0.11s inference time.*

## Project Structure
Typical output structure of the augmented dataset.

augmented_data
images
original and augmented images
labels
corresponding Pascal VOC XML annotations
augmentation_samples.png
visual comparison of augmented samples


## Visualization
The repository includes utilities for.

Visualizing ground truth bounding boxes

Visualizing model predictions with confidence scores

Plotting training loss curves


## Limitation

Extremely small original dataset

Limited variation in geographic and seasonal conditions

Absence of large scale benchmark evaluation


## Future Work

Collection of larger annotated datasets

Standard evaluation using mean average precision

Exploration of lightweight models for real time deployment

Extension to additional agricultural object classes


## Usage
The project is designed to be executed in Google Colab. Dataset directories must follow the specified image and annotation structure before training or evaluation.

## Citation
If you use or reference this work, please cite it as a course project.

## Acknowledgment
The authors acknowledge the contributors of the field collected cocoa image dataset and the open source libraries used in this project.
## Team Contributions
- Bikram Regmi: Dataset labelling, Data Agumentation, Model training, inference, and evaluation, Repository setup and final integration
  
- Prabhat Pouel: Dataset  labelling, Data Agumentation, Model training, inference, and evaluation
  
- Mina Baidhya: Dataset labelling,Data Agumentation, Model training, inference, and evaluation
