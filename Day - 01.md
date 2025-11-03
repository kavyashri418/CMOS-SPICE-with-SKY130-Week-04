# Basics of NMOS Drain Current (Id) vs Drain to Source Voltage (Vds)

## 1 Introduction to Circuit Design and SPICE Simulations

## Why do we need SPICE simulation?

SPICE (Simulation Program with Integrated Circuit Emphasis) is essential for analyzing and verifying electronic circuits before fabrication. It allows designers to simulate circuit behavior accurately, predicting voltages, currents, and timing under different conditions without building physical prototypes. By modeling real device characteristics such as MOSFETs, BJTs, and diodes, SPICE helps identify design issues like wrong biasing, signal distortion, or instability early in the design phase. It supports DC, AC, transient, and noise analyses, making it invaluable for both analog and mixed-signal circuit design. Overall, SPICE simulation saves time, reduces cost, and ensures reliable, optimized circuit performance.

![WhatsApp Image 2025-10-25 at 1 35 17 PM](https://github.com/user-attachments/assets/413a6398-2bbe-4462-8bf5-b71fa3ff3cfb)
![WhatsApp Image 2025-10-25 at 1 35 37 PM](https://github.com/user-attachments/assets/09b73170-6a43-45f8-9eaf-df98f1c84618)

## 1.1 Introduction to Basic Element in Circuit Design - NMOS

![WhatsApp Image 2025-10-25 at 1 17 17 PM](https://github.com/user-attachments/assets/54a93760-ab50-414c-9da5-5dcda59cacfb)

- 4 terminal device
- Consists of p-substrate
- Isolation region (SiO2)
- n+ diffusion region
- Gate oxide
- Poly-Si or metal gate
- G=Gate
- S=Source
- D=Drain
- B=Body

## 1.2 Strong Inversion and Threshold Voltage

![WhatsApp Image 2025-10-25 at 1 19 31 PM](https://github.com/user-attachments/assets/474515e3-69f3-44a6-877f-22fd72a10a4b)

Vgs=0
- Drain, Source, Bulk, connected to Gnd
- Substrate source and substrate drain from p-n junction diode
- Both junctions are 'off' due to 0v bias 
- Hence S-D resistance is 'high'
- Apply +ve Vgs voltage
- Increase gate voltage 'Vgs'
- This phenomenon is called strong inversion
- The 'Vgs' voltage at which strong inversion occurs is called threshold Vgs (Vt)
- Further increase 'Vgs'
- No change in depeletion layer width
- Electrons from heavily doped 'n+' source regions are drawn in region under gate 'G'
- Continuous n-channel formation from S-D whose conductivity is modulated by 'Vgs'

## 1.3 Threshold Voltage with Positive Substrate Potential

<img width="3720" height="1811" alt="Screenshot 2025-10-18 085353" src="https://github.com/user-attachments/assets/ebc99659-91a9-4c23-bb32-4581ccef9b7f" />

Additional reverse bias between source 's' and substrate 'b'. Therefore, depletion layer width is slightly high near 's', increase 'Vgs'
Threshold volatage equation 

Vto = Threshold voltage at Vsb = 0, and is a function of manufacturing process.

γ = body effect coefficient, express the impact of changes in body bias Vsb.

ϕF = fermi potential

γ = √(2qN<sub>A</sub>ε<sub>si</sub>) / C<sub>ox</sub>

ε<sub>si</sub> = relative permittivity of silicon=11.7

N<sub>A = doping concentration

q = charge of the electron

Cox = oxide capacitance

ϕ<sub>F</sub> = −ϕ<sub>T</sub> × ln(N<sub>A</sub> / n<sub>i</sub>)

ni = intrinsic doping parameter for the substrate
 
## 2 NMOS Resistive Region and Saturation Region of Operation

## 2.1 Resistive region of operation with small drain-source voltage

<img width="2146" height="1471" alt="Screenshot 2025-10-18 091123" src="https://github.com/user-attachments/assets/78808a06-6ac5-46ec-adb5-35701341c52e" />

Resistive Operation
- The 'Vgs' voltage at which strong inversion occurs is called threshold Vg (Vt)
- Since, Vgs = Vt, let us consider what happens at different voltages of 'Vgs' > 'Vt'
- Hence, in the channel (shown in yellow circle), induced charge (Qi) ∝ (Vgs-Vt)
- Lets analyse at Vgs = 1v and small Vds (say 0.05v). Assume Vt(NMOS) = 0.45v
- Let 'x' axis be along the channel and 'y' axis be perpendicular to channel
- Now, in the channel Induced charge at any point 'x' 
Qi(x) ∝ -([Vgs-V(x)]-Vt)
ie Qi(x) = -Cox([Vgs-V(x)]-Vt)

## 2.2 Drift Current

Qi(x) = -Cox([Vgs-V(x)]-Vt)

Cox = Gate Oxide Capacitance

$~~~~~~~~ C_{ox} = \dfrac{\epsilon_{ox}}{t_{ox}}$

​εox​​ = oxide permittivity

      3.97 x ​εo (relative permittivity)
      3.5 x 10e⁻¹¹ F/m
      
tox = oxide thickness

From devie point of view, we have two kinds of currents
1) Drift current - current due to potential difference
2) Diffusion current - current due to difference in carrier concentration

## 2.3 Drain current model for linear region of operation

<img width="3684" height="2159" alt="Screenshot 2025-10-18 095828" src="https://github.com/user-attachments/assets/2cfea25e-6b11-46c4-bbaa-664c6fecb7fc" />

Id = velocity of charge carriers over channel width x available charge
Id = -Vn(x).Qi(x).W
Velocity Vn((x) = mobility.electric field
Id = -Vn(x).Qi(x).W
Substituting and integrating dx over channel length L will give the V-I relation of NMOS transistor
$I_D = -v_n(x) * Q_i(x) * W$
The electron velocity is related to the electric field through a parameter called the mobility $\mu_n$ (expressed in $\dfrac{m^2}{V.s}$).  

Drift velocity, $v_n = -\mu_n \dfrac{dV}{dx}$

$\therefore I_D = -\mu_n \dfrac{dV}{dx} * -C_{ox} [V_{GS} - V(x) - V_{TH}] * W$  

$i.e., I_D dx = \mu_n C_{ox} W [V_{GS} - V(x) -V_{TH}] dV$

Integrating the equation over the length of the channel L yields the voltage-current relation of the transistor:  
$\boxed{I_D = {k_n}^\prime \dfrac{W}{L} \left[ (V_{GS}-V_{TH})V_{DS} - \dfrac{{V_{DS}}^2}{2} \right]
     = k_n \left[ (V_{GS}-V_{TH})V_{DS} - \dfrac{{V_{DS}}^2}{2} \right]}$

$where:$  
$~~~~~~~~ {k_n}^\prime$ is the _process transconductance parameter._  
$~~~~~~~~ {k_n}^\prime = \mu_nC_{ox}$

The product of process transconductance, ${k_n}^\prime$ and the $\dfrac{W}{L}$ ratio of the transistor is called the _gain factor_, $k_n$ of the device.

$~~~~~~~~ k_n = {k_n}^\prime * \left( \dfrac{W}{L} \right)$

Now, the above equation for Drain Current:  
$I_D = k_n * \left[(V_{GS} - V_{TH}) * V_{DS} - \dfrac{V_{DS}^2}{2}\right]$
is a quadratic function of $V_{DS}$.  

But at low values, the $\dfrac{V_{DS}^2}{2}$ term can be ignored as it is close to zero. Hence the equation for $I_D$ can be approximated to be a linear function of $V_{DS}$:  

$\boxed {i.e., I_D = k_n * (V_{GS} - V_{TH}) * V_{DS}} ~~~~ $
_Hence the name Linear Region_

## 2.4 Pinch-Off region condition

<img width="1851" height="1292" alt="Screenshot 2025-10-18 103208" src="https://github.com/user-attachments/assets/2eb1dce4-f895-489e-a8ae-4c18d9551496" />

  - When a $V_{DS}$ voltage is applied, the channel voltage becomes a function of both $V_{GS}$ and $V_{DS}$.
  - Since the induced channel depth depends on the channel voltage relative to the Gate terminal, and specifically on the amount by which this voltage exceeds the threshold voltage, $V_{TH}$, we find that the channel is no longer of uniform depth; rather, the channel will take a tapered shape:
    - being deepest at the Source end, where the depth is proportional to $[V_{GS}-V_{TH}]$, and
    - shallowest at the drain end, where the depth is proportional to $[V_{GS}-V_{TH}-V_{DS}]$.
 - As the value of the Drain-Source voltage is increased further, the assumption that the channel voltage is larger than the threshold all along the channel ceases to hold.
    - In the limiting case, the channel depth at the drain end reduces to zero and the channel is said to be **"pinched-off"**. This happens when $V_{GD}$ is just equal to the threshold voltage, $V_{TH}$.
    - i.e., $V_{DS}= V_{GS}-V_{TH} ~~~~~~~~ (=V_{OV})$, Gate Over-drive voltage
  - At this point, the induced charge is zero, and the conducting channel disappears or is pinched off starting from the Drain end.

## 2.5 Drain current model for saturation region of operation

<img width="3609" height="1962" alt="Screenshot 2025-10-18 104742" src="https://github.com/user-attachments/assets/8d8f265a-d0ba-4788-b801-82cbb51b07c7" />

 - Increasing $V_{DS}$ beyond the $V_{DSsat}$ value of ($V_{GS}-V_{TH}$) has no effect on the channel shape and charge.
  - Thus, the current through the channel remains constant at the value reached for $V_{DS}= V_{GS}-V_{TH}$.
  - The MOSFET is said to have entered **saturation/ pinch-off regsion** at:
    - $V_{DS} = V_{DSsat} = V_{GS}-V_{TH}$
  - Subsequently, the Saturation Drain current:
    - $I_D = I_{Dsat} = {k_n}^\prime \dfrac{W}{L} \left[ (V_{GS}-V_{TH})V_{DSsat} - \dfrac{{V_{DSsat}}^2}{2} \right]$
    - $\boxed{i.e., I_{Dsat} = \dfrac{1}{2} {k_n}^\prime \dfrac{W}{L} {\left[ {V_{GS}-V_{TH}}^2\right]}}$
  

  - **Channel pinch-off does not imply channel blockage**
    - Current continues to flow through the pinched-off channel.
    - The electrons that reach the drain end of the channel are accelerated through the depletion region that exists there and into the drain terminal.
    - Any increase in $V_{DS}$ above $V_{DSsat}$ appears as a voltage drop across the depletion region
    - Thus, both the current through the channel, $I_{Dsat}$ and the voltage drop across the channel $i.e., V_{DSsat} = (V_{GS}-V_{TH})$ **remain constant in saturation**.

## 2.6 Channel Length Modulation and Finite Output Resistance in Saturation

 - The above Drain current equation seems to indicate that in sarutation, $I_D$ is independent of $V_{DS}$
  - Thus a change, $\Delta V_{DS}$, in the Drain-to-Source voltage causes a zero change in $I_D$, which implies that the incremental resistance looking into the drain of a saturated MOSFET is infinite.
  - This, however, is an idealization based on the premise that once the channel is pinched off at the drain end, further increases in $V_{DS}$ have no effect on the channel’s shape.
  - But, in practice, increasing $V_{DS}$ beyond $V_{GS}-V_{TH}$ does affect the channel somewhat.
    - As $V_{DS}$ is increased, the channel pinch-off point is moved slightly away from the drain, toward the source.
    - That is, the voltage across the channel remains constant at $V_{GS}-V_{TH}$, and
    - The additional voltage applied to the drain appears as a voltage drop across the narrow depletion region between the end of the channel and the drain region.
    - This voltage accelerates the electrons that reach the drain end of the channel and sweeps them across the depletion region into the drain.
  

  - Note, however, that (with depletion-layer widening) the channel length is reduced from $L$ to $(L-\Delta L)$, called **Channel Length Modulation (CLM)**.

  - Since $I_D$ is inversely proportional to the channel length, $I_D$ increases with $V_{DS}$.
  - CLM can be accounted for in the expression for $I_D$ by including a factor $[1 + \lambda (V_{DS}-V_{DSsat})]$.  
    For simplicity, we use: $[1 + \lambda V_{DS}]$

    $\boxed{\therefore I_{D} = \dfrac{1}{2} {k_n}^\prime \dfrac{W}{L} \left[ {(V_{GS}-V_{TH}}^2\right] (1 + \lambda V_{DS})}$

  - The CLM parameter, $\lambda$ is a device parameter having the units of $V^{-1}$ . Its value depends both on the process technology used to fabricate the device and on the channel length, $L$ that the circuit designer selects.

  - Output Resistance, $r_o = \dfrac{1}{\lambda I_D}$

## LAB - 01 : ID vs VDS for different VGS (W=5um, L=2um)
<details> <summary> SPICE File: day1_nfet_idvds_L2_W5.spice </summary>

```
*** Model Description ***
.param temp=27

*** Including sky130 library files ***
.lib "sky130_fd_pr/models/sky130.lib.spice" tt

*** Netlist Description ***
XM1 vdd n1 0 0 sky130_fd_pr__nfet_01v8 w=5 l=2
R1 n1 in 55
Vdd vdd 0 1.8
Vin in 0 1.8

*** Simulation Commands ***
.op
.dc Vdd 0 1.8 0.1 Vin 0 1.8 0.2

.control
run
display
setplot dc1
.endc

.end
```
</details>

```
git clone https://github.com/kunalg123/sky130CircuitDesignWorkshop.git
cd sky130CircuitDesignWorkshop/design
sudo apt install ngspice
ngspice day1_nfet_idvds_L2_W5.spice
```
![WhatsApp Image 2025-11-03 at 11 45 51 AM](https://github.com/user-attachments/assets/90775c0d-ae6e-4a64-b7b5-1d2e5148c54f)







