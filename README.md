# Checkbox Detection and Classification

This Python script detects and classifies checkboxes in a given image. It identifies checkboxes in forms or documents and determines if they are ticked or unticked. The script uses OpenCV for image processing and `numpy` for numerical operations. The results are displayed visually and printed in a readable format.

It also contains the jupyter notebook for executing the files in a folder and plot the results using matplotlib

## Requirements

- Python 3.x
- OpenCV (`cv2`)
- NumPy (`numpy`)
- Matplotlib (`matplotlib`)

## Installation

To install the required libraries, you can use pip:

```sh
pip install opencv-python-headless numpy matplotlib
```

## Usage

Run the script from the command line, providing the path to the image file as an argument:

```sh
python script.py path/to/your/image.png
```

## Description

### Functions

1. **detect_checkboxes(image, line_min_width=15, line_max_width=15)**
   - Converts the image to grayscale.
   - Binarizes the image to highlight potential checkboxes.
   - Uses morphological operations to detect horizontal and vertical lines.
   - Combines the results to identify checkbox-like structures.
   - Finds connected components in the processed image.
   - Returns the statistics and labels of the detected components.

2. **classify_checkboxes(image, stats, min_width=10, max_width=50, tick_threshold=0.1)**
   - Filters components based on size and aspect ratio to identify checkboxes.
   - Extracts the region of interest (ROI) for each checkbox.
   - Preprocesses the ROI by converting to grayscale, applying Gaussian blur, and binarizing.
   - Counts non-white pixels in the binarized ROI to determine if the checkbox is ticked.
   - Classifies and labels the checkbox as 'Ticked' or 'Unticked'.
   - Draws rectangles and labels on the image for visualization.
   - Returns a list of classified checkboxes.

3. **process_image(image_path)**
   - Reads the image from the provided path.
   - Calls `detect_checkboxes` and `classify_checkboxes` to process the image.
   - Displays the processed image using Matplotlib.
   - Returns the list of classified checkboxes.

### Command-Line Interface

The script uses the `sys` module to handle command-line arguments. The image path is provided as an argument, and the script processes the image and prints the results.

### Example Output

When you run the script, it will display the processed image and print the results in the following format:

```
path/to/your/image.png: [(694, 109, 10, 12, 'Unticked'), (146, 813, 25, 26, 'Ticked'), ...]
(694, 109, 10, 12, 'Unticked')
(146, 813, 25, 26, 'Ticked')
...
```

Each tuple in the list represents a detected checkbox with its coordinates, dimensions, and classification ('Ticked' or 'Unticked').

## Example

To process an image named `test_image1.jpg`:

```sh
python script.py test_image1.jpg
```

The script will output:

```
test_image1.jpg: [(694, 109, 10, 12, 'Unticked'), (146, 813, 25, 26, 'Ticked'), (352, 813, 25, 25, 'Ticked'), (615, 813, 25, 25, 'Ticked'), (905, 813, 25, 25, 'Ticked'), (1249, 813, 25, 25, 'Ticked')]
(694, 109, 10, 12, 'Unticked')
(146, 813, 25, 26, 'Ticked')
(352, 813, 25, 25, 'Ticked')
(615, 813, 25, 25, 'Ticked')
(905, 813, 25, 25, 'Ticked')
(1249, 813, 25, 25, 'Ticked')
```

And display the image with highlighted checkboxes.

---


## Credits

Special thanks to:

This project was inspired by the work of [Sreekiranar](https://github.com/Sreekiranar/box_detection_opencv).

