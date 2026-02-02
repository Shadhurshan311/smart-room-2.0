# 🏠 Smart Room 2.0 – IoT‑Based Room Automation System

## 📌 Project Overview

**Smart Room 2.0** is an IoT‑based room automation system designed using **ESP32**, **MQTT**, and **Node‑RED** to enable real‑time environmental monitoring and intelligent control of room appliances. The system continuously measures **temperature and humidity** using a DHT22 sensor and allows both **automatic** and **manual** control of devices such as a fan, LED lighting, and NeoPixel RGB ambient lights.

This project demonstrates a complete IoT workflow—from sensor data acquisition and wireless communication to dashboard‑based visualization and control—making it well suited for **academic demonstrations, IoT mini projects, and undergraduate final‑year projects**.

---

## ✨ Key Features

* 🌡️ **Real‑Time Environmental Monitoring**
  Live temperature and humidity sensing using DHT22

* 📊 **Interactive Dashboard Visualization**
  Real‑time gauges and controls via Node‑RED

* 🌀 **Smart Fan Control**

  * Automatic operation based on sensor thresholds
  * Manual override through dashboard

* 💡 **LED Lighting Control**
  Simple ON/OFF switching

* 🌈 **NeoPixel RGB Lighting**
  Color selection via Node‑RED color picker

* 🔄 **AUTO / MANUAL Mode Switching**
  Manual mode takes priority over automation

* 📡 **MQTT‑Based Communication**
  Reliable publish/subscribe messaging between ESP32 and Node‑RED

---

## 🧠 System Architecture

```
[DHT22 Sensor]
        ↓
      ESP32
        ↓   (MQTT Publish)
   Node‑RED Dashboard
        ↑   (MQTT Subscribe)
[Fan / LED / NeoPixel]
```

The ESP32 acts as the edge device, publishing sensor data to the MQTT broker while subscribing to control commands issued from the Node‑RED dashboard.

---

## 🔧 Hardware Components

| Component     | Description                    |
| ------------- | ------------------------------ |
| ESP32         | Main IoT controller            |
| DHT22         | Temperature & humidity sensor  |
| Servo Motor   | Used to simulate fan operation |
| LED           | Room light indicator           |
| NeoPixel Ring | RGB ambient lighting           |

⚠️ **Note:** In the Wokwi simulation environment, a **servo motor** is used to represent the fan operation (0° = OFF, 180° = ON).

---

## 🔌 GPIO Pin Configuration

| Device       | ESP32 GPIO |
| ------------ | ---------- |
| DHT22 Data   | GPIO 15    |
| Fan (Servo)  | GPIO 18    |
| LED          | GPIO 2     |
| NeoPixel DIN | GPIO 4     |

---

## 📡 MQTT Topic Structure

### ESP32 → Node‑RED

* `room/temperature`
* `room/humidity`

### Node‑RED → ESP32

* `room/mode` → `AUTO` / `MANUAL`
* `room/fan` → `ON` / `OFF`
* `room/led` → `ON` / `OFF`
* `room/neopixel` → `{ "r":255, "g":0, "b":0 }`

---

## 🖥️ Node‑RED Dashboard Components

**Gauges**

* Temperature (°C)
* Humidity (%)

**Controls**

* AUTO / MANUAL mode switch
* Fan ON / OFF switch
* LED ON / OFF switch
* NeoPixel RGB color picker

---

## 🧠 Control Logic

### 🔹 Automatic Mode

* Fan turns **ON** when:

  * Temperature exceeds a predefined threshold **OR**
  * Humidity exceeds a predefined threshold
* Fan turns **OFF** when values fall below thresholds

### 🔹 Manual Mode

* Fan and lighting are controlled directly from Node‑RED
* Sensor values do not affect device states
* **Manual mode has higher priority** than automatic mode

---

## 🛠️ Software & Tools Used

* **ESP32** (Arduino Framework)
* **Node‑RED**
* **MQTT Broker** (Mosquitto)
* **Wokwi Simulator**

**Libraries:**

* DHT Sensor Library
* PubSubClient
* ESP32Servo
* Adafruit NeoPixel

---

## 🎓 Academic Relevance

This project demonstrates key concepts in:

* IoT system architecture
* MQTT‑based publish/subscribe communication
* Real‑time sensor data acquisition and visualization
* Embedded control logic (AUTO vs MANUAL modes)
* Smart home and room automation systems

---

## 🚀 Future Enhancements

* Fan speed control using PWM
* Mobile or web app integration
* Secure MQTT with authentication and TLS
* Data logging and analytics
* Voice assistant integration

---

## 👤 Author

**Shadhurshan Navaretnam**

`Electrical & Electronic Engineering` |
`University of Peradeniya, Sri Lanka`

---

⭐ *If you find this project useful, feel free to explore the repository and suggest improvements!*
