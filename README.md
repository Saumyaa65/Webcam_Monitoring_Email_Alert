# Webcam Monitoring with Email Alert

This project provides a simple yet effective **webcam monitoring system** that detects motion and sends an email alert when movement is detected. It's built using **OpenCV** for real-time video processing and a custom module for email functionality.

## Overview

The system continuously monitors a live webcam feed. When it identifies significant motion, it triggers an email notification, acting as a basic surveillance tool. This can be useful for simple home security or office monitoring applications.

## Features

* **Real-time Motion Detection:** Analyzes live video feed to identify movement.
* **Contour-based Object Detection:** Uses image processing techniques (thresholding, dilation, contour finding) to pinpoint moving objects.
* **Visual Feedback:** Displays the live video feed with bounding boxes drawn around detected motion.
* **Email Alerts:** Sends an email notification when motion starts (i.e., a change from no motion to motion).

## Technologies Used

* Python
* OpenCV (`cv2`)
* `time` module
* Custom `emailing` module (for sending emails)

## How It Works

The core logic of the system operates as follows:

1.  **Video Capture:** The project initializes and continuously reads frames from the default webcam.
2.  **Preprocessing:** Each captured frame is converted to grayscale and then a Gaussian blur is applied to reduce noise, making motion detection more robust.
3.  **Baseline Comparison:** The first frame captured is saved as a baseline. Subsequent frames are compared to this `first_frame` to detect differences, highlighting areas where motion has occurred (`delta_frame`).
4.  **Motion Isolation:** The `delta_frame` undergoes thresholding (converting differences to binary white/black pixels) and dilation (enlarging white areas) to better identify and connect areas of movement.
5.  **Contour Detection:** OpenCV's contour finding algorithm is used to identify
