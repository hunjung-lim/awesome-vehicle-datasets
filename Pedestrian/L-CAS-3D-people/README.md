![](https://i1.wp.com/lcas.lincoln.ac.uk/wp/wp-content/uploads/2016/09/rviz_screenshot.png)

# 1.1 L-CAS 3D Point Cloud People Dataset

- [Lincoln Centre for Autonomous Systems](https://lcas.lincoln.ac.uk/wp/research/data-sets-software/l-cas-3d-point-cloud-people-dataset/)
- 센서 : Velodyne VLP-16
- 수집 데이터 : 영국 링컨 대학교에서 49분간, 28,002 Velodyne scan frames, [[다운로드]](https://lcas.lincoln.ac.uk/owncloud/index.php/s/wu2NILXZ7mzjovS),

- 제공 데이터
- Robot Operating System (ROS) rosbag files recording ground truth from the 3D LiDAR, robot odometry, ROS transform tree, as well as a panoramic camera.
- Point Cloud Data (PCD) files corresponding to each scan frame, which is the official file format supported by the Point Cloud Library (PCL).
- Annotation files in text format, including single-person (pedestrian) labels and human-group (group) labels.
- A Qt-based GUI tool for data annotation, providing a semi-automatic labelling function, released as open-source.

#### A. label data

```python
pedestrian 16.8915 0.282575 0.0424143 16.7578 0.0922886 -0.296726 17.0572 0.498739 0.297738 0
pedestrian 6.55263 0.582247 0.132658 6.34313 0.284879 -0.561632 6.95758 0.850341 0.822374 0
pedestrian 7.62397 -0.641525 0.162471 7.3658 -0.872086 -0.67842 7.73205 -0.440035 0.662384 0
pedestrian 13.5868 1.9875 0.214493 13.4329 1.83353 -0.241367 13.8208 2.21375 0.724958 0
pedestrian -3.31128 -3.02812 -0.0352137 -3.61874 -3.23663 -0.392724 -3.1304 -2.77111 0.408237 0
pedestrian 1.13967 -8.59664 0.111699 0.982876 -8.71929 -0.444542 1.29828 -8.34763 0.455323 0
pedestrian 12.6652 2.21514 0.47063 12.508 2.12521 0.22175 12.7653 2.35142 0.679425 0
pedestrian 14.9873 0.837819 -0.262016 14.8933 0.72961 -0.264125 15.1031 0.947489 -0.26032 0
"""
Column 1:	category (pedestrian or group)
Column 2-4:	centroid (x-y-z)
Column 5-7:	minimum bounds (x-y-z)
Column 8-10:	maximum bounds (x-y-z)
Column 11:	visibility (0 = visible, 1 = partially visible)
"""
```

#### B. LCAS rosbag에서 velodyne_points 토픽 추출

```bash
1. $rosbag play -l LCAS_20160523_1200_1218.bag
2. $rosrun nodelet nodelet standalone velodyne_pointcloud/CloudNodelet
3. $watch 'rostopic list' 로 /velodyne_points 추가됨을 확인
4. $rosrun rosbag record -O Lcas_pointcloud.bag /velodyne_points 로 [Lcas_pointcloud.bag]파일 생성
```



---

> [Annotation tool](https://github.com/lcas/cloud_annotation_tool) 제공

#
## 1.1 L-CAS Annotation tool

- [깃허브](https://github.com/lcas/cloud_annotation_tool)
- 개발 환경 : VTK5, Qt4, and PCL1.7 under Ubuntu 14.04.
- qt4 docker : `docker pull msoares/qt4-dev`

- Prerequisites
```
sudo apt-get install libqt4-dev qt4-qmake
sudo apt-get install libvtk5-dev python-vtk
sudo apt-get install libpcl-1.7-all-dev # add-apt-repository ppa:v-launchpad-jochen-sprickerhof-de/pcl
```

- Build script
```
git clone https://github.com/LCAS/cloud_annotation_tool.git
cd cloud_annotation_tools
mkdir build
cd build
cmake .. # apt-get install cmake
make
```

에러 #1 : libGL error: failed to load driver: swrast -> [nvidia 드라이버 재설치](https://github.com/adioshun/System_Setup/wiki/4_CUDA_CuDNN-Setup#%EC%B0%B8%EA%B3%A0-%EB%93%9C%EB%9D%BC%EC%9D%B4%EB%B2%84-%EC%84%A4%EC%B9%98)

에러 #2 : Xlib: extension "NV-GLX" missing on display "localhost:10.0".-> remove the nouveau module `sudo apt-get --purge remove xserver-xorg-video-nouveau`

