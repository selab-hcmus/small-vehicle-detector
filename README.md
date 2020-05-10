# Small Vehicle Detector

## Requirements

- Python 2.7.+

- TensorFlow v1.+

- OpenCV 

## Install

1. Clone the repository
  ```Shell
  git clone https://github.com/HCMUS-Smart-Environment-Group/small-vehicle-detector
  ```

2. Update your -arch in setup script to match your GPU
  ```Shell
  cd tf-faster-rcnn/lib
  # Change the GPU architecture (-arch) if necessary
  vim setup.py
  ```

  | GPU model  | Architecture |
  | ------------- | ------------- |
  | TitanX (Maxwell/Pascal) | sm_52 |
  | GTX 960M | sm_50 |
  | GTX 1080 (Ti) | sm_61 |
  | Grid K520 (AWS g2.2xlarge) | sm_30 |
  | Tesla K80 (AWS p2.xlarge) | sm_37 |

  **Note**: You are welcome to contribute the settings on your end if you have made the code work properly on other GPUs. Also even if you are only using CPU tensorflow, GPU based code (for NMS) will be used by default, so please set **USE_GPU_NMS False** to get the correct output.


3. Build the Cython modules
  ```Shell
  make clean
  make
  cd ..
  ```

4. Install the [Python COCO API](https://github.com/pdollar/coco). The code requires the API to access COCO dataset.
  ```Shell
  cd data
  git clone https://github.com/pdollar/coco.git
  cd coco/PythonAPI
  make
  cd ../../..
  ```

## Download Pretrain Model

[Link](https://drive.google.com/drive/folders/1N2ovW8PU8xgQdKTH5LEC43OC3NHl1xf8?usp=sharing)

Request Access is required. Contact email smartenvironment@selab.hcmus.edu.vn

Create mall-vehicle-detector/output/res101 folder

After extracting file, copy those files to small-vehicle-detector/output/res101

## Demo

```
python tools/demo.py
```
## Citations
Please consider citing this project in your publications if it helps your research:

```
@Inproceedings{nktuan-AICity2019,
  Title          = {Vehicle Re-identification with Learned Representation and Spatial Verification and Abnormality Detection with Multi-Adaptive Vehicle Detectors for Traffic Video Analysis},
  Author         = {Khac-Tuan Nguyen and Trung-Hieu Hoang and Minh-Triet Tran and Trung-Nghia Le and Ngoc-Minh Bui and Trong-Le Do and Viet-Khoa Vo-Ho and Quoc-An Luong and Mai-Khiem Tran and Thanh-An Nguyen and Thanh-Dat Truong and Vinh-Tiep Nguyen and Minh N. Do},
  BookTitle      = {The IEEE Conference on Computer Vision and Pattern Recognition (CVPR) Workshops},
  Year           = {2019},
}
```

------------------
The code is used for academic purpose only.
