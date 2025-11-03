# Velocity Saturation and Basics of CMOS Inverter VTC

## 1 Velocity Saturation

- The behavior of transistors with very short channel lengths (called short-channel devices) deviates considerably from the resistive and saturated models.
  - The main reason for this deviation is the _**velocity saturation effect**_.
  - We had seen previously that the drift velocity is modelled by:  
    Drift velocity, $v = -\mu \dfrac{dV}{dx}$
      - i.e., the velocity of the carriers is proportional to the electrical field, independent of
the value of that field. In other words, the carrier mobility is a constant.
  - However, at high electric field strengths, the carriers fail to follow this linear model.
  - When the electrical field along the channel reaches a critical value $E_c$, the velocity of the carriers tends to saturate due to scattering effects (collisions suffered by the carriers).

![WhatsApp Image 2025-10-25 at 3 28 02 PM](https://github.com/user-attachments/assets/3ac61bb4-20b0-4ae4-af24-b73024ccbf0c)

## 2 Drain Current in Resistive/ Linear Region
**Now the drain current equation in the resistive region can be re-evaluated using:**  
<br>

$I_D = -v_n(x) * Q_i(x) * W$  
$I_D = -v_n(x) * -C_{ox} [V_{GS} - V(x) -V_{TH}] * W$  
$v_n = \dfrac{\mu_n E}{1+(E/E_c)}$  

Now, $E = \dfrac{dV}{dx}$  

$\therefore v_n = \dfrac{\mu_n (dV/dx)}{1+(1/E_c)(dV/dx)}$  


$\therefore I_D = \dfrac{\mu_n (dV/dx)}{1+(1/E_c)(dV/dx)} * C_{ox} [V_{GS} - V(x) - V_{TH}] * W$  

$i.e., I_D \left[ 1+\dfrac{1}{E_c}\dfrac{dV}{dx}\right] = \mu_n \dfrac{dV}{dx} * C_{ox} [V_{GS} - V(x) - V_{TH}] * W$  

Integrating w.r.t $x$ from $x=0 ~~ (where ~~ V=0)$ to $x=L ~~ (where ~~ V=V_{DS})$, we get:  

$I_D \left[ L+(V_{DS}/E_c)\right] = \mu_n C_{ox} [(V_{GS} - V_{TH})V_{DS} - \dfrac{V_{DS}^2}{2} ] * W$  

Re-arranging:  
$I_D = \left[\dfrac{1}{L+(V_{DS}/E_c)}\right] \mu_n * C_{ox} [(V_{GS} - V_{TH})V_{DS} - \dfrac{V_{DS}^2}{2} ] * W$  

$i.e., I_D = \left[\dfrac{1}{1+(V_{DS}/E_c L)}\right] \mu_n * C_{ox} [(V_{GS} - V_{TH})V_{DS} - \dfrac{V_{DS}^2}{2} ] * \dfrac{W}{L}$  

$i.e., \boxed{I_D = \left[\dfrac{1}{1+(V_{DS}/E_c L)}\right]~\mu_n C_{ox} \dfrac{W}{L} [(V_{GS} - V_{TH})V_{DS} - \dfrac{V_{DS}^2}{2} ]}$  

$~~~~~~~~~~~~\boxed{I_D = \kappa(V_{DS}) \mu_n C_{ox} \dfrac{W}{L}\left[(V_{GS}-V_{TH})V_{DS} - \dfrac{{V_{DS}^2}}{2} \right]}$  

$~~~~~~~~~~~~where, ~~~~ \kappa(V_{DS}) = \dfrac{1}{1+(V_{DS}/E_c L)}$  

  - $\kappa$ is a measure of the velocity saturation since $V_{DS}/L$ is the average field in the channel.
  - In the case of long-channel devices (where $L$ is large), or when the value of $V_{DS}$ is small, $\kappa$ approaches 1 and the above equation simplifies to the traditional equation we had derived first using the constant mobility model.
  - For short-channel devices, $\kappa$ is smaller than 1, implying the delivered current is smaller than what would be normally expected.

## 2.2 Drain Current in Saturation Region

**Coming to the Drain current in saturation region:**  
<br>

$I_D = -v_n(x) * -C_{ox} [V_{GS} - V(x) -V_{TH}] * W ~~~~~~~~ |with ~~ v_n(x)=v_{sat} ~~ and ~~ V(x)=V_{DSAT}$  
$i.e., \boxed{I_{DSAT} = v_{sat} C_{ox} W [(V_{GS} - V_{TH}) - V_{DSAT}]}$  

$I_{DSAT}$ can also be evaluated by replacing $V_{DS}=V_{DSAT}$ in the linear region equation derived in the previous section.  

$\therefore ~~~~ \boxed{I_{DSAT} = \kappa(V_{DSAT}) \mu_n C_{ox} \dfrac{W}{L}\left[(V_{GS}-V_{TH})V_{DSAT} - \dfrac{{V_{DSAT}^2}}{2} \right]}$


Equating these two expressions for $I_{DSAT}$ to solve for $V_{DSAT}$, we get:  
$I_{DSAT} = v_{sat} C_{ox} W [(V_{GS} - V_{TH}) - V_{DSAT}]~= \kappa(V_{DSAT}) \mu_n C_{ox} \dfrac{W}{L}\left[(V_{GS}-V_{TH})V_{DSAT} - \dfrac{{V_{DSAT}^2}}{2} \right]$

$i.e.,$  
$\dfrac{\mu_n E_c}{2} C_{ox} W [(V_{GS} - V_{TH}) - V_{DSAT}] = \kappa(V_{DSAT}) \mu_n C_{ox} \dfrac{W}{L}\left[(V_{GS}-V_{TH})V_{DSAT} - \dfrac{{V_{DSAT}^2}}{2} \right]$

$E_c L [(V_{GS} - V_{TH}) - V_{DSAT}] = \kappa(V_{DSAT}) \left[2(V_{GS}-V_{TH})V_{DSAT} - {V_{DSAT}^2} \right]$

This can be further simplified to the below:  
$~~~~~~~~ \boxed{V_{DSAT} = \kappa(V_{GT}) ~ V_{GT}} ~~~~ , where ~ V_{GT} = (V_{GS} - V_{TH})$  

<br>

<img width="2968" height="1725" alt="Screenshot 2025-10-18 123008" src="https://github.com/user-attachments/assets/c0096c6e-c012-481e-8e5b-36e4137d622e" />

<img width="3839" height="1865" alt="Screenshot 2025-10-18 135910" src="https://github.com/user-attachments/assets/aba00b7a-6be4-40f7-80d3-0db069276daa" />

<img width="3839" height="1917" alt="Screenshot 2025-10-18 122239" src="https://github.com/user-attachments/assets/e24fa5a6-160f-42bc-80d5-b443257df11c" />

## LAB - 02  Velocity Saturation - ID vs VDS
<details> <summary> SPICE File: nmos_chara_W1.8u_L1.2u.spice </summary>

```
*** Netlist Description ***
M1 vdd n1 0 0 nmos W=1.8u L=1.2u
R1 in n1 55
Vdd vdd 0 2.5
Vin in 0 2.5

*** .include model ***
.lib "tsmc_025um_model.mod" cmos_models

*** Simulation Commands ***
.op
.dc Vdd 0 2.5 0.1 Vin 0 2.5 0.5

.control
run
display
setplot dc1
plot -vdd#branch
.endc

.end
```
</details>

<details> <summary> SPICE File: nmos_chara_W0.375u_L0.25u.spice </summary>

```
*** Netlist Description ***
M1 vdd n1 0 0 nmos W=0.375u L=0.25u
R1 in n1 55
Vdd vdd 0 2.5
Vin in 0 2.5

*** .include model ***
.lib "tsmc_025um_model.mod" cmos_models

*** Simulation Commands ***
.op
.dc Vdd 0 2.5 0.1 Vin 0 2.5 0.5

.control
run
display
setplot dc1
plot -vdd#branch
.endc

.end
```
</details>



## LAB - 2.1 Velocity Saturation - sky130 (W=0.39u, L=0.15u)
<details> <summary> SPICE File: day2_nfet_idvgs_L015_W039.spice </summary>

```
*** Model Description ***
.param temp=27

*** Including sky130 library files ***
.lib "sky130_fd_pr/models/sky130.lib.spice" tt

**** Netlist Description ***
XM1 Vdd n1 0 0 sky130_fd_pr__nfet_01v8 w=0.39 l=0.15
R1 n1 in 55
Vdd vdd 0 1.8V
Vin in 0 1.8V

*** Simulation Commands ***
.op
.dc Vin 0 1.8 0.1 Vdd 1.8 1.8 0.2 

.control
run
display
setplot dc1
.endc

.end
```
</details>



## 3 CMOS Voltage Transfer Characteristics (VTC)

## 3.1 MOSFET as a switch

<img width="2747" height="882" alt="Screenshot 2025-10-18 140539" src="https://github.com/user-attachments/assets/79afd660-0e15-4ad6-bc15-a585c6dcfa7b" />

- With infinite OFF resistance when |Vgs| < |Vt|
- With finite ON resistance when |Vgs| > |Vt|

<img width="2020" height="2159" alt="Screenshot 2025-10-18 141117" src="https://github.com/user-attachments/assets/21cbd582-2d86-4aa5-bdda-7660cb7c7f37" />

## 3.2 Introduction to standard MOS Voltage Current Parameter

<img width="1350" height="1151" alt="Screenshot 2025-10-18 142124" src="https://github.com/user-attachments/assets/cb44b6a4-af26-46e6-a2d8-a5ee73e9168e" />

- When Vin = Vdd
- Direct path exists between Vout and Vss, resulting in Vout = 0
- When Vin = 0
- Direct path exists between Vdd and Vout, resulting in Vout = Vdd

## 3.3 PMOS/NMOS Drain Current vs Drain Voltage

By observation
V<sub>gsN</sub> = V<sub>in</sub> - V<sub>ss</sub> = V<sub>in</sub>

V<sub>dsN</sub> = V<sub>out</sub>

V<sub>gsP</sub> = V<sub>in</sub> - V<sub>dd</sub>

V<sub>dsP</sub> = V<sub>out</sub> - V<sub>dd</sub>

## NMOS I<sub>dsN</sub> vs V<sub>dsN</sub> Curve

<img width="1288" height="1259" alt="Screenshot 2025-10-18 143511" src="https://github.com/user-attachments/assets/a16701f5-e2bc-4763-afc4-15e5aa1297f2" />

## PMOS I<sub>dsP</sub> vs V<sub>dsP</sub> Curve

<img width="1117" height="1390" alt="Screenshot 2025-10-18 143539" src="https://github.com/user-attachments/assets/1ea5f1fa-13c4-45f9-99e0-b35ec46ea774" />

## 3.4 Convert PMOS gate-source-voltage to Vin

Step-1 Below are the steps to obtain voltage-transfer characteristics (VTC) for Static CMOS Inverter 
Let us assume below values (Vdd = 2V)

<img width="1114" height="724" alt="Screenshot 2025-10-18 145055" src="https://github.com/user-attachments/assets/a1a7b995-0c80-4cbf-b96f-e470d626f0dd" />

## 3.5 Convert PMOS and NMOS drain-source-voltage to Vout

Step-2 & Step-3

<img width="2730" height="1394" alt="Screenshot 2025-10-18 150238" src="https://github.com/user-attachments/assets/c3157666-6791-49ef-80b0-e442b8e5ffc0" />

Let us obtain the load curve for NMOS transistor using the equation.

## 3.6 Merge PMOS-NMOS load curves and plot VTC

Step-4 We will superimpose the load curve of NMOS on the load curve of PMOS and plot Vin v/s Vout from the above graph

<img width="3840" height="2160" alt="Screenshot 2025-10-18 151026" src="https://github.com/user-attachments/assets/dd7047e4-9d15-44c5-b333-3bf16981ab12" />

Vin and Vout are common to PMOS and NMOS graphically, we will pick up Vin points from the intersection of corresponding load lines.

**Relationships between voltages for the three regions of operation of PMOS, NMOS in a CMOS inverter:**  
| | Cutoff | Linear | Saturation |
|:---|:---|:---|:---|
| **NMOS** | $V_{GSn} < V_{Tn}$ <br>  $V_{in} < V_{Tn}$ <br>  <br>  <br>  <br>  | $V_{GSn} > V_{Tn}$ <br>  $V_{in} > V_{Tn}$ <br>  <br>  $V_{DSn} < (V_{GSn}-V_{Tn})$ <br>  $V_{out} < (V_{in}-V_{Tn})$ | $V_{GSn} > V_{Tn}$ <br>  $V_{in} > V_{Tn}$ <br>  <br>  $V_{DSn} > (V_{GSn}-V_{Tn})$ <br>  $V_{out} > (V_{in}-V_{Tn})$ |
| **PMOS** | $V_{GSp} > V_{Tp}$ <br>  $V_{in} > V_{DD} - \mid V_{Tp} \mid$ <br>  <br>  <br>  <br>  | $V_{GSp} < V_{Tp}$ <br>  $V_{in} < V_{DD}-\mid V_{Tp} \mid$ <br>  <br>  $V_{DSp} > (V_{GSp}-V_{Tp})$ <br>  $V_{out} > (V_{in}+\mid V_{Tp} \mid)$ | $V_{GSp} < V_{Tp}$ <br>  $V_{in} < V_{DD}-\mid V_{Tp} \mid$ <br>  <br>  $V_{DSp} < (V_{GSp}-V_{Tp})$ <br>  $V_{out} < (V_{in}+\mid V_{Tp} \mid)$ |




