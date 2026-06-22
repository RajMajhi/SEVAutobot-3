<img width="1311" height="800" alt="RSP 4B" src="https://github.com/user-attachments/assets/e5c9f899-0e40-4b9f-8dac-6c2d01e78929" />


=============================================================================
                                 APPLICATION / USER LAYER
========================================================================================
     [ Mobile App ]  <--- (Wi-Fi 802.11ac) ---> [ ROS 2 Teleop / Web Server Node ]
     [ Remote PC ]   <--- (SSH / Terminal) ---> [ Robot Control & State Monitoring ]
                                  |
                                  v
========================================================================================
                         MIDDLEWARE & SOFTWARE PROCESSING LAYER
                     (Raspberry Pi 4B 8GB RAM - ROS 2 Humble / Ubuntu)
========================================================================================
   +-----------------------+    +------------------------+    +---------------------+
   |   Vision Processing   |    |    Navigation Node     |    |  Actuator Control   |
   |  (OpenCV 4.5.1 Node)  |    | (Line/Obstacle Avoid)  |    |  (Kinematics Node)  |
   +-----------------------+    +------------------------+    +---------------------+
               ^                            ^                            |
       (Video Streams)               (Sensor Data)               (Drive Commands)
               |                            |                            v
========================================================================================
                               HARDWARE INTERFACE LAYER
========================================================================================
   [ USB 3.0 Controller ]       [ GPIO Pins / I2C Bus ]       [ Custom Expansion Board ]
             |                             |                             |
      (USB Cable)                   (Ribbon/Jumpers)             (40-Pin GPIO Header)
             v                             v                             v
   +--------------------+       +--------------------+       +----------------------+
   | USB HD Camera Mount|       | - RGB Ultrasonic   |       | - Motor Drivers (4x) |
   | (2-DOF Pan/Tilt)   |       | - 4-Ch IR Line Foll|       | - Servo Drivers (2x) |
   +--------------------+       +--------------------+       +----------------------+
                                                                 ^              ^
======================================================================================== |
                             PHYSICAL ACTUATOR & POWER LAYER                            |
======================================================================================== |
   +--------------------------------------------------------+                    |
   |                   ACTUATORS & WHEELS                   |                    |
   |  - 4x TT DC Gear Motors  ==>  4x Mecanum Wheels        |                    |
   |  - 2x PWM Servos         ==>  Pan-Tilt Camera Bracket  |                    |
   +--------------------------------------------------------+                    |
                               ^                                                 |
                         (Motor Power)                                     (7.4V Power)
                               |                                                 |
   +-----------------------------------------------------------------------------+
   |                      POWER MANAGEMENT SUBSYSTEM                                     
   |  - Battery Source: 2x 3.7V 1800mAh Li-ion Cells (Series Connected = Nominal 7.4V)   
   |  - Power Distribution: Steps down 7.4V to 5V/3A for Pi 4B & handles high-current cell loads
   |  - External Charging Path: 5V 1-2A USB Charger Input ==> 4.2V 1000mA Output to individual cells
   +-----------------------------------------------------------------------------+
========================================================================================
