# Basic PDF Editor

This project is a simple desktop application built with **Python** and **Tkinter**. It lets users select a PDF file, convert all of its pages to grayscale, and automatically boost brightness and contrast.

---

## Screenshots

### Input (File Selection Screen)
![Input](input.png)

### Output (After Processing)
![Output](output.png)

---

## Features

- Simple, user-friendly interface
- Select a PDF file from the local machine
- Automatically convert PDF pages to grayscale
- Automatically increase brightness and contrast for readability
- Save the processed file as a new PDF

---

## Installation and Usage

### Requirements
- Python 3.8 or newer

### Steps

#### 1. Clone the repository
```bash
git clone https://github.com/mehmetaytugyuruk/Image-Processing-Projects.git
cd Image-Processing-Projects/Basic-PDF-Converter-Auto-Contrast-Auto-Brightness-GrayScale-Computer-Vision
```

#### 2. Install dependencies
```bash
pip install -r requirements.txt
```

#### 3. Run the application
```bash
python main.py
```

---

## Automatic EXE Build (GitHub Actions)

This project uses GitHub Actions to automatically build a Windows `.exe` on every push to the **main** branch.

### Downloading the .exe
1. Go to this repository's **Actions** tab.
2. Select the **"Build Windows EXE"** workflow from the left menu.
3. Click the latest successful run.
4. Download the **PDFEditor-Windows** artifact from the bottom of the page.

---

## License
This project is open source. See the `LICENSE` file for details.
