---
layout: post
title: AISecurity–An End-to-End Facial Recognition Sign-In System
---

AISecurity is a machine-learning-driven addition to Millburn’s security system. It leverages facial recognition in order to better monitor the flow of people in and out of the school, and was built by the students of the Millburn AI program, a part of the Computer Science Integrated Initiative.

After approval from educational officials (school principal, district superintendent, and district technology officer), AISecurity has been cleared to be a part of Millburn High School's regular sign-in system. Since AISecurity is a production system rather than a research project, there are no awards to list.

*AISecurity is a team project, of which I am the lead programmer and founder.*

### Goals
This project seeks to enhance security while simultaneously providing a learning opportunity for students in the AI program. Inspired by Millburn High School’s student leaders, AISecurity is a significant step forward in terms of student-led community initiatives. Through this project, my team and I have learned invaluable real-world skills while creating a novel and privacy-conscious way to better our school environment.

### Implementation

AISecurity is a full-stack project consisting of several parts:

1. **Physical kiosks**

<img style="float:left;margin:0px 15px 0px 35px" src="/public/kiosks.png" width="312" height="311"> 
The outmost physical component of AISecurity is a wooden kiosk, designed to house the necessary hardware for sign-in to work. On the left, three kiosk frames are displayed during the development process.

The frames were custom-cut and ordered for this sign-in system. 
<br><br><br>

2. **Edge computing hardware**

   AISecurity uses the [Jetson Nano](https://developer.nvidia.com/embedded/jetson-nano-developer-kit) and a [CSI camera](https://www.raspberrypi.org/products/camera-module-v2/) to run facial recognition. A 15W power bank is used to power the Jetson Nano and its peripherals, making the system lightweight and portable. All hardware is housed in the wooden kiosk frame.

3. **Facial recognition software**

   The software consists of integration at the hardware level, face detection, and face recognition. Face detection is done through a multi-task cascaded network, trained in Python TensorFlow and deployed in Cython/C++ NVIDIA TensorRT. A [pretrained FaceNet CNN](https://github.com/davidsandberg/facenet) was used as the base of the facial recognition program. All computational graphs were optimized and exported to TensorRT.

4. **Database communications**

   The facial recognition software interfaces with a MySQL database with student pictures and IDs. A Django server provides a GUI used by the security office during sign-in/sign-out periods such as lunchtime. Student picture data is encrypted with AES to ensure that personal information is always secure.

5. **User-facing hardware**

   Embedded into the wooden kiosk frame are an LCD display and a keypad. The LCD display is used to communicate with the user (i.e., ID has been accepted or not), and the keypad is a redundancy in the event that the facial recognition system goes temporarily offline.

### Privacy Concerns

In addition to Millburn’s cybersecurity system, AISecurity has an internal three-point security defense to ensure that any personal data is inaccessible by humans.

1. **Database processing**

   Instead of storing actual images, AISecurity relies on an AI algorithm to convert pictures into a format that is not recognizable by humans or machines. This transformation cannot be reversed: it is not possible to retrieve the original image from the processed result.

2. **Encryption**

   As another security measure, AISecurity will take the processed database and apply AES encryption to it. AES is a NIST-approved and currently unbroken encryption algorithm used by the US government since 2002 for top classified information.

3. **Locality**

   All data is stored locally on the school server. As a result, it would be difficult anyone to access these images without permission.

### Slide Presentation
<object data="/public/aisecurity.pdf" type="application/pdf" width="720px" height="    405px">
  <p>If your browser doesn't support inline PDF viewing, you can see my presen    tation <a href="/public/aisecurity.pdf">here</a>.</p>
</object>
