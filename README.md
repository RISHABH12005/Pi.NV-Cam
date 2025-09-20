# Raspberry Pi Camera & Night Vision NORI Camera

> Comprehensive reference for Raspberry Pi Camera Modules and Night Vision NORI Camera, including features, installation, and setup.

---

## About

Raspberry Pi cameras are designed for capturing high-quality images and videos on Raspberry Pi devices. Night Vision cameras, like the NORI Camera, allow imaging in low-light and dark environments using infrared illumination.

---

## Raspberry Pi Camera Modules

* **Interface:** 15-pin MIPI CSI-2 connector
* **Supported Resolutions:** Up to 8 MP for standard cameras, 12.3 MP for High Quality (HQ) Camera
* **Video Capabilities:** 1080p @ 30fps, 720p @ 60fps, VGA @ 90fps; HQ Camera supports interchangeable lenses
* **Features:** Auto-exposure, auto-white balance, raw capture, video streaming
* **Compatibility:** Raspberry Pi 3, 4, 5, and Compute Modules
* **Software Support:** `libcamera`, `raspistill`, `raspivid`, Python libraries (e.g., `picamera2`)

---

## Night Vision NORI Camera

* Interface: Typically USB 2.0/3.0 or CSI depending on the model
* Infrared Illumination: Built-in IR LEDs allow recording in total darkness
* Video Resolution: Models support 720p, 1080p, or higher depending on variant
* Frame Rate: Typically 30 fps for standard night vision recording
* Image Output: Black-and-white IR images; some models can simulate pseudo-color IR video
* Real-Time Streaming: Supports live monitoring over USB or network (with software)
* Power: Powered via USB or CSI (RPi 3,4) interface; low power consumption suitable for 24/7 monitoring

---

## Installation & Setup

### CSI Camera Modules (Standard & HQ)

1. Locate the CSI port (15-pin) near HDMI on the Raspberry Pi.
2. Lift the plastic clip, insert the camera ribbon cable (metal contacts toward HDMI), then press clip back down.
3. Enable the camera interface:

   ```bash
   sudo raspi-config
   # Navigate to Interface Options -> Camera -> Enable
   sudo reboot
   ```

### Night Vision NORI Camera (USB)

1. Connect the camera to a USB port (USB 3.0 recommended for high-speed models).
2. Verify detection:

   ```bash
   lsusb
   ```
3. Install manufacturer-provided drivers or software if required.

---

## Software Examples

### Capture Image (CSI Camera)

```bash
libcamera-still -o image.jpg
```

### Record Video (CSI Camera)

```bash
libcamera-vid -t 10000 -o video.h264
```

### Python Example (Picamera2)

```python
from picamera2 import Picamera2
picam2 = Picamera2()
picam2.start_preview()
picam2.capture_file('test.jpg')
```

### NORI Night Vision Camera (USB, OpenCV)

```python
import cv2
cap = cv2.VideoCapture(0)
while True:
    ret, frame = cap.read()
    if not ret:
        break
    cv2.imshow('NORI Camera', frame)
    if cv2.waitKey(1) & 0xFF == ord('q'):
        break
cap.release()
cv2.destroyAllWindows()
```
