# Purpose of the drone
## Motivation
Modern drones are designed to control the motors via PWM. This method is easy to implement as most autopilots have PWM outputs and most ESCs require PWM for control. However, it is a poor approach for controlling drones. PWM signals are vulnerable to distortion from strong electromagnetic fields and do not use data integrity checking or redundancy. To avoid this it is suggested to use a digital CAN bus.

## Suggestion 
Replacing the control signal with a CAN bus will increase the stability of the system. To test the Cyphal and DroneCAN protocols, a drone design was developed. To perform the tests, the drone design is changed according to the following list:

 - [x] PWM flights. Autopilot cables go directly from the autopilot to the ESC.
 - [x] DroneCAN flights on [RaccoonLab PWM NODE v2](https://raccoonlab.co/tproduct/360882105-449815179261-cyphal-and-dronecan-pwm-node-v2)
 - [x] Cyphal flights on [RaccoonLab PWM NODE v2](https://raccoonlab.co/tproduct/360882105-449815179261-cyphal-and-dronecan-pwm-node-v2)
 - [ ] Cyphal flights on [Zubax Robotics Myxa](https://zubax.com/products/myxa)

## Drone

### CAD

Render of a quadcopter:

![renderQuadcopter](https://github.com/olegogogo/Cyphal-Drone/assets/45263316/24a4b8bc-7d8c-483f-a6e9-f7a338418e70)

Sensors: 

In addition to ESC Node, [MUX](https://raccoonlab.co/tproduct/360882105-264880131491-can-mux), [ESC Current sensor](https://raccoonlab.co/tproduct/390642159-585609994241-bec-and-current-sensor) and [GNSS module](https://raccoonlab.co/tproduct/390642159-261315362991-cyphal-and-dronecan-gnss-f9p-magnetomete) were used in this work:

![image](https://github.com/olegogogo/Cyphal-Drone/assets/45263316/d9e95d90-4db3-4565-9f48-ea6afa46ec92)


## Results

The data of all flights are recorded in a table. Below the table you will find the wiring diagrams for each flight

| Protocol | Flight Time | Maneuvers | Wind Speed | Flight Date | Log Link | Video Link |
|----------|-------------|-----------|------------|-------------|----------|------------|
| Cyphal   | 1.35 min    | Turns, right, left, circle | 4.5 m/s | 21 May 2024 | [Log](https://review.px4.io/plot_app?log=d568d1c8-1d69-4ec4-ada4-c3bba3c6452f) | [Video](https://youtu.be/OQSTiOVPHFI) |
| Cyphal   | 2.31 min    | Turns, right, left, circle, up | 3.9 m/s | 23 Apr 2024 | [Log](https://review.px4.io/plot_app?log=e5a8ef8b-2a77-4e41-ab36-2fea505b1bb5) | [Video](https://youtu.be/5DsmymIM6T4) |
| Cyphal   | 1.08 min    | Turns, right, left, circle | 4.7 m/s | 22 Apr 2024 | [Log](https://review.px4.io/plot_app?log=9430bbb8-d338-49f2-aeb1-94bf418a2b03) | [Video](https://youtu.be/HDFo5cQEWIE) |
| Cyphal   | 2.19 min    | Turns, circle, up | 4.2 m/s | 18 Apr 2024 | [Log](https://review.px4.io/plot_app?log=50bcc929-d9f1-4c23-8f3b-0aff1351e8ce) | [Video](https://youtu.be/DMQ_uFp9GC8) |
| DroneCAN | 12.20 min   | Turns, right, left | 3.8 m/s | 28 Mar 2024 | [Log](https://review.px4.io/plot_app?log=267315de-17ea-458a-a083-d736de84dffb) | [Video](https://youtu.be/I_uR951W_0I) |
| DroneCAN | 5.41 min    | Turns, right, left, circle | 4.0 m/s | 26 Mar 2024 | [Log](https://review.px4.io/plot_app?log=1a95ffb9-f365-4d48-9dae-9e10be2324c9) | [Video](https://youtu.be/-_-Hau36b2o?si=XCnLyRr9R_jYNAQt) |
| DroneCAN | 5.39 min    | Turns, right, left, circle, up | 3.7 m/s | 11 Mar 2024 | [Log](https://review.px4.io/plot_app?log=4a3cf87a-0712-4381-9e35-fb9721ceb05d) | [Video](https://youtu.be/0hR0CX1QG-s) |
| PWM      | 3.29 min    | Up, rotation, forward, swaying | 5.0 m/s | 31 Jan 2024 | [Log](https://review.px4.io/plot_app?log=15b0ad61-4d66-4981-8859-f853cad3dc1c) | [Video](https://www.youtube.com/watch?v=bF6pm1bQ9Ks) |
| PWM      | 3.20 min    | Low flight, drifting | 4.8 m/s | 30 Jan 2024 | [Log](https://review.px4.io/plot_app?log=9a09421f-5872-44e7-a61a-f9717f8e9e5b) | - |


### PWM

The connection via PWM was the first one. The wiring diagram is shown below:

![PWMsheme](assets/PWMMOTOR.png)

Flight: [video](https://www.youtube.com/watch?v=bF6pm1bQ9Ks) | [log](https://review.px4.io/plot_app?log=15b0ad61-4d66-4981-8859-f853cad3dc1c)

Flight: [log](https://review.px4.io/plot_app?log=9a09421f-5872-44e7-a61a-f9717f8e9e5b)

### DroneCAN
Diagram:

![CANsheme](assets/CANPWMMOTOR.png)

Flight: [video](https://youtu.be/0hR0CX1QG-s) | [log](https://review.px4.io/plot_app?log=4a3cf87a-0712-4381-9e35-fb9721ceb05d)

Flight: [video](https://youtu.be/-_-Hau36b2o?si=XCnLyRr9R_jYNAQt) | [log](https://review.px4.io/plot_app?log=1a95ffb9-f365-4d48-9dae-9e10be2324c9)

Flight: [video](https://youtu.be/I_uR951W_0I) | [log](https://review.px4.io/plot_app?log=267315de-17ea-458a-a083-d736de84dffb)

### Cyphal on PWM Node v2
Diagram is the same:

![CANsheme](assets/CANPWMMOTOR.png)

Flight: [video](https://youtu.be/DMQ_uFp9GC8) | [log](https://review.px4.io/plot_app?log=50bcc929-d9f1-4c23-8f3b-0aff1351e8ce)

Flight: [video](https://youtu.be/HDFo5cQEWIE) | [log](https://review.px4.io/plot_app?log=9430bbb8-d338-49f2-aeb1-94bf418a2b03)

Flight: [video](https://youtu.be/5DsmymIM6T4) | [log](https://review.px4.io/plot_app?log=e5a8ef8b-2a77-4e41-ab36-2fea505b1bb5)

Flight: [video](https://youtu.be/OQSTiOVPHFI) | [log](https://review.px4.io/plot_app?log=d568d1c8-1d69-4ec4-ada4-c3bba3c6452f)


### Cyphal on Myxa (work in progress)
Diagram:

![CANsheme](assets/CANMOTOR.png)

**work in progress**
