# ESP32
A public showing of my ESP32 mini projects
# ESP32 Wi-Fi Weather Station (1602 LCD)

A compact weather station project built using an ESP32 microcontroller and a standard 1602A LCD screen. The system connects to a local Wi-Fi network, fetches real-time outdoor temperature data from the Open-Meteo REST API, and displays it on the screen.

---

## Hardware Requirements

| Component | Quantity | Description / Role |
| :--- | :---: | :--- |
| **ESP32 Development Board** | 1 | 38-pin version (or standard ESP-WROOM-32 with breakout board) |
| **1602A LCD Display** | 1 | Standard 16x2 character display operating in 4-bit mode |
| **10K Potentiometer** | 1 | Used for manual display contrast adjustment |
| **Breadboard & Jumper Wires** | - | Male-to-male and male-to-female jumper wires |
| **Micro-USB / USB-C Cable** | 1 | Power supply and programming connection |

---

## Circuit Wiring Pinout

### 1602A LCD to ESP32 / Power Rails

| LCD Pin | Label | Connection Target | Description |
| :---: | :---: | :--- | :--- |
| **1** | VSS | **GND Rail** (Blue) | System ground |
| **2** | VDD | **5V / VIN Rail** (Red) | Main power input (+5V) |
| **3** | V0 | **Center Pin of Potentiometer** | Display contrast control |
| **4** | RS | **ESP32 GPIO 19** (P19) | Register Select pin |
| **5** | RW | **GND Rail** (Blue) | Read/Write control (GND for Write mode) |
| **6** | E | **ESP32 GPIO 23** (P23) | Enable pin |
| **7–10**| D0–D3 | Unconnected | Unused in 4-bit parallel mode |
| **11** | D4 | **ESP32 GPIO 18** (P18) | Data Bit 4 |
| **12** | D5 | **GPIO 17** (P17) | Data Bit 5 |
| **13** | D6 | **GPIO 16** (P16) | Data Bit 6 |
| **14** | D7 | **GPIO 15** (P15) | Data Bit 7 |
| **15** | A | **5V / VIN Rail** (Red) | Backlight Anode (+) |
| **16** | K | **GND Rail** (Blue) | Backlight Cathode (-) |

### 10K Potentiometer

- **Left Pin:** GND Rail
- **Right Pin:** 5V Rail
- **Center Pin:** LCD Pin 3 (V0)

---

## Software Prerequisites

- **Arduino IDE** (version 1.8.x or 2.x)
- **ESP32 Board Manager Package** installed within Arduino IDE.
- Required built-in libraries (included with the ESP32 board package):
  - `WiFi.h` (Handles Wi-Fi connections)
  - `HTTPClient.h` (Handles HTTP GET requests)
  - `LiquidCrystal.h` (Drives the 1602 LCD interface)

---

## Installation and Configuration

1. Clone or download the repository containing the `.ino` file.
2. Open the file in **Arduino IDE**.
3. Select your target board under **Tools > Board > ESP32 Arduino > ESP32 Dev Module**.
4. Select the corresponding serial communication port under **Tools > Port**.
5. Update the Wi-Fi credentials and geographic coordinates in the code:

```cpp
const char* ssid     = "YOUR_WIFI_SSID";
const char* password = "YOUR_WIFI_PASSWORD";

// GPS Coordinates for target location (e.g., Vrnjacka Banja, Serbia)
String latitude  = "43.62";
String longitude = "20.90";
