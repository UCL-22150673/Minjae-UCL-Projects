Real-Time Audio Descrambler (FPGA) (Dec 2025)

UCL ELEC0008 Scenario Project

1. Project Overview
   
A real-time audio descrambler implemented on DE0 Nano FPGA to recover a secret scrambled message. This project was part of a scenario where criminals used audio scrambling to hide their plans, and the goal was to descramble the intercepted message to prevent a robbery.

2. Key Objectives

Analyze scrambled audio signals in time and frequency domains using MATLAB

Reverse-engineer the scrambling algorithm

Implement real-time digital filters on FPGA

Reconstruct clear audio from scrambled input

3. Technical Implementation

1) Signal Analysis (MATLAB)

Imported original and scrambled WAV files (44.1kHz sampling frequency)

Performed time-domain and frequency-domain analysis

Reverse-engineered the scrambling algorithm by comparing signal characteristics

Determined appropriate filter specifications for descrambling

2) Digital Filter Design

Used MATLAB's filterDesigner tool to design FIR/IIR filters

Quantized filters to 12-bit fixed-point for FPGA implementation

Generated Verilog code for digital filters

Selected optimal sampling frequency (50kHz) for high-fidelity reconstruction

3) FPGA Implementation (DE0 Nano)

Implemented real-time FIR/IIR digital filters in Verilog

Developed SPI interface drivers for ADC/DAC communication

Integrated PLL block for clock generation

Used Signal Tap Logic Analyzer to verify internal signals

4) Hardware Integration

Connected external ADC for scrambled audio input

Connected external DAC for descrambled audio output

Designed anti-aliasing analogue filters (Sallen-Key topology)

Verified timing compliance with logic analyzer

3. My Contribution

I was responsible for the DAC interface validation and analog output verification. I successfully generated and smoothly output a 7 kHz sine wave, which was essential for confirming the system's fundamental analog output capabilities before processing actual audio signals. Maintaining the signal's smoothness demonstrated precise control over the DAC interface timing and SPI communication protocol. This validation step ensured that once the descrambling filters were applied, the reconstructed audio would be output without distortion or glitches. My work provided confidence that the hardware layer was reliable, allowing the team to focus on optimizing the digital filter performance.

4. Technologies/Tools Used

Analysis: MATLAB (audioread, filterDesigner, FFT analysis)

FPGA Design: Quartus II, Verilog HDL, Signal Tap Logic Analyzer

Hardware: DE0 Nano FPGA, ADC, DAC, oscilloscope, logic analyzer

Filters: FIR/IIR digital filters, Sallen-Key active analogue filters

Communication: SPI protocol, PLL clock generation

