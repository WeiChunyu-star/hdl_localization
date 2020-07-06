# hdl_localization
***hdl_localization*** is a ROS package for real-time 3D localization using a 3D LIDAR, such as velodyne HDL32e and VLP16. This package performs Unscented Kalman Filter-based pose estimation. It first estimates the sensor pose from IMU data implemented on the LIDAR, and then performs multi-threaded NDT scan matching between a globalmap point cloud and input point clouds to correct the estimated pose. IMU-based pose prediction is optional. If you disable it, the system predicts the sensor pose with the constant velocity model without IMU information.




## install hdl_localization
### Requirements
***hdl_localization*** requires the following libraries:
- OpenMP
- PCL 1.7

```bash
git clone https://github.com/koide3/ndt_omp.git
cd ~/catkin_ws
catkin_make
```

### Compile this repository
```bash
cd ~/catkin_ws
catkin_make
```



## Example

```bash
rosparam set use_sim_time true
roslaunch hdl_localization omtb_ndl.launch
```

```bash
roscd hdl_localization/rviz
rviz -d hdl_localization.rviz
```

```bash
roslaunch omtb_gazebo 1tb_room2.launch
```



## Parameters
All parameters are listed in *launch/hdl_localization.launch* as ros params.<br>
You can specify the initial sensor pose using "2D Pose Estimate" on rviz, or using ros params.

If it doesn't work well, change *ndt_neighbor_search_method* in *hdl_localization.launch* to "DIRECT1". It makes the scan matching significantly fast, but a little bit unstable.



## Contact
Kenji Koide, k.koide@aist.go.jp

Active Intelligent Systems Laboratory, Toyohashi University of Technology, Japan [\[URL\]](http://www.aisl.cs.tut.ac.jp)  
Robot Innovation Research Center, National Institute of Advanced Industrial Science and Technology, Japan  [\[URL\]](https://unit.aist.go.jp/rirc/en/team/smart_mobility.html)


