# Software Setup

## Operating System

The TurboPi platform is configured with:

| Component    | Version                        |
| ------------ | ------------------------------ |
| OS           | Debian GNU/Linux 11 (Bullseye) |
| Kernel       | Linux 6.1.21-v8+               |
| Architecture | ARM64 (aarch64)                |

Verification:

```bash
cat /etc/os-release
uname -a
```

---

## Python Environment

The TurboPi software stack is primarily Python-based.

Verify Python installation:

```bash
python3 --version
```

Example output:

```text
Python 3.9.x
```

---

## OpenCV

OpenCV is used for image acquisition and computer vision functions.

Verify installation:

```bash
python3 -c "import cv2; print(cv2.__version__)"
```

---

## TurboPi Software Directory

Main project location:

```text
/home/pi/TurboPi
```

Project structure:

```text
TurboPi/
├── Camera.py
├── CameraCalibration/
├── Functions/
├── HiwonderSDK/
├── MecanumControl/
├── TurboPi.py
├── RPCServer.py
├── MjpgServer.py
├── servo_config.yaml
└── lab_config.yaml
```

---

## Camera Configuration

Camera type:

```text
USB Camera (icspring camera)
```

Detected device:

```text
/dev/video0
```

Verification:

```bash
v4l2-ctl --list-devices
```

---

## Network Configuration

Remote access is enabled using SSH.

Connect from a remote computer:

```bash
ssh pi@<robot-ip-address>
```

Example:

```bash
ssh pi@192.168.0.102
```

---

## Storage Configuration

External USB storage can be mounted for dataset collection.

Example mount location:

```text
/media/pi/SEVA (SHBM)
```

Recommended dataset structure:

```text
dataset/
├── images/
└── videos/
```

---

## ROS Status

ROS is not currently installed on the system.

Verification:

```bash
ros2 topic list
rostopic list
```

Output:

```text
command not found
```

Future integration may include ROS 2 Humble for advanced robotics applications.

---

## Recommended Development Tools

* Python 3
* OpenCV
* SSH
* Git
* VS Code (Remote SSH)
* V4L2 Utilities

Install V4L2 tools:

```bash
sudo apt install v4l-utils
```

Verify camera devices:

```bash
v4l2-ctl --list-devices
```

