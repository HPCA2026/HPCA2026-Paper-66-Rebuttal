
# Actual Measurement Results of HR-DCIM Silicon Verification

&nbsp;&nbsp; This document provides the measured results of HR-DCIM silicon verification. This measurement report includes three parts: *1) Chip Micrograph and Summary of Silicon Verification;* *2) Test Platform Setup for Silicon Verification;* *3) Measurement Results of Silicon Verification.* **Key measured metrics include: area/energy efficiency, accuracy, cell error distribution, bit error rate (BER), and iteration latency.** Compared to the simulation results presented in our paper, **the average deviation between simulation and actual silicon verification results is less than 2%.**

## 1. Chip Micrograph and Summary of Silicon Verification

&nbsp;&nbsp; Figure 1 presents the HR-DCIM chip micrograph, the scaling curves of frequency versus voltage, and summarizes the measurement results of the silicon verification. HR-DCIM is fabricated in 28nm CMOS technology, with **2.45×1.47mm<sup>2</sup>** die area. The chip can work at **0.55~1.0V** supply, **95~500MHz,** with power consumption of only **4.01~48.35mW.** HR-DCIM supports both floating-point (BF16) and integer (INT8) precision for NN acceleration. **The peak performance reaches 0.51TOPS for INT8 and 0.46TFLOPS for BF16 at 1.0V, 500MHz. The highest macro energy efficiency is 36.07TOPS/W for INT8 and 30.39TFLOPS/W for BF16 at 0.65V, 165MHz.**

<div align="center">
	<img src="https://github.com/HPCA2026/HPCA2026-Paper-66-Rebuttal/blob/main/images/Die%20Photo.png" alt="Editor" width="600">
</div>
<div align=center>
  Figure 1: HR-DCIM’s chip micrograph, voltage-frequency scaling curve, and specifications.
</div>


## 2. Test Platform Setup for Silicon Verification

&nbsp;&nbsp; Figure 2 illustrates the test platform for the fabricated HR-DCIM silicon verification. The system is composed of a HR-DCIM test chip, Xilinx VC709 FPGA board, DC power, oscilloscope, and host computer. The test dataset and NN model are stored in the FPGA board's DDR3 memory. The FPGA sends control signals and data to the HR-DCIM test chip board via the FPGA mezzanine connector (FMC). The DC power supplies 0.55~1.0V core voltage for the test chip. The oscilloscope observes the test chip's state signals. The computer uses Vivado 2020.1 to generate bitstream and program it into the FPGA board to set up the test platform. During computation, the test chip sends computing results to the FPGA. The computer receives the results transferred from the FPGA and probes FPGA's internal key signals. The screen displays the results and signals in Vivado, which can be used for further analysis.

<div align="center">
	<img src="https://github.com/HPCA2026/HPCA2026-Paper-66-Rebuttal/blob/main/images/Test%20Platform.png" alt="Editor" width="600">
</div>
<div align=center>
  Figure 2: Test platform for the fabricated test chip. The FPGA sends control signals and data to the test chip. The DC power supplies 0.55~­1.0V voltages for the test chip. The results from the test chip are collected by the FPGA and then sent to the computer.
</div>


## 3. Measurement Results of HR-DCIM Silicon Verification

### 3.1 Accuracy Measurement versus Block Bit-widths for BF16 and INT8

&nbsp;&nbsp; This part presents the actual measured accuracy of HR-DCIM silicon verification. As mentioned in our paper, for the same design, we can select any block bit-widths (4b, 8b, 12b, and 16b) for HR-DCIM based on reliability requirements. Therefore, we evaluated the actual measured accuracy versus operating voltages with different block bit-width parameter settings for HR-DCIM chip, including gating error correction logic (i.e., block bit-width = 0b), block bit-width = 4b, block bit-width = 8b, block bit-width = 12b, and block bit-width = 16b. Figure 3 and Figure 4 illustrate the actual measured accuracy under different voltages with different block bit-widths and voltages for BF16 and INT8 formats, respectively. **Compared the simulation results with block bit-width = 8b in our paper, the average accuracy deviation of the simulation and the measurement results of silicon verification is less than 2%.**

<div align="center">
	<img src="https://github.com/HPCA2026/HPCA2026-Paper-66-Rebuttal/blob/main/images/Accuracy-BF16.png" alt="Editor" width="600">
</div>
<div align=center>
  Figure 3: Accuracy measurement results of HR-DCIM silicon verification under different operating voltages and block bit-width parameter settings for the BF16 format.  
</div>  

&nbsp;
<div align="center">
	<img src="https://github.com/HPCA2026/HPCA2026-Paper-66-Rebuttal/blob/main/images/Accuracy-INT8.png" alt="Editor" width="600">
</div>
<div align=center>
  Figure 4: Accuracy measurement results of HR-DCIM silicon verification under different operating voltages and block bit-width parameter settings for the INT8 format.
</div>

### 3.2 Measurements Results of Cell Error Distribution and BER  

&nbsp;&nbsp; This part shows the actual cell error distribution and bit error rate (BER) of HR-DCIM silicon verification under different operating voltages. For the BER evaluation, we also select different block bit-width parameter settings for the HR-DCIM chip, similar to the accuracy evaluation in Sec.3.1.  Figure 5 illustrate the measured cell error distribution versus voltage scaling (Left) and the BER versus voltage scaling with different block bit-widths (Right). **Compared the simulation results with block bit-width = 8b in our paper, the average BER deviation of the simulation and the measurement results of silicon verification is less than 1.86%.**

<div align="center">
	<img src="https://github.com/HPCA2026/HPCA2026-Paper-66-Rebuttal/blob/main/images/BER-Cell%20Error%20Distribution.png" alt="Editor" width="600">
</div>
<div align=center>
 Figure 5: Left: Cell error distribution versus operating voltages of HR-DCIM silicon verification. Right: BER versus operating voltages of HR-DCIM silicon verification with different block bit-width parameter settings.
</div>

### 3.3 Actual Iteration Latency Measurement versus Block Bit-widths

&nbsp;&nbsp;  Figure 6 shows the measured average iteration latency of HR-DCIM silicon verification across different block bit-widths. Our silicon-verified HR-DCIM features 137b×128 CIM macros with the correction hardware parallelism = 8, as mentioned in our paper. The theoretical worst-case iteration latency is shown in Figure 6-Right. **Even using the smallest block bit-width (i.e., 4b) with the highest aliasing degree (137b / 4b ≈ 35), its worst-case iteration latency is still much less than CIM bit-serial computing cycles.** In other words, **the iteration correction can be fully overlapped by CIM bit-serial computation without introducing additional latency.**

<div align="center">
	<img src="https://github.com/HPCA2026/HPCA2026-Paper-66-Rebuttal/blob/main/images/Latency.png" alt="Editor" width="600">
</div>
<div align=center>
    Figure 6: Left: Average iteration latency versus block bit-widths of HR-DCIM silicon verification. Right: Theoretical worst iteration latency under different block bit-widths for HR-DCIM chip, where we use the ceiling function to round it up to the nearest integer, thereby ensuring our theoretical model covers the worst-case latency boundary.
</div>



