# Navi-Qart: Design and Implementation of an Autonomous Shopping Cart with Grid-Based Navigation
> **Note:** Source code is currently private/closed-source for now. This repo showcases the project's design and documentation only.
## Overview
Short demo video of the robotic prototype in action: https://drive.google.com/file/d/1f9SJoHW_AML_yuuXWlHzMW8oweRDozNU/view?usp=sharing

Grocery shopping is a routine task but can pose significant challenges, especially for elderly individuals, people with mobility limitations, or those managing health-related concerns such as allergies. Traditional
shopping carts provide no assistance, leaving users to manage navigation, product search, and physical effort independently. For the public, the process remains time-consuming and inefficient. 

Navi-Qart is an intelligent shopping cart system designed to make the grocery shopping experience easier, faster, and more convenient for everyone. It combines modern technologies such as sensors, navigation systems, and
a smart application to assist users in finding products, avoiding obstacles, and managing their shopping lists efficiently. The cart can guide shoppers through store aisles and even provide real-time information such as
allergy concerns or health risks.

In simple terms, Navi-Qart acts as a personal shopping assistant that helps customers move around the store effortlessly. By reducing the physical effort of pushing heavy carts and the stress of searching for items, it
enhances accessibility for elderly shoppers, individuals with mobility challenges, and busy customers alike. The goal is to create a seamless and enjoyable shopping experience through innovation and automation. 

## Implementation
The Navi-Qart system integrates power management, motor control and sensor processing through a central Raspberry Pi 5 controller. The battery pack provides 14.8 V input, which is regulated using an adjustable buck
converter (or step-down transformer) to 12 V, usable by the L298-Motor Driver to power the robot’s wheels. In addition, the 22.5W power bank is used to exclusively power the processing unit of the design (Raspberry Pi 5).
GPIO pins 12 and 13 from the Raspberry Pi control the DC motors’ speed using Pulse-Width Modulation (PWM) and pins 5, 6, 17 and 21 are used to control the direction of the rotation of the motors. The RPLIDAR A1M8 connects
via USB for real-time distance feedback. All components share a common ground reference for circuit integrity.

<img width="940" height="449" alt="image" src="https://github.com/user-attachments/assets/eb959797-ff86-4604-a462-184032e0b43a" />

To develop the mobile app for users, Flutter Framework was used. The application communicates with Firebase using real-time database APIs (such as set, get, update and remove) to instantly sync data across all connected
users.

Using Flutter’s StreamBuilder tool, any change made in the database is immediately reflected on the app’s reactive UI, eliminating the requirement for manual refreshing and ensuring up-to-date information display. Below
are some snapshots of a live shopping session, where the users begins by connecting to a robot, then placing an item inside the cart.

<img width="348" height="634" alt="image" src="https://github.com/user-attachments/assets/0d7e9bfc-bee1-44f1-a21b-fdb715fe02b5" />
<img width="356" height="639" alt="image" src="https://github.com/user-attachments/assets/c7395dec-31d5-455d-ae0f-2db152445303" />
<img width="360" height="619" alt="image" src="https://github.com/user-attachments/assets/88dc7e90-0cd1-4224-a570-0a81b64808d8" />

## How It Works
The Navi-Qart system begins operation when the user selects a robotic cart that is unoccupied on Navi-Qart’s mobile app. Once a robot is selected, the robot is synced with the profile of the user, where it can receive
commands directly from the mobile app (e.g. drive to the milk section), then the robot starts to move to that location based on the pre-downloaded map of the store, all while avoiding live obstacles. 

As items are placed in the cart, the RFID scanner embedded near the cart’s storage area automatically identifies each product. These items are then added to a virtual shopping list within the app, allowing the system to
maintain an accurate digital checklist of all products currently in the cart. Once the shopping session is complete, the user can review and pay online directly through the app using the list generated via RFID scanning.

<img width="360" height="619" alt="image" src="https://github.com/user-attachments/assets/a3d3838f-4ced-4f84-8c9f-322c7eefa034" />

