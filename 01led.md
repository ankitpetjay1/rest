sudo apt-get install python-rpi.gpio  
sudo nano led.py

```python
import RPi.GPIO as GPIO
import time

GPIO.setwarnings(False)
GPIO.setmode(GPIO.BOARD)
GPIO.setup(40,GPIO.OUT)

print("Press q to exit")

try:
  while True:
    for num in range(2):
      GPIO.output(40,GPIO.HIGH)
      time.sleep(0.05)
except KeyboardInterrupt:
  pass
GPIO.output(40,GPIO.LOW)
GPIO.cleanup()
```
