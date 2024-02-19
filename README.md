# Basketball Dribble Detection

This repository contains a Python script for detecting basketball dribbles in a video. The script uses OpenCV for video processing and ball detection, and SciPy for peak detection in the y-coordinates of the ball.

## Implementation Details

The script is divided into several key steps:

1. **Video Download**: The script first downloads a video from a given URL using the `gdown` library. This library is specifically designed to download large files from Google Drive, which is where the video is hosted.

2. **Frame Processing**: The script then processes each frame of the video using OpenCV. This involves converting the frame to the HSV color space, which is more robust to changes in lighting conditions than the RGB color space. A mask is then applied to the frame to isolate the pixels that correspond to the color of the basketball. The centroid of these pixels is calculated to find the position of the ball.

3. **Ball Tracking**: The y-coordinate of the ball in each frame is tracked over time. This creates a list of y-coordinates that represents the motion of the ball.

4. **Data Smoothing**: The y-coordinate data is smoothed using the Savitzky-Golay filter from the `scipy.signal` library. This filter is used to remove noise from the data and make the peaks more distinct. The window size and polynomial order parameters of the filter can be adjusted to change the aggressiveness of the smoothing.

5. **Peak Detection**: Peaks in the smoothed y-coordinate list are found using the `find_peaks` function from the `scipy.signal` library. These peaks represent the dribbles. The distance parameter of the function can be adjusted to change the minimum distance between detected peaks.

6. **Dribble Analysis**: The total dribble count, average height of the dribbles, and average time between dribbles are then calculated and printed. The dribble count is simply the number of peaks. The average height is calculated by averaging the heights of the peaks, and the average time is calculated by averaging the distances between the peaks.

## Requirements

- Python 3.6 or later
- OpenCV
- SciPy
- NumPy
- gdown (for downloading the video from Google Drive)

## Usage

1. Clone this repository.
2. Install the required Python packages using pip:

    ```bash
    pip install opencv-python scipy numpy gdown
    ```

3. Run the script:

    ```bash
    python detect_dribbles.py
    ```

The script will download a video from Google Drive, process the video to detect the ball and its y-coordinates, and then use peak detection to count the number of dribbles. The total dribble count, average height of the dribbles, and average time between dribbles will be printed to the console.

## Customization

The script is currently set up to detect a yellow ball. The HSV color space boundaries for the ball can be adjusted in the `detect_dribbles` function to accommodate for different colors or lighting conditions.

The `window size` and `polynomial order` parameters in the `savgol_filter` function can be adjusted to change the aggressiveness of the smoothing applied to the y-coordinate data. A larger window size and polynomial order will result in more aggressive smoothing.

The `distance` parameter in the `find_peaks` function can be adjusted to change the minimum distance between detected peaks. A smaller distance will allow for closer peaks to be detected, potentially increasing the dribble count.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
