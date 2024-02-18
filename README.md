# Basketball Dribble Detection

This repository contains a Python script for detecting basketball dribbles in a video. The script uses OpenCV for video processing and ball detection, and SciPy for peak detection in the y-coordinates of the ball.

## How it Works

The script first downloads a video from a given URL using the `gdown` library. It then processes each frame of the video to detect the ball and its y-coordinates. The y-coordinate data is smoothed using the Savitzky-Golay filter from the `scipy.signal` library. Peaks in the smoothed y-coordinate list are found using the `find_peaks` function from the `scipy.signal` library. These peaks represent the dribbles. The total dribble count, average height of the dribbles, and average time between dribbles are then calculated and printed.

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
