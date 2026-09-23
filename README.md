# 2D Mobile Robot Localization and EKF-SLAM

A Python-based 2D mobile robot localization and landmark estimation simulation using motion prediction, range/bearing measurements, and an Extended Kalman Filter(EKF) update process.

## Overview

In autonomous mobile robotics, a robot operating without GPS needs to estimate its position based on its surrounding environment.

SLAM (Simultaneous Localization and Mapping) addresses this problem by allowing a robot to estimate its position while building or updating a representation of its surroundings.

This project explores the localization and landmark-estimation aspects of this problem in a simplified 2D simulation. The robot moves through an environment containing fixed landmarks and uses simulated range and bearing measurements to estimate the robot and landmark states.

## Project Objective

The objective of this project was to simulate the movement and localization of a mobile robot using sensor measurements from known landmarks.

The implementation demonstrates:

- 2D robot motion
- Robot pose estimation
- Landmark representation
- Range measurements
- Bearing measurements
- Motion prediction
- Measurement updates
- Covariance propagation
- Jacobian matrices
- Kalman gain calculation
- Noisy sensor measurements
- Landmark initialization
- Robot and landmark state estimation

## Robot Pose

The robot pose is represented as:

(x, y, θ)

where:

- `x` represents the robot's position along the x-axis
- `y` represents the robot's position along the y-axis
- `θ` represents the robot's orientation

The robot state is maintained together with the estimated positions of the landmarks.

## Landmarks

The simulation contains three fixed landmarks:

- Landmark 0: `(5, 5)`
- Landmark 1: `(10, 2)`
- Landmark 2: `(6, 8)`

The robot observes landmarks when they fall within the simulated sensor range.

## Sensor Measurements

The robot uses simulated:

- Range measurements
- Bearing measurements

Range represents the distance between the robot and a landmark.

Bearing represents the relative direction of the landmark from the robot.

Noise is added to the simulated measurements to represent uncertainty in sensor observations.

## Motion Prediction

The robot motion is predicted using a simple velocity-based motion model.

The simulation uses:

- Linear velocity `v = 1.0`
- Angular velocity `w = 0.1`
- Time step `dt = 0.1`

The predicted position is calculated using the robot's current orientation and motion inputs.

The covariance matrix is also propagated during the prediction step using the motion Jacobian and process-noise matrix.

## Measurement Update

After the motion prediction, the robot checks the distance to each landmark.

Only landmarks within a simulated sensor range of `8.0` units are considered.

For observed landmarks, the simulation:

1. Generates a noisy range and bearing measurement.
2. Initializes a landmark if it has not previously been observed.
3. Calculates the expected measurement for known landmarks.
4. Calculates the measurement residual.
5. Normalizes the bearing error.
6. Calculates the measurement Jacobian.
7. Calculates the innovation covariance.
8. Calculates the Kalman gain.
9. Updates the robot and landmark state.
10. Updates the covariance matrix.

This allows the estimated state to be corrected using the simulated sensor observations.

## Technologies
1. Python
2. NumPy
3. Extended Kalman Filter concepts
4. Motion modelling
5. Sensor modelling
6. Robot localization
7. Landmark estimation

## What I Learned

Through this project, I gained practical experience with:

1. Mobile robot localization
2. Robot motion modelling
3. Range and bearing measurements
4. Sensor uncertainty
5. State estimation
6. Covariance matrices
7. Jacobian matrices
8. Kalman filtering concepts
9. Landmark estimation
10. Implementing robotics algorithms in Python

## Future Improvements

Possible improvements to the project include:

1. Adding a graphical visualization of the robot and landmarks
2. Plotting the estimated robot trajectory
3. Comparing estimated and true robot positions
4. Visualizing landmark uncertainty
5. Adding more landmarks
6. Testing different sensor noise levels
7. Adding additional motion models
8. Extending the simulation toward a more complete SLAM implementation


## Author

Lemark Santos

## Simulation Results

The simulation produces estimated robot poses and landmark positions at regular intervals.

Example output:

```text
Step 0:
  Robot: (0.10, 0.00, 0.01)
  L0: (4.98, 5.00)

Step 10:
  Robot: (1.00, -0.08, 0.09)
  L0: (4.98, 5.01)

Step 20:
  Robot: (1.93, -0.06, 0.18)
  L0: (4.98, 5.01)

Step 30:
  Robot: (2.58, 0.19, 0.25)
  L0: (4.98, 4.99)
  L1: (9.95, 1.96)

Step 40:
  Robot: (3.30, 0.41, 0.35)
  L0: (4.98, 4.99)
  L1: (9.95, 1.96)

```text
2d-mobile-robot-ekf-slam/
│
├── 2d_mobile_robot_ekf_slam.ipynb
├── README.md
└── images/
    └── simulation-output.png
