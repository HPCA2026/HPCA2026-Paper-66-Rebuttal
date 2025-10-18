
# Actual Measurement Results of HR-DCIM Silicon Verification

&nbsp;&nbsp; This document provides the measured results of HR-DCIM silicon verification. The measurement report includes three parts: 1) Chip Micrograph and Summary of Silicon Verification; 2) Test Platform Setup for Silicon Verification; 3) Measurement Results of Silicon Verification. Key measured metrics include: **area/energy efficiency, accuracy, cell error distribution, bit error rate (BER), and iteration latency.** Compared to the simulation results presented in the paper, **the average deviation between simulation and actual silicon verification results is less than 2%.**

## Chip Micrograph and Summary of Silicon Verification

&nbsp;&nbsp; Figure 1 presents the HR-DCIM chip micrograph, the scaling curves of frequency versus voltage, and summarizes the measurement results of the silicon verification. HR-DCIM is fabricated in 28nm CMOS technology, with **2.45×1.47mm<sup>2</sup>** die area. The chip can work at **0.55~1.0V** supply, **95~500MHz,** with power consumption of only **4.01~48.35mW.** HR-DCIM supports both floating-point (BF16) and integer (INT8) precision for NN acceleration. **The peak performance reaches 0.51TOPS for INT8 and 0.46TFLOPS for BF16 at 1.0V, 500MHz. The highest macro energy efficiency is 36.07TOPS/W for INT8 and 30.39TFLOPS/W for BF16 at 0.65V, 165MHz.**


![image]([images/Die Photo.png](https://github.com/HPCA2026/HPCA2026-Paper-66-Rebuttal/blob/main/images/Die%20Photo.png))

