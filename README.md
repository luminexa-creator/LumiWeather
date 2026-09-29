🌤️ LumiWeather

"LumiWeather" (https://img.shields.io/badge/Project-LumiWeather-blue)
"ESP32" (https://img.shields.io/badge/Board-ESP32-green)
"Language" (https://img.shields.io/badge/Language-Arduino%20C%2B%2B-orange)
"Display" (https://img.shields.io/badge/Display-OLED%20SH1106-purple)
"API" (https://img.shields.io/badge/Weather%20API-Meteo-blue)
"Status" (https://img.shields.io/badge/Status-Active-success)

LumiWeather is an ESP32-based weather information device designed to display weather data for Tanzania, Kenya, and Uganda using a weather API.

The project connects to a Wi-Fi network, retrieves weather information from the API, and displays the results on a 1.3-inch SH1106 OLED display.

A single physical button allows the user to switch between the supported countries.

---

📌 Project Overview

LumiWeather was created as a simple embedded weather station that combines:

- 🌐 Wi-Fi connectivity
- ☁️ Weather API data
- 🖥️ OLED display
- 🔘 Physical button control
- ⚡ ESP32 microcontroller

The main goal is to create a compact device that can provide weather information without requiring a smartphone or computer.

---

✨ Features

- 🌍 Multi-country weather information
  
  - Tanzania 🇹🇿
  - Kenya 🇰🇪
  - Uganda 🇺🇬

- 📡 Wi-Fi connectivity
  
  - ESP32 connects to a configured Wi-Fi network.

- 🌦️ Weather API integration
  
  - Retrieves weather information through a Meteo weather API.

- 🖥️ OLED display
  
  - Uses a 1.3-inch SH1106 OLED display to present weather information.

- 🔘 One-button country switching
  
  - Press the button once to switch to the next country.

---

🧰 Hardware Requirements

Component| Quantity| Purpose
ESP32 Dev Board| 1| Main microcontroller
1.3" SH1106 OLED| 1| Weather information display
Push Button| 1| Change selected country
Jumper Wires| As required| Connections
USB Cable| 1| Programming and power

---

💻 Technologies Used

Technology| Purpose
ESP32| Main controller and Wi-Fi
Arduino C++| Firmware development
SH1106 OLED| Display interface
Meteo Weather API| Weather data
HTTP/HTTPS| API communication
JSON| Processing API responses

---

🔌 How It Works

The basic operation of LumiWeather is:

             ┌──────────────────┐
             │    Wi-Fi Router  │
             └────────┬─────────┘
                      │
                      │ Internet
                      ▼
             ┌──────────────────┐
             │   Meteo Weather  │
             │       API        │
             └────────┬─────────┘
                      │
                  Weather Data
                      │
                      ▼
             ┌──────────────────┐
             │      ESP32       │
             │                  │
             │  Wi-Fi + API     │
             │  Processing      │
             └───────┬─────┬────┘
                     │     │
                  I²C│     │GPIO
                     │     │
                     ▼     ▼
              ┌─────────┐ ┌─────────┐
              │ SH1106  │ │ Button  │
              │  OLED   │ │         │
              └─────────┘ └─────────┘

Operating Flow

Power ON
   ↓
ESP32 starts
   ↓
Connect to Wi-Fi
   ↓
Request weather data
   ↓
Receive API response
   ↓
Process weather data
   ↓
Display information on OLED
   ↓
Button pressed?
   ├── No → Continue displaying current country
   │
   └── Yes → Change country
                  ↓
            Request new data
                  ↓
            Update OLED

---

⚙️ Setup & Installation

1. Prepare the Arduino IDE

Install the required ESP32 board support and libraries needed by the project.

The exact libraries may depend on the current version of the LumiWeather source code.

---

2. Configure Wi-Fi

Open the LumiWeather source code and find the Wi-Fi configuration section.

Example:

const char* WIFI_SSID = "YOUR_WIFI_NAME";
const char* WIFI_PASSWORD = "YOUR_WIFI_PASSWORD";

Replace:

YOUR_WIFI_NAME

with your Wi-Fi network name.

Replace:

YOUR_WIFI_PASSWORD

with your Wi-Fi password.

«⚠️ Do not upload your real Wi-Fi password or private API credentials to a public GitHub repository.»

---

3. Connect the Hardware

Connect the SH1106 OLED display to the ESP32 using the appropriate I²C pins.

The button should be connected to a GPIO pin configured by the LumiWeather firmware.

Example configuration:

#define OLED_SDA 21
#define OLED_SCL 22
#define BUTTON_PIN 4

«The exact GPIO pins may be changed depending on your hardware configuration.»

---

4. Upload the Firmware

Connect the ESP32 to your computer using USB.

Select the correct:

Board: ESP32 Dev Module
Port: Your ESP32 COM Port

Then compile and upload the LumiWeather firmware.

---

▶️ How to Use

After uploading the firmware:

Step 1 — Power the ESP32

Turn on the ESP32 and wait for it to connect to the configured Wi-Fi network.

Step 2 — View Weather Information

The OLED display will show the weather information retrieved from the Meteo API.

Step 3 — Change Country

Press the button once to switch to the next country.

The device cycles through:

Tanzania
   ↓
Kenya
   ↓
Uganda
   ↓
Tanzania
   ↓
...

---

🌍 Supported Countries

Country| Supported
🇹🇿 Tanzania| ✅
🇰🇪 Kenya| ✅
🇺🇬 Uganda| ✅

---

🖥️ Display

LumiWeather uses a:

1.3-inch OLED
Controller: SH1106
Interface: I²C

Example display concept:

┌────────────────────────┐
│       LUMIWEATHER      │
├────────────────────────┤
│ 🇹🇿 TANZANIA            │
│                        │
│ Temperature: 27°C      │
│ Weather: Cloudy        │
│ Humidity: 72%          │
│                        │
│ Press Button: Change   │
└────────────────────────┘

The exact information displayed depends on the weather data provided by the API.

---

📂 Project Structure

A recommended project structure is:

LumiWeather/
│
├── LumiWeather.ino
├── README.md
├── LICENSE
│
├── src/
│   └── weather.cpp
│
├── include/
│   └── weather.h
│
└── images/
    └── lumiweather.jpg

For a simple Arduino project, the main ".ino" file can also contain the complete firmware.

---

🔐 Security

Never publish sensitive information such as:

WIFI_PASSWORD
API_KEY
PRIVATE_TOKEN

Instead, use a separate configuration file or environment-specific configuration.

For example:

const char* WIFI_SSID = "YOUR_WIFI_NAME";
const char* WIFI_PASSWORD = "YOUR_WIFI_PASSWORD";

---

🚀 Future Improvements

Possible future versions of LumiWeather could include:

- 📍 More African countries
- 🌡️ More weather parameters
- 🌧️ Rain probability
- 💨 Wind speed and direction
- 🕒 Local time and date
- 📊 Weather forecast
- 🔋 Battery-powered operation
- 🌐 Web-based configuration
- 📱 Mobile application
- 🔄 Automatic location selection
- 🎨 Improved OLED user interface

---

🧪 Project Status

Current Version: Initial Release
Status: Active Development
Platform: ESP32

LumiWeather is an ongoing embedded-systems project and may receive additional features and improvements in future versions.

---

👨‍💻 Creator

Ibrahim Salehe

🇹🇿 Tanzania

Interested in:

- Mechatronics Engineering
- Embedded Systems
- Robotics
- Electronics
- IoT
- Artificial Intelligence

---

📜 License

This project can be distributed under the license included in this repository.

If no license has been added yet, consider adding an open-source license such as the MIT License before publishing the project publicly.

---

⭐ Support the Project

If you find LumiWeather interesting, you can:

- ⭐ Star the repository
- 🍴 Fork the project
- 🛠️ Build your own version
- 💡 Suggest improvements
- 🐛 Report bugs

---

🌤️ LumiWeather

«Weather information. Simple hardware. Connected world.»
