# Setup instructions for OctoPrint on Bullseye

Uses libcamera / Picamera2 to connect to Raspberry Pi Camera Module 3 for web cam streaming with OctoPrint

## Primary Source
[Setting up OctoPrint on a Raspberry Pi running Raspberry Pi OS (Debian) - Get Help / Guides - OctoPrint Community Forum](https://community.octoprint.org/t/setting-up-octoprint-on-a-raspberry-pi-running-raspberry-pi-os-debian/2337)

## Setup Steps

1. Follow instructions on [OctoPrint Community Forum](https://community.octoprint.org/t/setting-up-octoprint-on-a-raspberry-pi-running-raspberry-pi-os-debian/2337) up until "Optional: Webcam"
2. Put `ct-webcam.service` in `/lib/systemd/system/`
3. Put `mjpeg_server.py` in `/home/pi/scripts/`
4. Assign proper file permissions and install the service:
```
sudo chmod 644 /lib/systemd/system/ct-webcam.service
chmod +x /home/pi/scripts/mjpeg_server.py
sudo systemctl daemon-reload
sudo systemctl enable ct-webcam.service
sudo systemctl start ct-webcam.service
```
5. Update OctoPi settings
  * Use `http://octoprint.local/webcam/stream.mjpg` for the "Stream URL" (or `http://octoprint.local:8080/stream.mjpg` if Haproxy is not used)
  * Use `http://octoprint.local/webcam/snapshot.jpg` for the "Snapshot URL" (or `http://octoprint.local:8080/snapshot.jpg` if Haproxy is not used)
