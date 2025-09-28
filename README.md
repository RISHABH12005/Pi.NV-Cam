# Raspberry Pi Camera & Night Vision NoIR Camera

## About
RPi cameras are designed for capturing high quality img. & vid. on RPi devices. Night Vision NoIR cameras allow imaging in low light & dark env. using infrared illumination.

## RPi Cam Module
* *Interface:* 15 pin MIPI CSI-2 connector.
* *Supported Resolutions:* Up to 8 MP for standard cameras, 12.3 MP for High Quality (HQ) Camera.
* *Video Capabilities:* 1080p @ 30fps, 720p @ 60fps, VGA @ 90fps; HQ Camera supports interchangeable lenses.
* *Features:* Auto-exposure, auto-white balance, raw capture, video streaming.
* *Compatibility:* Raspberry Pi 3, 4, 5 & Compute Module.
* *Software Support:* `libcamera`,`picamera2`, `OpenCV`.

## Night Vision NoIR Cam Module
* Interface: Typically USB 2.0/3.0 or CSI depending on the model.
* Infrared Illumination: Built-in IR LEDs allow recording in total darkness.
* Video Resolution: Models support 720p, 1080p, or higher depending on variant.
* Frame Rate: Typically 30 fps for standard night vision recording.
* Image Output: Black-and-white IR images; some models can simulate pseudo color IR video.
* Real-Time Streaming: Supports live monitoring over USB or network (with software).
* Power: Powered via USB or CSI (RPi 3,4) interface; low power consumption suitable for 24/7 monitoring.

## Installation
1. Locate the CSI port (15-pin) near HDMI on the RPi.
2. Lift the plastic clip, insert the camera ribbon cable (metal contacts toward HDMI), then press clip back down.
3. Enable the camera interface:
   ```bash
   sudo raspi-config
   # Navigate to Interface Options -> Camera -> Enable
   sudo reboot
   ```
   ```bash
   lsusb # Verify detection
   ```

### Picamera Library
```bash
sudo apt install python-picamera -y
# or
sudo apt install -y python-picamera2
```
```bash
python # Verify
```
```python
import picamera2
```

### libcamera & utilities Library
```bash
sudo apt install -y libcamera-apps libcamera-tools
```
```bash
libcamera-still -o image.jpg # Capture Img.
```
```bash
libcamera-vid -t 10000 -o video.h264 # Record Vid.
```

### OpenCV
```bash
sudo apt install -y python3-opencv libopencv-dev
```
```bash
python # Verify
```
```python
import opencv
```
