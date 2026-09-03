#  ESP32 BLE Spammer (Web UI & Button Editions)

> A lightweight, ESP32-based tool to broadcast Bluetooth Low Energy (BLE) advertisement packets (Apple, Beats, Flipper Zero, etc.) featuring a built-in Wi-Fi Web Server for remote control, along with an ultra-low power standalone Button-controlled version.


### Features (Web UI Version)

* **Web UI Control:** Start and stop the BLE broadcasts instantly via a responsive web browser interface.
* **Access Point Mode:** The ESP32 creates its own standalone Wi-Fi network—no external router required.
* **MAC Address Spoofing:** Generates a random MAC address for each packet cycle to bypass basic rate-limiting and spam filters.
* **NimBLE Optimization:** Uses the lightweight `NimBLE-Arduino` library for faster, memory-efficient, and highly stable BLE broadcasting.
* **Non-Blocking Architecture:** Utilizes `millis()` instead of `delay()` to ensure the web interface remains highly responsive during active broadcasts.

### Features (Headless / Button Edition)

* **One-Button Control:** Start and stop the BLE broadcasts instantly using the physical BOOT button (GPIO 0) on the ESP32.
* **RGB LED Status Feedback:** Utilizes the built-in NeoPixel RGB LED (defaults to Pin 48, common on ESP32-S3 boards), which illuminates **GREEN** when an attack is active and turns off when in standby mode.
* **Ultra-Low Power:** Wi-Fi is completely disabled for maximum battery life and 100% dedicated BLE antenna performance.

---

###  Requirements

* ESP32 or ESP32-S3 Development Board
* Arduino IDE
* [NimBLE-Arduino](https://github.com/h2zero/NimBLE-Arduino) library (Tested with v1.4+)
* [Adafruit NeoPixel](https://github.com/adafruit/Adafruit_NeoPixel) library *(Required for the Headless/Button Edition LED)*
---

### Installation

1. Install the required libraries in your Arduino IDE via **Sketch > Include Library > Manage Libraries**:
   * Search for and install **NimBLE-Arduino**.
   * Search for and install **Adafruit NeoPixel**.
2. Open the desired `.ino` file (Web Server or Headless version) in Arduino IDE.
3. *(Optional for Web Version)* The default Access Point credentials are set as follows. You can edit them at the top of the code if needed:
   ```cpp
   const char* ssid = "BLE_Spam_AP";
   const char* password = "password123";
Select your ESP32 board and corresponding COM port, then compile and upload the code.

 Usage (Web UI Version)
Plug the ESP32 into a power source (e.g., a power bank or USB port).

Open your smartphone or computer's Wi-Fi settings and connect to the following network:

Network Name (SSID): BLE_Spam_AP

Password: password123

Open a web browser and navigate to the control panel at http://192.168.4.1.

Click Start Attack to begin broadcasting BLE packets. Click Stop Attack to immediately halt the broadcast and return to standby mode.

 Usage (Button Edition)
Plug the ESP32 into a power source.

* **Start Attack:** Press the BOOT button once. The built-in RGB LED will turn **GREEN**.

* **Stop Attack:** Press the BOOT button again. The RGB LED will turn **OFF** and broadcasts will halt immediately.

:handshake: Credits & Acknowledgements
The core BLE packet structures and device lists in this project were based on the [Nugget-BLE-Spam
](https://github.com/ryan-richards/Nugget-BLE-Spam) repository by [Ryan-Richards](https://github.com/ryan-richards)

⚠️ Disclaimer
For Educational and Research Purposes Only.

This project is provided solely for educational, testing, and research purposes. The author is not responsible for any damage, disruption, or legal consequences caused by the use of this code. Do not use this tool on public networks or to disrupt devices you do not explicitly own.
