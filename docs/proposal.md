# Project Proposal

## 1. Motivation & Objective

What are you trying to do and why? (plain English without jargon)

As technological sensors improve in their capabilities, their pool of possible applications also continues to widen. One main area of development is the use of technology in sports, with basketball being among the most prominent of them. This is the motivation for the current project, in which I aim to use both sensor data to help basketball players hone their shooting technique down to a science. By collecting QVAR Neuromuscular data and IMU acceleration data, the goal is to build a model to ensure that the athlete's muscles are firing with the exact same intensity and their arm is moving in the exact same manner for every shot.

## 2. State of the Art & Its Limitations

How is it done today, and what are the limits of current practice?

Currently, one of the most prominent ways to track and hone one's basketball shooting tendencies using technology is a mobile app named "HomeCourt" (https://www.homecourt.ai/). The app is officially partnered with the NBA, and uses machine vision with a smartphone camera to track statistics such as release angle, release time, ball speed, release time, and more. Although this application provides a numerous data points from the visual input from the camera, one area in which it is lacking is biological data, such as which muscles are being used and how much they are being exerted. This particular area of limitation is where this project fits in, with the goal of providing another form of data to help perfect the science of shooting a basketball.

## 3. Novelty & Rationale

What is new in your approach and why do you think it will be successful?

The novelty in this approach comes from the use of the QVAR sensor. This is a newly developed sensor that is sensitive to very small changes in charge, making it able to detect neuromuscular signals which travel through the body when a muscle is recruited. By pinpointing the muscles that are recruited when shooting a basketball and placing the sensors in positions to detect the signals from those specific muscles, the goal is to collect a new form of data that can aid in building a more consistent basketball shot form.
I believe this new approach will be successful, as this sort of data has never been collected before (to my knowledge) and has the potential to provide a completely new level of insight to the sport.

## 4. Potential Impact

If the project is successful, what difference will it make, both technically and broadly?

If successful, this project opens up a whole new horizon of possibilities for development with QVAR sensors. Specifically in just the field of sports, athletes are always working to become more consistent at shooting, throwing, kicking, or any other physical movement. This successful project will serve as not only a tool for basketball players to become more consistent in their shooting, but also as a proof or concept for future similar applications in other sports such as football, soccer, weightlifting and more, where neuromuscular data from these sensord could be analyzed to ensure proper form and optimal muscle recruitment when performing any physical action.

## 5. Challenges

What are the challenges and risks?

There are challenges along every step of the way for this project, from data collection to processing to drawing conclusions from the data. For data collection, one challenge will be figuring out where to place the electrodes on the arm for the best readings. After the data has been collected, the next challenge will be figuring out how to process the data and which, if any, machine learning algorithm could be best applied to create a moedl whic could then be used to draw conclutions from the data. All of this, of course, will be under the time constraint of this class.

## 6. Requirements for Success

What skills and resources are necessary to perform the project?

This project will require both hardware and software skills, as an analog preprocessing circuit may be required for proper collection of the EMG data from the QVAR electrodes, and most, if not all, of the data processing will likely be done using python. Some embedded coding may also be used, as the sensor chips have the capabilities of implementing some form of processing on the chip itself.
In terms of resources, the main elements are the sensors along with everything else that seves as a peripheral to the sensors (Sensortile box, electrodes, phone app, etc.). These resources will all be from STMicroelectronics, the company that has developed these state-of-the-art QVAR sensors.

## 7. Metrics of Success

What are metrics by which you would check for success?

I will measure the success of the project by how well it is able to classify a basketball shot using the QVAR and IMU data, and the quality of the statistics that it will measure. The two main statistics that I will be looking at are acceleration (from the IMU), and the EMG data from the QVAR sensors. If these readings are consistent and can clearly be shown to characterize the strength, accuracy, etc. of a basketball shot, then the project will be considered a success. 

## 8. Execution Plan

Describe the key tasks in executing your project, and in case of team project describe how will you partition the tasks.

The main tasks for this project are data collection, processing, and interpreting the processed data. As there is only one member in the group there is no way to partition the work, so I (Umair) will be the sole contributor throughout each step of the project.

## 9. Related Work

### 9.a. Papers

List the key papers that you have identified relating to your project idea, and describe how they related to your project. Provide references (with full citation in the References section below).

Long-Term Polygraphic Monitoring through MEMS and Charge Transfer for Low-Power Wearable Applications [1]. This paper describes the work of a group that used STMicroelectronics QVAR  sensors, similar to the ones that will be used in this project, to acquire multiple different biopotentials from a subject's body, such as ElectroCardioGram (ECG) data. This paper provides a good reference for how the group collected the data, including things such as an analog preprocessing circuit.

MyoBuddy: Detecting Barbell Weight Using Electromyogram Sensors [2]. In this paper, researchers used dedicated Electromyography (EMG) sensors to detect muscular activity during weightlifting exercises. Although the sensors used in the MyoBuddy project are different than the QVAR sensors, the application of muscular EMG data collection is the same, so this paper provides good reference for this specific application of data.


### 9.b. Datasets

List datasets that you have identified and plan to use. Provide references (with full citation in the References section below).

As this is such a novel application, there are no existing datasets that have been found that can be used for this project.

### 9.c. Software

List softwate that you have identified and plan to use. Provide references (with full citation in the References section below).

To collect data from the sensors themselves, the software that will be used is the sensortile.box android app. The data processing will be done either partially on the chip by using STM32CubeProgrammer[3] and partially on Google Colab[4], or entirely on Google Colab.

## 10. References

List references correspondign to citations in your text above. For papers please include full citation and URL. For datasets and software include name and URL.

[1] Manoni A, Gumiero A, Zampogna A, Ciarlo C, Panetta L, Suppa A, Della Torre L, Irrera F. Long-Term Polygraphic Monitoring through MEMS and Charge Transfer for Low-Power Wearable Applications. Sensors. 2022; 22(7):2566. https://doi.org/10.3390/s22072566 

[2] Bo-Jhang Ho, Renju Liu, Hsiao-Yun Tseng, and Mani Srivastava. 2017. MyoBuddy: Detecting Barbell Weight Using Electromyogram Sensors. In Proceedings of the 1st Workshop on Digital Biomarkers (DigitalBiomarkers '17). Association for Computing Machinery, New York, NY, USA, 27–32. https://doi.org/10.1145/3089341.3089346

[3] STM32CubeProgrammer Software: https://www.st.com/en/development-tools/stm32cubeprog.html

[4] Google Colab Notebooks: https://colab.google/
