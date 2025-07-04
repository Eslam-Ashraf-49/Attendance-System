# Face Recognition Attendance System

Automated attendance using face recognition. This project captures real-time webcam input, detects and recognizes faces using reference images, and logs recognized individuals with timestamps into a CSV file.

## Table of Contents

- [Overview](#overview)
- [How It Works](#how-it-works)
- [Installation](#installation)
- [Project Structure](#project-structure)
- [Usage](#usage)
- [Dataset Preparation](#dataset-preparation)
- [Output](#output)
- [Requirements](#requirements)
- [Limitations](#limitations)
- [License](#license)

---

## Overview

This tool uses the webcam to recognize pre-encoded faces from a folder of images and mark attendance in a `CSV` file. It supports:

- Real-time video processing
- One-time attendance per session
- Clean and modular codebase
- Streamlit interface for interactive use

---

## How It Works

1. Loads all images from a folder (`AttendanceImages`)
2. Extracts face encodings from each image
3. Captures webcam video and resizes it for faster processing
4. Detects faces in each video frame and compares them to known encodings
5. If a face matches a known encoding, it logs the name and current time into `Attendance.csv` (if not already logged)

---

## Installation

### 1. Clone the repository

```bash
git clone https://github.com/your-username/system-attendance.git
cd system-attendance
```

### 2. Install required packages

Use the `requirements.txt` file:

```bash
pip install -r requirements.txt
```

Make sure `dlib` is installed properly, as it is a dependency of `face_recognition`. If installation fails, install system dependencies manually.

---

## Project Structure

```
system-attendance/
├── AttendanceImages/       # Folder containing reference face images
├── Attendance.csv          # Output file for attendance logs
├── app.py                  # Streamlit interface
├── main.py                 # Original OpenCV script (optional)
├── requirements.txt        # Required packages
└── README.md               # Documentation
```

---

## Usage

### Run the Streamlit app

```bash
streamlit run app.py
```

### Interface

- Checkbox starts or stops webcam feed
- Recognized names appear on video frame
- Attendance is saved to `Attendance.csv`

---

## Dataset Preparation

1. Create a folder named `AttendanceImages`
2. Add clear, front-facing photos
3. Use filenames as the person's name, e.g.:

```
AttendanceImages/
├── Alice.jpg
├── Bob.png
├── Charlie.jpeg
```

Each image should contain only one face.

---

## Output

- `Attendance.csv` file will contain rows like:

```
Name,Time
ALICE,09:32:15
BOB,09:35:42
```

- No duplicate names per session

---

## Requirements

```
face_recognition
opencv-python
numpy
streamlit
```

Install with:

```bash
pip install -r requirements.txt
```

---

## Limitations

- Each person must have one clear reference image
- Only one face per reference image
- Works best with frontal face images
- Webcam quality and lighting affect accuracy
- Cannot detect spoofing (e.g., printed photo)

---

## License

This project is licensed under the MIT License.
