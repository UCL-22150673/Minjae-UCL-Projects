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

5. Performance Results

Power Analysis:

Battery 1 (0V~9V): 44.5mA ~ 140mA → 0.4W ~ 1.26W

Battery 2 (-9V~0V): ~3.7mA → 0.033W

Motor (when used): ~0.3A → ~1.8W

Overall (without motor): 0.043W ~ 1.29W

Majority of power consumed by Arduino and output circuits

Noise Analysis:

ADC noise (electrodes disconnected): <5mV

ADC noise (electrodes connected): ~20mV rms (due to electrode pick-up)

Estimated SNR for the system: 36.9dB

Signal Processing:

MAV estimation through precision rectification and integration

Step size: ~25 ADC counts per LED

Saturation: Full LED bar activation at sensorValue ≥ 200

6. Testing Methodology
   
1) Benchtop Testing:

Tested each block individually using signal generator

Verified frequency response and transient response through simulations

Confirmed output after each processing stage

2) Electrode Testing:

sEMG recording from forearm muscles

Appropriate electrode placement research and implementation

Real-time signal acquisition and processing

3) Output Verification:

LED bar response to varying muscle contraction levels

Buzzer activation at threshold

Servo motor proportional control

7. Ethical & Safety Considerations

Electrical Safety: Electrodes used only with battery-powered system after supervisor check; avoided mains-powered connection to the body

Risk Mitigation: On-body tests performed only on batteries with all mains instruments disconnected

Supervisor Check: System inspected by laboratory supervisor before bio-signal measurements

Privacy: EMG signals processed in real-time to prevent any privacy concerns

8. What I Learned (My Contributions)
Technical Contributions:

Buzzer Control Implementation: Programmed the audio feedback system using Arduino, setting appropriate thresholds and ensuring reliable activation

Output Integration: Worked on integrating multiple output modalities (LED, buzzer, servo) with the sEMG signal

Testing & Debugging: Assisted in benchtop testing and verification of system blocks

Code Optimization: Contributed to Arduino code development for responsive real-time control

Team Collaboration:

Worked alongside team members (Jiangtian, Mathis, Yifei) on different system components

Participated in design discussions and decision-making processes

Contributed to the 10-slide final presentation preparation

Assisted in troubleshooting during electrode testing phase
