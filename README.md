📡 ESP32 WiFi Signal Strength (RSSI) Monitor

This project demonstrates how to connect an ESP32-WROOM-32 to a WiFi network and continuously monitor the WiFi signal strength (RSSI) using the Arduino IDE. The RSSI value is displayed on the Serial Monitor in dBm.

🧠 Project Overview

  This project uses an ESP32-WROOM-32 microcontroller to connect to a WiFi network and measure the WiFi signal strength (RSSI) in real time. Once connected, the ESP32 displays its IP address, MAC address, and RSSI value on the Serial Monitor. The project helps in understanding WiFi connectivity and signal quality, which is essential for designing reliable IoT applications.

🛠️ Hardware Requirements

1. ESP32-WROOM-32 development board

2. USB cable (data cable)

3. Laptop / PC with Arduino IDE

💻 Software Requirements

1. Arduino IDE

2.ESP32 Board Package installed

3. USB drivers (CP2102 / CH340 if required)

⚙️ Arduino IDE Configuration

Set the following options:

Board: ESP32 Dev Module

Upload Speed: 115200

CPU Frequency: 240 MHz

Flash Size: 4MB

Debug Level: None

Programmer: Default

⚠️ Do not use Debug mode (OpenOCD is not supported on ESP32-WROOM-32).

📜 Source Code

#include <WiFi.h>

/* -------- WiFi Credentials -------- */
const char* WIFI_SSID = "YOUR_WIFI_NAME";
const char* WIFI_PASSWORD = "YOUR_WIFI_PASSWORD";
/* ---------------------------------- */

void setup() {
  Serial.begin(115200);

  WiFi.begin(WIFI_SSID, WIFI_PASSWORD);
  Serial.print("Connecting to WiFi");

  while (WiFi.status() != WL_CONNECTED) {
    delay(500);
    Serial.print(".");
  }

  Serial.println("\nConnected");
  Serial.print("IP Address: ");
  Serial.println(WiFi.localIP());
  Serial.print("MAC Address: ");
  Serial.println(WiFi.macAddress());
}

void loop() {
  Serial.print("WiFi RSSI: ");
  Serial.print(WiFi.RSSI());
  Serial.println(" dBm");
  delay(1000);
}


🧪 Output Example
Connecting to WiFi.....
Connected
IP Address: 192.168.1.23
MAC Address: 24:6F:28:XX:XX:XX
WiFi RSSI: -45 dBm
