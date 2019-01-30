
- [[Paper_2012] Are we ready for Autonomous Driving? The KITTI Vision Benchmark Suite](https://github.com/hunjung-lim/awesome-vehicle-datasets/blob/master/vehicle/kitti/paper-2012.md)




# KITTI Dataset

[The KITTI Vision Benchmark Suite Download](http://www.cvlibs.net/datasets/kitti/raw_data.php)
+ Stereo, Lidar, GPS		
+ Classes: Car, Pedestrian, Cyclist
+ GT: Bounding box

- [검증코드] kitti-object-eval-python : [깃허브](https://github.com/traveller59/kitti-object-eval-python)

용도 : Benchmarks for stereo, optical flow, object detection

|Recording platform|Sensor Setup|
|-|-|
|![](http://i.imgur.com/AhM5oqn.png)|![](http://i.imgur.com/EQAemV3.png)|


센서 :  
- 흑백 카메라 : 2 × PointGray Flea2 grayscale cameras (FL2-14S3M-C), 1.4 Megapixels, 1/2” Sony ICX267 CCD, global shutter

- 칼라 카메라 : 2 × PointGray Flea2 color cameras (FL2-14S3C-C), 1.4 Megapixels, 1/2” Sony ICX267 CCD, global shutter

- 4 × Edmund Optics lenses, 4mm, opening angle ∼ 90◦, vertical opening angle of region of interest (ROI) ∼ 35◦

- Lidar : 1 × Velodyne HDL-64E rotating 3D laser scanner, 10 Hz,64 beams, 0.09 degree angular resolution, 2 cm distance
accuracy, collecting ∼ 1.3 million points/second, field of view: 360◦ horizontal, 26.8◦ vertical, range: 120 m

-  GPS : 1 × OXTS RT3003 inertial and GPS navigation system,6 axis, 100 Hz, L1/L2 RTK, resolution: 0.02m / 0.1◦

> 두개의 카메라를 사용하는 이유 : Note that the color cameras lack in terms of resolution due
to the Bayer pattern interpolation process and are less sensitive to light. This is the reason why we use two stereo camera rigs, one for grayscale and one for color. 

대상 : traffic scenarios 

수집 지역 : Karlsruhe, Germany



|![](http://i.imgur.com/JGJmlBl.png)|<iframe width="560" height="315" src="https://www.youtube.com/embed/KXpZ6B1YB_k" frameborder="0" allowfullscreen></iframe>|
|-|-|

---
## 1. [Evaluation: object- 3D object](http://www.cvlibs.net/datasets/kitti/eval_object.php?obj_benchmark=3d)

### 1.1 데이터 분류 

The 3D object detection benchmark consists of 
- 7481 training images + pointcloud  
- 7518 test images + pointcloud 
- total of 80.256 labeled objects. 

### 1.2 [Label format ](https://github.com/NVIDIA/DIGITS/blob/v4.0.0-rc.3/digits/extensions/data/objectDetection/README.md)

`Pedestrian 0.00 0 -0.20 712.40 143.00 810.73 307.92 1.89 0.48 1.20 1.84 1.47 8.41 0.01`
- 1 type Describes the type of object
	- 'Car', 'Van', 'Truck','Pedestrian', 'Person_sitting', 'Cyclist', 'Tram','Misc' or 'DontCare'
- 1 truncated Float from 0 (non-truncated) to 1 (truncated), where truncated refers to the object leaving image boundaries
- 1 occluded Integer (0,1,2,3) indicating occlusion state:
	- 0 = fully visible, 1 = partly occluded
	- 2 = largely occluded, 3 = unknown
- 1 alpha Observation angle of object, ranging [-pi..pi]
- 4 bbox 2D bounding box of object in the image (0-based index):
	- contains left, top, right, bottom pixel coordinates
- 3 dimensions 3D object dimensions: height, width, length (in meters)
- 3 location 3D object location x,y,z in camera coordinates (in meters)
- 1 rotation_y Rotation ry around Y-axis in camera coordinates [-pi..pi]
- 1 score Only for results: Float, indicating confidence in detection, needed for p/r curves, higher is better.

> [KITTI](https://github.com/bostondiditeam/kitti/blob/master/resources/devkit_object/readme.txt), [QnA](https://github.com/NVIDIA/DIGITS/issues/992)

### 1.9 Download 
- Velodyne point clouds (29 GB): input data to VoxelNet
	- https://s3.eu-central-1.amazonaws.com/avg-kitti/data_object_velodyne.zip
- Training labels of object data set (5 MB): input label to VoxelNet
	- https://s3.eu-central-1.amazonaws.com/avg-kitti/data_object_label_2.zip
- Camera calibration matrices of object data set (16 MB): for visualization of predictions
	- https://s3.eu-central-1.amazonaws.com/avg-kitti/data_object_calib.zip
- Left color images of object data set (12 GB): for visualization of predictions
	- https://s3.eu-central-1.amazonaws.com/avg-kitti/data_object_image_2.zip

---

## 2. Evaluation : object- 2D object
---

## 3. Evaluation : Tracking

---


## 9. [RAW 데이터](http://www.cvlibs.net/datasets/kitti/raw_data.php)

- [KITTI+Dataset+Exploration.ipynb](https://github.com/hunjung-lim/awesome-vehicle-datasets/blob/master/vehicle/kitti/KITTI%2BDataset%2BExploration.ipynb)
- [KITTI+Dataset+Visualizing.ipynb](https://github.com/hunjung-lim/awesome-vehicle-datasets/blob/master/vehicle/kitti/KITTI%2BDataset%2BVisualizing.ipynb)

### 9.1 데이터 분류 

- City | Residential | Road | Campus | Person | Calibration

### 9.2 데이터 내용 ( synchronized at 10 Hz)

- 칼러/흑백 이미지 (`png` file, 0.5 Megapixels, 1382x512)
  - 'image_00': left rectified grayscale image sequence
  - 'image_01': right rectified grayscale image sequence
  - 'image_02': left rectified color image sequence
  - 'image_03': right rectified color image sequence

- 3D 포인트 클라우드 (`binary float matrix` format, 100k points per frame, Nx4 float matrix )
	- 4*num values: x, y, z, reflectance information
	- x,y and y are stored in metric (m) Velodyne coordinates.
	- `raw_lidar = np.fromfile('000000.bin, dtype=np.float32).reshape((-1, 4))`
	
- 3D GPS/IMU data (`text` file, 위치, 속도, 가속, 메타 정보 )

- Calibration (`text` file , Camera, Camera-to-GPS/IMU, Camera-to-Velodyne)

- 3D object tracklet 라벨 (`xml` file)
  - 'Car'
  - 'Van'
  - 'Truck'
  - 'Pedestrian'
  - 'Person (sitting)'
  - 'Cyclist'
  - 'Tram'
  - 'Misc'

> [KITTI_README.TXT](https://github.com/yanii/kitti-pcl/blob/master/KITTI_README.TXT)

![](http://i.imgur.com/wHxw8m6.png)
- Title : 2011_09_26_drive_0001 (0.4 GB) 
- Length: 114 frames (00:11 minutes)
- Image resolution: 1392 x 512 pixels
- Labels: 12 Cars, 0 Vans, 0 Trucks, 0 Pedestrians, 0 Sitters, 2 Cyclists, 1 Trams, 0 Misc
- Downloads: [unsynced+unrectified data] [synced+rectified data] [calibration] [tracklets] 
  - unsynced+unrectified(Raw 데이터): refers to the raw input frames where images are distorted and the frame indices do not correspond, 
  - synced+rectified(전처리된 데이터) : refers to the processed data where images have been rectified and undistorted and where the data frame numbers correspond across all sensor streams. (일반적으로사용되는파일)



```
2011_09_26_drive_0035_sync
- image_00 
  - data
    - 0000000000.png
    - 0000000130.png
  - timestamps.txt
- image_01 
- image_02 
- image_03 
- oxts
  - data
    - 0000000000.txt
    - 0000000130.txt
  - dataformat.txt
  - timestamps.txt
- velodyne_points
  - data
    - 0000000000.bin
    - 0000000130.bin
  - timestamps.txt
  - timestamps_end.txt
  - timestamps_start.txt
```

![](http://i.imgur.com/YS9mcMa.png)


## 관련 툴 

- QT 기반 시각화 툴 : [QtKittiVisualizer](https://github.com/MarkMuth/QtKittiVisualizer)

- Python 기반 parser for reading the object label XML files : [parseTrackletXML.py](http://www.cvlibs.net/datasets/kitti/downloads/parseTrackletXML.py)

- some python tools for loading and parsing the KITTI raw and odometry datasets : [pykitti](https://github.com/utiasSTARS/pykitti)

- ROS bag 변환 툴  : [kitti2bag](https://github.com/tomas789/kitti2bag), [kitti_to_rosbag](https://github.com/ethz-asl/kitti_to_rosbag)

--- 

- Andreas Geiger, "[Vision meets Robotics: The KITTI Dataset](http://www.cvlibs.net/publications/Geiger2013IJRR.pdf)", IJRR 2013, 현 데이터와 다른 부분이 있음(Update 반영 안됨)

- [Visualizing lidar data](https://navoshta.com/kitti-lidar/) : Alex Staravoitau, [Github](https://github.com/navoshta)

- [KITTI Dataset Exploration](https://github.com/navoshta/KITTI-Dataset/blob/master/README.md)

- [scripts to create KITTI Tracklet files from rosbag capture data and evaluate Tracklet files](https://github.com/udacity/didi-competition/tree/master/tracklets)



