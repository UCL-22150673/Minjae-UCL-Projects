Bio-signal Human Machine Interface (HMI) (Jan 2026)

UCL ELEC0008 Scenario W Project | Group 1

1. Project Overview

A bio-potential acquisition system designed to extract microvolt-level surface Electromyography (sEMG) signals from muscle activity and convert them into intuitive control signals for human-machine interaction. This project was developed as part of the Scenario W assessment at UCL, where we built a prototype HMI that produces audio-visual outputs correlated with the user's muscle activity.

2. Project Motivation & Objectives

Motivation:

Build a simple, low-cost sEMG-based Human-Machine Interface (HMI) that converts muscle activation into intuitive control signals

Overcome the engineering challenge: sEMG signals are low amplitude (microvolt level) and noisy, requiring reliable differential amplification, filtering, and envelope extraction

Demonstrate real-time human-computer interaction through multiple output modalities

Key Objectives:

Design and implement a single-channel sEMG acquisition pipeline producing stable "activation level" (envelope/MAV estimate)

Integrate with Arduino for ADC conversion and output control

Drive two audio-visual outputs (minimum requirement):

LED feedback (bar graph showing activation level)

Audio feedback (buzzer tone correlated with muscle activity)

Ensure electrical safety for human subjects (battery-powered operation only)

3. Technical Implementation

1) Analogue Front-End Design

Instrumentation Amplifier: Differential input configuration to extract microvolt-level sEMG signals while rejecting common-mode noise

Active Filtering: Bandpass filter design to isolate sEMG frequency band (~10 Hz to ~500 Hz)

50 Hz Noise Rejection: Mains interference suppression through differential recording and appropriate referencing

Signal Conditioning: Precision rectification and integration to evaluate Mean Absolute Value (MAV) - a robust amplitude estimator for sEMG

Integrator Design: Corner frequency set to match muscle activation frequency (1 Hz to 2 Hz), distinguishing between sEMG frequency band and muscle contraction rate

2) System Integration

Microcontroller: Arduino UNO for ADC conversion (10-bit resolution, 0-1023 mapping to 0-Vref)

ADC Input: Analog pin A1 reads processed sEMG signal (sensor_value = analogRead(A1))

Output Control Logic:

LED Bar (8 LEDs on pins D6-D13): Level mapping based on sensor value

Buzzer (pin D2): Activates when sensor value exceeds threshold (>100)

Servo Motor (pin D3): Proportional angle control (0° at rest to 180° at full contraction)

3) Output Demonstrations

Visual feedback through LED bar intensity/brightness

Audio feedback through voltage-controlled oscillator driving a speaker

Motion actuation through servo motor (correlated with muscle intensity)

4. Technologies/Tools Used

Analogue Design:	Instrumentation amplifiers, active filters (Sallen-Key topology), precision rectifiers, integrators

Microcontroller:	Arduino UNO, 10-bit ADC, PWM outputs

Output Devices:	LED bar (8 LEDs), buzzer, servo motor

Power:	Dual PP3 batteries (±9V), battery clips

ICs:	LMC660CN/NOPB, LM324N, UA741 op-amps

Passive Components:	Resistors (10Ω to 510kΩ), capacitors (1.6nF to 100nF), diodes (1N4001G)

Software:	Arduino IDE, MATLAB simulations
