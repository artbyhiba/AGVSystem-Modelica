# AGVSystem: Modelica-Based Automated Guided Vehicle Digital Twin

A modular Modelica library for simulating an Automated Guided Vehicle (AGV) with vehicle dynamics, tire-ground interaction, sensor noise, actuator models, and controller validation.

## Overview

This project implements a digital twin of an AGV in Modelica. The system includes:
- Longitudinal and lateral vehicle dynamics
- Yaw motion and position tracking
- Wheel-ground traction and slip modeling
- Ground friction and hill scenarios
- BLDC motor, motor driver, and geartrain models
- Noisy encoder and IMU sensor models
- Replaceable P, PI, and PID controllers
- Validation and example models for subsystem and system-level testing

<img width="3179" height="4494" alt="Digital Twin Presentation" src="https://github.com/user-attachments/assets/de6e5ace-733a-42bd-89bd-26413f2a2ff7" />

## Main Features

- Modular AGV architecture using package-based Modelica design
- Replaceable controllers for comparative control studies
- Sensor noise injection for realistic feedback simulation
- Split-mu and hill-climb ground scenarios
- Energy and power analysis support
- Dedicated validation cases for traction, planar motion, slope effects, and electrical behavior

## Package Structure

```text
AGVSystem
├── Vehicles
├── Validation
├── Utilities
├── Sensors
├── Interfaces
├── Examples
├── Controllers
├── Components
└── Actuators
```

## Key Models

### Vehicles
- `AGV`: Main integrated AGV model including chassis motion, wheel forces, gravity effect, and controller interface.

### Components
- `WheelGround`: Tire-road interaction and traction/slip behavior.
- `GroundModel`: Terrain height, slope, and friction scenario definition.
- `DriveUnit`: Motor, gearbox, wheel, and encoder assembly.
- `ChassisAdapter`: Adapter for causal interaction with translational connector variables.

### Sensors
- `IMU`: Measures longitudinal/lateral acceleration and yaw rate with Gaussian noise.
- `Encoder`: Measures wheel speed with injected measurement noise.

### Actuators
- `BLDCMotor`: Voltage-to-torque motor model with viscous friction.
- `MotorDriver`: Converts control command to drive voltage.
- `Geartrain`: Speed reduction and torque transmission model.

### Controllers
- `SimpleController`: Proportional controller.
- `PIController`: Proportional-integral controller.
- `PIDController`: Proportional-integral-derivative controller.

## Validation Models

- `TractionTest`
- `SlopeTest`
- `PlanarMotionTest`
- `NoiseValidationTest`
- `EnergyAnalysisTest`
- `ElectricalTest`
- `ControlPerformanceTest`

## Example

- `CompleteFunctionalTest`: Full AGV response to a speed step input.

## Requirements

- OpenModelica
- Modelica Standard Library 4.0.0

## How to Use

1. Open the `AGVSystem` package in OpenModelica.
2. Load the package and dependencies.
3. Open any model under `Examples` or `Validation`.
4. Simulate the selected model.
5. Plot relevant variables described in each model documentation.

## Suggested Plots

- `agv.velocity_longitudinal`
- `agv.position_x`, `agv.position_y`
- `agv.yaw_angle`
- `agv.measured_velocity_average`
- `agv.imu.out_accel_x.u`
- `total_power`, `total_energy`

## Future Work

- Path-following control
- Battery and powertrain efficiency modeling
- State estimation and sensor fusion
- Fault injection and robustness analysis
- Multi-AGV coordination scenarios
