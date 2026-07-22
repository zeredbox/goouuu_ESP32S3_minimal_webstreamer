# 📷 Goouuu ESP32-S3 Minimal Webstreamer

A minimal **HTTP MJPEG video streaming server** tailored specifically for the **Goouuu ESP32-S3 (N16R8)** development board paired with the **OV2640** camera sensor.

## 🚀 Key Features

* **Low Latency MJPEG Streaming:** Optimized HTTP server delivering a smooth video stream.
* **OPI PSRAM Double Buffering:** Asynchronous frame capture leveraging 8MB of OPI PSRAM to eliminate stutters.
* **WiFi Power Saving Disabled:** Prevents connection drops and stream freezes using `WiFi.setSleep(false)`.
* **Pre-configured Image Adjustments:** Automatic Exposure Control (AEC), Auto Gain Control (AGC), Auto White Balance (AWB), and Vertical Flip (`VFLIP`).

## 🛠️ Hardware Requirements

* **Board:** Goouuu ESP32-S3 N16R8 (16MB Flash / 8MB OPI PSRAM)
* **Camera:** OV2640
* **Power Supply:** USB-C Cable (5V / 1A minimum recommended)

## 📌 Camera Pinout (Goouuu ESP32-S3)

| Camera Signal | ESP32-S3 Pin | Camera Signal | ESP32-S3 Pin |
| :--- | :--- | :--- | :--- |
| **PWDN** | GPIO 21 | **Y9** | GPIO 16 |
| **RESET** | -1 (Unused) | **Y8** | GPIO 17 |
| **XCLK** | GPIO 15 | **Y7** | GPIO 18 |
| **SIOD (SDA)**| GPIO 4 | **Y6** | GPIO 12 |
| **SIOC (SCL)**| GPIO 5 | **Y5** | GPIO 10 |
| **VSYNC** | GPIO 6 | **Y4** | GPIO 8 |
| **HREF** | GPIO 7 | **Y3** | GPIO 9 |
| **PCLK** | GPIO 13 | **Y2** | GPIO 11 |

## 💻 Software Setup

### 1. Install Arduino IDE
Download and install the latest **Arduino IDE** (2.x recommended) from [arduino.cc/en/software](https://www.arduino.cc/en/software).

### 2. Install ESP32 Board Package
1. Open **Arduino IDE**.
2. Go to **Tools** > **Board** > **Boards Manager...**
3. Search for **"esp32"** and install **"esp32 by Espressif Systems"**.

### 3. Board Selection & Configuration
1. Go to **Tools** > **Board** > **esp32** > Select **`ESP32S3 Dev Module`**.
2. Configure the following settings under the **Tools** menu:
   * **PSRAM:** `OPI PSRAM` *(⚠️ CRITICAL for N16R8 boards)*
   * **Flash Size:** `16MB (128Mb)`
   * **Partition Scheme:** `16M Flash (3MB APP / 9.9MB FATFS)`
   * **Core Debug Level:** `None`

## 🖼️ Preview & Serial Output

### Serial Monitor Output
```text
==========================================
   ESP32-S3 CAMERA STREAMER INITIALIZATION 
==========================================
[OK] Camera hardware initialized successfully.
[WIFI] Connecting to SSID: MY_SSID ...
[OK] WiFi Connected!
[INFO] Video Stream URL: [http://10.161.x.x](http://10.161.x.x)
[OK] HTTP Server started successfully.
[Stream] 10 frames transmitted successfully
[Stream] 20 frames transmitted successfully
[Stream] 30 frames transmitted successfully
[Stream] 40 frames transmitted successfully
```

## 🌐 HTTP Endpoints

* **`http://<ESP32_IP>/`** : Web interface containing the live video player.
* **`http://<ESP32_IP>/stream`** : Raw MJPEG stream (compatible with Home Assistant, OpenCV, MotionEye, VLC, etc.).

### Web Page Output
<img width="992" height="802" alt="goouuu-video-output" src="https://github.com/user-attachments/assets/5508fc9d-03ad-4698-adbd-2c99dbfc307e" />

## 📄 License

Unlicense License
