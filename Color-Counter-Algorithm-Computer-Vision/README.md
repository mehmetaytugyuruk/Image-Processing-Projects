# M&M Color Counter

A computer vision project that uses OpenCV to count M&M candies in an image, grouped by color.

## Project Overview

Given an image containing several M&Ms, this project detects and counts how many candies of each color are present. It uses HSV color-space masking combined with an area-based counting heuristic to handle candies that are touching or overlapping.

## Input / Output

- `mm.jpg` - the main image containing the M&Ms to count
- `template.jpg` - a reference image of a single M&M, used for area calibration
- `result.jpg` - output image with detected candies outlined and counts annotated

![Input](mm.jpg) → ![Output](result.jpg)

## Method

### 1. HSV Color Space Conversion
```python
mm_hsv = cv2.cvtColor(mm, cv2.COLOR_BGR2HSV)
```
HSV is used instead of BGR because it is more robust to lighting variation and makes defining color ranges more intuitive.

### 2. Color Masking
HSV ranges were defined for each color:

| Color | Hue Range | Saturation | Value |
|-------|-----------|------------|-------|
| Blue | 100-130 | 120-255 | 50-255 |
| Red | 0-10, 160-179 | 100-255 | 100-255 |
| Orange | 10-25 | 100-255 | 100-255 |
| Yellow | 25-35 | 100-255 | 100-255 |
| Green | 35-85 | 80-255 | 80-255 |

Note: red wraps around both ends of the HSV hue axis (0deg and 360deg), so it requires two separate ranges.

### 3. Contour Detection and Filtering
```python
contours, _ = cv2.findContours(mask, cv2.RETR_EXTERNAL, cv2.CHAIN_APPROX_SIMPLE)
```
Only external contours are kept, and contours below a minimum area (10,000 px) are filtered out as noise.

### 4. Area-Based Counting

When M&Ms touch each other, they can be detected as a single merged contour. Morphological operations (erosion/dilation) did not reliably separate them, so a template-based area heuristic is used instead:

```python
# Area of a single M&M, computed from the template image
sum_template_area = single_mm_area

# Estimate count from contour area relative to the template
if area > sum_template_area * 0.8 and area < sum_template_area * 1.5:
    count += 1
elif area > sum_template_area * 1.5 and area < sum_template_area * 2.5:
    count += 2
# ... up to 5 merged M&Ms
```

This tolerates roughly 20% variation in area and correctly counts merged groups of up to 5 candies.

## Requirements

```bash
pip install opencv-python numpy
```

## Usage

File structure:
```
project/
├── mm_counter.py
├── mm.jpg          # main image
├── template.jpg    # reference image
└── README.md
```

Run:
```bash
python mm_counter.py
```

Output:
- Per-color counts printed to the console (e.g. `Blue objects: 3`)
- Contours drawn on the image
- Counts annotated in the corner of the result image

## Limitations

- Cannot reliably count more than 5 merged/touching objects
- Not suited for objects with very different sizes
- Heavy shadowing can affect detection
- The template image must be at roughly the same scale as the main image

## Possible Extensions

- Watershed segmentation to separate touching objects
- Adaptive thresholding for varying lighting conditions
- Replacing the heuristic with a learned object detector (e.g. YOLO) for more robust counting

## License

MIT License
