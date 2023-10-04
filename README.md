
<!-- PROJECT LOGO -->
<br />
<p align="center">
  <h1 align="center"> CloudPhysician Inter IIT</h1>

  <p align="center">
  </p>
</p>



<!-- TABLE OF CONTENTS -->
<details open="open">
  <summary>Table of Contents</summary>
  <ol>
     <li><a href="#about-the-project">About The Project</a>
     <li><a href="#contact">Contact</a></li>
     <li><a href="#acknowledgements">Acknowledgements</a></li>
  </ol>
</details>



<!-- ABOUT THE PROJECT -->
## About The Project

Patient monitoring is a crucial aspect of healthcare, as it allows healthcare professionals to closely track a patient's vital signs and detect any potential issues before they become serious.This project creates a <b>complete pipeline using computer vision</b> to extract important information from the ICU patient's monitor screen, such as <b>heart rate, blood pressure, and oxygen levels</b>. The pipeline takes input images of the monitors with a background and provides extracted vitals as output, along with a digitized graph of the heart rate.

### Getting Started 
To setup the environment to run this repo ensure the following steps.
- Python must be installed on you system. Run following commands to check the python availability in your system. 
```
python --version
pip --version
```
- Git should be installed in you system. Run the below command to ensure its availability.
  
```
git --version
```
- Clone the repository and install the dependencies from the requirements.txt file
```
git clone https://github.com/AryPratap/CloudPhysician_InterIIT.git
cd CloudPhysician_InterIIT
pip install -r requirements.txt
```
### Code structure
```
CloudPhysician_InterIIT
│   README.md
│   requirements.txt
│   pipeline.ipynb
└─── monitor extraction model
|     └─── F1_curve.png
|     └─── PR_curve.png
|     └─── P_curve.png
|     └─── R_curve.png
|     └─── confusion_matrix.png
|     └─── results.png
|     └─── test_image.jpeg
|     └─── README.md
└─── feature extraction model    
      └─── F1_curve.png
      └─── PR_curve.png
      └─── P_curve.png
      └─── R_curve.png
      └─── confusion_matrix.png
      └─── results.png
      └─── test_image.jpeg
      └─── README.md
      └─── feature_model_training.ipynb
```

### Data sources
#### Monitor segmentation dataset:
A dataset containing the segmentation boundaries  for the monitors in the image, a total of 2000 images.
#### Feature extraction dataset  
The monitors present in the images can be grouped into 4 
types, based on some screen characteristics. This dataset can consist of monitor images with bounding box labels for each of the particular features present in the monitor screen including, Heart Rate, SpO2, RR, Systolic Blood Pressure, Diabolic Blood Pressure, MAP and heart rate graph. 

### ML Pipeline 
The ML pipeline consist of two YOLOv7 models for monitor segmentation and feature extractions from the medical images. Further OCR and DBScan clustering step is applied for accurate text recognition from the predicted feature images. 
<br>
The complete pipeline in demonstrated in the below figure. 
![complete ML Pipeline](https://github.com/AryPratap/CloudPhysician_InterIIT/blob/main/icons/ML_pipeline.png)
<br>
The pipeline takes input images of the monitor with background as well and outputs the following extracted vitals from the image. <br> 
```
"HR", "SBP", "DBP", "MAP", "SPO2", "RR", "HR_W", "RR_W",  "SPO2_W"
```

### Monitor Detection Model
A pre-trained YOLOv7 was fine-tuned on the 2000 images of monitor segmentation dataset upto 40 epochs. <br>
#### Training details
Cloning the offical YOLOv7 repository and store the corresponding model weights file along with dataset into the respective folder as mentioned in the YOLOv7 repo instructions. 
```
git clone https://github.com/WongKinYiu/yolov7

python train.py --device 0 --batch-size 8 --epochs 50 --img 640 640 --data data/custom_data.yaml --hyp data/hyp.scratch.custom.yaml --cfg cfg/training/custom_yolov7.yaml --weights last.pt --name yolov7-custom
```
#### Model output
The model predicts the bounding boxes of the monitor screen from the original image and we get the final cropped monitor image to be passed on to the next stage of pipeline. 
<br>
<br>
![Monitor Detection](https://github.com/AryPratap/CloudPhysician_InterIIT/blob/main/icons/monitor_detection.png)

### Feature Extraction Model
This model recieves the cropped monitor image from the previous model, and its aim is to detect the bounding boxes of the individual vital features on the monitor as mentioned earlier. YOLOv7 model was trained on the feature extraction dataset of 1000 images, upto 50 epochs. 
<br> 
#### Training details
After cloning the YOLOv7 offical repo and setting up the model weights and dataset storage run the below command for training. 
```
python train.py --device 0 --batch-size 8 --epochs 50 --img 640 640 --data data/custom_data.yaml --hyp data/hyp.scratch.custom.yaml --cfg cfg/training/custom_yolov7.yaml --weights last.pt --name yolov7-custom
```
#### Model output
The model outputs the bounding boxes of the individual features present in the monitor image. Below image shows the predicted bounding boxes of the individual vitals present in the monitor screen.
<br>These are the corresponding vitals:- <b>"HR", "SBP", "DBP", "MAP", "SPO2", "RR", "HR_W", "RR_W",  "SPO2_W"</b>
<br> 
<br>
![feature](https://github.com/AryPratap/CloudPhysician_InterIIT/blob/main/icons/feature.png)
