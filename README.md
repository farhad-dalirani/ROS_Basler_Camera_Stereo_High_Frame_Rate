# ROS Basler Camera-USB 3.0 Stereo High Frame Rate

In this repositoty, I explained how two run two Basler-USB 3.0 Cameras with their maximum frame rate on ROS (Robotic Operating System) on Ubuntu 18.04.

1- Go to (Basler website)[baslerweb.com] and download the Pylon Viewer. For my case, it was `pylon 7.0.0 Camera Software Suite Linux x86 (64 Bit) - Debian Installer Package`.

2 Then, according to its README file install the `Pylon Viewer`.

3- Make sure you do the `USB3 Vision cameras` part in the README file. If you face error related to grub2-config, go to the file that it mentions the error occures, then change grub2 to grub.

4- Then go to (pylon ROS package)[https://github.com/basler/pylon-ros-camera] on github and install it accoding to its instructions.

5- Then you need to change device user id of you cameras. At each time plug-in only one of you cameras, and use this ROS service to change the user id:
```
roscore
rosrun pylon_camera set_device_usr_id your_device_user_id
```
It will not take effect untill you plug and unplug the Camera.

In our case, we set one of them as `ros_basler_left` and the other as `ros_basler_right`.

6- Then, open Pylon Viewer, and according to its documentation, set desired features for each camera. For example, features like gain, exposure, white balance, etc.

7- After setting features of each camera, in `Pylon Viewer`, upload features of each camera to its `UserSet1`. It is a memory on camera. We use some of these features.

8- Then go to ROS Pylon package on your catkin workstation, and delete `launch` and `config` files, and replace them with `launch` and `config` files that are available in this repository.

9- You can use one of cameras by 
```
roslaunch pylon_camera pylon_camera_node.launch 
```

10- You can use two of cameras by 
```
roslaunch pylon_camera pylon_camera_node_2RGB.launch 
```




