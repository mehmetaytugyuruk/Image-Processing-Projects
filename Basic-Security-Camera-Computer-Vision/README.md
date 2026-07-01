# Security Camera - Motion Detection System

A simple security camera application. Detects motion in the camera feed and automatically saves a screenshot.

## Features

- Real-time motion detection
- Automatic screenshot saving
- Terminal notification system
- Spam protection (checks every 2 seconds)

## Requirements

```bash
pip install opencv-python numpy
```

## Usage

1. Run the script:
```bash
python security_camera.py
```

2. Move in front of the camera once it opens.

3. Press **'q'** to quit.

## File Structure

```
project/
├── security_camera.py
└── screenshots/
    ├── motion_20240917_143052.jpg
    ├── motion_20240917_143125.jpg
    └── ...
```

## Settings

These values in the code can be adjusted as needed:

- `print_interval = 2.0` - notification frequency (seconds)
- `motion_detected = diff_norm > 50000` - motion sensitivity
- `motion_text_duration = 0.10` - how long the on-screen text stays visible

## How It Works

1. The first frame is stored as the background reference.
2. Each new frame is compared against the background.
3. If the difference exceeds the threshold, motion is detected.
4. A screenshot is saved automatically.

## Notes

- The camera opens from index 0 (default webcam).
- Screenshots are saved automatically to the `screenshots/` folder.
- Each screenshot is named with a unique timestamp.
