# Directory Structure

The TurboPi software package is located at:

```text id="f9c0wh"
/home/pi/TurboPi
```

## Project Structure

```text id="6xv7i0"
TurboPi/
├── Camera.py
├── CameraCalibration/
├── Functions/
├── HiwonderSDK/
├── MecanumControl/
├── MjpgServer.py
├── RPCServer.py
├── TurboPi.py
├── servo_config.yaml
├── lab_config.yaml
└── yaml_handle.py
```

---

## Directory Description

### CameraCalibration/

Contains tools and resources for camera calibration.

```text id="vg85f4"
CameraCalibration/
├── calibration_board.jpg
├── calibration_images/
├── calibration_param.npz
├── Calibration.py
├── CollectCalibrationPicture.py
├── GenerateCalibrationPlate.py
├── TestCalibration.py
└── README.txt
```

Purpose:

* Capture calibration images
* Generate calibration patterns
* Compute camera intrinsic parameters
* Correct image distortion

---

### Functions/

Contains computer vision and autonomous behavior modules.

```text id="4wyjx5"
Functions/
├── Avoidance.py
├── ColorDetect.py
├── ColorTracking.py
├── ColorWarning.py
├── FaceTracking.py
├── GestureRecognition.py
├── LineFollower.py
├── QuickMark.py
├── RemoteControl.py
├── Running.py
└── VisualPatrol.py
```

Purpose:

* Color detection
* Object tracking
* Face tracking
* Gesture recognition
* Line following
* Obstacle avoidance
* Remote control functionality

---

### HiwonderSDK/

Hardware abstraction and device control library.

```text id="dz7g3r"
HiwonderSDK/
├── Board.py
├── mecanum.py
├── PID.py
├── Sonar.py
├── FourInfrared.py
├── Misc.py
└── Demo Programs
```

Purpose:

* Motor control
* Servo control
* Sensor communication
* PID control
* Mecanum wheel kinematics
* Hardware interface functions

---

### MecanumControl/

Demonstration programs for robot movement.

```text id="pvv63d"
MecanumControl/
├── Car_Forward_Demo.py
├── Car_Move_Demo.py
├── Car_Slant_Demo.py
├── Car_Turn_Demo.py
└── Car_Drifting_Demo.py
```

Purpose:

* Test wheel movement
* Verify motor operation
* Demonstrate mecanum wheel capabilities

---

## Core Files

### TurboPi.py

Main application entry point.

Responsibilities:

* System initialization
* Module coordination
* Robot operation management

---

### Camera.py

Camera interface module.

Responsibilities:

* Camera initialization
* Frame acquisition
* Video stream management

---

### RPCServer.py

Remote Procedure Call server.

Responsibilities:

* Remote command execution
* Communication between user interface and robot

---

### MjpgServer.py

Video streaming server.

Responsibilities:

* MJPEG video streaming
* Remote camera monitoring

---

### yaml_handle.py

YAML configuration utilities.

Responsibilities:

* Read configuration files
* Store system settings

---

## Configuration Files

### servo_config.yaml

Stores servo-related parameters:

* Servo IDs
* Initial positions
* Motion limits

### lab_config.yaml

Stores computer vision parameters:

* Color thresholds
* Image processing settings
* Detection configuration

```
```

