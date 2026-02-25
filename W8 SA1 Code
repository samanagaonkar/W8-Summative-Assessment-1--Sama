from machine import Pin, PWM

import time
import neopixel 

irsensor = Pin(18, Pin.IN, Pin.PULL_UP)
led = Pin(19, Pin.OUT)
buzzer = Pin (22, Pin.OUT)
golfnp = neopixel.NeoPixel(Pin(27, Pin.OUT),16)
pb2 = Pin(21, Pin.IN, Pin.PULL_UP)
servo = PWM(Pin(13), freq=50)
pb1 = Pin(26, Pin.IN, Pin.PULL_UP)

while True:

#swing
    if pb1.value() == 0:
        servo.duty(80)     
        time.sleep(1)
        servo.duty(23)   
        time.sleep(1)
        
        while pb1.value() == 0:
            time.sleep(0.1)
        
#detect  
    ir_val = irsensor.value()
        
    if ir_val == 0:
        led.on()
        time.sleep(0.8)
        buzzer.on()
        time.sleep(0.3)
            
    if ir_val == 1:
        led.off()
        buzzer.off()
            
        time.sleep(0.2)
        
#feedback
    rev_val = pb2.value()
    
    if rev_val == 0:
       
        golfnp[2]=(0,100,0)
        golfnp[5]=(0,100,0)
        for x in range(8,16):
            golfnp[x] = (0,100,0)
            
        golfnp.write()
        time.sleep(2)
        
        golfnp[2]=(0,0,0)
        golfnp[5]=(0,0,0)
        for y in range(8,16):
            golfnp[y] = (0,0,0)
            
        time.sleep(1)
