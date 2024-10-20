# Object-Detection
This project performs object detection on shelf images using OpenCV and a pre-trained YOLOv3 model. It detects common objects (e.g., bottles, books) and displays bounding boxes with labels. The model is based on the COCO dataset, and the output image with detections is saved for further analysis or display.

Here's a basic template for your `README.md` file, including detailed instructions on setting up and executing each part of your project.

---

# Object Detection on Shelf Images Using YOLOv3

## Overview

This project demonstrates how to perform object detection on images of shelves using OpenCV and a pre-trained YOLOv3 model. The script processes an image to detect common objects (such as bottles, books, etc.) and outputs the image with bounding boxes and labels. The model used is trained on the COCO dataset.

### Project Structure:
- `yolov3.weights`: Pre-trained YOLOv3 weights.
- `yolov3.cfg`: YOLOv3 configuration file.
- `coco.names`: Class labels for the COCO dataset.
- `shelf1.png`: Example image of shelves used for object detection.
- `detected_output.png`: Output image with detected objects.
- `object_detection.py`: The Python script that performs object detection.
- `README.md`: Instructions on how to set up and run the project.

---

## Setup Instructions

### 1. Install Required Dependencies
The following libraries are required to run the object detection script. You can install them using `pip`.

```bash
pip install opencv-python numpy
```

Alternatively, if you are running the script in Google Colab, you can use the pre-installed libraries for OpenCV and NumPy.

### 2. Download the YOLOv3 Model and Class Labels

You will need to download the following files to run YOLOv3:

1. **YOLOv3 Weights**: Download the pre-trained weights from the [official YOLO website](https://pjreddie.com/media/files/yolov3.weights) and place it in the project directory.
   - Direct Download: [yolov3.weights](https://pjreddie.com/media/files/yolov3.weights)

2. **YOLOv3 Configuration File**: Download the configuration file from the official YOLO GitHub.
   - Direct Download: [yolov3.cfg](https://github.com/pjreddie/darknet/blob/master/cfg/yolov3.cfg)

3. **COCO Class Names**: Download the class names file, which contains the names of the 80 classes YOLO is trained to detect.
   - Direct Download: [coco.names](https://github.com/pjreddie/darknet/blob/master/data/coco.names)

Place all three files (`yolov3.weights`, `yolov3.cfg`, and `coco.names`) in the project directory.

### 3. Running the Script in Google Colab

If you're using Google Colab, follow these steps to run the object detection script:

1. Upload the required files (`yolov3.weights`, `yolov3.cfg`, `coco.names`, and an image) to your Colab environment.
2. Run the provided Python script (`object_detection.py`) or the final code provided in the notebook.

If you are running the script locally, make sure OpenCV is installed as mentioned in step 1.

---

## Execution Instructions

### Step 1: Modify the Image Path
Make sure to modify the image path in the script according to the image you want to process.

For example, replace the following line in the script:
```python
image = cv2.imread('/content/shelf1.png')  # Replace with your image path
```

### Step 2: Run the Object Detection Script

To execute the Python script and perform object detection, run the following command in your terminal (or Google Colab environment):

```bash
python object_detection.py
```

If you're running this in Colab, use the provided notebook cells to run the script.

### Step 3: View and Save the Output

Once the script has finished running, the detected objects will be shown in a window or within the Colab environment (via `cv2_imshow()`). The output image with bounding boxes will be saved as `detected_output.png`.

---

## Example Output

The script detects common objects on the shelf (like books, bottles, etc.) and overlays bounding boxes and class labels on the image.

---

## Troubleshooting

### 1. Image Not Found:
If you receive an error like `Error: Image not found or path is incorrect.`, ensure the image path is correct and that the image file is in the project directory or correctly referenced.

### 2. No Objects Detected:
If the message `No objects detected in the image.` appears, try using different images, or adjust the confidence threshold in the code to detect more objects:
```python
if confidence > 0.5:  # Adjust this threshold to 0.4 or lower if needed
```

### 3. Non-Maximum Suppression Issues:
If bounding boxes overlap too much, you can adjust the NMS threshold:
```python
indices = cv2.dnn.NMSBoxes(boxes, confidences, 0.5, 0.4)  # You can lower the second value (0.4) for stricter NMS

