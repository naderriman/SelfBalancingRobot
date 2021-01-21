# SelfBalancingRobot

I started by designing this project on fusion 360. Every component is 3d printed.


After finishing 3D printing, the first goal was to be able to balance itself. I used an Arduino MEGA because it has 6 timers (timer interrupts are required to precisely control the stepper motors). A cascaded PID loop is used for control, this inside loop is for controlling the angle and the outside loop is for controlling the velocity. 
I first started with the inner loop by giving the controller a certain angle and tuning the response based on it's behaviour.
However balancing based on a certain angle is not enough because the robot will always drift eventually, therefore we have to control the velocity of the robot.
After having tuned the outer velocity loop, the robot should remain stable at his position given a zero velocity reference.
The next stage is to test the dynamics of the robot by giving a step velocity and check the behavior while fine tuning the PID gains.
After perfecting the velocity, i worked on implementing the steering, which works as differential.

At this stage the robot is fully functioning and I further tested it's dynamics by adding an RC receiver and controlled it with an RC controller.

While developping the robot I was working in parallel on a LIDAR sensor equivalent. I bought a ToF laser sensor (Tof 10120) and mounted it on a servo (mg90s). The sensor is calibrated by checking the data and creating a 2D LIDAR map on PYTHON. ![alt text](https://github.com/[naderriman]/[SelfBalancingRobot]/blob/[main]/delay20.png)

This sensor is interfaced on another Arduino (UNO), the calculations are made on the arduino and the data is sent to the Arduino MEGA through I2C communication.
