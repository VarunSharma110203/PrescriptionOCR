# Prescription OCR Extraction

This project extracts useful information from prescription PDFs using Optical Character Recognition (OCR). The system converts the PDF pages into images, preprocesses them, and uses Tesseract OCR to extract the text. It then parses the extracted text to capture important fields such as patient name, date, address, medications, directions, and refill information.

## Features
- Converts prescription PDFs into images using `pdf2image`.
- Preprocesses the images to improve OCR accuracy.
- Uses `pytesseract` to perform OCR and extract text from the images.
- Extracts and prints useful information from the text using regular expressions, such as:
  - Patient Name
  - Prescription Date
  - Address
  - Medications and Dosages
  - Directions
  - Refill Information

## Requirements
To run this project, you'll need to install the following dependencies:

### System Dependencies
- `poppler-utils` (for PDF to image conversion)

### Python Dependencies
- `pytesseract`
- `pdf2image`
- `opencv-python`
- `numpy`
- `matplotlib`
- `google-colab` (for file uploads in Google Colab)

You can install the Python dependencies using:

```bash
pip install pytesseract pdf2image opencv-python numpy matplotlib
Installation Steps
Install Poppler (Required for PDF to Image Conversion): If you're using Google Colab, Poppler is already installed. However, if you're working locally, you'll need to install it. On Linux, run the following command:

bash
Copy code
sudo apt-get install poppler-utils
Install Python Libraries: You can install the required libraries using pip:

bash
Copy code
pip install pytesseract pdf2image opencv-python numpy matplotlib
Upload PDF: The script supports PDF file uploads from your local machine (for Google Colab). You can upload your prescription PDF, and the script will process it.

Run the Script: Once everything is set up, run the script to process the prescription PDF, convert it to an image, preprocess the image, and extract text. The script will then print the extracted useful fields, such as the patient's name, address, medications, directions, and refill information.

How It Works
Step 1: Upload PDF
The script allows you to upload the prescription PDF file from your local machine (in the case of Google Colab).

Step 2: Convert PDF to Images
The uploaded PDF is converted into images, one for each page using the pdf2image library.

Step 3: Preprocess the Image
The image is then preprocessed using OpenCV to improve the OCR accuracy. This includes:

Converting the image to grayscale.
Resizing the image.
Applying adaptive thresholding to make the text more distinguishable.
Step 4: Extract Text Using Tesseract OCR
Tesseract OCR is used to extract the text from the preprocessed image.

Step 5: Extract Useful Information
Once the text is extracted, regular expressions are applied to find key information such as the patient's name, prescription date, medications, and refill details.

Example Output
For a prescription containing details such as:

vbnet
Copy code
Name: Maria Sharapova
Date: 5/11/2022
Address: 9 tennis court, new Russia, DC
Medications: Prednisone 20 mg, Lialda 2.4 gram
Directions: Prednisone, Taper 5 mg every 3 days, Finish in 2.5 weeks
Lialda - take 2 pill everyday for 1 month
Refill: 2 times
The script will extract and print:

vbnet
Copy code
Name: Maria Sharapova
Date: 5/11/2022
Address: 9 tennis court, new Russia, DC
Medications: [('Prednisone', '20 mg'), ('Lialda', '2.4 gram')]
Directions: Prednisone, Taper 5 mg every 3 days, Finish in 2.5 weeks
Lialda - take 2 pill everyday for 1 month
Refill: 2
Limitations
The OCR quality depends on the quality of the input image/PDF. Poor image quality or text-heavy images may result in inaccurate OCR.
The regular expression-based text extraction may not work well with every prescription format. You may need to adjust regex patterns based on the input format.
Contributing
Feel free to fork this repository, open issues, and submit pull requests. Contributions are always welcome!

License
This project is licensed under the MIT License - see the LICENSE file for details.

Acknowledgments
Tesseract OCR for the powerful OCR functionality.
pdf2image for converting PDFs to images.
OpenCV for image preprocessing.
