# Purpose of the drone
## Motivation
Modern drones are designed to control the motors via PWM. This method is easy to implement as most autopilots have PWM outputs and most ESCs require PWM for control. However, it is believed that this approach is bad for drone control. PWM signals are vulnerable to distortion from strong electromagnetic fields and do not use data integrity checking or redundancy. This leads to reduced feedback quality in the Kalman filter. To avoid this it is suggested to use a digital CAN bus.

## Suggestion 
