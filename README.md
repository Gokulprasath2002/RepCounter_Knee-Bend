#STEPS:

1.Remove duplicate frames 
2.Configuring the Media Pipe
3.Estimating poses
4.Extracting joint coordinates
5.Calculating angles between joints
6.Inserting timer, stage (bent or relaxed), rep counter, and feedback

# 1. Remove duplicate frames
Using the ffmpeg open source software after playing with the parameters present in the mpdecimate module, successfully remove the duplicate frames and reduce the file size

# 2. Configuring the Media Pipe
Install and import Mediapipe, a Google-developed cross-platform library that offers fantastic, ready-to-use machine learning (ML) solutions for computer vision workloads.
Install and import certain more dependencies, such as OpenCV and NumPy, in addition to Mediapipe.

# 3. Estimating poses
We will calculate the total number of joints and body components in this stage.
Using the given video file, capture the video stream.
Recolor our image because it should be in RGB format when we provide it to mediapipe rather than BGR, which is the default when we read it.
To find the posture, use the Pose estimation model.
restore the image's original BGR colours.
Make detections, i.e., use the video feed to create landmarks (e.g., nose, eyes, ears, shoulders, elbows, wrists).

# 4. Extracting joint coordinates
As we did in the previous step, use the posture estimation model to extract landmarks using detected pose estimation.
To compute the number of reps for workouts that include knee bending, we must first extract the landmarks for the three primary joints—the hip, knee, and ankle.

# 5. Calculating angles between joints
To determine whether the leg is straight or bent, measure the angle at the hip, knee, and ankle.
Utilizing the hip, knee, and ankle as the three arguments supplied to the method calculate angle(), we will use a trigonometric function to calculate the radians before converting them to angles.

# 6.Inserting timer, stage (bent or relaxed), rep counter, and feedback
The stage of the leg will be bent if the estimated angle is less than or equal to 140°; otherwise, if the computed angle is more than 140° and the stage is bent, the stage will be relaxed.
The duration is computed by deducting the end time from the start time when the stage transitions from relaxed to bent. A timeholder is used to measure the start time when the stage transitions from relaxed to bent.
The user's rep count is increased if they can maintain the leg in the bent position for eight or more seconds.
Otherwise, the feedback will print "keep your knee bent" if the user is unable to remain in the bent state for more than 8 seconds.

# Note
In order to track the whole setup, python's logger module is imported and inserted to view the current flow of execution
