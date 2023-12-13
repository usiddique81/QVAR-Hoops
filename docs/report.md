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

## 1. Motivation & Objective

As technological sensors improve in their capabilities, their pool of possible applications also continues to widen. One main area of development is the use of technology in sports, with basketball being among the most prominent of them. This is the motivation for the current project, in which I used multimodal sensor data to help basketball players hone their shooting technique down to a science. By collecting both QVAR Neuromuscular data and IMU acceleration data, I was able to build a training system to help ensure that the athlete's muscles are firing with the exact same intensity and their arm is moving in the exact same manner for every shot.

## 2. State of the Art & Its Limitations

Currently, one of the most prominent ways to track and hone one's basketball shooting tendencies using technology is a mobile app named "HomeCourt" (https://www.homecourt.ai/). The app is officially partnered with the NBA, and uses machine vision with a smartphone camera to track statistics such as release angle, release time, ball speed, release time, and more. Although this application provides a numerous data points from the visual input from the camera, one area in which it is lacking is biological data, such as which muscles are being used and how much they are being exerted. This particular area of limitation is where this project fits in, with the goal of providing another form of data to help perfect the science of shooting a basketball.

## 3. Novelty & Rationale

The main aspect of novelty in this approach comes from the use of the QVAR sensor. This is a newly developed sensor by STMicroelectronics that is sensitive to very small variances in charge, making it able to detect neuromuscular EMG (Electromyographic) signals which travel through the body when a muscle is recruited. By pinpointing the muscles that are recruited when shooting a basketball and placing the sensors in positions to detect the signals from those specific muscles, We are able to collect a new form of data that can aid in building a more consistent basketball shot form.

## 4. Potential Impact

This project can serve as a proof of concept to open up a whole new horizon of possibilities for development with QVAR sensors. Specifically in just the field of sports, athletes are always working to become more consistent at shooting, throwing, kicking, or any other physical movement. This successful project will serve as not only a tool for basketball players to become more consistent in their shooting, but also as a proof or concept for future similar applications in other sports such as football, soccer, weightlifting and more, where neuromuscular data from these sensors could be analyzed to ensure proper form and optimal, consistent muscle recruitment when performing any physical action.

## 5. Challenges

There were challenges along every step of the way for this project, from data collection to processing to drawing conclusions from the data. For data collection, one challenge was ensuring noiseless collection of data, as there were many outside factors that could affect the readings, especially from the QVAR sensor. After the data was collected, the next challenge was figuring out how to process the data and which type of algorithm could be best applied to accomplish the necessary tasks of identifying and comparing the shots taken from the data signals. All of this was done also within the time constraint of the class.

## 6. Requirements for Success

This project required both hardware and software skills. Proper setup and calibration of the sensor chips themselves was required for accurate data collection of the EMG data from the QVAR electrodes as well as proper IMU Data collection. All of the data postprocessing was done using a python jupyter notebook, so knowlegde in that field was required as well.
In terms of resources, the main elements are the sensors along with everything else that seves as a peripheral to the sensors (Sensortile box, electrodes, phone app, etc.). These resources are all from STMicroelectronics, the company that has developed these state-of-the-art QVAR sensors. The Jupyter notebook was ran on Google Colaboratory.

## 7. Metrics of Success

I measured the success of the project by how well it was able to classify a basketball shot using the QVAR and IMU data, and the quality of the signals that were measured. The two main statistics that I looked at were acceleration (from the IMU), and the EMG data from the QVAR sensors. These readings were consistent and could clearly be shown to characterize a basketball shot. Another metric of success was whether I could output a metric which measured the consistency of the shots taken. This was also successful, as I was able to have the system calculate a "Consistency score" for both the IMU and the QVAR data. 

# 2. Related Work



# 3. Technical Approach

# 4. Evaluation and Results

# 5. Discussion and Conclusions

# 6. References
