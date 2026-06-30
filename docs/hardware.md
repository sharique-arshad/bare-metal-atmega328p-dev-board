# Hardware Documentation

This project is built around a standalone **ATmega328P-PU** microcontroller instead of a complete Arduino development board. The objective was to understand the minimum hardware required to run an AVR microcontroller and interface common peripherals using I²C.

---

# Hardware Overview

The development board was assembled on a general-purpose perfboard and consists of:

- Standalone ATmega328P-PU
- 16 MHz external crystal oscillator
- SSD1306 128×64 OLED display
- MPU6050 Accelerometer & Gyroscope
- Piezo buzzer
- Status LED
- Push buttons
- ISP programming header
- Power filtering capacitors

---

# Block Diagram

```text
                +----------------------+
                |     ATmega328P       |
                |      @16 MHz         |
                +----------+-----------+
                           |
          +----------------+----------------+
          |                                 |
          ▼                                 ▼
   SSD1306 OLED                      MPU6050 IMU
      (I²C)                              (I²C)

          |
          ▼
      Piezo Buzzer

          |
          ▼
      Status LED

          |
          ▼
      Push Buttons

          |
          ▼
     Arduino ISP Header
```

---

# Components

| Component | Purpose |
|----------|---------|
| ATmega328P-PU | Main Microcontroller |
| 16 MHz Crystal | System Clock |
| 22 pF Capacitors | Crystal Oscillator Load Capacitors |
| SSD1306 OLED | Sensor Data Display |
| MPU6050 | Accelerometer & Gyroscope |
| Piezo Buzzer | Audible Alert |
| LED | Status Indicator |
| Push Buttons | User Input / Reset |
| ISP Header | Firmware Upload |
| Perfboard | Hardware Prototype |

---

# Communication Interfaces

## I²C Bus

The OLED display and MPU6050 communicate with the ATmega328P over the I²C bus.

| Signal | ATmega328P Pin |
|---------|----------------|
| SDA | PC4 (A4) |
| SCL | PC5 (A5) |

---

# Clock Circuit

The ATmega328P operates using an external 16 MHz crystal oscillator.

Required components:

- 16 MHz Crystal
- Two 22 pF ceramic capacitors

This configuration provides accurate timing for I²C communication and general firmware execution.

---

# Programming

The microcontroller was programmed using an **Arduino Uno configured as an ISP programmer**.

Development workflow:

```text
Arduino IDE
      │
      ▼
Arduino Uno (ArduinoISP)
      │
      ▼
Standalone ATmega328P
```

Firmware was uploaded using **Upload Using Programmer**, allowing the ATmega328P to be programmed directly through the ISP interface.

---

# Development Process

The project was developed in two stages:

1. Breadboard prototype for firmware development and testing
2. Final soldered implementation on a perfboard

This approach made debugging easier before permanently assembling the hardware.

---

# Power Supply

The board is designed to operate from a regulated **5 V supply**.

The ATmega328P, OLED display, and MPU6050 share a common power and ground connection.

---

# Features Demonstrated

- Standalone ATmega328P operation
- External clock configuration
- I²C communication
- OLED graphics
- MPU6050 sensor interfacing
- Arduino ISP programming
- Embedded firmware development
- Perfboard prototyping

---

# Future Improvements

- Design a custom PCB in KiCad
- Add voltage regulation on-board
- Add USB-to-Serial programming
- Add UART debugging header
- Improve PCB layout for manufacturability
- Add expansion headers for additional sensors
