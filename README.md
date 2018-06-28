# CarND-PID-Control-Project
Self-Driving Car Engineer Nanodegree Program

In this project, a PID Controller was implemented for a car that drives on a track in the Udacity Simulator Enviroment. At each time step, the cross track error is received from the simulator and is used as input for a PID controller. The PID controller outputs the steering angle of the car. 

The chosen parameters were: 

* proportional control gain: **-0.15**
* integral control gain: **0**
* differential control gain: **-5.5**

This provided a good balance between steering power and damping, even at higher speeds. The gain for the integral control was left to 0, since no bias seemed to be present in the steering control action. Also, I tried very small valus and the car seemed to start drifting. 

In addition, a simple linear mapping between steering angle and throttle was implemented, such that the car safely reduces speed in sharper turns. 
The minimum throttle was considered 0.2, and the maximum 0.8. For the steering angle, the minimum angle was considered -1.0 and the maximum 1.0.

The equation used was:
```c
throttle = 0.2 + (1.0 - abs(steer_angle))*(0.8 - 0.2)
```

With this tuning, the car reaches a top speed between 78-80 mph while still staying on track (although it makes some very sharp turns). 

## Considerations
* A nonlinear mapping betwen throttle and steering wheel would have probably been better, reducing the speed even more drastically in very sharp turns, but not so much in wider turns. 
* A moving average filter of a few frames would make the steering a bit smoother, although introducing a slight time delay.

