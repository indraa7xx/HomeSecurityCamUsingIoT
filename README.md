# HomeSecurityCamUsingIoT
This Arduino sketch transforms an ESP32-CAM into a versatile, Wi-Fi-enabled security and monitoring device controlled entirely through a Telegram bot. It captures and sends images upon motion detection or user request, provides real-time temperature and humidity data, and allows for remote control of a connected light.

Telegram PIR Motion Camera with DHT11 using ESP32-CAM

This project allows you to create a smart security camera using an ESP32-CAM, a PIR motion sensor, and a DHT11 temperature/humidity sensor, all controlled via Telegram. Get instant photo alerts, check the environment, and even toggle a light!

Features
Motion Detection: Receive photo alerts on Telegram when motion is detected.
On-Demand Photos: Request photos from your ESP32-CAM directly via Telegram.
Flash Control: Take photos with or without flash.
Remote Light Control: Turn a connected light (via relay) on or off from Telegram.
Environmental Monitoring: Get temperature and humidity readings from the DHT11 sensor.
Getting Started
Prerequisites
ESP32-CAM (AI-Thinker model)
PIR Motion Sensor
DHT11 Temperature and Humidity Sensor
1-Channel Relay Module (optional, for light control)
Jumper Wires
Breadboard (optional)
Stable Wi-Fi connection
Telegram account
Software Setup
Arduino IDE: Download and install the Arduino IDE.
ESP32 Board Manager:
Open Arduino IDE, go to File > Preferences.
In "Additional Board Manager URLs", add: https://raw.githubusercontent.com/espressif/arduino-esp32/gh-pages/package_esp32_dev_index.json
Go to Tools > Board > Boards Manager, search for "esp32" and install version 2.0.5 (or a compatible version).
Libraries: Install the following libraries via Sketch > Include Library > Manage Libraries...:
UniversalTelegramBot (1.3.0): Search for "Universal Telegram Bot" by Witnessmenow.
ArduinoJson (6.20.0): Search for "ArduinoJson" by Benoit Blanchon.
DHT sensor library (1.4.4): Search for "DHT sensor library" by Adafruit.
Telegram Bot Setup
Create a New Bot:
Open Telegram and search for @BotFather.
Send /newbot to BotFather and follow the instructions to create a new bot.
BotFather will provide you with a BOT_TOKEN. Save this token.
Get your Chat ID:
Search for @myidbot in Telegram.
Start a chat with it and send /start. It will return your CHAT_ID. Save this ID.
Hardware Connections
Connect the components as follows:
PIR Sensor:
VCC to 3.3V (ESP32-CAM)
GND to GND (ESP32-CAM)
OUT to GPIO 13 (ESP32-CAM)
DHT11 Sensor:
VCC to 3.3V (ESP32-CAM)
GND to GND (ESP32-CAM)
DATA to GPIO 2 (ESP32-CAM)
Relay Module (for light):
VCC to 3.3V (ESP32-CAM)
GND to GND (ESP32-CAM)
IN to GPIO 12 (ESP32-CAM)
Flash LED (On-board):
GPIO 4 (already connected on ESP32-CAM)
Configuration
Open the esp32_cam_telegram.ino file in Arduino IDE and modify the following lines:
const char* ssid = "YOUR_WIFI_NAME";        // Replace with your WiFi Name
const char* password = "YOUR_WIFI_PASSWORD";    // Replace with your WiFi Password
String chatId = "YOUR_CHAT_ID"; // Replace with your Telegram Chat ID
String BOTtoken = "YOUR_BOT_TOKEN"; // Replace with your Telegram Bot Token
Uploading the Code
Select your ESP32-CAM board: Tools > Board > ESP32 Arduino > AI Thinker ESP32-CAM.
Select the correct COM Port: Tools > Port > (Your ESP32-CAM Port).
Important: When uploading, you might need to press and hold the RST or BOOT button on the ESP32-CAM board after compiling and then release it when you see "Connecting....." in the Arduino IDE console.
Cliok the "Upload" button.

Usage
Once uploaded and connected to Wi-Fi, open your Telegram chat with the bot.
Send /start to see a list of available commands.
/photo: Take a photo and send it to your chat.
/photoWithFlash: Take a photo with the onboard flash LED turned on temporarily.
/lightOn: Turn on the relay connected to GPIO 12.
/lightOff: Turn off the relay connected to GPIO 12.
/motionOn: Enable motion detection. The camera will send a photo when motion is detected.
/motionOff: Disable motion detection.
/weather: Get the current temperature and humidity from the DHT11 sensor.
