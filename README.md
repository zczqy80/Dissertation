# Dissertation
Low-cost loacl real-time dectection of people flow

## Project Overview
This project focuses on developing a low-cost, real-time indoor people flow detection system. By integrating infrared photoelectric sensors with OpenCV-based image processing on a Raspberry Pi platform, the system effectively addresses the limitations of traditional infrared sensors, especially in complex scenarios. The system is designed to balance cost, accuracy, and privacy, making it suitable for various indoor environments.

## Features
Low-Cost Implementation: The project successfully maintained a budget under £100 by using affordable components such as infrared photoelectric sensors, a Raspberry Pi, and a camera. The cost can be further reduced by using a Raspberry Pi Zero.

Real-Time Detection: The system processes data locally, allowing for real-time detection without the need for cloud processing or data uploads, ensuring privacy protection.

Complex Scenario Handling: Through the combination of sensors and image processing, the system can detect complex scenarios that single-type sensors may struggle with.

## Components Used
Infrared Photoelectric Sensors: Two infrared sensors priced at £10 from DFrobot each were used for detecting the interruption of the infrared beam when a person passes through the area.

<p align="center">
  <img src="https://github.com/user-attachments/assets/c401cafd-494e-4c00-b537-f05f5272fc50"  width="400" height="300">
</p>

Raspberry Pi: A Raspberry Pi 4B was used as the main processor, though a Raspberry Pi Zero can be used to further reduce costs.

<p align="center">
  <img src="https://github.com/user-attachments/assets/1dd45649-cc35-4cc4-9ddb-2d3af666d5d3"  width="400" height="300">
</p>

Camera Module: A £14 CSI picamera V2 module was used to integrate image processing with the sensor data.

<p align="center">
  <img src="https://github.com/user-attachments/assets/956c6b73-b95e-4619-a38f-d62d5e708898"  width="200" height="300">
</p>

LCD: Output for display data, like how many people in and out.

<p align="center">
  <img src="https://github.com/user-attachments/assets/843ce692-495e-4e7b-b278-60dddd70e40d"  width="600" height="250">
</p>

## System Architecture
The system integrates infrared sensors and a camera for dual detection of people flow. The infrared sensors are responsible for detecting interruptions in the beam, while the camera, positioned overhead, processes images to handle complex scenarios, such as overlapping individuals or environmental interference. The images are processed locally on the Raspberry Pi using OpenCV, ensuring that no data is uploaded, thus maintaining privacy.

## Infrared Beam Break Sensor Detection Process
The infrared beam break sensor system operates by detecting interruptions in an infrared beam emitted between a transmitter and a receiver. Here's how the process works:

<p align="center">
  <img src="https://github.com/user-attachments/assets/4faab5c1-7c2e-4e33-99c8-ea7bba9f95ec"  width="500" height="700">
</p>

Setup: The infrared beam break sensor consists of an emitter (transmitter) and a receiver. The emitter sends out a continuous infrared beam, which is received by the receiver on the opposite side.

Detection: When a person or object passes between the emitter and the receiver, the infrared beam is interrupted. This interruption is detected by the sensor, triggering an event in the system.

Processing: The system processes these events to count the number of interruptions, which corresponds to the number of people passing through the detection zone.

<p align="center">
  <img src="https://github.com/user-attachments/assets/adbbc4bd-acb8-42a3-be44-31c138b6b61e"  width="700" height="150">
</p>

## Camera-Based Detection Process with OpenCV
The camera-based detection process enhances the infrared sensor system by using image processing to handle more complex scenarios. Here's an overview of the process:

<p align="center">
  <img src="https://github.com/user-attachments/assets/9e2931ea-1d26-44a2-a039-19b40703f366"  width="550" height="700">
</p>

Setup: A camera module is positioned overhead to capture the entire detection area. This placement helps avoid issues like shadows and overlapping people in the field of view.

Image Capture: The camera continuously captures frames of the detection area. These images are processed locally on the Raspberry Pi using the OpenCV library.

Background Subtraction: To identify moving objects (i.e., people), the system uses background subtraction. This technique isolates moving elements from the static background, making it easier to detect people.

Thresholding and Contour Detection: After background subtraction, the system applies thresholding to convert the image to black and white, where moving objects are white, and the background is black. Contour detection is then used to identify the shapes of the moving objects.

Counting and Tracking: The system tracks the movement of identified objects across frames to count entries and exits. This helps in scenarios where multiple people may be present in the detection area simultaneously.

Challenges and Solutions: The system adjusts to different lighting conditions by modifying the threshold values dynamically. Additionally, repositioning the camera to an overhead view minimizes issues like overlapping individuals in the horizontal plane, ensuring more accurate detection.

<p align="center">
  <img src="https://github.com/user-attachments/assets/0a084ca5-2ff9-436e-afb5-c0f619808351"  width="700" height="150">
</p>

## Combining Both Systems
By combining infrared sensors with camera-based detection, the system leverages the strengths of both methods. The infrared sensors provide a reliable, low-cost solution for detecting simple entries and exits, while the camera system enhances accuracy in complex scenarios, ensuring robust detection even when people overlap or environmental conditions change with a LCD display to show the data，which like:

<p align="center">
  <img src="https://github.com/user-attachments/assets/3b5a4472-86ff-4d64-be10-80fe21fe034b"  width="700" height="200">
</p>

The code has been upload to Github

## PCB, Enclosure and Deployment
In order to enhance the stability of the connection, the PCB design contains 2 inputs for reading the IR photoelectric switch and 2 outputs for controlling the LCD display

<p align="center">
  <img src="https://github.com/user-attachments/assets/0a045067-17f8-45d9-b91c-f88ad23ee9d2"  width="600" height="300">
</p>

To give the project a better enclosure, the package of transmitter and receiver and Raspberry PI were laser cut from black acrylic sheets:

<p align="center">
  <img src="https://github.com/user-attachments/assets/3c6979e2-e0b5-45f8-a5d0-a8fca5cdd217"  width="600" height="350">
</p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/6a9614f5-a5bd-4df4-9d22-4c1430b697d5"  width="500" height="400">
</p>

The package of the Raspberry PI, which integrates the camera and LCD display, is shown below:

<p align="center">
  <img src="https://github.com/user-attachments/assets/57801ad3-6edb-4294-bc91-81fd78cf175a"  width="500" height="350">
</p>

In the end, the whole system could be placed like:

<p align="center">
  <img src="https://github.com/user-attachments/assets/a9fcba4b-a9f0-4268-847d-11fdbb0468cc"  width="700" height="500">
</p>

All the file of Enclosure has been upload to Github.

## Future Work
Improved Data Display: Currently, the data is displayed on an LCD positioned on the camera housing, which is inconvenient. Future iterations will explore uploading data to a web page or app using MQTT or similar technologies for easier access.

Further Cost Reduction: By replacing the Raspberry Pi 4B with a Raspberry Pi Zero, the total cost can be reduced even further while maintaining system functionality.
