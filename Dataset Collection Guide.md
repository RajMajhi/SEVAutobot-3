
<img width="1920" height="1080" alt="2026-06-24-155327_1920x1080_scrot" src="https://github.com/user-attachments/assets/033d56a7-65e9-455d-8c82-b97669bec564" />

<img width="15" height="10" alt="2026-06-24-161512_15x10_scrot" src="https://github.com/user-attachments/assets/74382d2c-22bd-4ca2-adef-9150fcdba315" />
<img width="1920" height="36" alt="2026-06-24-160206_1920x36_scrot" src="https://github.com/user-attachments/assets/b2c1915d-26ee-4022-b020-b8f67ca8ba5e" />
<img width="374" height="457" alt="2026-06-24-160040_374x457_scrot" src="https://github.com/user-attachments/assets/8c52b87e-07ba-4910-845c-ecf8f311bdfd" />
<img width="395" height="68" alt="2026-06-24-155836_395x68_scrot" src="https://github.com/user-attachments/assets/09012566-5004-4938-9463-8f24edabbce5" />
<img width="1920" height="1080" alt="2026-06-24-155416_1920x1080_scrot" src="https://github.com/user-attachments/assets/71cf1d16-a6aa-40ef-81b7-1146ee0045ee" />
<img width="1920" height="1080" alt="2026-06-24-155402_1920x1080_scrot" src="https://github.com/user-attachments/assets/ae0e244f-562d-4435-b7ff-e38c831e1f34" />



# Dataset Collection

This section describes the procedure for acquiring image datasets using the TurboPi onboard USB camera. The collected data can be used for computer vision applications such as object detection, image classification, tracking, segmentation, and robotics research.

---

# Camera Access

TurboPi already provides a camera interface module named `Camera.py`, which can be used to verify that the camera is functioning correctly.

Navigate to the TurboPi workspace:

```bash
cd ~/TurboPi
```

Launch the camera interface:

```bash
python Camera.py
```

If the camera initializes successfully, a preview window should appear displaying the live camera feed.

Example output:

```text
Camera initialized successfully
Video stream active
```

The successful appearance of the video stream confirms that:

* The USB camera is detected correctly.
* OpenCV can access the camera device.
* The video acquisition pipeline is operational.
* The camera can be used for dataset generation.

---

# Camera Property Inspection

Before collecting data, it is useful to inspect the characteristics of the camera, including:

* Resolution
* Frame rate
* Brightness
* Contrast
* Saturation
* Gain

Create a Python script named:

```bash
nano camera_info.py
```

Paste the following code:

```python
import cv2

cap = cv2.VideoCapture(0)

print("Opened:", cap.isOpened())

print("Width :", cap.get(cv2.CAP_PROP_FRAME_WIDTH))
print("Height:", cap.get(cv2.CAP_PROP_FRAME_HEIGHT))
print("FPS   :", cap.get(cv2.CAP_PROP_FPS))

print("Brightness :", cap.get(cv2.CAP_PROP_BRIGHTNESS))
print("Contrast   :", cap.get(cv2.CAP_PROP_CONTRAST))
print("Saturation :", cap.get(cv2.CAP_PROP_SATURATION))
print("Gain       :", cap.get(cv2.CAP_PROP_GAIN))

cap.release()
```

Execute:

```bash
python3 camera_info.py
```

Example output:

```text
Opened: True

Width : 640.0
Height: 480.0
FPS   : 30.0

Brightness : 0.0
Contrast   : 27.0
Saturation : 40.0
Gain       : 0.0
```

---
<img width="475" height="453" alt="image" src="https://github.com/user-attachments/assets/3d682149-e0d2-44a1-b3d1-f6461b458dc1" />

<img width="557" height="419" alt="image" src="https://github.com/user-attachments/assets/3cc73329-b824-48c1-8fd8-5d9b774c2753" />

# Camera Characteristics

The camera properties obtained during inspection are summarized below.

| Parameter  | Value     |
| ---------- | --------- |
| Resolution | 640 × 480 |
| Frame Rate | 30 FPS    |
| Brightness | 0         |
| Contrast   | 27        |
| Saturation | 40        |
| Gain       | 0         |

These parameters provide useful metadata for documenting the dataset acquisition process.

---

# Raw Image Acquisition

To capture raw images from the camera, create a script named:

```bash
nano capture_images.py
```

Paste the following code:

```python
import cv2
import os

save_dir = "dataset/images"

os.makedirs(save_dir, exist_ok=True)

cap = cv2.VideoCapture(0)

counter = 0

while True:

    ret, frame = cap.read()

    if not ret:
        break

    cv2.imshow("Camera", frame)

    key = cv2.waitKey(1)

    if key == ord('s'):

        filename = f"{save_dir}/img_{counter:05d}.png"

        cv2.imwrite(filename, frame)

        print("Saved:", filename)

        counter += 1

    elif key == ord('q'):

        break

cap.release()

cv2.destroyAllWindows()
```

Execute:

```bash
python3 capture_images.py
```

Keyboard controls:

| Key | Function           |
| --- | ------------------ |
| S   | Save current frame |
| Q   | Quit application   |

---

# Dataset Organization

Captured images are stored inside:

```text
dataset/
└── images/
    ├── img_00000.png
    ├── img_00001.png
    ├── img_00002.png
    └── ...
```

Example:

```text
dataset/images/img_00000.png
dataset/images/img_00001.png
dataset/images/img_00002.png
```

PNG format was selected because it preserves image quality without introducing compression artifacts, making it suitable for machine learning datasets.

---

# Sample Dataset

The image below demonstrates an example frame captured using the TurboPi onboard camera.

*(Insert captured image here)*

---

# Dataset Metadata

The following metadata should be recorded alongside the collected dataset:

| Attribute           | Value                 |
| ------------------- | --------------------- |
| Camera Interface    | USB Camera            |
| Device Node         | `/dev/video0`         |
| Resolution          | 640 × 480             |
| Frame Rate          | 30 FPS                |
| Operating System    | Debian 11 Bullseye    |
| Platform            | Raspberry Pi 4B (8GB) |
| Acquisition Library | OpenCV 4.5.1          |

Maintaining metadata improves dataset reproducibility and simplifies future experimentation.

---

# Future Improvements

Potential enhancements to the data acquisition pipeline include:

* Video recording support
* Automatic timestamp generation
* Metadata logging in JSON format
* High-resolution image capture
* Continuous dataset acquisition
* Image annotation integration
* Camera calibration data storage
* Direct storage to external USB devices
