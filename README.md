# Purpose of the drone
## Motivation
Modern drones are designed to control the motors via PWM. This method is easy to implement as most autopilots have PWM outputs and most ESCs require PWM for control. However, it is a poor approach for controlling drones. PWM signals are vulnerable to distortion from strong electromagnetic fields and do not use data integrity checking or redundancy. This leads to reduced feedback quality in the Kalman filter. To avoid this it is suggested to use a digital CAN bus.

## Suggestion 
Replacing the control signal with a CAN bus will increase the stability of the system. To test the Cyphal and DroneCAN protocols, a drone design was developed. To perform the tests, the drone design is changed according to the following list:

 - [x] PWM flights. Autopilot cables go directly from the autopilot to the ESC.
 - [x] DroneCAN flights. CAN cables go from the autopilot to the [PWM Node](https://raccoonlab.co/tproduct/360882105-449815179261-cyphal-and-dronecan-pwm-node-v2), and then PWM cables go to the ESC
 - [x] Cyphal flights. CAN cables go from the autopilot to the [PWM Node](https://raccoonlab.co/tproduct/360882105-449815179261-cyphal-and-dronecan-pwm-node-v2), and then PWM cables go to the ESC
 - [ ] Cyphal flights. CAN cables go from the autopilot to [Myxa](https://zubax.com/products/myxa)

## Results

### PWM

