# README.md

## Overview

This code is a simple web application built with Flask that uses a pre-trained emotion detection model to detect emotions in real-time video stream from a webcam. The application uses OpenCV to capture video frames, detect faces in the frames, and predict emotions on the detected faces. The predicted emotions are then displayed on the frames and streamed to a web page.

## Requirements
- Flask
- OpenCV
- Keras
- Numpy

## Usage
1. Clone the repository
git clone https://github.com/[username]/emotion-detection-webapp.git

2. Install the required packages
pip install -r requirements.txt

3. Run the application
python app.py

4. Open http://0.0.0.0:8000 in a web browser to see the video stream with emotion detection.

## Model
The model used in this application is `fer2013_mini_XCEPTION.102-0.66.hdf5` which is trained on the FER2013 dataset. The model is loaded from the `emotion_model` directory. The model is taken from [this GitHub repository](https://github.com/oarriaga/face_classification)

## Code Explanation
- `app.py` is the main script that runs the Flask application.
- `index.html` is the template for the main page of the application.
- `lib/python3.10/site-packages/cv2/data/haarcascade_frontalface_default.xml` is the xml file for the Haar cascade classifier used for face detection.
- `emotion_dict` is a dictionary that maps the integer labels of emotions to the corresponding emotion names.
- `apply_offsets` and `preprocess_input` are helper functions used for preprocessing the detected face before feeding it to the model.
- `gen` is a generator function that captures video frames, detects faces, predicts emotions, and yields the video frames with emotion labels to the Flask application.
- `video_feed` is a Flask endpoint that streams the video frames with emotion detection to the web page.

## Note
- Make sure you have a working webcam connected to your machine.
- The emotion detection model is trained on grayscale images. Therefore, the video frames are converted to grayscale before being passed to the model.
- The emotion detection model is not very accurate, so don't expect perfect results.
- The code is using the flask library for serving the web page and openCV for capturing the video stream.
