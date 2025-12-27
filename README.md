# Rpi5_Webserver_ESP32
I control an RPi 5 robot car remotely via Wi-Fi.
The control flow is: User → web server → Wi-Fi → RPi 5 (brain) → ESP32 → devices.
The ESP32 connection is based on in my section “ros_bridge_esp32”, and the RPi 5 server code is provided in this section.

* Note
  
  in "serial_io.py" set /dev/ttyUSB0 or /dev/ttyUSB1 or so on

  in "camera_ai.py" set cv2.VideoCapture(0) or cv2.VideoCapture(1) or so on

<img width="1650" height="808" alt="image" src="https://github.com/user-attachments/assets/c2147dfc-d5fc-4d73-954c-e13089ed5d4c" />


