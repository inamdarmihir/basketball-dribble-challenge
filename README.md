# Basketball Dribble Detection

This repository contains a Python script for detecting basketball dribbles in a video. The script uses OpenCV for video processing and ball detection, and SciPy for peak detection in the y-coordinates of the ball.

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

The script is currently set up to detect a yellow ball against a white background. The HSV color space boundaries for the ball can be adjusted in the `detect_dribbles` function.

The `size` parameter in the `uniform_filter1d` function and the `distance` parameter in the `find_peaks` function can be adjusted to fine-tune the dribble detection.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
