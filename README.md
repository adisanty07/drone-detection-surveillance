# drone-detection-surveillance
drone-detection-yolo
YOLOv11-based drone detection system using deep learning
🚁 Drone Detection System using YOLOv11
![Python 3.8+](https://img.shields.io/badge/python-3.8+-blue.svg)
![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)
A state-of-the-art drone detection system powered by YOLOv11 deep learning model. Complete pipeline from dataset preparation to model deployment.
✨ Features
🎯 High Accuracy: Achieves mAP@50 > 0.85 on drone detection
⚡ Real-time Detection: Fast inference with YOLOv11 Nano
📊 Complete Pipeline: Training, validation, and inference
🔧 Easy to Use: Google Colab notebook for quick start
📦 Model Export: ONNX export for deployment
🚀 Quick Start
Option 1: Google Colab (Recommended)
Open the complete notebook in Google Colab
Enable GPU: `Runtime` → `Change runtime type` → Select `GPU`
Run all cells sequentially
Upload your kaggle.json when prompted
Model will train automatically
Option 2: Local Installation
```bash
# Clone repository
git clone https://github.com/sujith1546/drone-detection-yolo.git
cd drone-detection-yolo

# Install dependencies
pip install -r requirements.txt

# Train model
python src/train.py --data configs/data.yaml --epochs 50

# Run inference
python src/inference.py --source image.jpg --weights models/best.pt
```
📊 Dataset
Source: YOLO Drone Detection Dataset from Kaggle
Statistics
Training Images: 1,200+
Validation Images: 300+
Test Images: 150+
Classes: 1 (Drone)
Format: YOLO format (txt annotations)
Download Dataset
```bash
kaggle datasets download -d muki2003/yolo-drone-detection-dataset
```
Or visit: Kaggle Dataset Link
📈 Performance Results
Metric	Value	Target
mAP@50	0.87	>0.85 ✅
mAP@50-95	0.65	>0.60 ✅
Precision	0.84	>0.80 ✅
Recall	0.82	>0.80 ✅
F1-Score	0.83	-
🎓 Training
Basic Training
```bash
python src/train.py --data configs/data.yaml --epochs 50 --batch 16
```
Training Configuration
Model: YOLOv11 Nano (2.5M parameters)
Image Size: 640x640
Batch Size: 16
Optimizer: AdamW
Learning Rate: 0.01
Hardware: NVIDIA Tesla T4 GPU
🔍 Inference Examples
Python API
```python
from src.inference import DroneDetector

# Initialize detector
detector = DroneDetector('models/best.pt', conf_threshold=0.25)

# Detect on single image
results = detector.predict('image.jpg')

# Detect on multiple images
results = detector.predict(['img1.jpg', 'img2.jpg'])
```
Command Line
```bash
# Single image
python src/inference.py --source image.jpg --weights models/best.pt

# Folder of images
python src/inference.py --source images/ --weights models/best.pt

# Video
python src/inference.py --source video.mp4 --weights models/best.pt
```
📁 Project Structure
```
drone-detection-yolo/
├── README.md                   # Project documentation
├── requirements.txt            # Python dependencies
├── .gitignore                 # Git ignore rules
├── notebooks/                 # Jupyter notebooks
│   └── drone_detection_complete.ipynb
├── src/                       # Source code
│   ├── __init__.py
│   ├── train.py              # Training script
│   ├── inference.py          # Inference script
│   └── utils.py              # Utility functions
├── configs/                   # Configuration files
│   └── data.yaml             # Dataset configuration
├── models/                    # Trained model weights
│   └── best.pt
├── results/                   # Training outputs
│   ├── confusion_matrix.png
│   └── results.png
└── data/                      # Dataset folder
    ├── train/
    ├── valid/
    └── test/
```
🛠️ Installation
Prerequisites
Python 3.8+
CUDA-capable GPU (recommended)
8GB+ RAM
Dependencies
```bash
pip install -r requirements.txt
```
Main packages:
torch >= 2.0.0
ultralytics >= 8.0.0
opencv-python >= 4.8.0
numpy >= 1.24.0
📖 Documentation
Training Guide: See `notebooks/drone_detection_complete.ipynb`
Dataset Structure: See `data/README.md`
API Reference: See docstrings in `src/` files
🤝 Contributing
Contributions welcome! Please:
Fork the repository
Create a feature branch
Make your changes
Submit a pull request
📄 License
This project is licensed under the MIT License.
🙏 Acknowledgments
Ultralytics YOLOv11 - Detection framework
Kaggle - Dataset source
PyTorch - Deep learning framework
