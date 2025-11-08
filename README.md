# 🌦️ Weather_Eye

A small, practical weather terminal made with an **ESP8266** and a **DHT11**.  
Built to be simple to set up and easy to use — it creates its own Wi-Fi access point and serves a compact terminal-style web dashboard that shows temperature, humidity and a computed "feels like" (heat index) value. I made this because I wanted a tiny, standalone sensor that I could check from my phone without relying on any external network.

---

## What it does
- Runs as an **ESP8266 Access Point** (no router needed).  
- Reads **temperature** and **humidity** from a DHT11 sensor.  
- Computes a **feels-like (heat index)** value from those readings.  
- Serves a simple terminal-like web UI that refreshes every second.  
- Provides a JSON endpoint (`/data`) for programmatic access.

---

## Why I built it
I wanted something reliable and offline — useful for quick ambient checks in a room, greenhouse or workshop. No cloud, no external services. Just plug in, connect to the "Weather Eye" Wi-Fi, open a browser and you have current sensor data.

---

## Hardware
- ESP8266 (NodeMCU or Wemos D1 Mini recommended)  
- DHT11 temperature + humidity sensor  
- Jumper wires (male-female)  
- Breadboard (optional)

**Wiring (simple):**
- DHT11 `VCC` → ESP8266 `3.3V`  
- DHT11 `GND` → ESP8266 `GND`  
- DHT11 `DATA` → ESP8266 `D4`

(If you use a different pin, update the `#define DHTPIN` in the firmware.)

---

## Quick setup
1. Install **ESP8266** support in Arduino IDE.  
2. Add these libraries if you don't have them: `DHT` (by Adafruit or equivalent).  
3. Paste the provided firmware into a new sketch and upload to your board.  
4. Power the board. On your phone or PC, connect to the Wi-Fi SSID: **Weather Eye** (password: `12345678`).  
5. Open a browser and go to `http://192.168.4.1` (or simply open any page — captive portal redirects to the dashboard).  
6. The page shows temperature (°C), humidity (%) and the computed "feels like" value; `/data` returns JSON.

---

## Notes & tips
- DHT11 is affordable and fine for basic projects, but it has coarse resolution and slower response. For higher accuracy, swap in a **DHT22** or other better sensor — changes are minimal in code.  
- If the DHT stops responding the UI shows **N/A** and the status becomes **ERROR**.  
- The default refresh is every 1 second — you can increase that interval in firmware to save CPU/time if you like.  
- The web UI is intentionally simple and self-contained (no external CSS/JS). It runs directly from the ESP.

---
