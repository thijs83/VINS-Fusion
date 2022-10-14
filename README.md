# VINS-Fusion Fork updated for OpenCV 4.*



### 1.2. **Ceres Solver**
Follow [Ceres Installation](http://ceres-solver.org/installation.html).
```
    sudo apt-get install libeigen3-dev libboost-all-dev libceres-dev
```

## 2. Build VINS-Fusion
Clone the repository and catkin_make:
```
    cd ~/catkin_ws/src
    git clone https://github.com/thijs83/VINS-Fusion.git
    cd ../
    catkin_make
    source ~/catkin_ws/devel/setup.bash
```
(if you fail in this step, try to find another computer with clean system or reinstall Ubuntu and ROS)



### 3.1 Monocualr camera + IMU

```
    roslaunch vins vins_rviz.launch
    rosrun vins vins_node ~/catkin_ws/src/VINS-Fusion/config/realsense_d435i/realsense_stereo_imu_config.yaml
    (optional) rosrun loop_fusion loop_fusion_node ~/catkin_ws/src/VINS-Fusion/config/realsense_d435i/realsense_stereo_imu_config.yaml 
    roslaunch ~/catkin_ws/src/VINS-Fusion/config/realsense_d435i/rs_camera.launch
```




### 6.2 Camera calibration
VINS-Fusion support several camera models (pinhole, mei, equidistant). You can use [camera model](https://github.com/hengli/camodocal) to calibrate your cameras. We put some example data under /camera_models/calibrationdata to tell you how to calibrate.
```
cd ~/catkin_ws/src/VINS-Fusion/camera_models/camera_calib_example/
rosrun camera_models Calibrations -w 12 -h 8 -s 80 -i calibrationdata --camera-model pinhole
```

## 8. Acknowledgements
We use [ceres solver](http://ceres-solver.org/) for non-linear optimization and [DBoW2](https://github.com/dorian3d/DBoW2) for loop detection, a generic [camera model](https://github.com/hengli/camodocal) and [GeographicLib](https://geographiclib.sourceforge.io/).

## 9. License
The source code is released under [GPLv3](http://www.gnu.org/licenses/) license.

We are still working on improving the code reliability. For any technical issues, please contact Tong Qin <qintonguavATgmail.com>.

For commercial inquiries, please contact Shaojie Shen <eeshaojieATust.hk>.
