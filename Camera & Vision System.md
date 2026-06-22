# Camera Specifications -
    Camera Name- ICSpring camera 
    Driver - USB Video Class
    CSI camera integrated into a 2-DOF (Degrees of Freedom) pan-tilt mount
    camera uses OmniVision or Sony IMX sensor.
    Resolution - 640 × 480 
    Detect a specific color and trigger an alert.
    Execute predefined robot actions based on recognized colors.
    Display the position of detected objects.
    Track a selected target using pan-tilt and chassis control. 
    YUVY pixel format,it groups 2 pixels into 4 byte sequence

### Single Color Recognition (Color Warning) -
      When the target color is detected:
      Draw a circle around the object.
      Display the detected color name.
      Activate the buzzer. 
      
### Color Recognition -
|   Color  |  RGB LED | Buzzer | Robot Motion |
|----------|----------|--------|--------------|
|    Red   |   Red    |  Beep  |     Nod      |
|   Green  |  Green   |  Beep  |  Shake Head  |
|    Blue  |   Blue   |  Beep  |  Shake Head  |

### Color Position Recognition -
      Detect colored objects and report their image coordinates
      For each detected object:
           Draw a bounding circle 
           Display its center coordinates 
           Show the processed image in real time

### Target Tracking - 
        
