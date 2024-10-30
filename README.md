# YOLOv11 Sign Language Detection

This project uses a custom-trained YOLOv11 model with 40 classes to detect hand signs for sign language recognition. The project employs OpenCV for real-time inference through webcam feed.

## Requirements

- Python 3.x
- OpenCV
- PyTorch
- Ultralytics YOLO (for ONNX model support)

## Installation

1. Clone the repository:

    ```bash
    git clone https://github.com/alihassanml/Yolo11-sign-language-detection.git
    cd Yolo11-sign-language-detection
    ```

2. Install dependencies:

    ```bash
    pip install -r requirements.txt
    ```

3. Ensure that `best.onnx` (the trained model) is in the project directory.

## Code Usage

Use the following code to run real-time sign language detection from your webcam:

```python
from ultralytics import YOLO
import cv2

model = YOLO('best.onnx')
cap = cv2.VideoCapture(0)

while True:
    ret, frame = cap.read()
    if not ret:
        print("Failed to grab frame.")
        break  

    results = model(frame)
    result = results[0]

    annotated_frame = result.plot() 
    cv2.imshow('YOLO Inference', annotated_frame)
    
    if cv2.waitKey(1) == 27:
        break

cap.release()
cv2.destroyAllWindows()
```

## Run the Project

Run the script with:

```bash
python sign_language_detection.py
```

## Repository Link

[YOLOv11 Sign Language Detection GitHub Repository](https://github.com/alihassanml/Yolo11-sign-lanugage-detection.git)
