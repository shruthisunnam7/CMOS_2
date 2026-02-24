# CMOS -CIRCUIT DESIGN AND SPICE SIMULATIONS IN SKY 130
This intensive 10-day workshop focused on CMOS circuit design and SPICE simulation using SKY130 130nm technology. The course was structured progressively, enabling participants to build a strong foundation in MOSFET physics, CMOS inverter design, switching behavior, noise analysis, and variation effects.

The training emphasized both theoretical derivations and practical SPICE-based simulations to understand real-world transistor-level circuit behavior.

# DAY 1
# Basics of NMOS structure and operation ,Understanding Drain Current (Id) and Drain-to-Source Voltage (Vds) Regions of operation (Cutoff, Linear, Saturation)

# Introduction to  circuit designs and SPICE simulations

<img width="1000" height="800" alt="image" src="https://github.com/user-attachments/assets/deab1783-a221-4103-9079-e9f86df42924" /> 
It is an inverter image where
- PMOS connected to VDD (Pull-up network)

- NMOS connected to VSS (Pull-down network)
  
- Gates of both transistors tied together → Vin
 
- Drains connected together 

- Load capacitor (CL) connected at output
  
- Circuit design ensures that PMOS and NMOS transistors are connected properly to achieve the required functionality, enabling the circuit to perform the desired operation efficiently.
  
<img width="1018" height="900" alt="image" src="https://github.com/user-attachments/assets/cc8bb6ea-bacb-46c6-89a9-7bbabab06124" />

- PMOS and NMOS characteristic curves are simulated using SPICE to understand their behavior. The resulting waveforms are analyzed to determine parameters such as delay  performance.
  
- The W/L ratio controls the amount of current flowing through the transistor where W is width of transistor and L is the  length of gate oxide of transistor, and this current influences the shape of the waveform. 
# why do we need spice ?

SPICE acts as the base tool for verifying CMOS circuit behavior. It helps in analyzing:
* NMOS and PMOS characteristics
  
* Drain current (Id) behavior
  
* Output waveform
  
* Delay of the circuit
  
* Effect of W/L ratio 
It allows us to validate theoretical equations using practical simulations.
<img width="1547" height="501" alt="image" src="https://github.com/user-attachments/assets/4b49291d-6f72-4a0d-aff5-8782538980cc" />
<img width="1600" height="409" alt="image" src="https://github.com/user-attachments/assets/4d3a98b8-f1dc-4d2b-84c2-1da17749ebc3" />
The figure shows a buffer circuit with given specifications and output load. To calculate the delay of the buffer, we use delay tables based on input slew rate and output load. From the delay tables of CBUF1 and CBUF2, we can see that even for the same input slew and load values, the delay differs. This difference occurs because the NMOS and PMOS transistors in the two buffers have different W/L ratios, which change their drive strength and switching behavior.

# NMOS BASIC ELEMENTS IN CIRCUIT DESIGN

<img width="1600" height="1338" alt="image" src="https://github.com/user-attachments/assets/9d270771-18eb-4555-9f63-e673226d8f0f" />
STRUCTURE OF NMOS DEVICE 
* N channel mosfet constructed on p substarte
  
* Four terminal device
  
* Isolation region created from SiO2 is present used to differntiate  two different transistor characteristics
  
* Two n+ diffusion region are present near the SiO2 layer in which one is SOURCE and other is DRAIN.
  
* It has a Gate oxide layer over p substrate
  
* A Poly-Si or metal gate  placed on top of the gate oxide layer which forms gate terminal and drives nmos .
There are a few abbreviations:
G means Gate
S means Source
D means Drain
B means Body
* Body terminal is connected directly to P substrate and it is grounded.It is important in finding threshold voltage the nmos.

* PMOS is inverted to nmos
# THRESHOLD VOLTAGE 

<img width="1027" height="515" alt="image" src="https://github.com/user-attachments/assets/168eb4f5-e5ab-45a6-affe-76594534a1cf" />
* let us take vt is a function of x,y,z .
  
* Vgs=0 and drain ,source and bulk are connected to ground .
  
* Here we can observe that the substrate and diffusion looks like PN junction diode and these are connected back to back.
  
* Both junctions are off due to 0V bias hence channel has high resistance therefore no connectivity between source and drain .
  
* Apply a small positive potential at VGS and the metal gate becomes positively charged and forms an oxide capacitance. As a result, it repels the positive charges in the substrate, leaving behind negative charges.
  
* This causes an accumulation of negative charges near the surface. Since it behaves like a pn junction diode, a depletion layer is formed.
  
* As the gate voltage increases, more positive charges are repelled, and the depletion region increases further. Eventually, it reaches a point where the p-type substrate surface is completely converted into an n-type surface.
  
* This phenomenon is called strong inversion, and the voltage at which strong inversion occurs is known as the threshold voltage vt.
  
* further increase in vgs there are no +ve particles near gate area to repel.so it will attracts negative charges from heavily doped ntype region.By this the channel width increases but there is no change in depletion width.There is a formation of continuous connection between to difusion regions through channel ormed in substrate.

* The channel has bridged the gap between source to drain regions. But as there is no Drain voltage so the elctrons will not move, this is "Cut Off Region"
  
#  How Body terminal in deciding thershold voltage 

<img width="729" height="655" alt="image" src="https://github.com/user-attachments/assets/e4d68997-7b02-4cb7-9ae8-3a8396007666" />

* when vsb = 0 there is no positive potential applied between the source and body, increasing the gate to source voltage the depletion layer increase , further increase in vgs there will cause  surface inversion that is vgs=vto where vto threshold voltage at which surface inversion occurs in the absence of vsb .
 
<img width="873" height="515" alt="image" src="https://github.com/user-attachments/assets/25f84efd-beb1-4c0c-b9b7-c94b46af93db" />

* when vsb has some positive potentional applied  to the source and negative potential  applied to body junction ,the depletion layer width gets widenes due to additibal reverse bias that is applied to pn junction .

  <img width="837" height="625" alt="image" src="https://github.com/user-attachments/assets/67a5e48e-1206-4687-9dac-c07b70179b98" />

*Increase in depletion width leads to accumilate  more  negative charges , as the terminal is connected  to positive potential there will be more accumilation of negative charges in vsb positive side .

*Due to +vsb ,few charges from channel are pulled towards source ,further increase in vgs semiconductor surface inverts to n type material at voltage vgs=vto+1 .In presence of substrate bias vsb additional potential is required for strong inversion .
# THRESHOLD VOLTAGE EQUATION 

<img width="1600" height="580" alt="image" src="https://github.com/user-attachments/assets/2b1934d6-26ee-4fd9-9826-adb2fd7f4fcc" />

* Body  effect coefficient equation:
  
  <img width="642" height="553" alt="image" src="https://github.com/user-attachments/assets/a58d12af-23c7-4ae8-aa55-3d36e51bd0f5" />

  # NMOS RESISTIVE OPERATION WITH SMALL DRAIN TO SOURCE VOLTAGE 

* It is also known as the Linear Region of operation
*  observe changes when Vgs > Vt .
*  Induced charges (Qi) α (Vgs-Vt) .
*  when vt = 0.45v ,vgs = 1v, vgs > vt transitor turn on and conducting channel is present between source and drain and we can see  source is connected to ground and drain  is connected to some potential ,there will be a voltage gradient present across the channel . Also effective length is less than actual channel length .
  
*  <img width="965" height="620" alt="image" src="https://github.com/user-attachments/assets/234eceb1-96ff-43f3-be5d-e809891c1a38" />

*  lets plot a graph ,'x' is along the channel and 'y' is perpendicular to channel , y axis represents width , when x=0,1,2,3...,n  at every point v1,v2 ,..,vn the voltage will be different ,all values are different because of small voltage applied ie vds . Every point on x axis will vary w.r.t to Vgs-V(x), this will decide the current equation. where V(x) be the voltage at any point 'x' along the channel and  Vgs-V(x) is the gate-to-channel voltage at that point .
  
# drift current theory 
We know the effective channel voltage will vary w.r.t x, for example at x=0, Vgs=1V and V(x)=0, So the Vgs-Vx=1V. At x=Vds=0.05V, Vgs-Vx=0.95V. 
 * The induced charge at any point 'x' is  Qi(x) α - ((Vgs-V(x))-Vt) ie  Qi(x) = -cox ((Vgs-V(x))-Vt)
   
<img width="531" height="553" alt="image" src="https://github.com/user-attachments/assets/17a4710e-94a3-41df-9917-05ba8d561fff" />

From device point of view ,we have  2 kinds of currents in 
** drift current : current due to potential differnce 

**diffusion current : current due to difference in carrier concentration

<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/ebdef17f-9787-45a7-9983-db3b7aa98fdc" />

# Drain current model for linear region of operation 

*drain  current id = (velocity of charge carriers * available charge) over the chanel width .

* velocity vn(x) = product of mobility and electric field .small distance of L there is a change in voltage ,as a result of change in voltage ,velocity differs .
  
* vn(x) = μn.dv/dx .
 
<img width="599" height="900" alt="image" src="https://github.com/user-attachments/assets/78b39a84-03e2-4560-97bd-8f2129e55125" />

we will integrate the above equation,where limits of dV will be from 0 to Vds and limits of dx will be from 0 to L.

<img width="619" height="183" alt="image" src="https://github.com/user-attachments/assets/1bc82a41-91ba-4e56-8a1c-14de16bb9c17" />

Here, Cox, W/L, Vgs, un and Vt are the 'technology parameters', we will simulate usinf SPICE and find out the characteristics.

<img width="580" height="332" alt="image" src="https://github.com/user-attachments/assets/0f5e944d-5451-4722-b7be-1c5a6f36b821" />

The equation is simplified into this form where kn' is Cox * mobility. still we simplify this equation into linear form.This equation is suitable only for Vds value is small.so we can neglect square term from the equation.So we get Id=Kn*(Vgs-Vt)
  
<img width="888" height="597" alt="image" src="https://github.com/user-attachments/assets/895a46e4-56e8-4c8f-87ec-3df64cbe10f8" />

we need to find the impact of Vds and Vgs on Id drain current.The NMOS works in linear region only when Vds <= Vgs-Vt.

*For calculating Id drift current for diferent conditions on Vgs and Vgs to find it's sweeping ranges we are using an engine to do all the work which is SPICE simulation to get drain current waveforms.
