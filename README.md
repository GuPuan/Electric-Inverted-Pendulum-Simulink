# Inverted Pendulum Modelling and Control

## Introduction
This project simulates an inverted pendulum system using MATLAB's Simulink. The primary goal is to stabilize the inverted pendulum to a user-specified angle. The control system is built using a PID controller and various modules, such as PWM, DC motors, and planetary gears. The simulation demonstrates effective control with a closed-loop system that meets predefined design specifications within acceptable error margins.

### Key Design Parameters:
| Parameter                       | Value  | Unit       |
|----------------------------------|--------|------------|
| Mass of the object (m)           | 0.3    | kg         |
| Length of the pendulum (L)       | 0.6    | m          |
| Speed reduction rate of gear (n) | 2      | unitless   |
| Inertia of gear (Jt)             | 0.01   | kg⋅m²      |

## System Overview

### 1. DC Motor and Planetary Gear Subsystem
This subsystem includes various components such as the **DC Motor**, **Gear Box**, **Rotational Friction**, and **Torque Sensors**. The input signal is processed via **PWM** and a **PID controller**, generating the input voltage required for the DC motor. The motor parameters are as follows:

| Parameter            | Value    | Unit     |
|----------------------|----------|----------|
| Armature resistance   | 0.0609   | Ohms     |
| Armature inductance   | 0.023    | mH       |
| Torque constant       | 46       | m⋅Mn/A   |
| DC supply voltage     | 18       | V        |
| Rotor inertia         | 1380     | cm²⋅g    |

### 2. PID Control and PWM Subsystem
This subsystem implements a **PID controller** that adjusts the pendulum's angle by controlling the motor's input voltage. The **PWM generator** outputs a pulse signal every 0.01 seconds. The PID controller uses **P = 80**, **I = 10**, and **D = 10** for the default configuration.

### 3. Gyroscope and Sensor Fusion Subsystem
A **gyroscope** is employed to collect angular velocity, with noise introduced to simulate real-world conditions. A **bandpass filter** is used to filter out noise, allowing cleaner data for further processing. An **optical encoder** works alongside the gyroscope to enhance sensor accuracy using sensor fusion.

### 4. Planetary Gear Nonlinearity Simulation
To simulate a non-linear gear system, rotational friction was added to the gear subsystem, including parameters such as breakaway friction torque and viscous friction torque.

| Parameter                    | Value | Unit |
|------------------------------|-------|------|
| Breakaway friction torque     | 2     | N⋅m  |
| Coulomb friction torque       | 2     | N⋅m  |
| Viscous friction torque       | 1     | N⋅m⋅s/rad |

### 5. Multibody Simulation
The simulation was further enhanced with **Multibody Simulation** tools such as **Solid Bricks** and **Revolute Joints** to represent the inverted pendulum physically. Real-world parameters, such as rod length and object mass, were incorporated to improve accuracy.

### 6. System Testing and Tuning
The system's response was evaluated by changing the P, I, and D values. The results showed that increasing the proportional gain (P) resulted in a faster response, while increasing the integral gain (I) reduced steady-state error. The derivative gain (D) smoothened the response.

#### Figures:
- P tuning: 20, 60, 100
- I tuning: 1, 5, 10
- D tuning: 1, 10, 20

## Conclusion
This project successfully simulates the control of an inverted pendulum using a PID controller in MATLAB Simulink. The system can achieve stable control with minimal error, providing insight into the dynamics of pendulum stabilization.

## Requirements
- **MATLAB** with **Simulink** package
- **Maxon Motor 353294** (DC motor specifications used)
- Basic understanding of PID control and multibody simulations

## References
1. Maxon Motor 353294. [Link](https://www.maxongroup.com/maxon/view/product/353294)

## How to Run
1. Open MATLAB and load the Simulink model.
2. Input desired pendulum angle.
3. Run the simulation and adjust the PID parameters if needed for better control.

