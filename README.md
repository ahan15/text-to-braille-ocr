# Abraham Worklog
## 2023-02-17 TA meeting
We're free to use equipment from the white cabinet from the lab.

Look at CHARM (previous project from the FA2022 semester) as a reference guide for the design document. Look at the project design document for clues on formatting and content.

Updates from the machine shop: plastic will be used as a housing material. The housing will be in a rectangular box form. Instead of motors, solenoids will be used to drive the braille pins.

The high-level weight requirement proposed in the project proposol must be changed. Weight is not cricitcal to the function of the project device (or hard to argue that it is critical), thus we must find a different high-level requirement. 

The TA suggests that subsystems should be localized for rigorous testing of individual subsystems in the event of system integration failure. One proposal is a testing suite to calculate the image-to-character conversion accuracy of the control unit subsystem. This would be great to include in the tolerance analysis section of the final report.

<br>

## 2023-02-21 TA meeting
Design proposal regrade deadline occurs after the design interview. We might get some good feedback from the design interview which could be implemented into the revised design proposal.

Professor Viktor Gruev is our assigned professor for our project. We can sign up fo design interviews after the TA meeting. A powerpoint presentation is not required for the interview. The proposal will mainly just be us going through our proposal document.

A new high-level requirement will be that all the solenoids raise each braille pin up 0.5cm.

With regards to the PCB microcontroller, the TA suggests we use a STM32 micrcontroller. Any questions regarding this micrcontroller should be directed towards Jason or Matthew who have office hours on Mondays and Fridays at 11am at the senior design project lab. If needed, questions can be elevated to Professor Gruev himself.

In the design proposal, voltalge values need to be added in the block diagram. Double check this when resubmitting the design proposal.

The accuracy of the braille display is a safety concern. Displaying incorrect information may prove to be dangerous to the user depending on how and what the user is using our device for. Keep this in mind as we continue developing the project.

The PCB design and procurement will be based off of the components that we've decided to use. Prioritize the component decisions first as this is the first step towards creating a PCB design. Once component decisions have been made, then we can work on designing the PCB and working on resubmitting the proposal. 

<br>

## 2023-02-21 Team Meeting (after TA meeting)
We largely discuss which microcontroller (external one that would be running the OCR software) we would be using. This is important for one: interfacing with the microcontroller on the PCB, and it needs to be low-powered enough such that the battery would be able to power it. The Raspberry Pi 4 is the first option that came to mind but due to the chip shortage, the production has slowed, and scalpers are reselling the Raspberry Pi 4 for double, if not triple the MSRP. Alternatives are researched and a couple options have been found: Arduino Uno Rev3, Libre Le Potato, and the Orange Pi 3 LTS. The Libre Le Potato is favored because it's the most low-powered but still has a fast processor which would be required to shorten the processing time of the OCR software.

The choice of OCR engine software is also discussed. Tesseract and GOCR are the popular choices that are open source and free to use. Kraken is also discussed, however, Tesseract is favored for the extensive documentation and positive reviews on the ease of implementation with python. 

<br>

## 2023-03-08 TA Meeting
Most camera sensors are using a MIPI interface. Make sure that the microcontroller that we've decided to use also has MIPI as an I/O interface to allow for the connection between them. An external clock signal will be coming from the microcontroller (which will be required for the camera sensor). Look for the specific hertz oscillator from the microcontroller and make sure that the frequencies are compatible for the camera sensor. 

XTAL1 and XTAL2 on the left side of the microcontroller, micrcontrollers may need a clock signal that comes from a crystal, an external clock signal. D+ and D- are typically related to the USB.

Double checking the camera sensors, we find that 48MHz is the maximum clock frequency that it can take.

Be careful when it comes to the software side of the project. 

When working with a PCB, make sure that things that are labeled as the same are actually physically connected to one another. 

Make the 5V power trace on our PCB design as wide as possible so that it's easy to connect to. 

Find the minimum size VIA for the PCB design.

Make sure that the whole PCB design fits within the 10cm x 10cm dimension constraints. 

Make the solenoid trace coming from the battery really really wide because at max current, we'll be drawing 6A. This is a lot of current. Put a big capacitor right next to the solenoid connection because when turned on, the current is going to be super wavy (~100 microfarads).

On PCB way (the site we're ordering the PCB from), double check the minimum spacing. Right now, the minimum spacing is 4 mils, but minimum 6+ mils is what is recommended. 

Make sure that the USB C connector sits flush with the edge of the PCB. Generally try to find a different connector that has a wider spacing in between the connections. This connector is going to be the weakest component on the PCB, thus a liability issue in terms of the success of the project.

On the development of the PCB, creating Design Rule Checks can be a fast way to test whether design constraints are being met in concurrence to the design of the PCB. The professor recommends that we set 5mil spacing, hole size, VIA to line spacing, VIA to VIA spacing Design Rule Checks so that we can rapidly test for our desired PCB design constraints in concurrence to the desigining.

Put multiple, smaller VIAs that are in parallel for the power line. 

Send the zip file of our PCB to the TA by midnight, and fill out the team evaluation form by tonight on Canvas. 

<br>

## 2023-03-08 Team Meeting (after TA meeting)
Minimum spacing is widened as suggested. 

We were unable to find and implement the Design Rule Checks into the software for rapid development. This wasn't too big of an issue as we were able to quickly make sure that the PCB fit into our desired design constraints. 

Capacitors are added to the solenoid connections in order to smooth out the current flow (when the solenoids are switched on). 

The solenoid trace is widened to accomodate for potential high current going into the solenoids from the battery. 

The total PCB design size is made smaller to fit the 10cm x 10cm design requirement. 

Generally, changes to the PCB as suggested by the professor and TA are implemented. 

<br>

## 2023-03-28 TA meeting
Detailed specifications on the resubmission of the Design Document was outlined in the weekly email. Resubmission is due Friday. 

We haven't retrieved our PCB board yet. The TA suggests that it is better to get our PCB board as fast as possible. Thursday afternoon is the deadline for the 3rd round of PCB applications. 4th round is next week.

Individual progress reports are due tomorrow by midnight. The grading rubric is outlined on the website.

Make sure that lab notebooks are being maintained. Meeting notes with the TA should be included, but meeting notes within our own team should be included as well. Things such as testing and observations from our work should be added and maintained throughout the semester. Better to start now if haven't yet, as many important deadlines will happen close together near the lab notebook deadline time. Start sooner than later!

Most of the components that we've ordered online have been received. 

An email to the machine shop about our team project design should be sent. We should keep in touch with them so that we can get our design in time.

Are there any calculations that we should be applying for the project? For one: statisical analysis for the braille conversion. We need some sort of simulation, experimental testing. Simulation testing. 

<br>

## 2023-03-28 Team meeting (after TA meeting)
Plans to pick up the PCB, and emailing to the machine shop are coordinated.

The statistical analysis of the control unit, essentially accuracy testing of the OCR engine, is discussed. A labeled character dataset is determined to be essential to test for the accuracy. Individual characters are favored for the ease of labeling and testing. Python will be the programming language for the ease of use, and because a python module that interfaces with the OCR engine already exists. The alterantive is C++ but Python is favored for the ease of use, and readability. 

<br>

## 2023-04-03 Individual Progress
A barebones non-GUI Ubuntu 22.04 (proprietary version released by Libre) is installed onto a micro SD card which is used as the boot drive for the Libre Le Potato microcontroller. The process is tedius, but is successful. Packages are updated, and the Tesseract OCR engine is successfully installed onto the microcontroller. Primitive testing by running some images through the engine is conducted and is successful. 

<br>

## 2023-04-05 Individual Progress
A public dataset of images of individual characters is acquired. The resolution, or pixel ratio of the images are small, but this is intentional. The thought process is that a user would be taking images of text that contain multiple characters, thus the actual individual characters in the image will be small resolution. Therefore, an image that is "small" makes sense for our use case. The "true" accuracy of the image-to-character translation would only be found in small resolution images of the characters.

The dataset is divided into multiple folders, named by the character the images inside are of. For example, the folder named "A" contain many images of the character A. Each image varies in the font type, style, size, thickness, contrast, and brightness from one another. The dataset has been selected because of this as we felt that it was necessary to find a dataset that would replicate "real world" image data. 

<br>

## 2023-04-07 Individual Progress
A python script is written to calculate a basic accuracy of Tesseract, the OCR engine. The test accuracy is 67%, which is far below the testing accuracy of our high-level requirement. Through further research, the methods to increase this testing accuracy is to preprocess the image data. 

Image preprocessing will be done through the OpenCV image and video processing library. The library is open source, and is the industry standard in image processing. Many common preprocessing algorithms are implemented as function methods and can just be called on the image data. 

Initially, simple binary thresholding is the preprocessing method of choice, and it brings the testing accuracy up to 74%. Further research into preprocessing methods will be needed in order to bring the testing accuracy up to the high-level requirement levels. 

<br>

## 2023-04-09 Individual Progress
Otsu's Binarization Thresholding algorithm is the breakthrough that was needed. Paired with Grayscaling and Noise Removal, the testing accuracy has been raised to 89.13% which we have determined to be acceptable levels of accuracy. 

<br>

## 2023-04-11 TA Meeting
Any modifications to the high level modifications need to be run by the professor.

Keep track of the testing accuracy rates on the different iterations of the image preprocessing code.

We won't be ordering any more components.

Next week is the mock demo. The TA recommends to go through the grading rubric and to familiarize ourselves with what we will be specifically graded on. PCB is 30/150. System integration. Individual subsystem testing. We should be aware of every point.

Mock demo time slots will become available tomorrow. In case all the slots don't work we should let the TA know so that we can try to make an alterantive slot time. 

We must find a programming cable so that we can program the PCB micrcontroller. Alternatively, we can repurpose the Arduino Nanos that are lying around so that we can interface with and program the chip.

If at any point we run into any hurdles with the project, we can briefly mention these hurdles, but during the mock demo, and the final demo, we should focus on the positive accomplishments of our project. 

<br>

## 2023-04-18 Mock Demo
While running the python script right before the mock demo, the power to the microcontroller running the python script is accidentally unplugged. After trying to reboot and troubleshoot, the microSD card has been corrupted and the micrcontroller is unresponsive. 

I was unfortunately unable to show the script running, but will be fixing the microSD card and the microcontroller for our project device.

<br>

## 2023-04-24 Team Meeting
The programming cable for the microcontroller on the PCB is not functioning. Perhaps the microcontroller on the PCB is not functioning. After many hours of testing the voltages and double checking the connections, we were unsuccessful in getting the Arduino IDE in recognizing the microcontroller device. 

This has proved detrimental to the system integration portion of our project as the PCB microcontroller is at the heart of tying everything together. We are unable to show that the solenoids are working as intended. We are unable to receive image data from our camera sensor. We are unable to interface between the PCB microcontroller and the microcontroller that is running the OCR software. 

We are successful in showing that the power subsystem is working as intended by feeding the components the correct voltages that are required to power them.

<br>

## 2023-04-25 Team Meeting (after Final Demo)
After demo-ing what we had working to the professor, we've been given an opportunity to give a make-up demo to show more subsystem functionality. 

We started by hooking up an Arduino Uno Rev3 to the camera module. We've created a circuit on a breadboard in order for the microcontroller to interface with the camera sensor properly. By using software on the laptop, we're able to retrieve image data from the sensor. However, the image data takes 20 seconds to retrieve, and the image data is full of white lines and noise. We've realized that the image sensor is not very good and high quality. Definitely not to the point where we would be able to accurately perceive the characters of any text in the image. 

Then we worked on hooking the solenoids up to the Arduino so that we can show that the solenoids are properly hooked up and can display braille characters. For the previous final demo, we just power each of the solenoids so that we show that each of them "work" but the professor wanted to see them displaying braille characters. We wrote simple scripts so that the solenoids run through the braille alphabet. 

I will bring a monitor and keyboard to show that the python script running through the dataset to calculate the testing accuracy actually works and runs on the external microcontroller for the make-up demo. The professor wanted to see it running on the microcontroller and not just on my laptop (which is what I did for the previous final demo). 
