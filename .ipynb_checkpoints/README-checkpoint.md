
# Road Damage Detection and Segmentation Pipeline

## Project Overview

This project implements a complete computer vision pipeline for automatic road damage detection using OpenCV and Python. The system processes road video footage and detects multiple types of road surface defects including:

- Potholes
- Alligator Cracks
- Edge Cracks
- Faded Pedestrian Crossings

The pipeline performs preprocessing, region masking, feature extraction, segmentation, contour analysis, and visual annotation on each video frame.

---

# Folder Structure

```text
project_folder/
│
├── full_pipeline.py          # Main executable program
├── v9.mp4                    # Input road video
│
├── output/
│   └── final.avi             # Final processed output video
│
└── README.md                 # Project documentation
````

---

# Required Libraries

Install the following Python libraries before running the program:

```bash
pip install opencv-python numpy
```

---

# Technologies Used

* Python
* OpenCV
* NumPy

---

# Pipeline Stages

The system follows the following processing pipeline:

```text
Input Video
      ↓
Frame Extraction
      ↓
Preprocessing
(Grayscale + Gaussian Blur + CLAHE Enhancement)
      ↓
Road ROI Masking
      ↓
Feature Extraction
(Edges / Thresholding / Line Detection)
      ↓
Damage Segmentation
      ↓
Morphological Refinement
      ↓
Contour Analysis
      ↓
Damage Classification
      ↓
Output Annotation
      ↓
Final Video Generation
```

---

# Damage Detection Methods

## 1. Alligator Crack Detection

* Uses crack density analysis
* Detects interconnected crack regions
* Uses contour area and aspect ratio filtering

## 2. Edge Crack Detection

* Focuses on left and right road boundaries
* Detects elongated crack structures
* Uses sliding window crack density estimation

## 3. Pothole Detection

* Uses intensity thresholding
* Applies morphological operations
* Removes stripe-like false detections

## 4. Faded Crossing Detection

* Uses Hough Line Transform
* Detects parallel horizontal faded crossing lines
* Validates spacing consistency

---

# Input Description

| Input    | Description                              |
| -------- | ---------------------------------------- |
| `v9.mp4` | Road inspection video used for detection |

### Supported Input

* MP4 video format
* Road surface driving videos

---

# Output Description

| Output             | Description                                                   |
| ------------------ | ------------------------------------------------------------- |
| `output/final.avi` | Final annotated output video containing detected road damages |

### Output Features

* Bounding boxes around damages
* Damage labels
* Real-time damage counts
* Combined visualization:

  * Original frame
  * Enhanced frame
  * Detection output

---

# How to Run the Program

## Step 1 — Place Input Video

Copy your input video into the project folder and rename it as:

```text
v9.mp4
```

---

## Step 2 — Run the Program

Execute the following command:

```bash
python full_pipeline.py
```

---

## Step 3 — View Results

During execution:

* Real-time detection window will appear
* Press `ESC` to stop execution

After completion:

```text
output/final.avi
```

will contain the final processed video.

---

# Main Functional Components

| Function                  | Purpose                         |
| ------------------------- | ------------------------------- |
| `enhance()`               | Image enhancement using CLAHE   |
| `road_mask()`             | Defines road Region of Interest |
| `detect_cracks()`         | Extracts crack edges            |
| `detect_edge_cracks()`    | Detects edge cracking           |
| `detect_alligator()`      | Detects alligator cracking      |
| `detect_pothole()`        | Detects potholes                |
| `detect_faded_crossing()` | Detects faded crossings         |

---

# Detection Color Codes

| Damage Type     | Color  |
| --------------- | ------ |
| Alligator Crack | Green  |
| Edge Crack      | Cyan   |
| Pothole         | Red    |
| Faded Crossing  | Orange |

---

# Example Display

```text
Input Frame | Enhanced Frame | Detection Output
```

The output screen displays all three stages side-by-side for easy comparison.

---

# Future Improvements

* Deep learning based segmentation
* YOLO integration
* Real-time webcam support
* GPS-based road mapping
* Damage severity estimation
* Performance optimization using GPU

---


```
