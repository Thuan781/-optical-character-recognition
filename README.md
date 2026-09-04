# Optical Character Recognition Using Image Processing

This project demonstrates how text can be extracted from images using **Tesseract OCR** and improved through basic image preprocessing techniques with **OpenCV**.

The notebook is designed to run in **Google Colab**. Instead of depending on an external image URL, the user uploads an image directly from their computer, making the workflow easier to reproduce and test with different images.

## Project Objectives

- Extract text from an uploaded image using Tesseract OCR.
- Clean unwanted symbols from the extracted text.
- Apply image preprocessing techniques to improve OCR readiness.
- Detect characters and selected words using bounding boxes.
- Demonstrate template matching and skew correction with OpenCV.

## Workflow

1. Install Tesseract OCR and Python dependencies.
2. Import the required Python libraries.
3. Upload an image directly to Google Colab.
4. Resize and save the image as `sample.png`.
5. Extract text using `pytesseract.image_to_string()`.
6. Remove unwanted symbols from the OCR output.
7. Load the image with OpenCV.
8. Apply grayscale conversion.
9. Remove image noise using median blur.
10. Apply Otsu thresholding.
11. Perform erosion.
12. Perform morphological opening.
13. Detect edges using the Canny algorithm.
14. Correct image skew.
15. Perform template matching.
16. Draw character-level bounding boxes.
17. Highlight a selected word or text pattern.

## Technologies Used

- Python
- Google Colab
- Tesseract OCR
- PyTesseract
- OpenCV
- Pillow (PIL)
- NumPy
- Regular Expressions (`re`)

## Repository Structure

```text
.
├── Optical_Character_Recognition_using_Image.ipynb
├── README.md
├── requirements.txt
└── .gitignore
```

## Running the Project

### Recommended: Google Colab

1. Open `Optical_Character_Recognition_using_Image.ipynb` in Google Colab.
2. Run the installation cells at the beginning of the notebook.
3. Run the image-upload cell.
4. Select an image containing readable text from your computer.
5. Continue running the remaining cells sequentially to view OCR and preprocessing results.

### Local Python Environment

Install Tesseract OCR on your operating system first.

On Ubuntu/Debian:

```bash
sudo apt update
sudo apt install tesseract-ocr libtesseract-dev
```

Install the Python dependencies:

```bash
pip install -r requirements.txt
```

Then open the notebook in Jupyter Notebook or JupyterLab.

> The notebook contains Google Colab-specific image upload code (`google.colab.files`). For local execution, replace that upload cell with a local image path.

## Main OCR Configuration

The notebook uses the following Tesseract configuration for initial text extraction:

```python
custom_config = r'-l eng --oem 3 --psm 6'
text = pytesseract.image_to_string(image, config=custom_config)
```

- `-l eng` selects English.
- `--oem 3` lets Tesseract choose the available OCR engine automatically.
- `--psm 6` treats the image as a single uniform block of text.

## Image Preprocessing

The project demonstrates several OpenCV preprocessing operations:

| Operation | Purpose |
| --- | --- |
| Grayscale conversion | Reduces color information and simplifies processing |
| Median blur | Helps remove image noise |
| Otsu thresholding | Separates foreground text from background |
| Erosion | Modifies foreground boundaries |
| Morphological opening | Helps remove small foreground artifacts |
| Canny edge detection | Detects strong edges |
| Deskewing | Attempts to align tilted text |
| Template matching | Compares a template with an image region |

## Text and Pattern Detection

PyTesseract is also used to obtain position information for detected text. The notebook demonstrates:

- character-level bounding boxes with `pytesseract.image_to_boxes()`
- word-level OCR data and confidence values with `pytesseract.image_to_data()`
- highlighting a selected word or pattern when OCR confidence is above a defined threshold

## Limitations

OCR performance depends strongly on image quality, font style, text size, lighting, background complexity, and orientation. The preprocessing methods in this notebook are demonstrations and may not improve every type of image equally.

## Future Improvements

Possible extensions include:

- automatic selection of the best preprocessing pipeline
- OCR confidence comparison before and after preprocessing
- support for multiple languages
- document layout detection
- handwritten text recognition
- exporting extracted text to PDF, CSV, or TXT
- a Streamlit or web-based interface

## Author

**Thuankubuan Kamei**

GitHub: [Thuan781](https://github.com/Thuan781)

## Acknowledgements

This project uses the open-source Tesseract OCR engine and OpenCV computer vision library for text extraction and image preprocessing.
