### Getting Python ready for the RFID RC522  

sudo apt-get update  
sudo apt-get upgrad

### Setting up Raspbian for the RFID RC522

sudo raspi-config  
sudo reboot  
lsmod | grep spi  

### Install python3-dev, python-pip and git packages

sudo apt-get install python3-dev python3-pip  
cd  
pwd  
git clone https://github.com/lthiery/SPI-Py.git  
ls  
cd SPI-Py/  
pwd  
ls  
sudo python setup.py install  
git clone https://github.com/pimylifeup/MFRC522-python.git  
ls  
cd MFRC522-python/  
ls  
pwd  

### Write.py file

sudo nano write.py

```python
import RPi.GPIO as GPIO
from mfrc522 import SimpleMFRC522
GPIO.setmode(GPIO.BCM)
GPIO.setwarnings(False)
reader = SimpleMFRC522()
try:
 text = input('New data:')
 print("Now place your tag to write")
 reader.write(text)
 print("Written")
finally:
 GPIO.cleanup()
```

### Run the write.py file

sudo python write.py  
> Input the name above and then flash the card to have data written to it

### read.py file

sudo nano read.py

```python
import RPi.GPIO as GPIO
from mfrc522 import SimpleMFRC522
reader = SimpleMFRC522()
try:
 id, text = reader.read()
 print(id)
 print(text)
finally:
 GPIO.cleanup()
```

### Run read.py

sudo python read.py  
> Flash the card on RFID
