# EduBot ROS2 Documentation
Documentation repository for the EduBot ROS2 compatibility project

## Related Repositories
PRIZM ROS2 package: [prizm_ros2](https://github.com/LTU-Actor/prizm_ros2) <br>
PRIZM Arduino microcode for prizm_ros2: [prizm_ros2_arduino](https://github.com/LTU-Actor/prizm_ros2_arduino) <br>
EduBot LDS-01 LiDAR ROS2 Driver: [hls_lfcd_lds_driver](https://github.com/LTU-Actor/hls_lfcd_lds_driver) <br>
ROS2 Webcam Publisher: [usb_cam](https://github.com/ros-drivers/usb_cam) <br>
EduBot ROS2 Examples: [prizm_ros2_examples](https://github.com/LTU-Actor/prizm_ros2_examples)

## Setup

### Step 1: Clone the Repositories
Clone the following repositories into a ROS2 workspace: <br><br>
prizm_ros2
``` bash
git clone https://github.com/LTU-Actor/prizm_ros2.git
```
prizm_ros2_arduino
``` bash
git clone https://github.com/LTU-Actor/prizm_ros2_arduino.git
```
hls_lfcd_lds_driver
``` bash
git clone https://github.com/LTU-Actor/hls_lfcd_lds_driver.git -b humble
```
usb_cam
``` bash
sudo apt install ros-jazzy-usb-cam
```
prizm_ros2_examples
``` bash
git clone https://github.com/LTU-Actor/prizm_ros2_examples.git
```

### Step 2: Build the ROS2 Packages
Build the EduBot ROS2 packages with the following lines:
``` bash
colcon build --packages-select prizm_ros2 hls_lfcd_lds_driver prizm_ros2_examples
```
``` bash
source <ros2 workspace>/install/setup.bash
```


### Step 3: Prepare the Tetrix PRIZM Controller
**NOTE: If your PRIZM controller already has the prizm_ros2_arduino microcode installed, you may skip this step.**<br>
Navigate to the [prizm_ros2_arduino](https://github.com/LTU-Actor/prizm_ros2_arduino) repository and follow the instructions there to set up the PRIZM Arduino with the prizm_ros2_arduino microcode.

## Usage

### prizm_ros2
#### Step 1: Connect the PRIZM Controller
Power on the Tetrix PRIZM controller and connect your machine by USB.

#### Step 2: Launch the Program
Launch the program with the following line:
``` bash
ros2 launch prizm_ros2 launch.py serial_port:=<device path to PRIZM>
```
The serial_port parameter defaults to `/dev/ttyUSB0`, but can be modified.

#### Step 3: Enable the PRIZM Controller
Shortly after launching prizm_ros2, the green LED should show on the PRIZM controller. Press the green button to enable the controller.

#### Step 4: ROS2 Usage
You may now use prizm_ros2 to control the bot's movement and LEDs. See the [prizm_ros2 ROS2 Info](https://github.com/LTU-Actor/prizm_ros2?tab=readme-ov-file#ros-info) for a full description of the ROS2 usage structure.

### hls_lfcd_lds_driver
#### Step 1: Connect the LDS-01 LiDAR
Connect the LiDAR to your machine by USB. The LiDAR should spin upon connecting.

#### Step 2: Launch the Program
Launch the program with the following line:
``` bash
ros2 launch hls_lfcd_lds_driver hlds_laser.launch.py
```
LiDAR ranging information should appear on the `/scan` topic.

#### Step 3: Visualization (Optional)
Visualization of the LiDAR ranging information can be done with the following line:
``` bash
rviz2 -d <driver directory>/rviz/hlds_laser.rviz
```
## Examples
Some basic examples are available:
#### Drive Forward Yaw
Drives the bot at a constant speed and yaw for a specified duration.
``` bash
ros2 run prizm_ros2_examples drive_forward_yaw
```

