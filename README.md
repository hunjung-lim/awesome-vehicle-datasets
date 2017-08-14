# awesome-vehicle-datasets

## 2D

## 3D

### LiDAR

### RGBD

- [NYU Depth Dataset V2](http://cs.nyu.edu/~silberman/datasets/nyu_depth_v2.html)

---
[SYDNEY URBAN OBJECTS DATASET](http://www.acfr.usyd.edu.au/papers/SydneyUrbanObjectsDataset.shtml)

---
1. Build a testbed / Select datasets
	+ Datasets: Traffic scenes
		+ KITTI [[Link]](http://www.cvlibs.net/datasets/kitti/)
			+ Stereo, Lidar, GPS		
			+ Classes: Car, Pedestrian, Cyclist
			+ GT: Bounding box
		+ Cityscapes [[Link]](https://www.cityscapes-dataset.com/)
			+ Stereo, Timestamp		
			+ Groups: flat, human, vehicle, construction, object, nature, sky, void
			+ GT: Dense pixel-level annotations 
		+ Virtual KITTI [[Link]](http://www.xrce.xerox.com/Research-Development/Computer-Vision/Proxy-Virtual-Worlds)
			+ Mono (forward / 15-deg-right, 15-deg-left)
			+ Classes: Car, Pedestrian, Cyclist
			+ GT: Bounding box, Instance-level pixel annotations, Optical-flow, Depth	
			+ Weather conditions: morning, sunset, overcast, fog, rain
		+ Synthia [[Link]](http://synthia-dataset.net/)
			+ 8 RGB (form binocular 360 deg), 8 depth sensors
			+ Classes: misc, sky, building, road, sidewalk, fence, vegetation, pole, car, sign, pedestrian, cyclist, lanemarking
			+ GT: Instance-level pixel annotations
			+ Seasons: winter, fall, spring, summer
			+ Lightings: dynamic light, shadows, day-time, rain, night-time
---

# Open Data
* [옥스포드 Robot Car Dataset](http://robotcar-dataset.robots.ox.ac.uk/index.html)
* [Comma.ai driving dataset](https://github.com/commaai/research) : 자율 주행, 7.5 hours of camera images, steering angles, and other vehicle data.
* [Traffic Sign](http://www.vision.ee.ethz.ch/~timofter/traffic_signs/) : 신호등 데이터셋
* [BelgiumTS Dataset](http://btsd.ethz.ch/shareddata/index.html) : 도로 안내판 데이터셋
* [Udacity Driving Dataset](https://medium.com/udacity/open-sourcing-223gb-of-mountain-view-driving-data-f6b5593fbfa5#.1aq6pztwj) : Mountain View, 223G(10시간)
- [INI](http://benchmark.ini.rub.de/?section=gtsrb&subsection=dataset) : 독일 신호등 데이터셋
- [Udacity_Annotated Driving Dataset](https://github.com/udacity/self-driving-car/tree/master/annotations) : 도로상 차량, 트럭, 보행자 4.5GB
- [KITTI](http://www.cvlibs.net/datasets/kitti/): 동영상??
- [GTI](http://www.gti.ssr.upm.es/data/Vehicle_database.html): 차량 이미지 데이터셋
- [CMU Visual Localization Data Set](http://3dvis.ri.cmu.edu/data-sets/localization/): Dataset collected using the Navlab 11 equipped with IMU, GPS, Lidars and cameras.
- [NYU RGB-D Dataset](http://cs.nyu.edu/~silberman/datasets/): Indoor dataset captured with a Microsoft Kinect that provides semantic labels.
- [TUM RGB-D Dataset](http://cvpr.in.tum.de/data/datasets/rgbd-dataset): Indoor dataset captured with Microsoft Kinect and high-accuracy motion capturing.
- [New College Dataset](http://www.robots.ox.ac.uk/NewCollegeData/): 30 GB of data for 6 D.O.F. navigation and mapping (metric or topological) using vision and/or laser.
- [The Rawseeds Project](http://www.rawseeds.org/): Indoor and outdoor datasets with GPS, odometry, stereo, omnicam and laser measurements for visual, laser-based, omnidirectional, sonar and multi-sensor SLAM evaluation.
- [Victoria Park Sequence](http://www-personal.acfr.usyd.edu.au/nebot/victoria_park.htm): Widely used sequence for evaluating laser-based SLAM. Trees serve as landmarks, detection code is included.
- [Malaga Dataset 2009](http://www.mrpt.org/Paper:Malaga_Dataset_2009) and [Malaga Dataset 2013](http://www.mrpt.org/MalagaUrbanDataset): Dataset with GPS, Cameras and 3D laser information, recorded in the city of Malaga, Spain.
- [Ford Campus Vision and Lidar Dataset](http://robots.engin.umich.edu/SoftwareData/Ford): Dataset collected by a Ford F-250 pickup, equipped with IMU, Velodyne and Ladybug.

- [Build Your Own Real Time Traffic Data Feed]http://www.chioka.in/build-your-own-real-time-traffic-data-feed/): 교통카메라를 이용항 차량 이미지 획득 방법에 대하여

- [US 차량 궤적](https://www.fhwa.dot.gov/publications/research/operations/its/06135/index.cfm): NGSIM (Next Generation SIMulation이라 하여 미국 고속도로에 대해 비디오 분석 및 수작업을 통해 추적한 차량의 주행 궤적자료를 포함
