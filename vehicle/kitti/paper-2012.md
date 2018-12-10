|
논문명 |Are we ready for Autonomous Driving? The KITTI Vision Benchmark Suite |
| --- | --- |
| 저자\(소속\) | Andreas Geiger\(\) |
| 학회/년도 | CVPR2012, [논문](http://www.cvlibs.net/publications/Geiger2012CVPR.pdf) |
| 키워드 | |
| 데이터셋(센서)/모델 | |
| 관련연구||
| 참고 |[홈페이지](http://www.cvlibs.net/datasets/kitti/) |
| 코드 |[Download stereo 2015/flow 2015/scene flow 2015 data set (2 GB)](http://kitti.is.tue.mpg.de/kitti/data_scene_flow.zip) |


# The KITTI Vision Benchmark Suite

- stereo
- optical flow
- visual odometry / SLAM
- 3D object detection



## 1. Introduction

- 기존 benchmarks
- Caltech-101[17],
- Middlebury for stereo [41]
- optical flow [2]

![](https://i.imgur.com/AdIrsHK.png)
```
기존 데이터셋 vs KITTI데이터셋
```

## 2. Challenges and Methodology

- 2.1 실시간으로 데이터 수집 `collection of large amounts of data in real time`
- 2.2 칼리브레이션 `the calibration of diverse sensors working at different rates,`
- 2.3 GT 생성 `the generation of ground truth minimizing the amount of supervision required`
- 2.4 the selection of the appropriate sequences and frames for each benchmark
- 2.5 the development of metrics for each task.

### 2.1. Sensors and Data Acquisition

### 2.2. Sensor Calibration

### 2.3. Ground Truth

#### A. stereo and optical flow
- Given the **camera calibration**, the corresponding **disparity maps** are readily computed
- **Optical flow fields** are obtained by projecting the **3D points into the next frame**

#### B. visual odometry/SLAM

- The ground truth for visual odometry/SLAM is directly given by the output of the GPS/IMU localization unit projected into the coordinate system

#### C. 3D object

- 사람이 직접 진행
-
### 2.4. Benchmark Selection

### 2.5. Evaluation Metrics


#### A. stereo and optical flow
- we evaluate **stereo** and **optical flow** using the average number of **erroneous pixels** in terms of disparity and end-point error.
#### B. visual odometry/SLAM

#### C. 3D object

- 3단계로 구분 되어 있다. `Our 3D object detection and orientation estimation benchmark is split into three parts: `

##### 가. average precision (AP)
- First, we evaluate classical 2D object detection by measuring performance
- using the well established **average precision (AP)** metric as described in [16].

- Detections are iteratively assigned to ground truth labels starting with the largest overlap, measured by bounding box intersection over union.

- We require true positives to overlap by more than 50% and count multiple detections of the same object as false positives.

- We assess the performance of jointly detecting objects and estimating their 3D orientation using a novel measure which we called the **average orientation similarity (AOS)**

##### 다.

- Finally, we also evaluate pure classification (16 bins for cars) and regression (continuous orientation) performance on the task of 3D object orientation estimation in terms of orientation similarity.

## 3. Experimental Evaluation

### 3.1. Stereo Matching
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTY4OTAyNDcyN119
-->
