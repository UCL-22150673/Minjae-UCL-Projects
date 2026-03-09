4. Real-Time Audio Descrambler (FPGA) (Dec 2025)

UCL ELEC0008 Scenario Project

Project Overview

A real-time audio descrambler implemented on DE0 Nano FPGA to recover a secret scrambled message. 

This project was part of a scenario where criminals used audio scrambling to hide their plans, and the goal was to descramble the intercepted message to prevent a robbery.

Key Objectives

Analyze scrambled audio signals in time and frequency domains using MATLAB

Reverse-engineer the scrambling algorithm

Implement real-time digital filters on FPGA

Reconstruct clear audio from scrambled input

Technical Implementation

1. Signal Analysis (MATLAB)

Imported original and scrambled WAV files (44.1kHz sampling frequency)

Performed time-domain and frequency-domain analysis

Reverse-engineered the scrambling algorithm by comparing signal characteristics

Determined appropriate filter specifications for descrambling

2. Digital Filter Design

Used MATLAB's filterDesigner tool to design FIR/IIR filters

Quantized filters to 12-bit fixed-point for FPGA implementation

Generated Verilog code for digital filters

Selected optimal sampling frequency (50kHz) for high-fidelity reconstruction

3. FPGA Implementation (DE0 Nano)

Implemented real-time FIR/IIR digital filters in Verilog

Developed SPI interface drivers for ADC/DAC communication

Integrated PLL block for clock generation

Used Signal Tap Logic Analyzer to verify internal signals

4. Hardware Integration

Connected external ADC for scrambled audio input

Connected external DAC for descrambled audio output

Designed anti-aliasing analogue filters (Sallen-Key topology)

Verified timing compliance with logic analyzer

Technologies/Tools Used

Category	Tools

Analysis	MATLAB (audioread, filterDesigner, FFT analysis)

FPGA Design	Quartus II, Verilog HDL, Signal Tap Logic Analyzer

Hardware	DE0 Nano FPGA, ADC, DAC, oscilloscope, logic analyzer

Filters	FIR/IIR digital filters, Sallen-Key active analogue filters

Communication	SPI protocol, PLL clock generation

