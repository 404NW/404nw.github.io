# Electrooster

## Team 
Minghui Ni: github.com/minghuin

Yizhe Wang: github.com/ApolloW1
# Design
Elect-rooster is an intelligent clock system. Current time and temperature are shown on the screen of Pico4ml and the brightness of the screen will be adjusted automatically based on the environment. The rooster will crow every morning when it sees the light. 


![05AC778D-8127-456B-AF4F-78B8116FB1DC_1_102_a](https://user-images.githubusercontent.com/114015725/209373902-898495f5-73e6-4c86-8a3a-431418999f2f.jpeg)


## Feature
Initialization of current time is realized by WiFi module ESP 8266.

Instant temperature is collected by the temperature sensor on Pico4ml. 

Another interesting feature is that the brightness of the screen would automatically adjust based on the environment. It will go dark in a dark environment, so your eyes won't get hurt. This is realized by the average brightness calculation based on the pictures shot by the camera. 


## Demo

https://github.com/ApolloW1/ESE519_Project/blob/main/media/demos/IMG_0537.gif

## Diagram
<img width="416" alt="image" src="https://user-images.githubusercontent.com/114015725/209372855-7c0fa8dc-8ebf-4236-869c-a21c33068fa6.png">



# Materials

Pico4ml

https://github.com/ApolloW1/ESE519_Project/blob/main/media/materials/Pico4ml.jpg

Buzzer

https://github.com/ApolloW1/ESE519_Project/blob/main/media/materials/Buzzer.jpg

WiFi module: ESP 8266

https://github.com/ApolloW1/ESE519_Project/blob/main/media/materials/ESP%208266.png

Power Bank

https://github.com/ApolloW1/ESE519_Project/blob/main/media/materials/Power%20Bank.png

Camera Module: HiMax HM01B0

Temperature sensor: ICM-20948

Screen: 0.96 inch LCD SPI Display

# Development Overview
1. Realize screen display
 
2. Realize temperature measuring

3. Realize time correction

https://github.com/ApolloW1/ESE519_Project/blob/main/media/demos/demo.gif

4. Buzzer control by light detection from the camera

5. Complete screen brightness adjusting with the camera

6. WiFi module setup

7. Get initial time from website

# Troubleshooting
## Temperature Measuring Problem
At first, the data obtained by the temperature sensor is nor correct, which is because of the intrinsic setting on different sensors. We measure the outdoor temperature and indoor temperature as anchor to adjust the algorithms in the code, resulting in accurate temperature measuring.
```
float temp = 27-(result-0.706)/0.003021;
```

## Time Accuracy Problem
The time is not accurate when we simply set sleep time to 1000 ms in the code. We then record the difference of 100 s and 1000 s of the program and compare it with the real time to adjust the sleep time, which gives us a relative correct timestemp.

# Reflection
This system operates independantly without the laptop, which makes it portable and pratical in life. The WiFi module makes the initilization easier without setting the time manually.

The buzzer could be replaced by a speaker which could play different sound to produce a ringtone.

There is a time delay caused by the WiFi module catching time information from the website.

# Code
https://github.com/minghuin/ESE519_General/blob/main/rp2040_hm01b0_st7735/main.c
