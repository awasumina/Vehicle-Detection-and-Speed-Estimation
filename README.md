# Vehicle Detection and Tracking with YOLO and Deep SORT

This project implements real-time object detection, tracking, and speed estimation using the YOLO (You Only Look Once) object detection model and Deep SORT (Simple Online and Realtime Tracking). The system detects various object classes (like cars, persons, buses, etc.), tracks their movements, and estimates their speed as they pass through a predefined line in the camera frame.

## Features
- **Real-time Object Detection:** Utilizes the YOLO model for fast and accurate detection of objects in video streams.
- **Object Tracking:** Tracks multiple objects across frames using the Deep SORT tracker.
- **Speed Estimation:** Calculates the speed of moving objects based on their pixel displacement and an estimated pixels-per-meter value.
- **Directional Counting:** Counts the number of objects moving in a specific direction (e.g., entering or exiting an area).



## How It Works

1. **Vehicle Detection with YOLO:**  
   YOLO detects vehicles (cars, buses, motorbikes, etc.) in the video stream using pre-trained weights from the COCO dataset. It outputs bounding boxes and class labels for each detected object.

2. **Tracking with Deep SORT:**  
   Deep SORT tracks vehicles across frames by assigning unique IDs. It uses a deque to store recent positions, ensuring accurate tracking and preventing ID switching.

3. **Speed Estimation:**  
   The system calculates vehicle speed using the Euclidean distance between consecutive positions. This distance is converted from pixels to real-world meters using a predefined Pixels Per Meter (ppm) constant, and speed is displayed in km/h.

4. **Vehicle Counting:**  
   Vehicles are counted when they cross a designated line in the frame. The `intersect()` function checks if the vehicle moves across the line, and the direction is determined based on the y-coordinate.

5. **Bounding Boxes and Visual Feedback:**  
   Bounding boxes and vehicle speeds are displayed using OpenCV, with trails showing vehicle movement paths. Different colors are used for different vehicle types (e.g., cars, buses).


### Project Implementation

- **`predict.py`:** Main script handling detection, tracking, and speed estimation.
- **YOLOv5 Model:** Detects vehicles and outputs bounding boxes and labels.
- **Deep SORT:** Tracks vehicles with unique IDs and maintains position history.
- **Speed Estimation:** Calculates speed based on vehicle movement over time.



###  Results:
The script will output a video file or stream where:
- Objects are detected with bounding boxes and labels.
- The speed of each object is displayed.
- A count of objects moving in specific directions is shown on the video.

## Speed Estimation
The speed estimation is based on the Euclidean distance between an object's positions in consecutive frames and a defined pixels-per-meter value (PPM). The speed is calculated in km/h.

## Customization
- **Line for Counting:** The script defines a line on the video frame (`line = [(100, 500), (1050, 500)]`). You can adjust this line to suit the area you're monitoring.
- **Object Classes:** The script currently recognizes persons, cars, motorbikes, and buses. You can add more classes by modifying the `compute_color_for_labels` function.


Special thanks to Muhammad Moin Faisal for his open-source implementation, which served as a valuable reference for this project.