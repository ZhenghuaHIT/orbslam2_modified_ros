# orbslam2_modified_ros
**Authors**: Zhenghua.Hou HIT 16S108281

**2017.12.9**: Use to ros run orbslam2_modified with Kinect v2.

**Introduction**: Dr.Gao Xiang has modified the ORB_SLAM2 so that it can display the point cloud map, but this version does not have the function of point cloud integration and point cloud preservation. Replace the provided document and project can save the point cloud as a PCD file after voxel filtering. Provides documentation for running under ROS

**Reference**: Dr.Gao Xiang's [GitHub](https://github.com/gaoxiang12); [ORB_SLAM2](https://github.com/raulmur/ORB_SLAM2) by raulmur

# 1. License
Only Myself and My junior of laboratory.

# 2. Prerequisites
## Install orbslam_modified  
### 1. download & install project
```
git clone https://github.com/gaoxiang12/ORBSLAM2_with_pointcloud_map.git
```

### 2. Precautions    

 ORB_SLAM2_modified/Vocabulary missing txt of BoW model, can be copied from ORB_SLAM2 source code    

 Recompile g2o    

 Recompile the BOW library    

 The project only supports opencv2  
 
# 3. Usage

### 1. Modify CMakeLists in orbslam_modified  

Orbslam_modified version didnot modify the CMakeLists in ROS. Due to the addition of the PCL library, and the way to compile g2o. we need to be modified.

"CMakeLists.txt" under the "ORBSLAM2_with_pointcloud_map/orbslam2_modified/ORB_SLAM2_modified/Example/ROS/ORB_SLAM2" folder

### 2. Modify the environment variable  
```
gedit .bashrc
export ROS_PACKAGE_PATH=${ROS_PACKAGE_PATH}:/home/hou/ORBSLAM2_with_pointcloud_map/orbslam2_modified/ORB_SLAM2_modified/Examples/ROS
```
### 3. Open the **driver** and **program** under ROS  
```
roscore
roslaunch freenect_launch freenect-registered-xyzrgb.launch
cd ORBSLAM2_with_pointcloud_map/orbslam2_modified/ORB_SLAM2_modified/Examples/ROS
rosrun ORB_SLAM2 RGBD /home/hou/ORBSLAM2_with_pointcloud_map/orbslam2_modified/ORB_SLAM2_modified/Vocabulary/ORBvoc.txt /home/hou/ORBSLAM2_with_pointcloud_map/orbslam2_modified/ORB_SLAM2_modified/Examples/RGB-D/kinect1.yaml
```
