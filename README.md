***
# Quad-Leggs Simulation setting

***
<br>

# Index
<!--
### 1. Prerequisites
####    &nbsp;&nbsp;&nbsp;&nbsp;● LCM
####    &nbsp;&nbsp;&nbsp;&nbsp;● Boost
####    &nbsp;&nbsp;&nbsp;&nbsp;● CMake
####    &nbsp;&nbsp;&nbsp;&nbsp;● unitree_legged_sdk
####    &nbsp;&nbsp;&nbsp;&nbsp;● aliengo_sdk
-->
### 1. Install
### 2. Applying Model
####    &nbsp;&nbsp;&nbsp;&nbsp;● I used [robot_name]
### 3. Run
####    &nbsp;&nbsp;&nbsp;&nbsp;● tele-operation using ROS topic publisher 
<br><br>
+ **reference github link**: [champ](https://github.com/chvmp/champ)

<!--
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
-->

## 1. Install
+ installing champ (controller for quad-legs robot)
```
$ sudo apt install -y python-rosdep
$ cd <your_ws>/src
$ git clone --recursive https://github.com/chvmp/champ
$ git clone https://github.com/chvmp/champ_teleop
$ cd ..
$ rosdep install --from-paths src --ignore-src -r -y
```

+ installing robot models
```
$ cd && $ git clone https://github.com/chvmp/robots.git
$ cd robots && ./install_deescriptions
$ mv robots/configs/<your_model>_config <your_ws>/src/champ/
$ mv robots/descriptions/<your_model>_description <your_ws>/src/champ/
$ cd <your_ws> && catkin_build -j8
```


## 2. Applying Model
#### ● Actually, I used anymal_b_config model only.
<br><br>

## 3. Run
+ please refer my [gazebo.launch]()
```
$ roslaunch anymal_b_config gazebo.launch # load anymal_b robot model and world
$ roslaunch anymal_b_config slam.launch rviz:=true
```

