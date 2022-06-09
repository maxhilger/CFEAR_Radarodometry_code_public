



# CFEAR Radarodometry
This guide describes how to download data and estimate radar odometry using CFEAR_Radarodometry
![final odometry](odometry_oxford.jpg)
  
## Prerequisites
  * Google Ceres solver  http://ceres-solver.org/installation.html
  * ROS Melodic or later


Ask questions [here](https://github.com/dan11003/CFEAR_Radarodometry_code_public/issues).

## How to build with catkin

```
$ cd ~/catkin_ws/src/
$ git clone https://github.com/dan11003/CFEAR_Radarodometry_code_public.git
$ cd ~/catkin_ws
$ catkin_make -DCMAKE_BUILD_TYPE=Release 
$ source ~/catkin_ws/devel/setup.bash
```
## Downloading data (Oxford Radar Robotcar)
Currently, only rosbags that contain sensor_msgs/Image are supported.
We prepared a rosbag from the Oxford Radar Robotcar dataset on our [google drive](https://drive.google.com/drive/folders/12YNIvHQqSO5Et3UIzKD1z3XQACpoGZ1L?usp=sharing)
Download the Oxford bag file from (processed rosbag)/2019-01-10-12-32-52-radar-oxford-10k.bag to the folder created below:
```
mkdir -p /home/${USER}/Documents/oxford-eval-sequences/2019-01-10-12-32-52-radar-oxford-10k/
cd /home/${USER}/Documents/oxford-eval-sequences/2019-01-10-12-32-52-radar-oxford-10k/
```

## Running
The odometry an be launched in two modes.
* Offline: (used in this guide) runs at the maximum possible rate.
* Online: Standard rostopic interface. radar_driver_node and odometry_keyframes. The radar_driver_node subscribes to "/Navtech/Polar" 

```
roscd cfear_radarodometry/launch
./oxford_demo 
```
## Updates
Follow our updates [here](https://github.com/dan11003/CFEAR_Radarodometry).

This repository is based on the conference paper presented at [IROS 2021](https://ieeexplore.ieee.org/document/9636253). Journal is currently under review.
<details>
<summary>Bibtex</summary>
 
```
@INPROCEEDINGS{9636253,  author={Adolfsson, Daniel and Magnusson, Martin and Alhashimi, Anas and Lilienthal, Achim J. and Andreasson, Henrik},
booktitle={2021 IEEE/RSJ International Conference on Intelligent Robots and Systems (IROS)},
title={CFEAR Radarodometry - Conservative Filtering for Efficient and Accurate Radar Odometry},
year={2021},  volume={},  number={},  pages={5462-5469},
doi={10.1109/IROS51168.2021.9636253}}
  
```
</details>  


## Troubleshooting
```console
# Problem
user@computer:~$ terminate called after throwing an instance of 'rosbag::BagFormatException' what():  Required 'op' field missing
# Solution
rosbag reindex 2019-01-10-12-32-52-radar-oxford-10k.bag
```

