# Document Scanner - Perspective Correction Tool

## Example Output

| Input | Output |
|:---:|:---:|
| ![Input](image.jpg) | ![Output](scanned.jpg) |
| *Document photographed at an angle with a phone camera* | *Corrected, scanned-looking document* |

---

A Python application that automatically detects a document in a photo and warps it into a flat, top-down view.

## Features
- Automatic background removal (via rembg)
- Edge and contour detection
- Automatic detection of document corner points
- Perspective correction
- Clean, scanned-looking output

## Requirements
```bash
pip install opencv-python numpy matplotlib rembg
```

## Usage
1. Place a photo named `image.jpg` in the project folder.
2. Run the script:
```bash
python document_scanner.py
```
3. The result is saved as `scanned.jpg`.

## File Structure
```
project/
├── document_scanner.py
├── image.jpg           # input photo
├── scanned.jpg          # output (scanned document)
├── input_example.jpg    # example input
└── output_example.jpg   # example output
```

## How It Works
1. **Background removal**: `rembg` removes the background from the photo.
2. **Edge detection**: edges are found using the Canny algorithm.
3. **Contour analysis**: the largest rectangular contour is identified.
4. **Corner detection**: the document's four corner points are located.
5. **Perspective transform**: the document is warped into a flat view.

## Settings
These values can be adjusted as needed:
```python
edges = cv2.Canny(removed, 50, 150)        # edge detection sensitivity
epsilon = 0.02 * cv2.arcLength(hull, True) # corner detection sensitivity
```

## Notes
- Supported input formats: JPG, PNG
- Output is saved as JPG
- Best results require a document with all four corners clearly visible
- Complex backgrounds are removed automatically

## Example Use Case
Turns an angled phone-camera photo of a document into a flat, scanned-looking image. Well suited for receipts, ID cards, and certificates.
