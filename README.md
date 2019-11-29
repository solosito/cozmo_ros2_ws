# cozmo_ros2_ws

## Dependencies
### ROS2
This repository was tested using [ROS 2 Eloquent Elusor](https://github.com/ros2/ros2/releases/tag/release-eloquent-20191122) (follow [official documentation](https://index.ros.org/doc/ros2/Installation/Eloquent/) for installation)

### PyCozmo
[Link to official site](https://github.com/zayfod/pycozmo)

Currently using a forked version.

For installing it follow the steps from [Clone and build](https://github.com/solosito/cozmo_ros2_ws#clone-and-build)


### opencv-python
`python3 -m pip install opencv-python`

## Clone and build
1. Create a new ROS2 workspace or use an existing one  
`mkdir -p ~/cozmo_ros2_ws/src`

1. Clone this repo  
`git clone --recursive https://github.com/solosito/cozmo_ros2_ws.git ~/cozmo_ros2_ws/src/.`

1. Install PyCozmo local version
```shell
cd ~/cozmo_ros2_ws/src/pycozmo
python3 -m pip install -e .
```

1. Build the code  
Go to the workspace folder  
`cd ~/cozmo_ros2_ws`  
then  
`colcon build`

1. Source the workspace  
`.  ~/cozmo_ros2_ws/install/setup.bash`

## Run
1. Connect to the Cozmo Wi-Fi network  

1. Run the cozmo bringup node  
`ros2 run cozmo_ros2_nosdk bringup`  

1. Run the cozmo keyboard teleop controller node **in a new terminal (need to source workspace)**  
`ros2 run cozmo_ros2_nosdk teleop_twist_keyboard`  

1. Run the image viewer  
`ros2 run image_tools showimage --ros-args --remap image:=/cozmo/camera`  

## Troubleshooting
Error:  
Cannot connect to cozmo:  

```shell
pycozmo.exception.ConnectionTimeout: Failed to connect to Cozmo.
```
Solution:  
Stop the rest of the nodes before starting the cozmo bringup node.  
