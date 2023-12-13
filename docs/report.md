# Table of Contents
* Abstract
* [Introduction](#1-introduction)
* [Related Work](#2-related-work)
* [Technical Approach](#3-technical-approach)
* [Evaluation and Results](#4-evaluation-and-results)
* [Discussion and Conclusions](#5-discussion-and-conclusions)
* [References](#6-references)

# Abstract

As athletes continue to look to improve their game in many facets, one of the main emerging ways to help them do this is through technology. For basketball players, one of the main points of training is having as consistent of a shot as possible. By using both accelerometer and neuromuscular data from numerous sensors, this project aims to use that data to help basketball players ensure that their shots are as consistent as possible from a neuromuscular standpoint as well as in terms of arm trajectory. This is done by collecting data from IMU and STMicroelectronics-QVAR sensors, and processing it to classify different characteristics of an athlete's basketball shot form. The collected data is then consolidated into one main signal to characterize the "macro" movement of the player's arm (IMU Acceleration Data), and one main signal to characterize the "micro" movement (QVAR Neuromuscular Data). These two characterizing signals are then analyzed using a cosine similarity function, which identifies all of the shots taken and calculates a consistency score, which is then outputted to give the user a notion of the level of consistency of their shots from an acceleration and neuromuscular standpoint. This data can then be used to supplement an athlete's training regimen and improve their form consistency over time.

# 1. Introduction

## a. Motivation & Objective

As technological sensors improve in their capabilities, their pool of possible applications also continues to widen. One main area of development is the use of technology in sports, with basketball being among the most prominent of them. This is the motivation for the current project, in which I used multimodal sensor data to help basketball players hone their shooting technique down to a science. QVAR sensing is a new field of sensing that was recently introduced by STMicroelectronics, and has the potential to see use in amny differnet fields of application. QVAR atands for charge(Q) variance(var), and so these sensors are able to detect very small changes in electrostatic potential, even down to the EMG (Electromyographic) signals that are emitted by muscles when they contract. By collecting both this QVAR Neuromuscular data and IMU acceleration data, The objective was to be able to build a training system which could help ensure that the athlete's muscles are firing with the exact same intensity and their arm is moving in the exact same manner for every shot.

## b. State of the Art & Its Limitations

Currently, one of the most prominent ways to track and hone one's basketball shooting tendencies using technology is a mobile app named "HomeCourt" (https://www.homecourt.ai/). The app is officially partnered with the NBA, and uses machine vision with a smartphone camera to track statistics such as release angle, release time, ball speed, release time, and more. Although this application provides a numerous data points from the visual input from the camera, one area in which it is lacking is biological data, such as which muscles are being used and how much they are being exerted. This particular area of limitation is where this project fits in, with the goal of providing another form of data to help perfect the science of shooting a basketball.

## c. Novelty & Rationale

The main aspect of novelty in this approach comes from the use of the QVAR sensor. This is a newly developed sensor by STMicroelectronics that is sensitive to very small variances in charge, making it able to detect neuromuscular EMG (Electromyographic) signals which travel through the body when a muscle is recruited. By pinpointing the muscles that are recruited when shooting a basketball and placing the sensors in positions to detect the signals from those specific muscles, We are able to collect a new form of data that can aid in building a more consistent basketball shot form.

## d. Potential Impact

This project can serve as a proof of concept to open up a whole new horizon of possibilities for development with QVAR sensors. Specifically in just the field of sports, athletes are always working to become more consistent at shooting, throwing, kicking, or any other physical movement. This successful project will serve as not only a tool for basketball players to become more consistent in their shooting, but also as a proof or concept for future similar applications in other sports such as football, soccer, weightlifting and more, where neuromuscular data from these sensors could be analyzed to ensure proper form and optimal, consistent muscle recruitment when performing any physical action.

## e. Challenges

There were challenges along every step of the way for this project, from data collection to processing to drawing conclusions from the data. For data collection, one challenge was ensuring noiseless collection of data, as there were many outside factors that could affect the readings, especially from the QVAR sensor. After the data was collected, the next challenge was figuring out how to process the data and which type of algorithm could be best applied to accomplish the necessary tasks of identifying and comparing the shots taken from the data signals. All of this was done also within the time constraint of the class.

## f. Requirements for Success

This project required both hardware and software skills. Proper setup and calibration of the sensor chips themselves was required for accurate data collection of the EMG data from the QVAR electrodes as well as proper IMU Data collection. All of the data postprocessing was done using a python jupyter notebook, so knowlegde in that field was required as well.
In terms of resources, the main elements are the sensors along with everything else that seves as a peripheral to the sensors (Sensortile box, electrodes, phone app, etc.). These resources are all from STMicroelectronics, the company that has developed these state-of-the-art QVAR sensors. The Jupyter notebook was ran on Google Colaboratory.

## g. Metrics of Success

I measured the success of the project by how well it was able to classify a basketball shot using the QVAR and IMU data, and the quality of the signals that were measured. The two main statistics that I looked at were acceleration (from the IMU), and the EMG data from the QVAR sensors. These readings were consistent and could clearly be shown to characterize a basketball shot. Another metric of success was whether I could output a metric which measured the consistency of the shots taken. This was also successful, as I was able to have the system calculate a "Consistency score" for both the IMU and the QVAR data. 

# 2. Related Work

As mentioned earlier, a company which does related work to this project, namely in the basketball sector, is Homecourt.ai. This smartphone app designed by previous apple engineers uses machine vision algorithims on video data from a phone camera to determine statistics about a player's shooting form, among other things. This can be seen in the screenshot below, in which it shows the app containing data such as release angle, leg angle, release time, and release height, along with some other shot metrics. This app uses advanced ML algorithms to process the visual data and gather meaningful information, but is limited to only gathering information that can be obtained visually.
<p align="center">
<img src="https://github.com/usiddique81/QVAR-Hoops/assets/150395293/34f0ff14-9a54-4dd9-9c3e-df54c406fb35" height="200" class="center"/>
</p>
In terms of application of QVAR technology, one company that is at the forefront of this is a venture called Pison Technology (https://pisontechnology.com). This company uses QVAR electrodes placed on the wrist to measure very minute and precise hand movements/gestures. This company claims to be able to detect ENG (ElectroNeurography) signals, which are the signals that the brain sends to the muscles to tell them to contract. This means that they are able to detect the movement before it even occurs. The possible application of this technology is widespread, with Pison advertising its possible uses in fields such as interfacing with smart home devices, augmented and virtual reality, and more.
<p align="center">
<img src="https://www.irongatevc.com/wp-content/uploads/2023/07/Pison-ALS.png" height="200" class="center"/>
</p>
# 3. Technical Approach

The technical approach for this project has two main steps: data collection, and data consolidation/processing, which then leads to the final output and the results of the entire system. In this section, I will be discussing both the data collection process as well as the data processing aspects.

## a. Data Collection

To be able to use the data from the QVAR and IMU sensors, the first logical step is to ensure proper data collection methods. Both of these sensors were on STMicroelectronics sensor chips, which would be connected to a SensortileBox.PRO. This sensortile box would then wirelessly connect to an android device from which I could alter certain parameters of data collection within the sensors if necessary. Once calibrated, I could press a button to have the sensortile box begin logging the desired data, which would be saved on a MicroSD card that was already inserted into the sensortile. Once data collection was complete, I would then remove the SD card from the box and connect it to my computer, and proceed to copy over the collected data onto my device for processing.

In terms of the setup for the IMU sensor, there was not much configuration of the sensor itself, as there were no parameters for me to alter in the Sensortile android app for this sensor. However, one area of challenge for IMU data collection was reagrding the placement of the sensor itself. Initially, I had planned to place the sensor on the back of the hand (as shown below) in order to collect the most accurate and representative IMU data, which would best model the acceleration that was seen by the basketball during the course of a shot.
<p align="center">
<img src="https://github.com/usiddique81/QVAR-Hoops/assets/150395293/03b6bda4-83c8-4442-a1ba-7630a3ef6715" height="200" />
</p>
However, during initial data collection tests, I found out that this sensor placement configuration would cause some issues. This was particularly due to the nature of the action of shooting a basketball, as the flicking of the wrist creates a strong jolt for the sensor. This would cause the IMU sensor to fall off from the back of my hand repeatedly during testing, essentially rendering the data useless. I decided to circumvent this by moving the placement of the IMU sensor down to the upper forearm (as shown below), just below the wrist rather than just above it. This would deal with the issue of the sensor falling off during testing, but still allow for precise IMU data to be collected, and for the data to still be characteristic of the shooting action taking place.
<p align="center">
<img src="https://github.com/usiddique81/QVAR-Hoops/assets/150395293/8c640a3d-68d6-47f9-96b8-f371375ef808" height="200" />
</p>
In addition to IMU data, the main focus of this project was the data collected by the state-of-the-art QVAR sensors. As mentioned earlier, these sensors can detect very small changes in electric potentials, making them even able to detect the potential changes that occur when a muscle contracts. This data is collected from electrodes, whic can be placed on the human body itself to measure the electric potential variations within certain body areas or muscle groups. When deciding where to place the electrodes for this particula rapplication, I first did some research on which muscles would be recruited the most. The main muscles that are used when shooting a basketball are those within the forearm, and as shown in the image below, they can be split into two main functional groups: the wrist flexors and the wrist extensors.
<p align="center">
<img src="https://github.com/usiddique81/QVAR-Hoops/assets/150395293/a7401adf-1b49-484f-9fae-ec7f04f3ff3f" height="200" />
</p>
Taking this into account, I began to set up the sensing circuit for the QVAR data. In addition to the Sensor chip and the sensortile box, the folks at STMicroelectronics also provided a multiplexer board (shown below). This board would enable multiple electrodes to be attached to one QVAR Sensor, allowing for data to be collected from multiple places on the body. Because of this capability, I was able to use the multiplexer board to connect two electrodes, one to each main muscle group in the forearm (also shown below).
<p align="center">
<img src="https://github.com/usiddique81/QVAR-Hoops/assets/150395293/f33389e4-f385-4184-a06a-942e3ae763c9" height="200" />
<img src="https://github.com/usiddique81/QVAR-Hoops/assets/150395293/de006018-a2c0-4b47-b18a-4630d4c6519a" height="200" />
</p>
Once the QVAR electrode placement was decided, the next step was to optimize the data collection parameters. A shown below in the screenshot of the sensortile box android app, there are many parameters that can be changed when collecting QVAR Data. The two parameters in specific were the input impedance (Zin) and the Gain of the sensor. These parameters each had 4 possible values, with Zin being either 75, 175, 310, or 520 MegaOhms, and the Gain being either 0.5, 1, 2, or 4. To determine which parameter setting would lead to optimal data collection, I decided to collect QVAR data for 5 shot movements with each possible parameter configuration, and plott them all in a matrix to determine which setting resulted in the best data. This matrix is also shown below, and the final setting that I ended up choosing was a Zin of 520 MegaOhms and a Gain of 2.
<p align="center">
<img src="https://github.com/usiddique81/QVAR-Hoops/assets/150395293/a604daae-a7cc-45a2-bd8a-13c206bcb2e5" height="300" />
<img src="https://github.com/usiddique81/QVAR-Hoops/assets/150395293/72ab10e0-1f54-431b-8c02-61ef53e0e81d" height="300" />
</p>
Once I had the calibration for both sensors figured out, I decided to go to the basketball courts to put up some shots and collect data to use for processing (pictured below, left). However, when I returned and transferred the data to my computer, I saw that the QVAR data was extremely noisy and basically unusable. I determined that this was due to external factors such as the engagement of the forearm muscles when rebounding, catching, or even simply holding a basketball, which weighs 22 oz at regulation. This caused me to downscale the data collection procedure into one that isolates forearm engagement more, by using a smaller ball and hoop, and strictly limiting any movement that isn't shooting a basketball. This new data collection procedure is shown below in the image to the right.
<p align="center">
<img src="https://github.com/usiddique81/QVAR-Hoops/assets/150395293/31439d96-7828-40ea-a880-2c974bf24edc" height="200" />
<img src="https://github.com/usiddique81/QVAR-Hoops/assets/150395293/8cdbdb73-dac2-4898-a9a9-e3b019fa510f" height="200" />
</p>
The updated data collection procedure isolated the desired data as best as possible, and at this point I had clear IMU Data for all 3 axes of motion (X, Y, and Z), as well as 2 channel QVAR data. This data was accurately and clearly representative of the shots that were taken in a given window, and so I decided to move into the data processing stage. Examples of the current state of the 3-axis IMU and 2-channel QVAR data are shown below.
<p align="center">
<img src="https://github.com/usiddique81/QVAR-Hoops/assets/150395293/ce3bc82d-0d17-4adf-98b2-f742a851e4da" height="400" />
</p>

## b. Data Processing

When processing the Data, I had 2 main output results set as a goal: this first was to be able to detect a pattern in the input signals and identify the numbers of shots taken, and the second was to be able to compare all of the shots that were taken and output some sort of consistency metric for both the macro (IMU) and micro (QVAR) movement signals. The first step to accomplishing this was to consolidate all of the IMU and QVAR data into two single signals, rather than the 3-dimensional IMU and 2-dimensional QVAR data that was originally collected. This was fairly trivial for the QVAR sensor data, since as we can see in the above image of the 2-channel QVAR data, each channel sees near identical signals. For this reason, I was able to simply drop off the second channel and only use readings from channel 1. To consolidate all of the IMU information into one signal, I simply calculated the magnitude of the X_accel, Y_accel, and Z_Accel data, and normalized it to zero. This led me to having one final consolidated signal for all of the QVAR information, and one final consolidated signal for all of the IMU information. A sample of these two signals with a dataset in which I took 10 shots is shown in the screenshot below.
<p align="center">
<img src="https://github.com/usiddique81/QVAR-Hoops/assets/150395293/da968b30-8e11-4718-b3d1-8361e37cbb7c" height="200" />
</p>
With all of the data consolidated into a main 'micro' and 'macro' signal, the next step was to implement an algorithm which could detect similar instances within a signal, effectively keeping track of how many shots were taken across the entire span of the signal. One limitation that I had to keep in mind when deciding on an algorithm was that I did not have any lengthy training data sets, so there was no way for me to train any sort of classifier or neural network to be able to detect shots. Because of this, I decided to settle on using a Cosine similarity algorithm, which is very well explained here: (https://builtin.com/machine-learning/cosine-similarity). I manually selected a window in which a shot was taken, then swept that window across the entire length of the signal, keeping track of any instances where the cosine similarities were high enough to reasonably conclude that a shot had been taken. I used this method for both the IMU and QVAR data and it worked successfully. A use of this in the 10-shot data set from earlier is shown below, and as we can see the algorithm correctly Identifies all 10 shots that are taken in both the IMU and QVAR Data:
<p align="center">
<img src="https://github.com/usiddique81/QVAR-Hoops/assets/150395293/40e08229-8364-497a-b7b7-c321699d195e" height="300" />
</p>
Once these shots are collected, the next and final result that is sought is the consistnecy score, or similarity metric between all shots. I again used cosine similarity for this, first by overlaying all of the shots identified by the previous step and then calculating the average similarity between all of the shots that were taken. This final output also ended up being successful, as I will discuss in the Evaluation and Results section.

# 4. Evaluation and Results

As shown earlier in the technical approach section, the first result of the project, the shot counter, was successful and worked as intended. With some tweaking of the code and some parameter optimization, I was able to get the algorithm to properly detect every instance of a shot being taken, in both the QVAR and IMU consolidated signals. However, the counter only serves as a sort of intermediate result, with the main final output being a consistency score along with a graph that players can use to see the of their shot, and work to improve over time. As detailed earlier, this was also calculated using cosine similarity between overlays of all of the identified shots from the previous data processing step. The successful final results of the algorithm from the 10-shot data set are shown below, with the IMU consistency score/graph on the left and the QVAR consistency score/graph on the right.
<p align="center">
<img src="https://github.com/usiddique81/QVAR-Hoops/assets/150395293/ab93e258-8f73-41a6-9a09-86d5c12da15f" height="300" />
<img src="https://github.com/usiddique81/QVAR-Hoops/assets/150395293/ed10862c-94c6-4a85-83fd-135aa1caf77e" height="300" />
</p>

# 5. Discussion and Conclusions

From these results, we can see that this multimodal sensor technology can be used to help players evaluate, track, and, over time, improve the consistency of their basketball shot from a macro level in terms of acceleration, but also a micro level in terms of neuromuscular recruitment. This integrates a completely new level of data collection and a completely new type of sensor into a field that hasn't seen anything like it, and it can serve as a proof of concept for many other implementations of QVAR sensing technology as well. This can be (but isn't limited to) other fields in which both macro and micro movement is combined and people are looking to improve in consistency, such as throwing a football, kicking a soccer ball, throwing a punch, or any other such movement, whether it be sports related or not. There are many other directions in which this project could be taken in the future as well; For example, the STMicroelectronics sensor chips themselves are ML enabled, so with some embedded coding, the shot counting and consistency tracking algorithms could possibly be implemented on the chip itself in order to compute all of the results in real time. Another future direction is to improve the data collection procedure, so that data can be collected from much noisier environments, and the proper features of the shots that are taken can still be isolated and analyzed as they were in this project. This also calls to attention the importance of clear, accurate, and representative data collection, as none of the calculation and conclusions would have worked if the collected data had been inadequate to begin with.

Overall, this project serves as a stepping stone into the domain of QVAR Sensing in sports applications, and serves as a proof of concept to open up a plethora of new areas of development using this state of the art technology.

# 6. References

Manoni A, Gumiero A, Zampogna A, Ciarlo C, Panetta L, Suppa A, Della Torre L, Irrera F. Long-Term Polygraphic Monitoring through MEMS and Charge Transfer for Low-Power Wearable Applications. Sensors. 2022; 22(7):2566. https://doi.org/10.3390/s22072566 

Bo-Jhang Ho, Renju Liu, Hsiao-Yun Tseng, and Mani Srivastava. 2017. MyoBuddy: Detecting Barbell Weight Using Electromyogram Sensors. In Proceedings of the 1st Workshop on Digital Biomarkers (DigitalBiomarkers '17). Association for Computing Machinery, New York, NY, USA, 27–32. https://doi.org/10.1145/3089341.3089346

STM32CubeProgrammer Software: https://www.st.com/en/development-tools/stm32cubeprog.html

Google Colab Notebooks: https://colab.google/

Understanding cosine similarity and its applications. Built In. (n.d.). https://builtin.com/machine-learning/cosine-similarity 

HomeCourt.AI App: https://www.homecourt.ai/

Pison Technology: https://pisontechnology.com

Roberto Merletti; Dario Farina, "Biophysics of the Generation of EMG Signals," in Surface Electromyography: Physiology, Engineering, and Applications , IEEE, 2016, pp.1-24, doi: 10.1002/9781119082934.ch02. https://ieeexplore.ieee.org/document/7471015

