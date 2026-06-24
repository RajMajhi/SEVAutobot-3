# Hardware Bill of Materials (BOM)

# Hardware Bill of Materials (BOM)

| Item No. | Component                         | Quantity | Description                             | Manufacturer            | Model Name      | Specifications            | Verification Status |
| -------- | --------------------------------- | -------- | --------------------------------------- | ----------------------- | --------------- | ------------------------- | ------------------- |
| 1        | Raspberry Pi 4 Model B (8 GB RAM) | 1        | Main processing unit                    | Raspberry Pi Foundation | Raspberry Pi 4B | 8 GB RAM, ARM Cortex-A72  | Verified            |
| 2        | MicroSD Card                      | 1        | Operating system and storage            | TBD                     | TBD             | Capacity TBD              | Verified            |
| 3        | USB HD Camera                     | 1        | Vision sensor for image acquisition     | iCSpring                | TBD             | USB Camera, `/dev/video0` | Verified            |
| 4        | Pan-Tilt Camera Bracket           | 1        | Camera mounting mechanism               | Hiwonder                | TBD             | 2-DOF Pan-Tilt Mount      | Verified            |
| 5        | PWM Servo Motor                   | 2        | Pan and tilt control                    | TBD                     | TBD             | PWM Controlled Servo      | Assumed             |
| 6        | Mecanum Wheel                     | 4        | Omnidirectional wheel system            | Hiwonder                | TBD             | Mecanum Drive Wheel       | Verified            |
| 7        | DC Gear Motor                     | 4        | Drive motors                            | TBD                     | TBD             | Geared DC Motor           | Verified            |
| 8        | Hiwonder Expansion Board          | 1        | Motor and servo control board           | Hiwonder                | TBD             | GPIO Expansion Board      | Assumed             |
| 9        | RGB Ultrasonic Sensor             | 1        | Distance sensing and obstacle detection | Hiwonder                | TBD             | RGB Ultrasonic Module     | Assumed             |
| 10       | Four-Channel Infrared Sensor      | 1        | Line tracking sensor                    | Hiwonder                | TBD             | IR Line Tracking Module   | Assumed             |
| 11       | Li-ion Battery (3.7V, 1800mAh)    | 2        | Power source                            | TBD                     | TBD             | 3.7V, 1800mAh             | Assumed             |
| 12       | Battery Holder                    | 1        | Battery mounting                        | TBD                     | TBD             | Dual Cell Holder          | Assumed             |
| 13       | Power Distribution Circuit        | 1        | Voltage regulation and distribution     | Hiwonder                | TBD             | Power Management Board    | Assumed             |
| 14       | Robot Chassis                     | 1        | Structural frame                        | Hiwonder                | TurboPi Chassis | Aluminum/Acrylic Frame    | Verified            |
| 15       | Wi-Fi Adapter (Integrated)        | 1        | Wireless communication                  | Raspberry Pi Foundation | Integrated      | 802.11ac Wi-Fi            | Verified            |
| 16       | Mounting Screws and Standoffs     | Multiple | Mechanical assembly                     | Various                 | Various         | Assorted Hardware         | Verified            |
| 17       | USB Flash Drive (Optional)        | 1        | Dataset storage                         | Various                 | Various         | USB Storage Device        | Verified            |
| 18       | Jumper Cables and Connectors      | Multiple | Hardware connections                    | Various                 | Various         | Electrical Interconnects  | Verified            |

TBD stands for:
To Be Determined

## Purchase links
1. https://www.hiwonder.com/products/turbopi?variant=43978005610583&srsltid=AfmBOoqCfewBF4_eSFuxYdAxmSHvLomeNOSZqfXoPJ3biB68jSH5r9hE 
   or
2. https://www.amazon.in/LewanSoul-Raspberry-Educational-Programming-Programmable/dp/B0CHYQFQBB?th=1


lsusb
ls ~/TurboPi/HiwonderSDK


# Battery
Capacity: 10,000 mAh
Voltage: 5 V
Energy: 50 Wh

Energy = 10000/1000 × 5 = 50Wh  

## Estimated Camera Battery Runtime
##### Amount of time the battery is expected to last 
<img width="344" height="49" alt="Screenshot 2026-06-23 163135" src="https://github.com/user-attachments/assets/6b8ff668-9b8f-488e-8094-0e3478802702" />

## Battery usage while running camera
##### The power or energy consumed by the camera while it is operating.
###### 4W power consumption while the camera is active.
<img width="273" height="46" alt="Screenshot 2026-06-23 165239" src="https://github.com/user-attachments/assets/e629d663-adcf-44c7-88b9-163b591bbd0b" />

