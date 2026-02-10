# docTR OCR – Installation & Usage Guide

docTR is a deep-learning based OCR (Optical Character Recognition) library by Mindee that supports printed text extraction from images and PDFs.

This guide explains how to install and run docTR on a **local system (Windows/Linux/Mac)**.

---

## Prerequisites

Make sure the following are installed:

- **Python 3.8 – 3.11** (recommended: 3.9 or 3.10)
- **pip** (comes with Python)
- **Virtual environment (recommended)**

Check versions:
```bash
python --version
pip --version
python -m venv doctr-env
doctr-env\Scripts\activate
```
linux
```bash
source doctr-env/bin/activate
```
```sh
pip install python-doctr[torch]
```

Basic OCR Example (PNG to Text)
```sh
from doctr.io import DocumentFile
from doctr.models import ocr_predictor

model = ocr_predictor(pretrained=True)

doc = DocumentFile.from_images(["sample.png"])
result = model(doc)

for page in result.pages:
    for block in page.blocks:
        for line in block.lines:
            print(" ".join([word.value for word in line.words]))
```
