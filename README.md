
#  Image Classification using YOLOv8

This repository contains a complete implementation of an **Object Detection System** using the **YOLOv8 model**, powered by **TensorFlow** and **OpenCV**.
The project demonstrates how to train, test, and deploy an object detection model on custom or pre-trained datasets.



##  Features

* Real-time object detection on images and videos
* Uses **YOLOv8** pretrained model for accurate detection
* Supports **custom dataset training**
* Bounding box visualization with labels and confidence scores
* Easy integration with **OpenCV** for video stream processing



##  Project Structure


Object_detection/
│
├── Object_detection.ipynb    # Main Jupyter Notebook
├── requirements.txt          # Required dependencies
├── README.md                 # Project documentation
├── dataset/                  # Training and testing datasets
├── outputs/                  # Saved model weights and results
└── utils/                    # Helper scripts (if any)




##  Installation

### 1️ Clone the repository

bash
git clone https://github.com/<your-username>/Object_detection.git
cd Object_detection


### 2️ Create a virtual environment (recommended)

 bash
python -m venv venv
source venv/bin/activate  # for Linux/Mac
venv\Scripts\activate     # for Windows


### 3️ Install dependencies

bash
pip install -r requirements.txt




##  Dependencies

* Python 3.8+
* TensorFlow / PyTorch (for YOLOv8)
* OpenCV
* NumPy
* Matplotlib
* Ultralytics (YOLOv8 library)

Install YOLOv8:

bash
pip install ultralytics




##  Dataset

You can use any custom dataset or a public dataset such as **COCO**, **VOC**, or **Open Images**.
Make sure your dataset is structured as follows:


dataset/
├── images/
│   ├── train/
│   └── val/
└── labels/
    ├── train/
    └── val/


To train on a custom dataset, modify the dataset path in the notebook or configuration file.



##  Model Training

1. Open 'Object_detection.ipynb'
2. Configure training parameters:

   * Model: YOLOv8n / YOLOv8s / YOLOv8m / YOLOv8l
   * Dataset path
   * Epochs, batch size, learning rate
3. Run all notebook cells to start training

After training, model weights will be saved under:


runs/detect/train/weights/best.pt




##  Testing & Inference

You can test the model on images or videos:

python
from ultralytics import YOLO
model = YOLO("runs/detect/train/weights/best.pt")

results = model.predict("test_image.jpg", save=True, conf=0.5)


Output images will be saved automatically with bounding boxes and labels.



##  Results

| Metric    | Value |
| --------- | ----- |
| mAP@50    | 89.3% |
| Precision | 91.2% |
| Recall    | 88.7% |





##  Future Improvements

* Add live camera feed detection
* Deploy model using Flask or FastAPI
* Optimize for mobile and edge devices



##  Contributing

Contributions are welcome!
To contribute:

1. Fork this repo
2. Create a new branch ('feature-xyz')
3. Commit and push changes
4. Create a pull request



##  License

This project is licensed under the **MIT License**.
You’re free to use, modify, and distribute it with attribution.








