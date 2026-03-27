
---
layout: default
title: ESP32-CAM Smart Door Lock System
---

# 🔐 ESP32-CAM Smart Door Lock System  
### *Face Recognition + Email Notification + IoT Security*
> 🎓 Major Project | Electronics & Communication Engineering  
> 📍 RV Institute of Technology and Management, Bengaluru  
> 📅 Academic Year: 2025–2026  

---

## 📌 Overview

This project presents an **AI-powered smart access control system** using the ESP32-CAM module.  
It utilizes **face recognition technology** to automatically unlock doors for authorized users.

For unknown individuals, the system enhances security by sending an **email alert with captured images**, enabling remote monitoring and decision-making.

🔗 **Project Repository:**  
👉 Click here to view the source code:  
[Click here](https://github.com/Shrujan138/ESP32-CAM-Face-Recognition-Smart-Door-Lock-System-With-Email-Notification)  

---

## ✨ Key Features

- 🔍 Face Detection & Recognition  
- 🔓 Automatic Door Unlock for Authorized Users  
- 📧 Email Alerts for Unknown Visitors  
- 🌐 Remote Access Monitoring  
- 🚪 Door Status Detection (MC38 Sensor)  
- 🖥 LCD Display Output  
- 📡 Live Video Streaming via Web Interface  

---

## 🏗 System Architecture


Person → Camera → Face Detection → Face Recognition → Decision

IF Recognized → Unlock Door → Display Name
IF Unknown → Send Email → Owner Decision → Allow/Deny


---

## 🔌 Hardware Components

| Component        | Quantity |
|-----------------|----------|
| ESP32-CAM       | 1        |
| Relay Module    | 1        |
| Solenoid Lock   | 1        |
| MC38 Sensor     | 1        |
| LCD Display     | 1        |

---

## 🔗 Pin Configuration

### 🔹 Relay Connection

| ESP32 Pin | Component |
|----------|----------|
| GPIO 2   | Relay IN |
| 5V       | VCC      |
| GND      | GND      |

### 🔹 Door Sensor (MC38)

| ESP32 Pin | Sensor |
|----------|--------|
| GPIO 12  | Output |
| GND      | GND    |

### 🔹 LCD (I2C)

| ESP32 Pin | LCD |
|----------|-----|
| GPIO 14  | SDA |
| GPIO 15  | SCL |

---

## 💻 Software Setup

### 🔧 ESP32 Board Manager URL


Click here to view the source code:  
[Click here](https://dl.espressif.com/dl/package_esp32_index.json)


### 📚 Required Libraries

- ArduinoWebsockets  
- ESP Mail Client  
- LiquidCrystal_I2C  
- ESP32 Camera  

---

## 📶 WiFi Configuration

```cpp
const char* ssid = "YOUR_WIFI_NAME";
const char* password = "YOUR_WIFI_PASSWORD";
📧 Email Configuration
#define SMTP_HOST "smtp.gmail.com"
#define SMTP_PORT 465
#define AUTHOR_EMAIL "your_email@gmail.com"
#define AUTHOR_PASSWORD "app_password"
#define RECIPIENT_EMAIL "owner_email@gmail.com"
🧠 Source Code

🔗 Main Code File:
👉 Click here to view the source code:  
[Click here](https://github.com/Shrujan138/ESP32-CAM-Face-Recognition-Smart-Door-Lock-System-With-Email-Notification/blob/main/ESP32-CAM-Face-Recognition-Smart-Door-Lock-System-With-Email-Notification-main/FaceDoorEntryESP32Cam.ino/FaceDoorEntryESP32Cam.ino)

📁 Full Project Repository:
👉 Click here to view the source code:  
[Click here](https://github.com/Shrujan138/ESP32-CAM-Face-Recognition-Smart-Door-Lock-System-With-Email-Notification)

🎮 Usage Instructions
Power on the ESP32-CAM module
Open the web interface using the device IP address
Capture and enroll authorized faces
Start real-time face recognition
Receive alerts for unknown users via email
🔐 Security Workflow
Face Detected → Match?

YES → Unlock Door  
NO  → Send Email → Owner Decision
🏭 Applications
🏠 Smart Homes
🏢 Offices
🏫 Hostels & Institutions
🔐 IoT-Based Security Systems
🚀 Future Enhancements
📱 Mobile Application Integration
☁ Cloud Database Support
🔥 Firebase Logging System
🎥 Multi-Camera Surveillance
👨‍💻 Author

Shrujan M

📧 mshrujan.28@gmail.com

🔗 Click here to view the source code:  
[Click here](https://www.linkedin.com/in/shrujan-m-804842361/)

📌 Conclusion

This project demonstrates how IoT + AI + Embedded Systems can be integrated to build a secure, intelligent, and automated access control system.
It provides a scalable solution for modern smart security applications.

