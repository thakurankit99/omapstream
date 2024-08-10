# OMAPS - Raspberry Pi Stream Setup

## Introduction

This guide provides the steps to start and access a Raspberry Pi webcam stream both locally and remotely.

## Prerequisites

- Raspberry Pi with a camera module or USB webcam
- PuTTY for SSH access
- Internet connection for remote access

## Steps to Start Raspberry Pi Stream

1. **Power on Raspberry Pi:**
   - Open PuTTY and enter the local IP address of your Raspberry Pi to connect.

2. **Navigate to the Stream Directory:**
   - Change to the `omapstream` directory:
     ```bash
     cd /path/to/omapstream
     ```

3. **Trigger the Webcam Server:**
   - Run the following commands to start the webcam stream:
     ```bash
     make
     ./mjpg_streamer -i "./input_uvc.so -d /dev/video0 -r 1280x720 -f 30" -o "./output_http.so -w ./www"
     ```

4. **Local Stream Started:**
   - The local stream has been successfully started.

## Steps to Access This Stream Remotely

1. **Login to Raspberry Pi Connect:**
   - Go to [Raspberry Pi Connect](https://connect.raspberrypi.com/) and log in with your user ID and password.

2. **Login to Raspberry Pi Connect on the Pi:**
   - Use the same credentials to log in inside the Raspberry Pi Connect.

By following these steps, you should be able to start and access your Raspberry Pi webcam stream both locally and remotely.
