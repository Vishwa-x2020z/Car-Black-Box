# 🚗 Car Black Box — Vehicle Event Recorder on PIC Microcontroller

> A PIC microcontroller-based vehicle event logger that records speed, gear shifts, and collision events using UART and I2C protocols — with a secure menu-driven interface and Real Time Clock.

---

## 🔍 Overview

This project replicates core **automotive black box functionality** on a PIC microcontroller. It logs critical driving events to non-volatile memory, timestamps them using an RTC, and provides a password-protected CLI to view, download, or clear the log.

Built as part of the Advanced Embedded Systems program at Emertxe (Govt. of India certified).

---

## 🛠️ Tech Stack

| Component | Role |
|---|---|
| PIC Microcontroller | Main controller (MPLAB X IDE) |
| ADC | Speed signal acquisition |
| Timers | Event timing, debounce |
| I2C (DS1307 RTC) | Timestamping events |
| UART | Serial log download to PC |
| CLCD (16x2) | User interface display |
| EEPROM | Non-volatile event log storage |

---

## ⚙️ System Architecture

```
Vehicle Signals (Speed / Gear / Collision)
          │
          ▼
     ADC + Digital I/O
          │
          ▼
     Event Detection Engine
          │
     ┌────┴────┐
     │         │
  RTC (I2C)  EEPROM Log
  Timestamp   Storage
     │         │
     └────┬────┘
          │
     UART Output ──► PC Serial Monitor
          │
     CLCD Display ──► Menu Interface
```

---

## 📂 Project Structure

```
car-black-box/
├── src/
│   ├── main.c             # Main loop, event detection
│   ├── adc.c              # Speed sensor ADC reading
│   ├── uart.c             # Serial communication (log download)
│   ├── i2c.c              # I2C driver for RTC
│   ├── rtc.c              # DS1307 RTC interface
│   ├── eeprom.c           # Log read/write to EEPROM
│   └── lcd.c              # CLCD 16x2 display driver
├── include/
│   └── config.h           # Pin mapping, thresholds
├── Makefile
└── README.md
```

---

## 🚀 Getting Started

### Requirements
- MPLAB X IDE + XC8 Compiler
- PICkit 3/4 programmer
- Proteus (for simulation)

### Build & Flash
```bash
# Open project in MPLAB X IDE
# Build: Production → Make and Program Device
# Or using command line:
make all
```

---

## 📋 Menu Interface (CLCD)

```
===== BLACK BOX MENU =====
1. View Log
2. Download Log (UART)
3. Clear Log
4. Set Time (RTC)
5. Exit
Enter PIN: ****
```

---

## 📊 Features

- ✅ **Event logging:** Speed threshold breach, gear change, collision impact
- ✅ **Timestamps:** All events tagged with RTC date/time (DS1307 via I2C)
- ✅ **Secure access:** PIN-protected menu to prevent tampering
- ✅ **UART download:** Log export to PC via serial terminal (115200 baud)
- ✅ **EEPROM storage:** Persistent log survives power loss

---

## 👤 Author

**Vishwanath Goroshi**  
📧 vishwa.goroshi@gmail.com | 📍 Bangalore, India
