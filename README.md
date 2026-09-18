# ESP32 Custom Development Board

A custom **4-layer ESP32 development board** designed in **EasyEDA Pro**, featuring USB-to-Serial communication, onboard 3.3V regulation, automatic programming support, BOOT/RESET controls, status LEDs, GPIO breakout headers, and an ESP32-WROOM-32E module.

The board is designed as a compact and practical ESP32 development platform for embedded systems, IoT prototyping, firmware development, hardware experimentation, and custom electronics projects.

---

## ✨ Features

- 📡 ESP32-WROOM-32E based development board
- 🔌 USB interface for power and serial communication
- 🔄 CP2102N USB-to-UART interface
- ⚡ Onboard 5V to 3.3V voltage regulation
- 🟢 Power status LED
- 🔴 User programmable LED
- 🔘 BOOT button
- 🔄 RESET / EN button
- ⚙️ Automatic programming circuit using DTR / RTS
- 📌 Dual GPIO breakout headers
- 🧩 4-layer PCB architecture
- 🌍 Dedicated ground reference plane
- ⚡ Dedicated power distribution layer
- 📶 ESP32 antenna keepout area
- 🛡️ USB protection circuitry
- 🔧 Easy access to UART and ESP32 GPIO pins
- 🧪 Suitable for development, testing, and prototyping

---

## 🧠 Hardware Architecture

The board consists of several main functional sections:

- ESP32-WROOM-32E module
- USB connector and USB protection
- CP2102N USB-to-UART bridge
- Automatic programming circuit
- 5V to 3.3V voltage regulator
- BOOT and RESET buttons
- Power and user LEDs
- GPIO breakout headers
- Local decoupling and filtering capacitors

---

## 📡 ESP32 Module

The main controller is an **ESP32-WROOM-32E** module.

The ESP32 provides:

- Wi-Fi
- Bluetooth
- GPIO
- UART
- SPI
- I²C
- ADC
- PWM
- Timers
- Hardware interrupts
- General-purpose embedded processing

The module is positioned near the edge of the PCB to provide proper clearance for the onboard antenna.

---

## 🔌 USB Interface

The board includes a USB connector that provides:

- 5V power input
- USB data communication
- Serial programming
- Debug communication

USB data lines are connected to the onboard CP2102N USB-to-UART converter.

The USB interface also includes protection components to help protect the circuit from unwanted electrical transients.

---

## 🔄 USB-to-Serial Interface

A **CP2102N** USB-to-UART bridge provides communication between the ESP32 and a computer.

The CP2102N is used for:

- Firmware flashing
- Serial debugging
- UART communication
- Automatic BOOT / RESET control

The primary UART connection is:

    CP2102N TX  → ESP32 RX
    CP2102N RX  → ESP32 TX

This allows development environments such as Arduino IDE, PlatformIO, ESP-IDF, and esptool to communicate with the ESP32.

---

## ⚙️ Automatic Programming Circuit

The board includes an automatic programming circuit using the CP2102N.

The `DTR` and `RTS` signals are used to automatically control:

- `GPIO0`
- `EN`

This allows the ESP32 to automatically enter serial bootloader mode when firmware is uploaded.

Under normal conditions, the user does not need to manually press the BOOT and RESET buttons during programming.

---

## ⚡ Power Supply

The board can be powered through the USB connector.

The power architecture is:

    USB 5V
      │
      ▼
    5V Power Rail
      │
      ▼
    3.3V Voltage Regulator
      │
      ▼
    3.3V Power Rail
      │
      ├── ESP32
      ├── CP2102N
      ├── LEDs
      └── Peripheral Circuitry

The board includes local decoupling capacitors to improve power stability during ESP32 current spikes.

---

## 🔋 Voltage Regulation

An onboard **3.3V voltage regulator** converts the incoming 5V supply to the 3.3V required by the ESP32 and supporting circuitry.

The regulator section includes input and output capacitors to improve voltage stability.

The regulated 3.3V rail is distributed throughout the PCB using the internal power layer and local power routing.

---

## 🧩 PCB Stackup

The board uses a **4-layer PCB architecture**.

| Layer | Purpose |
|---|---|
| Layer 1 | Components + signal routing |
| Layer 2 | Ground reference plane |
| Layer 3 | Power distribution / internal routing |
| Layer 4 | Secondary signal routing |

The multilayer design helps improve:

- Signal integrity
- Ground return paths
- EMI performance
- Power distribution
- PCB routing density
- Noise reduction
- Routing flexibility

---

## 🌍 Ground Plane

A dedicated internal ground reference layer is used to provide a low-impedance return path for signals.

This helps improve:

- Signal integrity
- USB communication
- ESP32 stability
- EMI performance
- Noise reduction

Ground copper is also used where appropriate on the outer PCB layers.

---

## ⚡ Power Distribution

The internal power layer is used to distribute power throughout the board.

Important power rails include:

- `+5V`
- `+3V3`
- `GND`

Power traces and copper regions are designed to support the current requirements of the ESP32 and associated circuitry.

---

## 📶 ESP32 RF Design

The ESP32 antenna is positioned at the edge of the PCB.

The antenna region is kept clear of unnecessary:

- Copper
- Ground planes
- Power planes
- Signal traces
- Vias
- Components

The antenna extends toward the edge of the board to reduce interference from the main PCB circuitry.

This helps maintain better Wi-Fi and Bluetooth RF performance.

---

## 🔌 GPIO Headers

The development board exposes the ESP32 GPIO pins through two standard header rows.

Available signals include:

- `3V3`
- `GND`
- `EN`
- `GPIO23`
- `GPIO22`
- `GPIO21`
- `GPIO19`
- `GPIO18`
- `GPIO17`
- `GPIO16`
- `GPIO15`
- `GPIO14`
- `GPIO13`
- `GPIO12`
- `GPIO5`
- `GPIO4`
- `GPIO2`
- `GPIO0`
- `GPIO25`
- `GPIO26`
- `GPIO27`
- `GPIO32`
- `GPIO33`
- `GPIO34`
- `GPIO35`
- `GPIO36`
- `GPIO39`
- `TX`
- `RX`

> Pin availability, input-only pins, boot-strapping pins, and peripheral functions should always be verified against the ESP32-WROOM-32E datasheet before connecting external hardware.

---

## 🔘 Onboard Controls

### RESET Button

The RESET button is connected to the ESP32 `EN` pin.

Pressing the button resets the ESP32 and restarts the running firmware.

Typical use cases include:

- Restarting firmware
- Recovering from software lockups
- Manual debugging
- Entering programming sequences

### BOOT Button

The BOOT button is connected to `GPIO0`.

It allows the ESP32 to enter serial bootloader mode when required for manual firmware flashing.

A typical manual programming sequence is:

    1. Hold BOOT
    2. Press RESET
    3. Release RESET
    4. Release BOOT

The automatic programming circuit normally handles this process automatically.

---

## 💡 LEDs

The board includes onboard LEDs for basic status indication and firmware testing.

### Power LED

The power LED indicates that the 3.3V power rail is active.

This provides a simple visual indication that the board is receiving regulated power.

### User LED

A programmable user LED is connected to an ESP32 GPIO.

It can be used for:

- Firmware testing
- Status indication
- Debugging
- Connection indication
- Application feedback

Example Arduino code:

    #define LED_PIN 18

    void setup() {
        pinMode(LED_PIN, OUTPUT);
    }

    void loop() {
        digitalWrite(LED_PIN, HIGH);
        delay(500);

        digitalWrite(LED_PIN, LOW);
        delay(500);
    }

> Verify the final GPIO assignment against the schematic before using this example.

---

## 🛡️ USB Protection

The USB interface includes protection circuitry to help protect the board from transient voltage events.

The protection circuit is placed close to the USB connector to reduce the path between the connector and protection components.

This helps provide additional protection for:

- USB D+
- USB D-
- Connected ICs
- ESP32 communication circuitry

---

## 🔧 Decoupling and Filtering

Local decoupling capacitors are positioned near major ICs and power sections.

These capacitors help:

- Reduce voltage fluctuations
- Suppress high-frequency noise
- Improve power stability
- Support ESP32 current transients
- Stabilize the USB-to-UART circuitry

Bulk capacitance is also included on the power rails where required.

---

## 🛠️ Design Software

The complete hardware design was created using:

**EasyEDA Pro**

The design process includes:

- Schematic capture
- Component selection
- Footprint assignment
- PCB layout
- 4-layer routing
- Copper pours
- Ground and power planes
- Component placement
- Design-rule verification
- 3D PCB visualization

---

## 🔧 Firmware Compatibility

The board can be programmed using common ESP32 development environments.

Supported development environments include:

- Arduino IDE
- PlatformIO
- ESP-IDF
- esptool

---

## Arduino IDE

The board can be programmed using the Arduino IDE with the ESP32 board package installed.

Typical workflow:

    1. Install Arduino IDE
    2. Install the Espressif ESP32 board package
    3. Connect the board through USB
    4. Select the appropriate ESP32 board
    5. Select the CP2102 serial port
    6. Compile the firmware
    7. Upload

---

## PlatformIO

Example `platformio.ini` configuration:

    [env:esp32dev]
    platform = espressif32
    board = esp32dev
    framework = arduino
    monitor_speed = 115200

PlatformIO can be used with:

- Visual Studio Code
- Arduino framework
- ESP-IDF
- Serial Monitor
- Library management
- Debugging tools

---

## ESP-IDF

The board is also compatible with Espressif's official **ESP-IDF** framework.

ESP-IDF can be used for:

- Low-level ESP32 development
- FreeRTOS applications
- Wi-Fi applications
- Bluetooth applications
- IoT development
- Networking
- Embedded security
- Production firmware

---

## 🚀 Programming

Connect the board to a computer through the onboard USB connector.

The CP2102N USB-to-UART interface should appear as a serial communication device.

A basic connection test can be performed using:

    esptool.py --chip esp32 flash_id

Firmware can then be uploaded using:

- Arduino IDE
- PlatformIO
- ESP-IDF
- esptool

The automatic programming circuit controls `EN` and `GPIO0` using the USB-to-UART interface, allowing firmware uploads without manually pressing the BOOT button under normal conditions.

---

## 🧪 Basic Firmware Test

A simple LED blink program can be used as an initial board test.

    #define LED_PIN 18

    void setup() {
        Serial.begin(115200);
        pinMode(LED_PIN, OUTPUT);

        Serial.println("ESP32 Custom Development Board");
    }

    void loop() {
        digitalWrite(LED_PIN, HIGH);
        delay(500);

        digitalWrite(LED_PIN, LOW);
        delay(500);
    }

---

## 🧪 Hardware Verification

Before manufacturing or assembling the board, verify:

- ✅ Schematic ERC
- ✅ PCB DRC
- ✅ No unrouted nets
- ✅ Correct net assignments
- ✅ Ground-plane continuity
- ✅ Correct 3.3V power routing
- ✅ Correct 5V power routing
- ✅ USB D+ / D− routing
- ✅ ESP32 antenna keepout
- ✅ CP2102N footprint orientation
- ✅ ESP32 module orientation
- ✅ Voltage regulator orientation
- ✅ Header pin numbering
- ✅ BOOT button operation
- ✅ RESET button operation
- ✅ Automatic programming circuit
- ✅ Component polarity
- ✅ Gerber files
- ✅ Drill files
- ✅ Board outline
- ✅ Solder-mask openings
- ✅ Silkscreen alignment

It is also recommended to inspect the generated Gerber files using an independent Gerber viewer before ordering the PCB.

---

## 🔎 Recommended Electrical Checks

Before powering the first assembled prototype, verify:

    USB 5V → Voltage Regulator Input
    Voltage Regulator Output → 3.3V
    3.3V → ESP32 VCC
    GND → ESP32 GND
    CP2102 TX → ESP32 RX
    CP2102 RX → ESP32 TX
    DTR / RTS → Automatic Programming Circuit
    Automatic Programming Circuit → EN / GPIO0

Also check for shorts between:

    5V ↔ GND
    3.3V ↔ GND
    5V ↔ 3.3V

---

## 📸 Board Preview

### 3D  View
<img width="1552" height="514" alt="Screenshot 2026-09-18 144637" src="https://github.com/user-attachments/assets/06051acf-449b-4531-a7c7-c8fecfd62f1d" />
<img width="1145" height="696" alt="image" src="https://github.com/user-attachments/assets/82b1b0f2-5be2-4479-a634-d3a0f5891275" />
<img width="1087" height="686" alt="image" src="https://github.com/user-attachments/assets/921e509d-c22c-41c4-b992-89c4771ba631" />
<img width="1546" height="529" alt="image" src="https://github.com/user-attachments/assets/c8553f3b-c169-4d42-a510-3b3947221544" />
<img width="1099" height="387" alt="image" src="https://github.com/user-attachments/assets/df1cf273-8fe7-4902-a351-2505fac46bd2" />
<img width="1541" height="536" alt="image" src="https://github.com/user-attachments/assets/2469dbd6-19ef-4e5a-a351-a4ff3f849114" />



### PCB Top Layer

<img width="1472" height="508" alt="image" src="https://github.com/user-attachments/assets/b8f80600-42a1-4d49-a7f6-13448fa9daa9" />


### PCB Bottom Layer

<img width="1452" height="484" alt="image" src="https://github.com/user-attachments/assets/f0da1fe5-e7e4-4522-8fa2-9af86309f876" />


### Inner Layer 1

<img width="1452" height="493" alt="image" src="https://github.com/user-attachments/assets/509b808a-d28e-4597-8db1-849378a393e2" />

### Inner Layer 2

<img width="1546" height="529" alt="image" src="https://github.com/user-attachments/assets/4f6c19ba-394e-4fa8-bb55-ab4a839a0494" />


### Schematic

<img width="1138" height="809" alt="Screenshot 2026-09-18 144612" src="https://github.com/user-attachments/assets/81e7487d-1f23-42f6-99c0-b0dd0baad438" />


---

## 🏗️ PCB Design Overview

The PCB was designed with emphasis on:

- Compact component placement
- Short critical signal paths
- Stable power distribution
- Continuous ground references
- USB signal routing
- RF antenna clearance
- Accessible GPIO headers
- Easy firmware programming
- Practical prototyping
- Clean mechanical layout

---

## 📐 Design Considerations

### Signal Integrity

Signal traces are routed with attention to:

- Return paths
- Trace spacing
- Via placement
- Layer transitions
- Ground referencing

### Power Integrity

The board includes:

- Dedicated power routing
- Ground plane
- Local decoupling capacitors
- Bulk capacitance
- Short power paths

These help provide stable power to the ESP32 during Wi-Fi and Bluetooth activity.

### RF Performance

The ESP32 antenna region is kept away from unnecessary copper and components.

The module is positioned near the PCB edge so that the onboard antenna can operate with reduced interference from the main PCB.

### USB Routing

USB D+ and D− traces are routed together between the USB connector and CP2102N.

The USB protection components are placed close to the connector.

---

## 🏭 Manufacturing

Before sending the design for manufacturing, generate and verify:

- Gerber files
- NC drill files
- Board outline
- Copper layers
- Solder mask
- Silkscreen
- Paste layers if assembly is required

Recommended workflow:

    EasyEDA Pro
       │
       ▼
    Run DRC
       │
       ▼
    Rebuild Copper Areas
       │
       ▼
    Generate Gerbers
       │
       ▼
    Inspect Gerbers
       │
       ▼
    Prototype Manufacturing
       │
       ▼
    Assembly
       │
       ▼
    Electrical Testing

---

## ⚠️ Project Status

This project is currently a **custom hardware development and prototype platform**.

The design should be independently verified before production use.

Important areas to verify include:

- Electrical design
- Component footprints
- PCB manufacturing constraints
- Power integrity
- USB connectivity
- ESP32 boot configuration
- RF antenna clearance
- Thermal performance
- Mechanical dimensions
- Component availability

It is recommended to manufacture and test prototype units before committing to large-scale production.

---

## 📋 Future Improvements

Possible future improvements include:

- USB-C connector support
- Improved power regulation
- Additional protection circuitry
- Additional onboard sensors
- Battery input
- Li-ion charging support
- Additional debugging headers
- Dedicated JTAG connector
- Additional test points
- Improved RF optimization
- Smaller board revision

---

## 🤝 Contributions

Contributions are welcome.

Possible contributions include:

- Hardware improvements
- PCB routing improvements
- Documentation updates
- Firmware examples
- Power-supply improvements
- ESP32 application examples
- Testing results
- Manufacturing feedback

To contribute:

1. Fork the repository
2. Create a new branch
3. Make your changes
4. Commit the changes
5. Push the branch
6. Open a pull request

---

## 📜 License

This project is licensed under the **MIT License**.

You are free to use, copy, modify, merge, publish, distribute, sublicense, and build upon this project under the terms of the MIT License.

See the [`LICENSE`](LICENSE) file for the full license text.

---

## 👨‍💻 Author

**Fernando S.M.H.G.**

Hardware Design • PCB Development • Embedded Systems • IoT

Designed using **EasyEDA Pro**.

---

## ⭐ Support

If you find this project useful, consider giving the repository a **⭐ Star**.

It helps support future:

- Hardware revisions
- Firmware examples
- PCB improvements
- Documentation updates
- ESP32 development projects

---

## 🧠 Technologies

`ESP32` • `ESP32-WROOM-32E` • `CP2102N` • `EasyEDA Pro` • `PCB Design` • `Embedded Systems` • `IoT` • `UART` • `Wi-Fi` • `Bluetooth`

---

### 🛠️ ESP32 Custom Development Board

**Designed for learning, prototyping, embedded development, and IoT experimentation.** 📡⚡
