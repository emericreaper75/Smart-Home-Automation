# Smart Home Automation System Using NodeMCU and Sensor Integration  

**By:** Amavasya Manoj Kumar Reddy  

---

## ABSTRACT

The Smart Home Automation System designed in this project aims to promote comfort, efficiency, and security through the integration of smart control of important home appliances and systems. Integrated around the NodeMCU ESP8266 microcontroller that has both general input/output functionality and Wi-Fi, the system manages lighting, motion, temperature sensing, and simple physical actuation.  

The utilization of low-cost sensors like the Light Dependent Resistor (LDR) and an LM393 comparator, IR motion sensors (TSSP58038), and NTC thermistors enables the NodeMCU to sense real-time conditions and make decisions regarding appliance control.  

- Variation in ambient light intensity can automatically switch on lighting systems.
- Motion detection can activate alarms or servo motors to mimic door movement.
- NTC thermistor readings allow temperature-based actions such as starting fans or sending alerts.
- Manual override is possible through push buttons.
- Real-time wireless control via IoT protocols like HTTP and MQTT supports smartphone/computer monitoring.

Overall, this system demonstrates how affordable and programmable hardware can transform homes into smart living spaces, with scalability for AI, voice assistants, cloud, and more.

---

## INTRODUCTION

Advances in embedded systems and the Internet of Things (IoT) have revolutionized the way humans interact with their homes. “Smart home” now implies an interactive environment where appliances react dynamically based on:

- User commands
- Environmental conditions
- Scheduling
- Remote control

This system focuses on **low-cost, scalable, and dependable** automation.  
The NodeMCU ESP8266 serves as the project’s core, offering:

- Built-in Wi-Fi
- Digital and analog interfaces
- Low power consumption
- Arduino IDE compatibility

**Sensors used:**
- LDR with LM393 comparator
- NTC temperature sensor
- IR motion sensor

**Outputs:**
- LEDs
- Buzzers
- Servo motor

Control can be **local (push button)** or **remote (web/mobile over Wi-Fi)**.

---

## SYSTEM DESIGN

The system is structured into **three subsystems**:

### 1. Input Sensing
- **LDR + LM393 Comparator**: Detects ambient light changes, triggers lights when below threshold.
- **IR Motion Sensor (TSSP58038)**: Detects movement and triggers security actions.
- **NTC Thermistor**: Reads analog temperature data via NodeMCU’s ADC (A0).
- **Push Buttons**: Allows manual override.

### 2. Processing & Control
- NodeMCU processes inputs via Arduino C/C++ code.
- Conditional logic controls outputs.
- Debouncing ensures clean button input.

### 3. Outputs/Actuators
- **LEDs** for status/light automation.
- **Buzzer** for alerts.
- **Servo Motor** for door simulation.
- **Wireless control** (HTTP/Blynk/MQTT).

---

## HARDWARE IMPLEMENTATION

- **NodeMCU ESP8266**
- Breadboard & regulated **5V power supply**
- Resistors, capacitors, potentiometers, jumper wires
- **LM393 comparator** generates digital output from LDR
- Potentiometer adjusts threshold sensitivity

---

## SOFTWARE IMPLEMENTATION

- **Arduino IDE** with standard C/C++ and ESP8266 libraries
- Functions used:
  - `digitalRead()`, `digitalWrite()` – Read/write digital pins
  - `analogRead()` – Read thermistor voltage
  - `Servo.attach()`, `Servo.write()` – Servo control
  - `ESP8266WiFi.h` – Wi-Fi connectivity
  - Optional: `ESP8266WebServer.h` or `PubSubClient.h`

**Core Arduino Code** (expect, full code in project files):

#include <Servo.h>

// Pin Definitions
#define IR_PIN D2
#define RED_LED D8       
#define BUZZ D5
#define GREEN_LED D3        
#define SERVO_PIN D4
#define BUTTON_PIN D7     
#define TOGGLE_PIN D6      
#define BLUE_LED D0
#define LDR_DO D1 

void setup() {
  Serial.begin(115200);

  pinMode(IR_PIN, INPUT);
  pinMode(RED_LED, OUTPUT);
  pinMode(BUZZ, OUTPUT);
  pinMode(GREEN_LED, OUTPUT);
  pinMode(BLUE_LED, OUTPUT);
  pinMode(LDR_DO, INPUT);
  pinMode(BUTTON_PIN, INPUT_PULLUP);
  pinMode(TOGGLE_PIN, INPUT_PULLUP);

  myServo.attach(SERVO_PIN);
  myServo.write(90); // Neutral position

  Serial.println("🔧 System Initialized");
  delay(1000);
}
---

## RESULTS

### Observations:
- **LDR module**: Correctly turned LEDs on/off with light changes.
- **IR sensor**: Detected motion up to 2m reliably.
- **Thermistor**: Calibrated readings converted to °C.
- **Servo motor**: Smooth, accurate position control.
- LEDs and buzzers worked as intended.

---

## DISCUSSION

Strengths:
- Low-cost, responsive system.
- Multiple sensor integration.
- Effective threshold-based automation.
- Stable NodeMCU performance with Wi-Fi.

Challenges:
- Analog noise from thermistor.
- Adjusting comparator thresholds.
- Servo calibration.
- Button debounce tuning.

---

## APPLICATIONS

- **Residential Homes**: Automated lighting, temperature control, and security.
- **Offices/Institutions**: Energy management.
- **Hospitals/Elder Care**: Fall detection, emergency alerts.
- **Hotels**: Automated room access and comfort controls.
- **Retail Shops**: Security alerts, temperature monitoring.

---

## CONCLUSION

The NodeMCU-based Smart Home Automation System is:
- Real-time
- Scalable
- Cost-effective
- Energy efficient

It integrates light, heat, and motion detection with automated responses. The system’s design makes it practical for real-world IoT applications.

---

## FUTURE SCOPE

Potential enhancements:
- **Smartphone App Integration** (MIT App Inventor, Flutter)
- **Cloud Storage** (Firebase, ThingSpeak)
- **Voice Assistant Support** (Alexa, Google Home)
- **Security Cameras**
- **Machine Learning-based automation**
- **Solar-powered backup**

---

**End of Report**
