# CMOS Noise Margin Robustness Evaluation

## 1 Static Behaviour Evaluation - CMOS Inverter Robustness Noise Margin

## 1.1 Introduction to Noise Margin 
In digital circuits, excessive noise voltage at a node can cause logic errors, leading to incorrect signal interpretation. To prevent this, a parameter known as the noise margin defines the maximum allowable noise level that can be tolerated without affecting circuit operation. If the noise amplitude remains within this limit, the disturbance is naturally suppressed as it propagates through logic gates, ensuring reliable signal transmission. In essence, the noise margin guarantees that a logic ‘1’ with minor noise interference is still interpreted as a valid ‘1’, and a logic ‘0’ with slight noise remains a valid ‘0’, preserving circuit integrity.

## 1.2 Noise Margin NM<sub>H</sub> and NM<sub>L</sub>

The following images show an ideal, a piece-wise linear 

<img width="1685" height="976" alt="Screenshot 2025-10-18 181613" src="https://github.com/user-attachments/assets/0482e56f-95a6-4fd3-8088-680bbf518375" />

Any output voltage level between 0 and V_OL will be treated as logic '0'

## 1.3 Noise Margin Voltage Parameters

I/O characteristic plotted on scale
<img width="1592" height="829" alt="Screenshot 2025-10-18 182500" src="https://github.com/user-attachments/assets/2a847eb4-23f5-4d1b-a183-8d17dd1f694b" />

Any signal in undefined region will be indefinite logic level.

**NM<sub>H</sub> = V<sub>OH</sub> − V<sub>IH</sub>**  
**NM<sub>L</sub> = V<sub>IL</sub> − V<sub>OL</sub>** 

### 1.4 Noise Margin Equation and Summary

<img width="2029" height="1299" alt="Screenshot 2025-10-18 183752" src="https://github.com/user-attachments/assets/df06158f-985c-4758-9797-3df42a38c981" />

(a) Bump height lies between Vol and Vil will be considered as logic '0'

(b) Bump height lies between Vil and Vih output logic 'undefined'

(c) Bump height lies between Vih and Voh will be considerd as logic '1'


<img width="2135" height="1594" alt="Screenshot 2025-10-18 184436" src="https://github.com/user-attachments/assets/decc56c5-1db3-41a3-ba0d-187843c01939" />

NM<sub>H</sub> = 0.42
NM<sub>L</sub> = 0.27
Vm = 1.4V

<img width="2085" height="713" alt="Screenshot 2025-10-18 184842" src="https://github.com/user-attachments/assets/070e847d-ac73-444d-9ff7-b4a75a257382" />

## LAB - 04  Noise Margin - sky130 Inverter (Wp/Lp=1u/0.15u, Wn/Ln=0.36u/0.15u)
<details> <summary> SPICE File: day4_inv_noisemargin_wp1_wn036.spice </summary>

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

*** Simulation Commands ***
.op
.dc Vin 0 1.8 0.01

.control
run
setplot dc1
display
let dVout = deriv(V(out))
meas dc vil find V(in) when dVout=-1 cross=1
meas dc vih find V(in) when dVout=-1 cross=2
meas dc voh find V(out) when dVout=-1 cross=1
meas dc vol find V(out) when dVout=-1 cross=2

let NML = vil - vol
let NMH = voh - vih
print NML
print NMH
.endc

.end
```
</details>

