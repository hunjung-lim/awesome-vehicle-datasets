


[The KITTI Vision Benchmark Suite Download](http://www.cvlibs.net/datasets/kitti/raw_data.php)


Data Category : City | Residential | Road | Campus | Person | Calibration

Data include following information ( synchronized at 10 Hz)
- Raw (unsynced+unrectified) and processed (synced+rectified) grayscale stereo sequences (0.5 Megapixels, stored in png format)
- Raw (unsynced+unrectified) and processed (synced+rectified) color stereo sequences (0.5 Megapixels, stored in png format)
- 3D Velodyne point clouds (100k points per frame, stored as binary float matrix)
- 3D GPS/IMU data (location, speed, acceleration, meta information, stored as text file)
- Calibration (Camera, Camera-to-GPS/IMU, Camera-to-Velodyne, stored as text file)
- 3D object tracklet labels (cars, trucks, trams, pedestrians, cyclists, stored as xml file)

![](http://i.imgur.com/wHxw8m6.png)
- Title : 2011_09_26_drive_0001 (0.4 GB) 
- Length: 114 frames (00:11 minutes)
- Image resolution: 1392 x 512 pixels
- Labels: 12 Cars, 0 Vans, 0 Trucks, 0 Pedestrians, 0 Sitters, 2 Cyclists, 1 Trams, 0 Misc
- Downloads: [unsynced+unrectified data] [synced+rectified data] [calibration] [tracklets] 
  - unsynced+unrectified: refers to the raw input frames where images are distorted and the frame indices do not correspond, 
  - synced+rectified : refers to the processed data where images have been rectified and undistorted and where the data frame numbers correspond across all sensor streams. (일반적으로사용되는파일)




```
2011_09_26_drive_0035_sync
- image_00 (gray images)
  - data
    - 0000000000.png
    - 0000000130.png
  - timestamps.txt
- image_01 (gray images)
- image_02 (color images)
- image_03 (color images)
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


--- 
[pykitti](https://github.com/utiasSTARS/pykitti)
