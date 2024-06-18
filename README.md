# Augmented Reality with Planar Homographies
This project implements an Augmented Reality (AR) application using planar homographies. The goal is to overlay frames from a source video onto a book in another video and create a new video with these overlays.

## Steps Involved:
### Getting Correspondences:
*   Utilize the SIFT descriptor from the OpenCV library to detect keypoints in both the book image (book.mov) and frames of the source video (ar_source.mov).
*   Employ the brute-force matcher from OpenCV to find correspondences between keypoints. Use K-nearest neighbors (KNN) and apply ratio checking between the best 2 matches to filter out good correspondences.

### Compute the Homography Parameters:
*   Implement a function to compute the 3x3 homography matrix H using the Direct Linear Transform (DLT) method and enhance it using Random Sample Consensus (RANSAC) to improve robustness against outliers.

### Calculate Book Coordinates:
*   Determine the coordinates of the four corners of the book in the video. This involves mapping the four corners of the book image (cover) to the frames of the book video using the previously computed homography matrix.

### Crop AR Video Frames:
*   Due to different aspect ratios between the book and the provided video (ar_source.mov), each frame of the source video is cropped to fit onto the book cover.

### Creating AR Application:
*   Overlay each cropped frame from the source video onto its corresponding frame in the book video to achieve the AR effect.
