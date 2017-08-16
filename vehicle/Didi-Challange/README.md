
## 1. 개요

[didi-competition](https://github.com/udacity/didi-competition)

## 2. Download link(torrent) 

[Dataset 1(32.80G](http://academictorrents.com/details/76352487923a31d47a6029ddebf40d9265e770b5)
NOT SUITABLE FOR TRACKLET GENERATION. 

Dataset intended for particpants to become familiar with the sensor data format and ROS in general. 

Tracklet code must be modified to work on this dataset, and no capture vehicle orientation is available unless using Course-Over-Ground techniques.


[Dataset 2(21.93G)](http://academictorrents.com/details/18d7f6be647eb6d581f5ff61819a11b9c21769c7)
Three different vehicles with a variety of maneuvers, and the Round 1 test seuence. 

Larger image sizes and two GPS RTK units on the capture vehicle for orientation determination. 

Velodyne points have been removed to reduce size, so a Velodyne LIDAR driver must be run during bag playback.

---
README.txt

Udacity is using a new dataset production method that allows for quick processing and release cycles. 

Instead of spending weeks (or months) waiting on 3D annotation data to be produced by third-party companies, we have elected to try out something new that enables datasets to be released immediately after they are recorded. 

While we do lose some sample distribution on each individual dataset due to the same obstacles being used for each session, the massive speedup in production and reduction in cost allows us to release new datasets daily (and with different obstacles with each session). 

In this manner, we can directly control the type of data being recorded so that we can cover all situations without hoping for them to happen on real roads, and we have extreme precision on obstacle location with differential RTK GPS technology.

Due to this new approach, there are some major differences from the Kitti datasets. 

It is important to note that recorded positions are recorded with respect to the base station, not the capture vehicle. 

The NED positions in the 'rtkfix' topic are therefore in relation to a FIXED POINT, NOT THE CAPTURE OR OBSTACLE VEHICLES. The relative positions can be calculated easily, as the NED frame is cartesian space, not polar. 

The single obstacle vehicle in this dataset is located in the 'obstacle/obs1/rear' topic namespace. Orientation of obstacles are not evaluated in Round 1, but will be evaluated in Round 2. The pose section of the ROS bags included in this release IS NOT A VALID QUATERNION, and does not represent either the pose of the capture vehicle or the obstacle. However, in this dataset, we have included an additional GPS antenna mounted on the rear of the capture vehicle to get a proper orientation. The tracklet generation code (link below) is currently being modified to translate the XML files into the porper vehicle frame with the capture vehicle orientation. Since this is open source code, we welcome your contributions and are looking forward to accepting Pull Requests.

Metadata about each obstacle (length, width, height, GPS antenna location as measured from the rear/left/ground) is included in each obstacle data directory. Tracklet file generation code, as well as sensor transforms/URDF files are available at this repository: https://github.com/udacity/didi-competition

This release requires running a ROS Velodyne driver for a HDL-32E to decode '/velodyne_packets' into '/velodyne_points'. The ROI for the captured camera imagery has also been enlarged at the community request to provide more data. Metadata for the obstacle has also been made available for Round 1.

Good luck!
