# Programming the Standalone ATmega328P

The firmware was uploaded to the standalone **ATmega328P-PU** using an **Arduino Uno configured as an ISP (In-System Programmer)**.

## Hardware Connections

| Arduino Uno | ATmega328P |
|-------------|------------|
| D10 | RESET (Pin 1) |
| D11 | MOSI (Pin 17) |
| D12 | MISO (Pin 18) |
| D13 | SCK (Pin 19) |
| 5V | VCC (Pins 7 & 20) |
| GND | GND (Pins 8 & 22) |

> **Note:** The ATmega328P was configured to run with an external **16 MHz crystal oscillator** connected to XTAL1 and XTAL2 using two 22 pF capacitors.

---

## Programming Steps

### 1. Prepare the Arduino Uno

- Connect the Arduino Uno to your computer.
- Open the Arduino IDE.
- Upload the **ArduinoISP** example sketch.

```
File → Examples → 11.ArduinoISP → ArduinoISP
```

---

### 2. Wire the ATmega328P

Connect the Arduino Uno to the standalone ATmega328P as shown in the table above.

---

### 3. Select the Target Board

In the Arduino IDE:

```
Board: Arduino Uno
Programmer: Arduino as ISP
```

If you have installed a standalone ATmega328P board definition (such as MiniCore), select the appropriate ATmega328P board instead.

---

### 4. Burn the Bootloader (First Time Only)

If using a fresh ATmega328P, burn the bootloader to configure the fuse bits for the external 16 MHz crystal.

```
Tools → Burn Bootloader
```

---

### 5. Upload the Firmware

Instead of using the normal Upload button, use:

```
Sketch → Upload Using Programmer
```

or press:

```
Ctrl + Shift + U
```

This uploads the firmware directly through the ISP interface.

---

## Development Setup

```
+-----------------+
|   Arduino IDE   |
+--------+--------+
         |
         | USB
         |
+--------v--------+
|   Arduino Uno   |
|   ArduinoISP    |
+--------+--------+
         |
         | SPI
         |
+--------v--------+
|  ATmega328P-PU  |
|  Standalone MCU |
+-----------------+
```

---

## Development Photo

The image below shows the standalone ATmega328P being programmed using an Arduino Uno configured as an ISP programmer.

![Programming via Arduino ISP](images/Arduino_Isp.jpg)
