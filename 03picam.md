### Step 1: Connect the Pi Camera Module  

### Step 2: Open the terminal  

Run `sudo raspi-config`  
Then select Interfacing options in which select Camera option to enable its functionality

Run `sudo reboot`

**Optional**  
`sudo apt-get install python-picamera python3-picamera`

**Optional: Quick capture method**  

Picture
`raspistill -o image.jpg`  

Video
`raspivid -o video.h264`  


### Step 3: Write Python code for picture

**For Picture**  

Run `sudo nano camera.py`

```python
import picamera  
from time import sleep
camera = picamera.PiCamera()
camera.resolution=(1024,768)
camera.brightness=60
camera.start_preview()
camera.annotate_text="hi"
sleep(10)
camera.capture('image1.jpeg')
camera.stop_preview()
```

Run `sudo python camera.py`

**For video**  

Run `sudo nano recording.py`  

```python
import picamera  
from time import sleep
camera = picamera.PiCamera()
camera.resolution=(640,480)
print()
camera.start_preview()
camera.start_recording('/home/pi/demo.h264')
camera.wait_recording(20)
camera.stop_recording()
camera.close()
print('Video recording stopped')
```

Run `sudo python recording.py`
