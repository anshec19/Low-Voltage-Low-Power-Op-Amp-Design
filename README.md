# Low-Voltage-Low-Power-Op-Amp-Design
This project focuses on designing a low-voltage, low-power operational amplifier using composite cascode architecture and indirect feedback compensation. The design leverages subthreshold operation to minimize power consumption, making it suitable for applications like ECG signal amplification.
# Introduction: 

In recent years, the demand for low-voltage and low-power portable electronic devices has surged. Operational amplifiers (op-amps) are critical components in analog circuits, especially in applications such as biomedical signal processing. However, designing op-amps to operate under low-voltage and low-power conditions presents significant challenges in achieving high gain and bandwidth. This project aims to develop a low-voltage, low-power CMOS operational amplifier that enhances gain and bandwidth while maintaining stability, making it suitable for biomedical applications requiring precise signal amplification.



# PROBLEM STATEMENT:

Low-voltage op-amps often face significant challenges in achieving high gain and wide bandwidth due to the inherent constraints imposed by low supply voltages. These limitations become particularly problematic in high-performance applications such as biomedical signal processing, where accurate and reliable amplification of small signals, like those in ECG monitoring, is crucial. In such cases, achieving both high gain and fast response times is essential to ensure precise signal acquisition and processing, making it critical to overcome these design bottlenecks for effective real-time medical diagnostics.

This project aims to achieve high DC gain by simulating an optimized low-power operational amplifier at a low supply voltage using various MOS technologies in LTSpice. The proposed op-amp is expected to exhibit a superior figure of merit (FOM) compared to existing designs, showcasing enhanced performance.

# Design Description:

# Composite Cascode Topology:
A composite cascode structure is used in the opamp to enhance the gain and output impedance. This technique reduces the Miller effect, allowing for better frequency response and bandwidth, critical for the amplification of low-frequency signals like those in ECG (typically around 0.5 Hz to 100 Hz).The cascode arrangement also ensures better voltage headroom, which is important when working with the low supply voltage of ±0.5V.

# Indirect Feedback Compensation:
Indirect feedback compensation is employed to stabilize the opamp and improve its overall performance across different frequencies. The feedback loop indirectly adjusts the gain, ensuring stable operation without directly influencing the input transistors.
This compensation technique helps manage the high gain provided by the composite cascode structure, ensuring that the opamp remains stable, especially in low-power and low-frequency applications.

# Subthreshold Operation:
The subthreshold region is utilized for the operation of the MOS transistors to achieve ultra-low power consumption. In this mode, the transistors operate at very low currents, which significantly reduces power dissipation.
This technique is particularly effective for low-voltage opamps designed for biomedical applications, where minimizing power consumption is essential.
The subthreshold operation provides an efficient way to meet the low-power requirements while still achieving a sufficient gain for ECG signal amplification.

# Low-Power Supply (±0.5V):
The opamp is designed to operate with a ±0.5V power supply, suitable for ultra-low power applications. This low-voltage supply is appropriate for wearable and portable medical devices, where battery life is a critical consideration. Despite the low voltage, the design ensures sufficient headroom and functionality by carefully selecting the biasing points and utilizing the composite cascode and subthreshold techniques effectively.

# Performance Targets:

* Gain:
The opamp is expected to provide a gain sufficient to amplify weak ECG signals, with a targeted gain in the range of 10,000 (40 dB or more), depending on the exact configuration.

* Bandwidth:
The bandwidth of the opamp should cover the typical frequency range of ECG signals, ensuring low distortion and accurate amplification.

* Power Consumption:
The total power consumption will be minimized by leveraging the subthreshold operation, ensuring the opamp is suitable for low-power applications.

* Stability:
The use of indirect feedback compensation ensures that the high gain from the composite cascode stage does not lead to instability, making the opamp reliable for ECG signal amplification.

# The Circuit:

![alt text](https://github.com/user-attachments/assets/b7fe89d5-a35b-4087-a5e1-82c4bfe2f921)
# Design Calculations:

* Assumptions and Values used:
  * Single ended output is taken
  * M1 and M2 are identical
  * M3 and M4 are identical
  * Higher current flows in outer circuit to provide high swing, than in the inner circuit
  * µpCox = 50 µAV-2 	   and          µnCox = 100 µAV-2
  * λp = 0.052 V-1                       and          λn = 0.011 V-1
  * Vthp = -0.4 V	                      and          Vthn = 0.4 V
  * Av1 = Vx/Vin	   	   and	  Av2 = Vout/Vx
  * Open Loop Gain = Av = Av1 x Av2

* Power = 8mW
* Vdd = 3.3V
* Id = 8mW/3.3V = 2.424242 mA

![alt text](https://github.com/nikhil1198/2-Stage-Operational-Amplifier/blob/master/calc.JPG)

# LTSpice Simulation Results:
* Input:

![alt text](https://github.com/nikhil1198/2-Stage-Operational-Amplifier/blob/master/input.JPG)

* Operation Point Analysis:

![alt text](https://github.com/nikhil1198/2-Stage-Operational-Amplifier/blob/master/op1.JPG)        ![alt text](https://github.com/nikhil1198/2-Stage-Operational-Amplifier/blob/master/op2.JPG)

* Frequency Response: 

  * The frequency response (Bode Plot curve) of the two stage op amp simulated is similar to a single pole one stage op amp in the required bandwidth (operation region)
  * The second pole occurs at 800MHz(P2=gm6/Cl , approx.) which in insignificant to our amplifier operation.
  * The only zero occurring at Z1=gm6/Cc  because of Miller capacitor introduced(Cc) is at 1.25 GHz(approx.) which is also insignificant to our operation.
  * Hence the Bode plot is as shown and is equivalent to a one pole system till a few hundred MHz  (until we have significant gain)

![alt text](https://github.com/nikhil1198/2-Stage-Operational-Amplifier/blob/master/out123.JPG)
 
# Conclusion:

* A common “workhorse” opamp for medium performance applications.
* A reasonably simple structure with reasonable performance
* Design issues introduced : Two poles close to each other introduced. Very poor phase margin and instability until high load capacitance used.
* Hence, the Concept of pole splitting introduced to decrease (shift left ) the dominant pole frequency which introduced because of stage one, causing stability

# Summary:

* A two stage OpAmp is designed with the given specifications. 
* First, a hand design was done followed by simulation in LTspice IV. The results are in agreement with the required value with a very small trade-off.
* The trade-off may be due to neglecting body effect or any other transistor in built properties.
