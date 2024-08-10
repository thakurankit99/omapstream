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

## Project Structure (OMaps Stream)

```
📦 
CMakeLists.txt
Dockerfile
LICENSE
Makefile
├─ README.md
├─ TODO
├─ cmake
FindGphoto2.cmake
FindProtobuf-c.cmake
FindZeroMQ.cmake
│  └─ mjpg_streamer_utils.cmake
├─ docker-start.sh
├─ makedeb.sh
├─ mjpg_streamer.c
├─ mjpg_streamer.h
├─ mjpg_streamer@.service
├─ plugins
input.h
input_control
│  │  ├─ Makefile
│  │  ├─ dynctrl.c
│  │  ├─ dynctrl.h
│  │  ├─ input_uvc.c
│  │  ├─ uvc_compat.h
│  │  └─ uvcvideo.h
input_file
│  │  ├─ CMakeLists.txt
│  │  ├─ Makefile
│  │  └─ input_file.c
input_http
│  │  ├─ CMakeLists.txt
│  │  ├─ input_http.c
│  │  ├─ misc.c
│  │  ├─ misc.h
│  │  ├─ mjpg-proxy.c
│  │  ├─ mjpg-proxy.h
│  │  └─ version.h
input_libcamera
│  │  ├─ CMakeLists.txt
│  │  ├─ LibCamera.cpp
│  │  ├─ LibCamera.h
│  │  ├─ README.md
│  │  ├─ common.h
│  │  ├─ input_libcamera.cpp
│  │  ├─ input_libcamera.h
│  │  ├─ jpeg_utils.c
│  │  └─ jpeg_utils.h
input_opencv
│  │  ├─ CMakeLists.txt
│  │  ├─ README.md
│  │  ├─ filters
│  │  │  ├─ cvfilter_cpp
│  │  │  │  ├─ CMakeLists.txt
│  │  │  │  ├─ README.md
│  │  │  │  └─ filter_cpp.cpp
│  │  │  └─ cvfilter_py
│  │  │     ├─ CMakeLists.txt
│  │  │     ├─ README.md
│  │  │     ├─ cmake
│  │  │     │  └─ FindNumpy.cmake
│  │  │     ├─ conversion.cpp
│  │  │     ├─ conversion.h
│  │  │     ├─ example_filter.py
│  │  │     └─ filter_py.cpp
│  │  ├─ input_opencv.cpp
│  │  └─ input_opencv.h
│  ├─ input_ptp2
│  │  ├─ CMakeLists.txt
│  │  ├─ input_ptp2.c
│  │  └─ input_ptp2.h
│  ├─ input_raspicam
│  │  ├─ CMakeLists.txt
│  │  ├─ README.md
│  │  ├─ RaspiCamControl.c
│  │  ├─ RaspiCamControl.h
│  │  ├─ input_raspicam.c
│  │  └─ mmal
│  │     ├─ CMakeLists.txt
│  │     ├─ core
│  │     │  ├─ CMakeLists.txt
│  │     │  ├─ mmal_buffer.c
│  │     │  ├─ mmal_buffer_private.h
│  │     │  ├─ mmal_clock.c
│  │     │  ├─ mmal_clock_private.h
│  │     │  ├─ mmal_component.c
│  │     │  ├─ mmal_component_private.h
│  │     │  ├─ mmal_core_private.h
│  │     │  ├─ mmal_events.c
│  │     │  ├─ mmal_format.c
│  │     │  ├─ mmal_logging.c
│  │     │  ├─ mmal_pool.c
│  │     │  ├─ mmal_port.c
│  │     │  ├─ mmal_port_clock.c
│  │     │  ├─ mmal_port_private.h
│  │     │  └─ mmal_queue.c
│  │     ├─ mmal.h
│  │     ├─ mmal_buffer.h
│  │     ├─ mmal_clock.h
│  │     ├─ mmal_common.h
│  │     ├─ mmal_component.h
│  │     ├─ mmal_encodings.h
│  │     ├─ mmal_events.h
│  │     ├─ mmal_format.h
│  │     ├─ mmal_logging.h
│  │     ├─ mmal_metadata.h
│  │     ├─ mmal_parameters.h
│  │     ├─ mmal_parameters_audio.h
│  │     ├─ mmal_parameters_camera.h
│  │     ├─ mmal_parameters_clock.h
│  │     ├─ mmal_parameters_common.h
│  │     ├─ mmal_parameters_video.h
│  │     ├─ mmal_pool.h
│  │     ├─ mmal_port.h
│  │     ├─ mmal_queue.h
│  │     ├─ mmal_types.h
│  │     ├─ util
│  │     │  ├─ CMakeLists.txt
│  │     │  ├─ mmal_component_wrapper.c
│  │     │  ├─ mmal_component_wrapper.h
│  │     │  ├─ mmal_connection.c
│  │     │  ├─ mmal_connection.h
│  │     │  ├─ mmal_default_components.h
│  │     │  ├─ mmal_graph.c
│  │     │  ├─ mmal_graph.h
│  │     │  ├─ mmal_il.c
│  │     │  ├─ mmal_il.h
│  │     │  ├─ mmal_list.c
│  │     │  ├─ mmal_list.h
│  │     │  ├─ mmal_param_convert.c
│  │     │  ├─ mmal_param_convert.h
│  │     │  ├─ mmal_util.c
│  │     │  ├─ mmal_util.h
│  │     │  ├─ mmal_util_params.c
│  │     │  ├─ mmal_util_params.h
│  │     │  ├─ mmal_util_rational.c
│  │     │  └─ mmal_util_rational.h
│  │     └─ vc
│  │        ├─ CMakeLists.txt
│  │        ├─ mmal_vc_api.c
│  │        ├─ mmal_vc_api.h
│  │        ├─ mmal_vc_api_drm.c
│  │        ├─ mmal_vc_api_drm.h
│  │        ├─ mmal_vc_client.c
│  │        ├─ mmal_vc_client_priv.h
│  │        ├─ mmal_vc_msgnames.c
│  │        ├─ mmal_vc_msgnames.h
│  │        ├─ mmal_vc_msgs.h
│  │        ├─ mmal_vc_opaque_alloc.c
│  │        ├─ mmal_vc_opaque_alloc.h
│  │        ├─ mmal_vc_shm.c
│  │        └─ mmal_vc_shm.h
│  ├─ input_testpicture
│  │  ├─ Makefile
│  │  ├─ input_testpicture.c
│  │  ├─ pictures
│  │  │  ├─ 160x120_1.jpg
│  │  │  ├─ 160x120_2.jpg
│  │  │  ├─ 320x240_1.jpg
│  │  │  ├─ 320x240_2.jpg
640x480_1.jpg
│  │  │  ├─ 640x480_2.jpg
│  │  │  ├─ 960x720_1.jpg
│  │  │  └─ 960x720_2.jpg
│  │  └─ testpictures.h
│  ├─ input_uvc
│  │  ├─ CMakeLists.txt
│  │  ├─ README.md
│  │  ├─ dynctrl.c
│  │  ├─ dynctrl.h
│  │  ├─ huffman.h
│  │  ├─ input_uvc.c
│  │  ├─ jpeg_utils.c
│  │  ├─ jpeg_utils.h
│  │  ├─ uvc_compat.h
│  │  ├─ uvcvideo.h
│  │  ├─ v4l2uvc.c
│  │  └─ v4l2uvc.h
│  ├─ output.h
│  ├─ output_autofocus
│  │  ├─ Makefile
│  │  ├─ output_autofocus.c
│  │  ├─ processJPEG_onlyCenter.c
│  │  └─ processJPEG_onlyCenter.h
│  ├─ output_file
│  │  ├─ CMakeLists.txt
│  │  ├─ examples
│  │  │  ├─ change_filename.sh
│  │  │  ├─ ftp_upload.sh
│  │  │  └─ show_filename.sh
│  │  ├─ output_file.c
│  │  └─ output_file.h
│  ├─ output_http
│  │  ├─ CMakeLists.txt
│  │  ├─ README.md
│  │  ├─ httpd.c
│  │  ├─ httpd.h
│  │  └─ output_http.c
│  ├─ output_rtsp
│  │  ├─ CMakeLists.txt
│  │  └─ output_rtsp.c
│  ├─ output_udp
│  │  ├─ CMakeLists.txt
│  │  └─ output_udp.c
│  ├─ output_viewer
│  │  ├─ CMakeLists.txt
│  │  ├─ README.md
│  │  └─ output_viewer.c
│  ├─ output_zmqserver
│  │  ├─ CMakeLists.txt
│  │  ├─ README.md
│  │  ├─ output_zmqserver.c
│  │  ├─ output_zmqserver.h
│  │  └─ package.proto
│  └─ test.txt
├─ postinstall.sh
├─ scripts
│  ├─ make_deb.sh
│  ├─ mjpg-streamer.default
│  ├─ mjpg-streamer.init
│  └─ mjpg-streamer.service
├─ start.sh
├─ utils.c
├─ utils.h
└─ www
   ├─ JQuerySpinBtn.css
   ├─ JQuerySpinBtn.js
   ├─ LICENSE.txt
   ├─ bodybg.gif
   ├─ cambozola.jar
   ├─ control.htm
   ├─ favicon.ico
   ├─ favicon.png
   ├─ fix.css
   ├─ functions.js
   ├─ index.html
   ├─ java.html
   ├─ java_control.html
   ├─ java_simple.html
   ├─ javascript.html
   ├─ javascript_motiondetection.html
   ├─ javascript_simple.html
   ├─ jquery.js
   ├─ jquery.rotate.js
   ├─ jquery.ui.core.min.js
   ├─ jquery.ui.custom.css
   ├─ jquery.ui.tabs.min.js
   ├─ jquery.ui.widget.min.js
   ├─ rotateicons.png
   ├─ script.js
   ├─ sidebarbg.gif
   ├─ spinbtn_updn.gif
   ├─ static.html
   ├─ static_simple.html
   ├─ stream_simple.html
   ├─ style.css
   └─ videolan.html
```
