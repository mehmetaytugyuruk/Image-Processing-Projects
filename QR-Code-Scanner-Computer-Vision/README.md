<div style="display: flex; gap: 20px;">
  <img src="input.png" alt="Input" width="300"/>
  <img src="output.png" alt="Output" width="300"/>
</div>

# QR Code Detection

This project uses OpenCV to detect and decode QR codes in an image.

## Requirements
- Python 3.x
- OpenCV (`pip install opencv-python`)

## Usage
1. Place an image file named `input.png` in the project folder.
2. Run the following script:
   ```bash
   python barcode_detector_on_image.py
   ```
3. The program draws a red box around the detected QR code and prints its decoded data to the terminal.

A live-camera version is also available:
```bash
python barcode_detector_on_video.py
```

## Output
- If a QR code is detected, a box is drawn around it and its data is printed.
- If no QR code is found, the terminal prints "QR code not found."
