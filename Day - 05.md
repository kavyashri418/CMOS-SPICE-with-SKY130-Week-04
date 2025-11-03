# CMOS Power Supply and Device Variation Robustness Evaluation

## Static Behavior Evaluation -  CMOS Inverter Robustness Power Supply Variation
## LAB - 5 Supply Scaling - sky130 Inverter (Wp/Wn=1u/0.36u, L=0.15u)
<details> <summary> SPICE File: day5_inv_supplyvariation_Wp1_Wn036.spice </summary>

```
*** Model Description ***
.param temp=27

*** Including sky130 library files ***
.lib "sky130_fd_pr/models/sky130.lib.spice" tt

*** Netlist Description ***
XM1 out in vdd vdd sky130_fd_pr__pfet_01v8 w=1 l=0.15
XM2 out in 0 0 sky130_fd_pr__nfet_01v8 w=0.36 l=0.15
Cload out 0 50fF
Vdd vdd 0 1.8V
Vin in 0 1.8V

.control
let powersupply     = 1.8
let powersupply_min = 0.8
let increment_step  = -0.2

dowhile powersupply >= powersupply_min
    dc Vin 0 1.8 0.01
    let powersupply = powersupply + increment_step
    alter Vdd = powersupply
end

plot dc1.V(out) dc2.V(out) dc3.V(out) dc4.V(out) dc5.V(out) dc6.V(out) vs in 
+ xlabel 'Input Voltage(V)' ylabel 'Output Voltage(V)' title 'Inverter VTC for different VDD'

plot deriv(dc1.V(out)) deriv(dc2.V(out)) deriv(dc3.V(out)) deriv(dc4.V(out)) deriv(dc5.V(out)) deriv(dc6.V(out)) vs in 
+ xlabel 'Input Voltage(V)' ylabel 'Gain (dVout/dVin)' title 'Inverter Gain for different VDD'
.endc

.end
```
</details>

<img width="1219" height="706" alt="Screenshot 2025-11-03 101848" src="https://github.com/user-attachments/assets/c3b3c4cc-dc32-4338-af59-5080477df6a0" />

We can see from the simulations that:
- The CMOS Inverter continues to work well at even 0.8V (below half the original supply voltage of 1.8V) close to the transistor threshold voltages!
- Since the transistor ratio, $r$ is fixed, the switching threshold, $V_M$ is approximately proportional to the $V_{DD}$.
- The gain of the inverter in the transition region increases with a reduction of the supply voltage.
- The width of the transition region also reduces when the supply voltage is scaled down compared to the original $V_{DD}$.


## 1 Smart SPICE Simulation for Power Supply Variation

Smart SPICE simulation for power supply variation involves performing detailed DC, transient, and parametric analyses to evaluate the impact of V<sub>DD</sub> fluctuations on circuit performance metrics such as propagation delay, static and dynamic power, rise/fall times, and noise margins. In advanced CMOS technologies, supply variations arise due to IR drop, Ldi/dt noise, and process-voltage-temperature (PVT) interactions, which can degrade timing and logic integrity. Using Smart SPICE, we can perform corner simulations and Monte Carlo analyses to model voltage droops and transients across operating conditions. This enables precise characterization of supply sensitivity, identification of critical timing paths, and optimization of device sizing and biasing to maintain robust operation and ensure design reliability under voltage scaling conditions.

## 2 Power Supply Scaling

Reducing the supply voltage yields a significant reduction in the energy dissipation, but it is absolutely detrimental to the performance of the gate, increasing the transition times greatly.
The DC characteristic becomes increasingly sensitive to variations in the device parameters such as the transistor threshold, once supply voltages and intrinsic voltages become comparable.
Scaling the supply voltage means reducing the signal swing. While this typically helps to reduce the internal noise in the system (such as caused by crosstalk), it makes the design more sensitive to external noise sources that do not scale.

Advantages of using 0.5V supply
- Increase in gain (close to 50% improvement)
- Significant reduction in energy (close to 90% improvement)

Disadvantages of using 0.5V supply
- Performance inputs

## Static Behavior Evaluation -  CMOS Inverter Robustness Device Variation

1 Source of variation - etching process

<img width="2753" height="1087" alt="Screenshot 2025-10-18 194109" src="https://github.com/user-attachments/assets/033a8072-c062-4342-ad4d-7be0875fc3c3" />
<img width="928" height="522" alt="CircuitDesignWorkshop_D5_CMOS_Inverter_Robustness_DeviceVariations_2" src="https://github.com/user-attachments/assets/b3f49721-92ec-42d6-9c3f-499a37aa56fe" />

2 Source of variation - oxide thickness

<img width="2845" height="1081" alt="Screenshot 2025-10-18 195559" src="https://github.com/user-attachments/assets/00dc446e-3fa7-4088-b7f6-2209d01f703e" />
<img width="928" height="527" alt="CircuitDesignWorkshop_D5_CMOS_Inverter_Robustness_DeviceVariations_4" src="https://github.com/user-attachments/assets/96d8380f-b59b-4b9d-bb90-8042d05643ae" />

In this exercise, we try to capture the CMOS Inverter's robustness in the case of a ridiculously extreme case of device width variation.

<img width="925" height="522" alt="CircuitDesignWorkshop_D5_CMOS_Inverter_Robustness_DeviceVariations_5" src="https://github.com/user-attachments/assets/dae3dbae-71f2-4e0a-85bc-083540eb1826" />


