# License_Plate_Detection_CV_Model


# Car License Plate Recognition Project

**Colab Notebook:** [Live Colab Demo](https://colab.research.google.com/drive/1PgHlHvY6DmYo857Oi4jqClB7kRFDBhB-)

---

## Overview
This repository contains a complete pipeline for Automatic License Plate Recognition (ALPR) using computer vision and OCR:

1. **Plate Detection** with YOLOv8s (fine-tuned on a custom car-plate dataset)  
2. **Text Recognition** using Microsoft’s Transformer-based TrOCR model  
3. **Batch & Live Inference** scripts for offline processing and real-time webcam demos
4. **Logging** of detected plates, timestamps, and fee calculation logic for student vs. outsider parking rates

Due to intermittent errors saving the Colab notebook directly to GitHub, please use the link above to access and run the full demo in Google Colab.

---

## Repository Structure
```
├── README.md                 # This file
├── plate_detection.ipynb     # Main Colab notebook (link above)
├── live_alpr.py              # Local webcam demo script for macOS
├── requirements.txt          # Python dependencies for local run
├── car_plate_dataset/        # YOLO dataset and config files
│   ├── images/               # Original plate images
│   ├── annotations/          # XML annotations
│   └── car_plate.yaml        # YOLOv8 data config
└── runs/                     # YOLOv8 training outputs (weights, plots)
```

---

## Setup (Local)
1. **Clone** this repo:
   ```bash
   git clone https://github.com/Lee-Minsoo-97/License_Plate_Detection_CV_Model.git
   cd License_Plate_Detection_CV_Model
   ```

2. **Create & activate** a virtual environment:
   ```bash
   python3 -m venv alpr-env
   source alpr-env/bin/activate
   ```

3. **Install dependencies**:
   ```bash
   pip install --upgrade pip
   pip install -r requirements.txt
   ```

4. **Download** your `best.pt` weights from the Colab demo and place it in the project root:
   ```bash
   mv ~/Downloads/best.pt .
   ```

---

## Usage (Local Webcam Demo)
```bash
python live_alpr.py
```
- Grants an OpenCV window showing your webcam feed.  
- Detected plates are boxed and annotated in real time.  
- Results are logged to `plate_log_webcam.csv` with timestamps and frame numbers.

---

## Batch Processing (Offline)
Use the Colab notebook or a similar script to process all images in `car_plate_dataset/images`:
```python
from scripts.batch_alpr import process_all_images
process_all_images('car_plate_dataset/images', 'plate_log.csv')
```

---

## Contributing
- Feel free to open issues or pull requests for improvements, bug fixes, or new features.  
- For major changes, please open a discussion first to align on design.

---

## License
This project is released under the MIT License. See [LICENSE](LICENSE) for details.

---

## Contact
Minsoo Lee — [leeminsoo6739@gmail.com](mailto:leeminsoo6739@gmail.com)   
Project Repo: https://github.com/Lee-Minsoo-97/License_Plate_Detection_CV_Model

