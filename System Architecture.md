<img width="1311" height="800" alt="RSP 4B" src="https://github.com/user-attachments/assets/e5c9f899-0e40-4b9f-8dac-6c2d01e78929" />


C:\Users\rajm4>ssh pi@192.168.0.102
pi@192.168.0.102's password:
Linux raspberrypi 6.1.21-v8+ #1642 SMP PREEMPT Mon Apr  3 17:24:16 BST 2023 aarch64

The programs included with the Debian GNU/Linux system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Debian GNU/Linux comes with ABSOLUTELY NO WARRANTY, to the extent
permitted by applicable law.
Last login: Mon Jun 22 15:17:58 2026

SSH is enabled and the default password for the 'pi' user has not been changed.
This is a security risk - please login as the 'pi' user and type 'passwd' to set a new password.

pi@raspberrypi:~ $ free -h
               total        used        free      shared  buff/cache   available
Mem:           7.6Gi       369Mi       6.5Gi        46Mi       757Mi       7.1Gi
Swap:           99Mi          0B        99Mi
pi@raspberrypi:~ $ script session1.txt
Script started, output log file is 'session1.txt'.
pi@raspberrypi:~ $ free -h
               total        used        free      shared  buff/cache   available
Mem:           7.6Gi       368Mi       6.5Gi        46Mi       757Mi       7.1Gi
Swap:           99Mi          0B        99Mi
pi@raspberrypi:~ $ cat /proc/cpuinfo | grep Model
Model           : Raspberry Pi 4 Model B Rev 1.5
pi@raspberrypi:~ $ ros2 topic list # for ROS2 if its running
bash: ros2: command not found
pi@raspberrypi:~ $ rostopic list
bash: rostopic: command not found
pi@raspberrypi:~ $ cat /etc/os-release
PRETTY_NAME="Debian GNU/Linux 11 (bullseye)"
NAME="Debian GNU/Linux"
VERSION_ID="11"
VERSION="11 (bullseye)"
VERSION_CODENAME=bullseye
ID=debian
HOME_URL="https://www.debian.org/"
SUPPORT_URL="https://www.debian.org/support"
BUG_REPORT_URL="https://bugs.debian.org/"
pi@raspberrypi:~ $ uname -a
Linux raspberrypi 6.1.21-v8+ #1642 SMP PREEMPT Mon Apr  3 17:24:16 BST 2023 aarch64 GNU/Linux
pi@raspberrypi:~ $ tree -L 2 ~/TurboPi
/home/pi/TurboPi
├── CameraCalibration
│   ├── calibration_board.jpg
│   ├── CalibrationConfig.py
│   ├── calibration_images
│   ├── calibration_param.npz
│   ├── Calibration.py
│   ├── CollectCalibrationPicture.py
│   ├── GenerateCalibrationPlate.py
│   ├── __pycache__
│   ├── README.txt
│   └── TestCalibration.py
├── Camera.py
├── Functions
│   ├── Avoidance.py
│   ├── ColorDetect.py
│   ├── ColorTracking.py
│   ├── ColorWarning.py
│   ├── EmptyFunc.py
│   ├── FaceTracking.py
│   ├── GestureRecognition.py
│   ├── ImgAddText.py
│   ├── lab_adjust.py
│   ├── LineFollower.py
│   ├── __pycache__
│   ├── QuickMark.py
│   ├── RemoteControl.py
│   ├── Running.py
│   └── VisualPatrol.py
├── HiwonderSDK
│   ├── Board.py
│   ├── BuzzerControlDemo.py
│   ├── FourInfrared.py
│   ├── hardware_test.py
│   ├── mecanum.py
│   ├── Misc.py
│   ├── MotorControlDemo.py
│   ├── PID.py
│   ├── PWMServoControlDemo.py
│   ├── __pycache__
│   ├── RGBControlDemo.py
│   └── Sonar.py
├── lab_config.yaml
├── MecanumControl
│   ├── Car_Drifting_Demo.py
│   ├── Car_Forward_Demo.py
│   ├── Car_Move_Demo.py
│   ├── Car_Slant_Demo.py
│   └── Car_Turn_Demo.py
├── MjpgServer.py
├── __pycache__
│   ├── Camera.cpython-39.pyc
│   ├── MjpgServer.cpython-39.pyc
│   ├── RPCServer.cpython-39.pyc
│   └── yaml_handle.cpython-39.pyc
├── RPCServer.py
├── servo_config.yaml
├── TurboPi.py
└── yaml_handle.py

9 directories, 49 files
pi@raspberrypi:~ $
