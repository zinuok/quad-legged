***
# Quad-Leggs Simulation setting

***
<br>

# Index
### 1. Prerequisites
####    &nbsp;&nbsp;&nbsp;&nbsp;● LCM
####    &nbsp;&nbsp;&nbsp;&nbsp;● Boost
####    &nbsp;&nbsp;&nbsp;&nbsp;● CMake
####    &nbsp;&nbsp;&nbsp;&nbsp;● unitree_legged_sdk
####    &nbsp;&nbsp;&nbsp;&nbsp;● aliengo_sdk
### 2. Install
### 3. Models
####    &nbsp;&nbsp;&nbsp;&nbsp;● I used [robot_name]
### 4. Run
####    &nbsp;&nbsp;&nbsp;&nbsp;● Uploaded folders for following setup: D435i, pixhawk4 mini 
####    &nbsp;&nbsp;&nbsp;&nbsp;● for using your own sensor setup, you have to get a calibration data using [kalibr](https://github.com/zinuok/kalibr)
<br><br>

## 1. Prerequisites
### ● LCM (>= 1.4.0)
```
$ git clone https://github.com/lcm-proj/lcm.git 
$ mkdir build && cd build
$ cmake.. && make
$ sudo make install
```
### ● Boost (>= 1.5.4)
you already had satisfied this through installing ROS

### ● CMake (>= 2.8.3)
you already had satisfied this through installing ROS

### ● unitree_legged_sdk
+ LCM, Boost, CMake must be installed before installing this
```
$ git clone https://github.com/unitreerobotics/unitree_legged_sdk.git
$ cd unitree_legged_sdk && mkdir build && cd build
$ cmake ../ && make
```

### ● aliengo_sdk
+ LCM, Boost, CMake must be installed before installing this
```
$ git clone https://github.com/unitreerobotics/aliengo_sdk.git
$ cd aliengo_sdk && mkdir build && cd build
$ cmake ../ && make
```
<br><br>

## 2. Install
+ installing champ (controller for quad-legs robot)
```
$ cd ~/catkin_ws/src
$ git clone https://github.com/chvmp/champ.git
$ cd ../ && catkin build -DCMAKE_BUILDTYPE=Release -j8
$ source ~/catkin_ws/devel/setup.bash
```

+ installing robots (various robot models)
```
$ cd ~/catkin_ws/src
$ git clone https://github.com/chvmp/robots.git
$ cd ../ && catkin build -DCMAKE_BUILDTYPE=Release -j8
$ source ~/catkin_ws/devel/setup.bash
```


## 3. Models
#### ● Actually, no installation difference among TX2, Xavier, and NX
<br><br>

## 4. Run
#### ● Uploaded folders for following setup: D435i, pixhawk4 mini 
#### ● for using your own sensor setup, you have to get a calibration data using [kalibr](https://github.com/zinuok/kalibr)
```
$ roslaunch realsense2_camera rs_camera.launch
$ roslaunch mavros px4.launch
$ rosrun vins vins_node [path of realsense_stereo_imu_config.yaml]
$ rosrun loop_fusion loop_fusion_node [path of realsense_stereo_imu_config.yaml]
$ roslaunch vins vins_rviz.launch
```

