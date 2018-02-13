# extract-facepoints-dataset
Script that captures frames from the computer's webcam, tries to detect a face in the frame and then saves the normalized distance between the center of the face detected and 60 facepoints in a Dataframe that can be saved as a dataset.

---
### Requirements

- pandas
- OpenCV
- Dlib
- NumPy

---
# How it works?

When the program starts, it will start to capture frames from the webcam, and it will try to detect a face in the frame. The method used for face detection returns 68 landmarks points, covering parts of a face, like eyes, mouth, chin etc. Using the position of 60 of the 68 landmarks detected, the program calculates the distance of each landmark point to the center of the rectangle that covers all facial landmarks.

Then, the program normalizes the distance, so the distances of all 60 facial landmarks have values going from 0 to 1 and adds the data captured as a row in a pandas Dataframe that can be saved as a csv file for later use (like applying a Machine Learning model to detect face position).

The DataFrame have a very simple format, the header is one of the 60 face landmarks (going from 0 to 59), and each row is the data extracted of a frame that detected a face:

| 0    | 1    | 2    | ...       | 58   | 59   |
|------|------|------|-----------|------|------|
| 0.87 | 0.92 | 0.88 |    ...    | 0.28 | 0.32 |
| 1.0  | 0.96 | 0.99 |    ...    | 0.34 | 0.40 |