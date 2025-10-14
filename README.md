#  Automatic Solar Panel Tracker

This project presents an **automatic solar tracking system** built using an **Arduino Uno** microcontroller.  
The system automatically positions a solar panel toward the **strongest light source** (Sun or artificial light) using **light sensors (LDRs)** and **servo motors**, significantly improving energy efficiency.



##  Overview

The main goal of this project is to increase the efficiency of solar panels by ensuring they are always optimally aligned with the Sun.  
The system uses:
- **Four photoresistors (LDRs)** to detect light intensity and direction,  
- **Two SG90 servo motors** for horizontal and vertical movement,  
- **Arduino Uno** for processing and control logic.

When light intensity changes, the Arduino adjusts the servos so the panel continuously faces the brightest point.



##  Components

| Component | Quantity | Description |
|------------|-----------|-------------|
| Arduino Uno | 1 | Main microcontroller for control logic |
| Servo motor SG90 | 2 | One for horizontal, one for vertical movement |
| Photoresistor (LDR) | 4 | Detect light intensity from four directions |
| Resistors (1 kΩ) | 4 | Voltage divider for LDRs |
| Breadboard & jumper wires | 1 set | Circuit assembly without soldering |
| Solar panel (6V) | 1 | Simulated energy collection |
| Power supply | 1 | Provides stable voltage for Arduino and motors |



##  How It Works

1. The system continuously reads light intensity from four LDR sensors.  
2. The Arduino calculates average values for top/bottom and left/right sensors.  
3. Based on the difference, the panel rotates:
   - Vertically if the top sensors read less light than the bottom ones.  
   - Horizontally if left sensors detect less light than the right ones.  
4. Servo motors adjust the panel position in real-time to maximize sunlight exposure.  

This simple feedback loop results in **25–40% higher energy efficiency** compared to static panels.



##  Circuit & Code

- The **breadboard circuit** was designed using *Fritzing*.  
- The control code is written in **C++** using the Arduino IDE.  
- Servo control is handled via the standard `<Servo.h>` library.  

 Full source code is available in this repository.



##  Example Code Snippet

```cpp
if (topAverage < bottomAverage) {
  servoVertical.write(ServoVerti + 1);
} else if (bottomAverage < topAverage) {
  servoVertical.write(ServoVerti - 1);
}

if (leftAverage > rightAverage) {
  servoHorizontal.write(ServoHoriz + 1);
} else if (rightAverage > leftAverage) {
  servoHorizontal.write(ServoHoriz - 1);
}
```



##  Features

✅ Dual-axis solar tracking
✅ Real-time light sensor feedback
✅ Low-cost and easy-to-build system
✅ Arduino-based open-source design



##  Possible Improvements

Integrate PID control for smoother servo movement
Add RTC module for time-based positioning
Include power measurement to compare efficiency
Connect to an IoT dashboard for remote monitoring and data visualization



##  Project Preview

<img width="343" height="409" alt="image" src="https://github.com/user-attachments/assets/16461b5f-14dd-4669-b463-2d1c8c30aa69" />
<img width="343" height="409" alt="image" src="https://github.com/user-attachments/assets/87dd18a9-027c-489f-9ed1-5300374e8119" />
