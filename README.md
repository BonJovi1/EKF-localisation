# EKF-localisation
Estimating the 2D pose of a robot using sensor measurements by applying an Extended Kalman Filter (EKF). \
If the notebook doesn't load, use the jupyter nbviewer. Here's the [link](https://nbviewer.jupyter.org/github/BonJovi1/EKF-localisation/blob/master/code.ipynb)

## The Question:
A ground robot is driving amongst a set of known landmarks. The robot has a wheel odometer that measures its translational and rotational speeds, and a laser rangefinder that measures the range and bearing to the landmarks. Both the sensors are noisy. We need to estimate the 2D pose of the robot throughout its traversal using these sensor measurements by applying an Extended Kalman filter.

The motion model and the sensor model has been given, and the data is provided in the form of a numpy archive file (dataset.npz). It contains the following variables:

- t: a 12609 × 1 array containing the data timestamps [s].
- x true: a 12609 × 1 array containing the true x-position, xk, of the robot [m].
- y true: a 12609 × 1 array containing the true y-position, yk, of the robot [m].
- th true: a 12609 × 1 array containing the true heading, θk, of the robot [rad].

- l: a 17 × 2 array containing the true xy-positions, (xl, yl), of all the 17 landmarks [m].
- r: a 12609 × 17 array containing the range, rkl , between the robot’s laser rangefinder and each landmark as measured by the laser rangefinder sensor [m]  (a range of 0 indicates the landmark was not visible at that timestep).

- r var: the variance of the range readings (based on groundtruth) [m2].
- b: a 12609 × 17 array containing the bearing, φlk, to each landmark in a frame attached to the laser rangefinder, as measured by the laser rangefinder sensor [rad]  (if the range is 0 it indicates the landmark was not visible at that timestep and thus the bearing is meaningless). The measurements are spread over a 240° horizontal-FoV, and the bearing is 0° when the landmark is straight ahead of the rangefinder.
- b var: the variance of the bearing readings (based on groundtruth) [rad2].
- v: a 12609×1 array containing the translational speed, vk, of the robot as measured by the robot’s
odometers [m/s].
- v var: the variance of the translational speed readings (based on groundtruth) [m2/s2].
- om: a 12609×1 array containing the rotational speed, ωk, of the robot as measured by the robot’s odometers [rad/s].
- om_var: the variance of the rotational speed readings (based on groundtruth) [rad2/s2]. d: the distance, d, between the center of the robot and the laser rangefinder [m].

Apply EKF and estimate the trajectory of the robot. 
