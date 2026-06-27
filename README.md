# NetCanary
A local network intrusion monitor built on an ESP32-C3. NetCanary continuously scans the home network for unknown devices and alerts in real time without cloud services nor router access.

Built for the Intelligent Edge Systems summer project at USJ.
# Team

Miguel Farha · Yasmine Mansour · Youmna Hammoud

Group: Ping&Pray
# How it works

The ESP32-C3 performs periodic ARP sweeps across the local subnet, resolves responding MAC addresses, and compares them against a whitelist of known devices. Unknown MACs trigger an alert on the onboard OLED (with vendor name looked up via the macvendors.com API) and are logged with a timestamp. A lightweight web dashboard hosted directly on the ESP32 lets you view connected devices, alert history, and last-seen times from any browser on the local network; by design, no network data ever leaves the subnet.
# Hardware

    • ESP32-C3 Supermini Development Board (with 0.42-inch OLED & Ceramic Antenna)

# Software / Libraries

    Arduino IDE, ESP32 board package
    ESPAsyncWebServer : local web dashboard
    ArduinoJson : parsing macvendors.com responses
    U8g2 : OLED display driver
    lwip : raw ARP/ICMP for subnet sweeping

# Setup

    Clone the repo
    Copy config.example.h → config.h and fill in your WiFi credentials (config.h is gitignored)
    Open netcanary.ino in Arduino IDE
    Install the libraries listed above via Library Manager
    Board settings: ESP32C3 Dev Module, correct COM port, CH340 driver installed if needed
    Upload, open Serial Monitor at 115200 baud

# Repo structure

NetCanary/
├── netcanary.ino        firmware (.ino)
├── web/               dashboard frontend (HTML/CSS/JS)
├── tools/             standalone debug sketches (I2C scanner, etc.)
├── config.example.h   template — copy to config.h, never commit config.h
└── .gitignore

# Status

🚧 In progress — Week 1 of 4

    Toolchain setup, WiFi station connectivity
    I2C/OLED display, ARP sweep
    Whitelist logic, macvendors.com integration
    FSM display states, web dashboard, final integration

# Commit Convention

Short prefixes to keep history scannable:

    feat: new functionality, e.g. feat: add ARP sweep
    fix: bug fix, e.g. fix: OLED offset on 72x40 panel
    docs: documentation only
    chore: config, gitignore, non-code housekeeping

Example: feat: whitelist comparison for known MACs
# Limitations

_To be documented.
