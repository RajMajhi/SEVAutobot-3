# Project Overview

TurboPi is an AI-powered mobile robotics platform developed by Hiwonder and built around the Raspberry Pi 4B. The robot combines computer vision, sensor integration, and mecanum-wheel mobility to support robotics education, research, and autonomous navigation experiments.

The platform features a USB camera, ultrasonic sensor, infrared line tracking sensors, servo-controlled pan-tilt mechanism, and a four-wheel mecanum drive system. These components enable the robot to perform tasks such as color detection, object tracking, face tracking, line following, obstacle avoidance, and remote operation.

This documentation provides a detailed analysis of the TurboPi hardware architecture, software stack, camera system, motion control modules, and operational workflow. It also serves as a reference for configuring, operating, troubleshooting, and extending the robot for future robotics and computer vision projects.

## Objectives

* Understand the hardware and software architecture of TurboPi.
* Document the complete system configuration.
* Analyze the vision and motion control subsystems.
* Explore dataset collection and computer vision applications.
* Provide a reference guide for future development and research.

## Key Features

* Raspberry Pi 4B (8 GB RAM) based control system
* USB camera for computer vision applications
* Mecanum wheel omnidirectional drive
* Servo-controlled camera pan-tilt mechanism
* Color detection and tracking
* Face tracking and gesture recognition
* Line following and obstacle avoidance
* SSH-based remote access and monitoring
* Expandable platform for AI and robotics research

## Hardware specification

# GPU Documentation

## Overview

The Raspberry Pi 4 Model B incorporates the Broadcom VideoCore VI graphics processing unit (GPU). The GPU is primarily designed for graphics rendering, multimedia processing, and display output rather than general-purpose GPU computing (GPGPU).

Unlike NVIDIA GPUs, the VideoCore VI does not support CUDA or Tensor Cores, and therefore cannot accelerate PyTorch or TensorFlow models using CUDA.

---

## Hardware Specifications

| Parameter        | Specification                  |
| ---------------- | ------------------------------ |
| GPU              | Broadcom VideoCore VI          |
| Manufacturer     | Broadcom                       |
| Graphics API     | OpenGL ES 3.1                  |
| Video Encoding   | H.264                          |
| Video Decoding   | H.264 (1080p60), H.265 (4Kp60) |
| Display Support  | Dual HDMI Output               |
| CUDA Support     | No                             |
| TensorRT Support | No                             |
| OpenCL Support   | Limited / Experimental         |
| AI Acceleration  | Not Supported                  |

---

## GPU Responsibilities

The VideoCore VI GPU performs the following tasks:

* Desktop rendering
* HDMI display output
* OpenGL graphics acceleration
* Camera preview rendering
* Hardware video encoding
* Hardware video decoding

---

## AI Workloads

The GPU is **not** intended for deep learning inference or training.

The following libraries execute on the CPU:

* OpenCV
* PyTorch
* TensorFlow
* Ultralytics YOLO

Unless external AI accelerators are installed, all neural network inference is performed by the Raspberry Pi's ARM Cortex-A72 CPU.

---

## System Verification

Kernel Information:

```bash
uname -a
```
<img width="468" height="48" alt="image" src="https://github.com/user-attachments/assets/7a81122e-231e-4558-94c6-f58f8f57b79f" />


GPU Firmware:

```bash
vcgencmd version
```
<img width="466" height="93" alt="image" src="https://github.com/user-attachments/assets/8c3b36f6-b31c-4464-b968-3d9eff900ce3" />

OpenGL Renderer:

```bash
glxinfo | grep "OpenGL renderer"
```
<img width="850" height="60" alt="image" src="https://github.com/user-attachments/assets/2644d520-efc8-4460-95ab-cb0d694eb795" />

Memory Information:

```bash
free -h
```
<img width="574" height="88" alt="image" src="https://github.com/user-attachments/assets/dbcba7ea-69f8-40b4-add4-de7b93e1f76f" />

---

## Current GPU Status

During system inspection:

* GPU firmware detected successfully.
* Raspberry Pi firmware initialized correctly.
* No CUDA-capable GPU detected.
* No GPU-accelerated PyTorch installation present.

---

## Limitations

* CUDA is not supported.
* TensorRT is unavailable.
* GPU cannot accelerate PyTorch models.
* GPU is optimized for graphics and multimedia processing.

---

## Possible AI Acceleration Upgrades

To improve AI performance, the following hardware accelerators may be considered:

* Google Coral USB Accelerator (Edge TPU)
* NVIDIA Jetson Nano
* NVIDIA Jetson Orin Nano

These platforms provide dedicated AI hardware capable of accelerating neural network inference.

## Current GPU Status

The GPU capabilities were evaluated using system inspection commands and software package verification.

| Observation                       | Verification Method                                                                                                                                          | Status                                                  |                |
| --------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------- | -------------- |
| GPU firmware detected             | `vcgencmd version`                                                                                                                                           | Verified                                                |                |
| Raspberry Pi firmware initialized | `vcgencmd version`                                                                                                                                           | Verified                                                |                |
| GPU hardware present              | `lspci` is not applicable on Raspberry Pi; GPU is integrated into the Broadcom SoC and identified through Raspberry Pi firmware and hardware specifications. | Verified                                                |                |
| CUDA support                      | `python3 -c "import torch; print(torch.cuda.is_available())"` (if PyTorch is installed)                                                                      | Not Supported                                           |                |
| PyTorch GPU support               | `python3 -c "import torch"`                                                                                                                                  | PyTorch not installed                                   |                |
| GPU renderer                      | `glxinfo                                                                                                                                                     | grep "OpenGL renderer"`*(after installing`mesa-utils`)* | To be Verified |
| OpenGL version                    | `glxinfo                                                                                                                                                     | grep "OpenGL version"`                                  | To be Verified |
| Vulkan support                    | `vulkaninfo` *(after installing `vulkan-tools`)*                                                                                                             | To be Verified                                          |                |

### Verification Commands

#### Check Raspberry Pi firmware

```bash
vcgencmd version
```

#### Check operating system and kernel

```bash
cat /etc/os-release
uname -a
```

#### Check GPU memory allocation

```bash
vcgencmd get_mem gpu
```

#### Check ARM memory allocation

```bash
vcgencmd get_mem arm
```

#### Check OpenGL renderer

Install Mesa utilities:

```bash
sudo apt install mesa-utils
```

Then run:

```bash
glxinfo | grep "OpenGL renderer"
```

#### Check OpenGL version

```bash
glxinfo | grep "OpenGL version"
```

#### Check Vulkan support

Install:

```bash
sudo apt install vulkan-tools
```

Run:

```bash
vulkaninfo
```

#### Check whether PyTorch is installed

```bash
python3 -c "import torch; print(torch.__version__)"
```

#### Check CUDA availability (if PyTorch is installed)

```bash
python3 -c "import torch; print(torch.cuda.is_available())"
```

Expected output:

```text
False
```

This is expected because the Raspberry Pi 4 does not provide CUDA support.

---

## Limitations

The following limitations were identified during hardware and software inspection:

| Limitation                                                       | Verification                                                                                                                            |                                        |
| ---------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------- |
| CUDA is not supported                                            | `torch.cuda.is_available()` returns `False` (when PyTorch is installed), and Raspberry Pi 4's VideoCore VI GPU does not implement CUDA. |                                        |
| TensorRT is unavailable                                          | `dpkg -l                                                                                                                                | grep tensorrt` (no packages installed) |
| GPU cannot accelerate PyTorch models                             | No CUDA backend is available for the Raspberry Pi VideoCore VI GPU.                                                                     |                                        |
| GPU is primarily intended for graphics and multimedia processing | Confirmed through Raspberry Pi hardware specifications and OpenGL capability inspection (`glxinfo`).                                    |                                        |
