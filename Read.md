# CMOS -CIRCUIT DESIGN AND SPICE SIMULATIONS IN SKY 130
This intensive 10-day workshop focused on CMOS circuit design and SPICE simulation using SKY130 130nm technology. The course was structured progressively, enabling participants to build a strong foundation in MOSFET physics, CMOS inverter design, switching behavior, noise analysis, and variation effects.

The training emphasized both theoretical derivations and practical SPICE-based simulations to understand real-world transistor-level circuit behavior.

# 📑 Table of Contents

## DAY 1
- [Why Do We Need SPICE?](#why-do-we-need-spice)
- [NMOS Basic Elements in Circuit Design](#nmos-basic-elements-in-circuit-design)
- [Threshold Voltage](#threshold-voltage)
- [NMOS Resistive Operation (Small Vds)](#nmos-resistive-operation-small-vds)
- [Drift Current Theory](#drift-current-theory)
- [Drain Current Model – Linear Region](#drain-current-model--linear-region)
- [SPICE Conclusion to Resistive Operation](#spice-conclusion-to-resistive-operation)
- [Saturation Region](#saturation-region)
- [Drain Current Model – Saturation Region](#drain-current-model--saturation-region)
- [Introduction to SPICE](#introduction-to-spice)
- [Circuit Description in SPICE Syntax](#circuit-description-in-spice-syntax)
- [Define Technology Parameters](#define-technology-parameters)
- [First SPICE Simulation](#first-spice-simulation)
- [SPICE Lab with SKY130 Models](#spice-lab-with-sky130-models)

## DAY 2
- [SPICE Simulations for Lower Nodes and Velocity Saturation](#spice-simulations-for-lower-nodes-and-velocity-saturation)
- [Drain Current vs Gate Voltage (Long vs Short Channel)](#drain-current-vs-gate-voltage-long-vs-short-channel)
- [Velocity Saturation at Different Electric Fields](#velocity-saturation-at-different-electric-fields)
- [Velocity Saturation Drain Current Model](#velocity-saturation-drain-current-model)
- [SKY130 Threshold Voltage Labs](#sky130-threshold-voltage-labs)
- [CMOS Voltage Transfer Characteristics (VTC)](#cmos-voltage-transfer-characteristics-vtc)
- [PMOS/NMOS Drain Current vs Drain Voltage](#pmosnmos-drain-current-vs-drain-voltage)
- [Merge PMOS-NMOS Load Curves](#merge-pmos-nmos-load-curves)

## DAY 3
- [Voltage Transfer Characteristics – SPICE Simulations](#voltage-transfer-characteristics--spice-simulations)
- [SPICE Simulation for CMOS Inverter](#spice-simulation-for-cmos-inverter)
- [Static Behaviour Evaluation – CMOS Inverter Robustness](#static-behaviour-evaluation--cmos-inverter-robustness)
- [Analytical Expression of Vm](#analytical-expression-of-vm)
- [Static and Dynamic Simulation of CMOS Inverter](#static-and-dynamic-simulation-of-cmos-inverter)
- [Applications of CMOS Inverter](#applications-of-cmos-inverter)

## DAY 4
- [Introduction to Noise Margin](#introduction-to-noise-margin)
- [Noise Margin Voltage Parameters](#noise-margin-voltage-parameters)
- [Noise Margin Equation](#noise-margin-equation)
- [Noise Margin Variation with PMOS Width](#noise-margin-variation-with-pmos-width)
- [SKY130 Noise Margin Labs](#sky130-noise-margin-labs)

## DAY 5
- [Smart SPICE Simulation for Power Supply Variations](#smart-spice-simulation-for-power-supply-variations)
- [Advantages and Disadvantages of Low Supply Voltage](#advantages-and-disadvantages-of-low-supply-voltage)
- [Sources of Variation – Etching Process](#etching-process-variation)
- [Sources of Variation – Oxide Thickness](#oxide-thickness-variation)
- [Smart SPICE Simulations for Device Variations](#smart-spice-simulations-for-device-variations)
- [SKY130 Device Variation Labs](#sky130-device-variation-labs)


# DAY 1
# Basics of NMOS structure and operation ,Understanding Drain Current (Id) and Drain-to-Source Voltage (Vds) Regions of operation (Cutoff, Linear, Saturation)

#  Introduction to  circuit designs and SPICE simulations

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
#  0-L1 why do we need spice ?

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

# L2 NMOS BASIC ELEMENTS IN CIRCUIT DESIGN

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
  
# L3 THRESHOLD VOLTAGE 

<img width="1027" height="515" alt="image" src="https://github.com/user-attachments/assets/168eb4f5-e5ab-45a6-affe-76594534a1cf" />

* let us take vt is a function of x,y,z .
  
* Vgs=0 and drain ,source and bulk are connected to ground .
  
* Here we can observe that the substrate and diffusion looks like PN junction diode and these are connected back to back.
  
* Both junctions are off due to 0V bias hence channel has high resistance therefore no connectivity between source and drain 
  
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

  # 1.1  L1 NMOS RESISTIVE OPERATION WITH SMALL DRAIN TO SOURCE VOLTAGE 

* It is also known as the Linear Region of operation
*  observe changes when Vgs > Vt .
  
*  Induced charges (Qi) α (Vgs-Vt) .
  
*  when vt = 0.45v ,vgs = 1v, vgs > vt transitor turn on and conducting channel is present between source and drain and we can see  source is connected to ground and drain  is connected to some potential ,there will be a voltage gradient present across the channel . Also effective length is less than actual channel length .
  
*  <img width="965" height="620" alt="image" src="https://github.com/user-attachments/assets/234eceb1-96ff-43f3-be5d-e809891c1a38" />

*  lets plot a graph ,'x' is along the channel and 'y' is perpendicular to channel , y axis represents width , when x=0,1,2,3...,n  at every point v1,v2 ,..,vn the voltage will be different ,all values are different because of small voltage applied ie vds . Every point on x axis will vary w.r.t to Vgs-V(x), this will decide the current equation. where V(x) be the voltage at any point 'x' along the channel and  Vgs-V(x) is the gate-to-channel voltage at that point .
  
# 1.1 L2 Drift current theory 

We know the effective channel voltage will vary w.r.t x, for example at x=0, Vgs=1V and V(x)=0, So the Vgs-Vx=1V. At x=Vds=0.05V, Vgs-Vx=0.95V. 
 * The induced charge at any point 'x' is  Qi(x) α - ((Vgs-V(x))-Vt) ie  Qi(x) = -cox ((Vgs-V(x))-Vt)
   
<img width="531" height="553" alt="image" src="https://github.com/user-attachments/assets/17a4710e-94a3-41df-9917-05ba8d561fff" />

From device point of view ,we have  2 kinds of currents in 
** drift current : current due to potential differnce 

**diffusion current : current due to difference in carrier concentration

<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/ebdef17f-9787-45a7-9983-db3b7aa98fdc" />

# 1.1 L3 Drain current model for linear region of operation 

*drain  current id = (velocity of charge carriers * available charge) over the chanel width .

* velocity vn(x) = product of mobility and electric field .small distance of L there is a change in voltage ,as a result of change in voltage ,velocity differs .
  
* vn(x) = μn.dv/dx .
 
<img width="599" height="900" alt="image" src="https://github.com/user-attachments/assets/78b39a84-03e2-4560-97bd-8f2129e55125" />

Integrating the above equation with x ranging from 0 to l and V from 0 to 𝑉 from 0 to vds .
	​
<img width="619" height="183" alt="image" src="https://github.com/user-attachments/assets/1bc82a41-91ba-4e56-8a1c-14de16bb9c17" />

Here, Cox, W/L, Vgs, un and Vt are the 'technology parameters', we will simulate usinf SPICE and find out the characteristics.

<img width="580" height="332" alt="image" src="https://github.com/user-attachments/assets/0f5e944d-5451-4722-b7be-1c5a6f36b821" />

The equation is simplified into this form where kn' is Cox * mobility. still we simplify this equation into linear form.This equation is suitable only for Vds value is small.so we can neglect square term from the equation.So we get Id=Kn*(Vgs-Vt)
  
<img width="888" height="597" alt="image" src="https://github.com/user-attachments/assets/895a46e4-56e8-4c8f-87ec-3df64cbe10f8" />

we need to find the impact of Vds and Vgs on Id drain current.The NMOS works in linear region only when Vds <= Vgs-Vt.

# 1.1 L4 SPICE conclusion to resistive operation 

<img width="729" height="221" alt="image" src="https://github.com/user-attachments/assets/1154ef38-6afa-4269-ad46-ae8e95a3263a" />

We need to find the impact of Vgs and Vds on the drain current equation using diffferent values of vgs and vds . If we consider different values of Vgs, under what condition the device will remain in Linear region depends on (Vgs-Vt) should be greater than Vds.

A MOSFET operates in the linear (resistive) region when: Vds < (Vgs − Vt) ,Where:
* Vt = 0.45 V
  
* Vgs = 0.5 V, 1 V, 1.5 V, 2 V, 2.5 V
  
* (Vgs − Vt) = 0.05 V, 0.55 V, 1.05 V, 1.55 V, 2.05 V
  
For each Vgs value, Vds is swept from 0 to (Vgs − Vt) to maintain linear operation.
SPICE simulation is performed to sweep Vds, calculate Id, and verify resistive behavior of the MOSFET.

# 1.1 L5 SATURATION REGION 

when Drain-source voltage exceeds the value (Vgs-Vt), the region of operation is called "Saturation Region" .

<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/1ece8121-74c0-49ac-b831-3694ebcb7674" />

* vgs is constant at 1v , vt is constant at 0.45 v and vds is increased gradually from 0.05 v to observe vgs-vds ie channel voltage .

  <img width="1600" height="650" alt="image" src="https://github.com/user-attachments/assets/48234bd7-17e6-430e-8e2a-190b17e82bdc" />

* When Vgs-Vds is greater than Vt, there will be a conducting channel.
  
* When Vgs-Vds is equal to Vt,  Inversion has happened at drain side and it is equal to Vt, therefore channel will start disappearing at drain side.
  
<img width="1600" height="659" alt="image" src="https://github.com/user-attachments/assets/4763e7f7-c3ed-49fd-b555-9ee35a8c43f6" />

* The phenomenon where channel gets disapper is called PINCH -OFF phenomenon .
  
* When Vgs-Vds<=Vt, there is no channel present near the Drain terminal, this region is saturation region .
  
# 1.1 L6 DRAIN CURRENT MODEL FOR SATURATION REGION OF OPERATION 

<img width="734" height="640" alt="image" src="https://github.com/user-attachments/assets/584a15e7-c939-4509-b667-ef66dcc1eeb0" />

In saturation region the channel voltage remains constant = vgs-vt . Drain current was  linear function of  vds .

*To get drain current equation in saturation region we will replace Vds as Vgs-Vt.

<img width="637" height="366" alt="image" src="https://github.com/user-attachments/assets/ef922a68-4d9f-4c5c-96ed-20aaff2621a3" />

At first , the MOSFET seems to act like a perfect current source. But in reality, when we increase vds
,the depletion region at the drain gets larger, which shortens the effective channel. This causes the drain current Id to slightly depend on vds . 

<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/d89ec2eb-b8cf-4020-8d8d-36125c4dca3e" />

The drain current equation is given below and  λ is  called channel length modulation .

 <img width="1600" height="312" alt="image" src="https://github.com/user-attachments/assets/e74e9892-b699-4538-a243-136d19bd378a" />

# 1.2 L1 Introduction to spice 

* SPICE is a software its a engine that has predefined models and models are part of engine we need to feed correct values inputs  to the engine and correct netlist to the engine ,and it will derive some wave forms , these waveforms are used to calculate delay of the cell, basic backups for delays . 

* STEP 1:  correct spice setup

  <img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/a1c11953-6307-45c4-adf4-3729b0767e4c" />

we need to feed models correct way so that spice understands and evaluates as expected .

<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/b95fae12-9c73-4ea2-97a3-70447a281a04" />

Technology constants are circled in yellow clr ,every technology node has unique value ,these are provided to engine through special file called model file . these has to correct to derive correct voltage and waveforms .

<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/3cf1d7f9-79e9-4f2d-9022-576af1c580cb" />

when spice model parameters +spice netlist added to spice software it gives graphs of the output 

*SPICE Netlist We need to feed the device into SPICE engine in certain manner, the circuit equivalent of given mosfet is as shown below.

<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/678d1fca-d7b0-414d-a9ce-abe26ff67c14" />

#  1.2 L2 Circuit description in SPICE syntax
* Defining nodes 
<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/522129d1-b7da-4daa-807c-3910322d7d6d" />

* Node means having no obstruction between two points ie If two terminals are directly connected by a wire, they belong to the same node.

* In circuit design, there is no strict restriction on node naming; nodes can be assigned any numerical value or meaningful label for easy identification.
  
* A MOSFET is a four-terminal device consisting of drain (D), gate (G), source (S), and substrate (bulk).

 * 4 nodes defines complete spice netlist .
 <img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/62aed6fa-867f-4a1f-ad9e-f27aa2940bd8" />
 
 * Names of node in,n1,0,vdd .the MOSFET is represented by the letter M. The drain terminal is connected to VDD, the gate is connected to node n1, and both the source and substrate are connected to ground (0 V), making it a DGSS configuration.

<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/36a49d73-da23-404e-acaa-d4196c4a3c07" />

The MOSFET is defined with a width (W) of 1.8μ and a long channel length (L) of 1.2μ. Any component whose name starts with the letter R represents a resistor; for example, R1  is connected between the input node and node n1, with a resistance value of 55 ohms.

<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/ef1e0fe6-a578-4da6-93a0-0e30fd291e0e" />

<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/ed50544b-74c1-4e4c-b0de-985b6b6eb4c1" />

 The technology file is defined by including all the necessary model parameters and constraints required for proper device operation and simulation, ensuring that the circuit follows the fabrication process specifications.

# 1.2 L3 Define technology parameters 

Here we will see how to model this NMOS transistor. The model parameters are already given, so it is easy to create the model using them. These parameters are available in the technology file. The NMOS model can be found in the file with the same or a similar model name.

<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/f40003ca-92b5-4312-8754-1f44a99fd391" />

<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/caa8aca2-0f21-4554-b652-2c4307daacd4" />

These are the parameters coming from foundry ,we can use it in spice by .MODEL as stated above .Here we can state parameters in its respective positions as it has predeined positions for diffrent values.
we just plug in this packaged file in .mod file and call this file in top level SPICE netlist.

<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/7a4e702d-f360-42af-a02e-9f3be1fdf454" />

* All these models can be stored in .lib format .This can be used in spice console .

2 VDS ARE LEFT 

# 1.2  L4 first spice simulation 
* Open Virtual box

* Type cd

* git clone https://github.com/kunalg123/sky130CircuitDesignWorkshop.git

<img width="1600" height="1028" alt="image" src="https://github.com/user-attachments/assets/8a6df2fb-a98c-4f61-8e34-8cb7fc709a7d" />

<img width="1600" height="785" alt="image" src="https://github.com/user-attachments/assets/aa462a34-8431-42e8-91de-14c3a79cfda6" />

<img width="1600" height="271" alt="image" src="https://github.com/user-attachments/assets/aef0be0d-528f-4229-8011-c443aebe2eae" />

<img width="1597" height="972" alt="image" src="https://github.com/user-attachments/assets/49f2944c-5adf-4cd0-8c80-0e162a046496" />

<img width="1600" height="992" alt="image" src="https://github.com/user-attachments/assets/b19040c7-7ed6-470b-b9a2-569a42966133" />

# 1.2 L5 SPICE LAB WITH SKY 130 MODELS 

If we go inside models folder, we will see all.spice file. If we open it we will see the scale of Width and Length.

<img width="1600" height="654" alt="image" src="https://github.com/user-attachments/assets/d3e50b25-111b-4bc9-936e-11e11de6b025" />

# DAY -2 2.1 L1 SPICE SIMULATIONS FOR LOWER NODES AND VELOCITY SATURATION 

Result of spice simulation 

<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/ec641455-cafb-4e33-8a37-77f8c77fcb9f" />

*The blue line in the graph represents the condition Vds = Vgs − Vt. This line separates the graph into two operating regions:
1. Linear Region:
In this region, Vds is small. Because of this, the current equation behaves almost linearly. Even though Vds is small, it still affects the diffusion current. As a result, the graph appears nearly straight, showing a linear relationship between Id and Vds.
<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/ff11773b-d685-4abd-899b-3d90043c4e07" />

2. Saturation Region:
When Vds reaches the value equal to (Vgs − Vt), the device enters saturation. In this region, the drain current (Id) becomes almost constant according to the equation. However, due to channel length modulation, there is a slight increase in Id instead of it being perfectly constant. Therefore, the graph looks nearly flat but with a small slope. below is cut off region .

* We can also see that when Vgs = 0, the drain current Id is zero. As Vgs increases beyond the threshold voltage, Id increases accordingly.

* when w/l is constant  and drain current should be constant but that doest happens with lower nodes ,Below is the spice deck where only the values of W and L is changed by keeping w=0.375 u,l=0.25u and other values remains same .  
  
<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/a0266d48-367e-43f4-9254-2651a5856ee9" />
 
<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/a7c2702d-bbda-4112-9c29-d4a5d56d9f28" />

# 2.1 L2 Drain current vs gate voltage for long and short channel device 

compare the two simulations :
observation 1: 

* For long channel device Drain current at each and every gate voltage at vds=2.5 v there is Quadratic dependence ,its not linearly increasing with gate voltage .
  
<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/6d93e12d-f17d-4bba-8d62-6df78d0f9207" />

* For short channel device initially at lower values of gate voltage we still have small amount of  quadratic dependence ,but  drain current linearly increasing with increasing  gate voltage .
  
*This happens due to VELOCITY SATURATION.

*Now we will plot Id vs Vgs at different value of Vds or vds at constant .

<img width="1392" height="900" alt="image" src="https://github.com/user-attachments/assets/f6056e01-b191-4dc9-aec9-66f0bd2b5afe" />

by  spice simulating for Id s Vgs at constant vds .

<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/41e62330-233d-4ac0-b635-343c1ea7c280" />

The plot we get is quadratic, it is only when Vds=2.5V .

# 2.1 L3 velocity saturation at lower and higher electric fields 

observation 1: For long channel ,the drain current (Id) follows clear quadratic relationship with Vgs . and for short channel ,at lower vgs drain current still shows quadratic but drain current increases linearly with increasing gate voltage .This happens due to velocity saturation .

<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/7d8fbd37-4041-4d99-9aa0-676f153d9c1a" />

For lower nodes there are four regions of operation ,they are : cutoff, linear,saaturation and velocity saturation .

VELOCITY SATURATION : For lower values of electric field  the velocity tends to linear function of electric field  and after certain point  it saturates .

<img width="1258" height="572" alt="image" src="https://github.com/user-attachments/assets/70a84914-8043-4ac4-935d-0f2189edccd3" />

at lower fields velocity tends to be at linear function 
<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/35f61cf9-9ebe-4b6d-8386-39a303835028" />

at higher fields velocity tends to be constant due to scattering effect.

<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/45238389-de17-4e7d-af5a-657d23924696" />

we need to add velocity constant in the below equation 

<img width="1600" height="504" alt="image" src="https://github.com/user-attachments/assets/5fdca34a-9fea-4bb8-a397-cceddbb0222e" />

we simplify the above equation using 2 different modes.
1. Long channel (>250nm)
2. Short channel (<250nm)
*In both modes major working regions regions are same.

*In short channel we can observe extra region namely "velocity saturation".

<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/991ba605-cfef-4b5e-ab04-48b4b4b82c4a" />

# 2.1 L4 velocity saturation drain current 

*lets call (vgs-vt)= vgt , we are dealing with higher values of  vgs.  we will use the drain current equation mentioned earlier.

*There is also another important technology parameter called vdsat. It is the value of drain-to-source voltage at which the device just starts entering the velocity saturation region. vdsat ie voltage at which device velocity saturates and independent of vgs or vds .

* when vgt =0 , there is no drain current .transistor enter into cut off region

 lets derive drain current equations for each and every operation .
 
 <img width="1599" height="606" alt="image" src="https://github.com/user-attachments/assets/c7d37482-7f2a-4d52-8df1-77bd196199f1" />

 1.When vgt = minimum value  ,it means vds and vdsat are high . so mosfet works in saturation region .the current equation is in above image 

 <img width="1600" height="586" alt="image" src="https://github.com/user-attachments/assets/3be89355-4a8e-470e-94e8-5580b890cfb8" />

 2. when vds = minimum value  , device enters into resistive or linear region of operation . When vds​ is small, the effect of the lambda (λ) term is very small, so we can ignore the term .

<img width="1600" height="602" alt="image" src="https://github.com/user-attachments/assets/42267b11-a86f-4891-8997-e83bbd1b94b4" />

3. when vdsat= minimum value , device enters into velocity saturation region of operation . 

<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/1a425842-d5f8-450e-bf60-85185958f972" />

* The saturation current at lower nodes is smaller, not higher. This happens because velocity saturation makes the device enter saturation earlier than expected. As a result, the maximum current reached at lower nodes is much less compared to higher nodes

  # 2.1  L5 labs
  We will now do simulation for lower nodes.
  <img width="1366" height="768" alt="image" src="https://github.com/user-attachments/assets/d18e0d61-9681-4dfe-996d-2cf9de50be50" />

<img width="1366" height="768" alt="image" src="https://github.com/user-attachments/assets/a4a7e32f-47d5-4a98-a950-5831a516aca6" />

<img width="733" height="530" alt="image" src="https://github.com/user-attachments/assets/fabf1aef-aaf7-48d8-af91-3962f8532116" />

The above plot is Id vs Vds for different values of Vgs. We can see for lower values of Vgs it is showing quadratic behaviour and for higher values of Vgs it is showing Linear behaviour. Now if want to see the peak current for Vgs=1.8V, just 'press' left click on mouse at Vgs=1.8V

<img width="290" height="22" alt="image" src="https://github.com/user-attachments/assets/2d9819fb-92a8-46cc-8c66-4d945f1103d9" />
So we can see it is approximately 198uA.

* Now let us observe Id vs Vgs
Here again we are taking values for L=0.15u and W=0.39u, Keeping Vds constant at 1.8V and sweeping Vgs from 0 to 1.8V with step of 0.1V.


<img width="1366" height="768" alt="image" src="https://github.com/user-attachments/assets/46092cd5-8143-456d-b178-a9ecb30e8b82" />


<img width="692" height="538" alt="image" src="https://github.com/user-attachments/assets/0f7a9c5f-934c-4e74-b5d9-8545ac860336" />

# 2.1 L6  labs sky 130 vt 

Now we will calculate Threshold Voltage Vt for Id vs Vgs curve.

<img width="292" height="30" alt="image" src="https://github.com/user-attachments/assets/394bf262-73f8-4fb9-9c97-78cea21b8206" />

In the curve we can see that Vt is the value when current increases drastically for small change in Vgs. To calculate we will draw tangent on the curve and see where it touches.

<img width="1366" height="768" alt="image" src="https://github.com/user-attachments/assets/2e3fc211-2ebc-49c5-b6fc-df812ac3bf5d" />

  # 2.2 L1 cmos voltage transfer characteristrics
  
 The MOSFET switch model is a simplified but very powerful way to understand how digital logic works without solving complex equations. 
 
 <img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/641ff6b3-8895-442c-9354-6dbbad1628b5" />
 
* A MOS transistor has three terminals: Gate, Source, and Drain.The gate controls the device,Carriers enter through the source and leave through the drain.
  
* important parameter is |vgs| which is compared with threshold value to know wheather transistor is on or off .
 
* if |vgs| exceeds threshold value  then device turns on .
 
<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/2f1297ab-e223-4db0-a0bc-b63feafa4f6a" />

*Transistor as a Switch

* With infinite OFF resistance when |Vgs| < |Vt| , No channel forms, so it acts like an open switch with very high (almost infinite) resistance.
  
* With finite ON resistance when |Vgs| > |Vt| ,A channel forms, so it behaves like a closed switch with low (finite) resistance.

  ## cmos inverter circuit

  <img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/5c9d883d-4a19-4166-8222-1b87c20b5576" />
  
* cmos complementary metal oxide semiconductor .  it is a complemetary circuit for  both PMOS and NMOS  which allows complementary logic.

* In a CMOS inverter, there are only two transistors: one PMOS and one NMOS.The PMOS has its source connected to Vdd, its gate connected to Vin, and its drain connected to Vout . The NMOS has its source connected to Vss (ground), its gate connected to Vin, and its drain also connected to Vout

* When the input voltage vin = supply voltage vdd the PMOS gate and source are at the same potential. This makes the gate-to-source voltage of the PMOS equal to 0 V. Since this value is smaller than its threshold voltage, the PMOS cannot turn ON. so, it stays OFF and behaves like an open switch, meaning no current flows through it.

 * At the same time, for the NMOS, the gate is at vdd and the source is at ground (0 V). So the gate-to-source voltage becomes equal to vdd. Because this voltage is higher than the NMOS threshold voltage, the NMOS turns ON. In this condition, it behaves like a closed switch with some resistance, allowing current to flow.

   <img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/01ee6cdd-84e8-4b4c-9663-42fda00aebac" />
   
# 2.2 L2 INTRODUCTION TO STANDARD MOS VOLTAGE CURRENT PARAMETERS 

 # CASE 1: Vin =Vdd  
  
 * When Vin=Vdd, the PMOS turns OFF (open switch) and the NMOS turns ON ,In this condition, the PMOS is OFF, so there is no connection between Vdd and the output. The NMOS is ON, so it connects the output to ground through its resistance RN  .Because of this, the output voltage is pulled down to 0 V. The load capacitor CL also discharges to 0 V.

So, when Vin = HIGH (Vdd), the output becomes LOW (0 V). This is the normal inverter operation — a high input gives a low output.

Here, the PMOS is OFF and the NMOS works in the linear region, acting like a resistor that pulls the output to ground.

For PMOS:

*	VgsP = Vin – Vdd = Vdd – Vdd = 0 V

*	Since |VgsP| = 0 < |Vtp|, the PMOS does not turn on

*	PMOS turns OFF → acts as an open switch (no connection between Vdd and Vout)

For NMOS:

*	VgsN = Vin – Vss = Vdd – 0 = Vdd

*	Since VgsN = Vdd > Vtn, the NMOS turns on

*	NMOS turns ON → acts as a closed switch with resistance Rn .
  
* The equivalent circuit for this case shows: Vdd → open switch (PMOS OFF) → disconnected, and Vout → Rn (NMOS ON) → Vss.
  
* Since the only path from the output node is through Rn to ground, the output voltage Vout is pulled down to 0 V. The load capacitor CL also discharges to 0 V through Rn.

* When Vin = Vdd → Vout = 0 (Output is LOW). This is the inverting property of the CMOS inverter.

<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/7e0cf1ab-a9fc-4fa7-8986-2d926c80831e" />

  #case 2:

* Vin is LOW (Vin = Vss = 0 V) We have analyzed the case when Vin is HIGH. Now we also need to analyze when vin=0 .By combining both cases, we can evaluate the total delay of the circuit.

<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/1a69c3c8-d95d-4896-bf38-ae6095458ddc" />

For PMOS:
*	VgsP = Vin – Vdd = 0 – Vdd = –Vdd

*	Since |VgsP| = Vdd > |Vtp|, the PMOS turns ON

*	PMOS turns ON → acts as a closed switch with resistance Rp

<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/64925900-a484-4215-83a3-1dfc34cb32b6" />

For NMOS:
*	VgsN = Vin – Vss = 0 – 0 = 0 V
	
*	Since VgsN = 0 < Vtn, the NMOS does not turn on
	
*	NMOS turns OFF → acts as an open switch (no path from Vout to Vss)
	
*	The equivalent circuit for this case shows:	Vdd → Rp (PMOS ON) → Vout, and Vout → open switch (NMOS OFF) → Vss.
	
*	Since there is no path from Vout to ground and there is a direct connection from Vdd through Rp to Vout, the output charges up to Vdd. The load capacitor CL charges to Vdd through Rp.

* When Vin = 0 → Vout = Vdd (Output is HIGH). The output is the logical inversion of the input.

Let us give the naming convention of the CMOS

<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/3e7256c3-2323-4279-92df-3b1b2bfcaafd" />

*	G = Gate, S = Source, D = Drain
  
*	Vgs = Gate – Source Voltage (controls transistor switching)
  
*	Vds = Drain – Source Voltage (across the transistor channel)
  
*	P, N = PMOS & NMOS respectively (used as subscripts)
  
*	IdsN = Drain–Source current through NMOS
  
*	IdsP = Drain–Source current through PMOS

#  2.2 L3 PMOS/NMOS drain current v/s drain voltage

<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/76e1b909-4bf9-41c8-8486-34a6a8131ea7" />

The CMOS inverter consists of two transistors:
*	PMOS: source connected to Vdd, gate connected to Vin, drain connected to Vout
  
*	NMOS: source connected to Vss (GND), gate connected to Vin, drain connected to Vout
  
*	Load capacitor CL is present at the output node
Terminal Voltage Derivation
We derive the Vgs and Vds expressions for each transistor by observing circuit connections.

<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/13c4e841-4ca4-4b4c-a240-0436a649bd34" />

For NMOS (source = Vss = 0V):
*	VgsN = Vin – Vss = Vin
  
*	VdsN = Vout – Vss = Vout
  
*	So, IdsN is a function of Vin and Vout

* The gate-to-source voltage of the NMOS is directly equal to the input voltage Vin, and the drain-to-source voltage is equal to the output voltage Vout. So, the NMOS drain current IdsN is a function of both Vin and Vout.
  
For PMOS (source = Vdd):
*	VgsP = Vin – Vdd
	
*	VdsP = Vout – Vdd
  
*	Both are negative (since Vin ≤ Vdd and Vout ≤ Vdd), which is consistent with PMOS operation

* Both VgsP and VdsP are negative values since Vin and Vout are always less than or equal to Vdd. This is consistent with PMOS operation, which requires negative gate-to-source voltage to turn on.

* Since both transistors share the same output drain node, the current flowing through PMOS must equal the current flowing through NMOS. The sign difference occurs due to the direction of current flow:
IdsP = – IdsN .This equation is very important. It means that whatever current the PMOS supplies (charging CL), the NMOS must sink (discharging CL) in steady state. In transient conditions, the difference in these currents determines how quickly the output node charges or discharges
* NMOS IdsN vs VdsN Characteristic Curve
  
* The Id vs Vds characteristic curve for the NMOS transistor, the curve is plotted with IdsN on the Y-axis and VdsN on the X-axis, with multiple curves corresponding to different values of VgsN.

* Since VgsN = Vin and VdsN = Vout, each curve on the graph corresponds to a fixed input voltage, and the X-axis represents the output voltage Vout. The curve shows:

*	At lower values of VdsN, the NMOS operates in the linear (resistive) region where IdsN increases almost linearly with VdsN .

*	Beyond the pinch-off point (VdsN = VgsN – Vtn), the NMOS enters saturation and the current flattens out

*	Higher values of VgsN (Vin) result in higher saturation currents – represented by the curves VgsN1 through VgsN5 from bottom to top

<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/bc8ac3cc-0f0e-4c6a-bbcf-1b157fee02d2" />

PMOS IdsP vs VdsP Characteristic Curve

Since PMOS operates with negative voltages:
*	The X-axis is plotted as –VdsP (which corresponds to Vdd – Vout)

*	The Y-axis is plotted as –IdsP (because PMOS current flows in the opposite direction)

*	Multiple curves are drawn for –VgsP1 through –VgsP5 representing different input voltage conditions

* The shape of the PMOS curve is similar to the NMOS curve but mirrored, since PMOS is structurally a complementary device.

<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/0b51c4f8-2ca3-4b9c-83ea-c3ddbbea0274" />

# 2.2 L4 Step 1- Convert PMOS gate-source-voltage to Vin

* We have seen various internal voltages, but actually in terms of user's perspective we can't see the internal voltages and only see the external Vin and Vout. From these we calculate the VTC and eventually we get to know the delay.

* Now we will see the steps to obtain Voltage Transfer Characteristics(VTC) for static CMOS inverter: Assumption: Let us assume that it is a long channel device with Vdd=2V

We will fix the Vgs values as shown below image ,Since Vdd = 2V, we assign actual values to the 5 PMOS gate-source voltage levels:

<img width="1600" height="592" alt="image" src="https://github.com/user-attachments/assets/06babafb-e17c-47df-a173-72acaf0c48c9" />

We know that Vgsp= Vin-Vdd, So we get the above values.So we get Vin = Vgsp+Vdd, we are trying to convert all the voltages as function of Vin and Vout.

We will try to plot the graph of PMOS in terms of Idsn, the plot will be as shown below. We can see that the corresponding Vin value of Vgsp is being plotted as shown in the above table.

<img width="1600" height="611" alt="image" src="https://github.com/user-attachments/assets/e6dbe2c2-dcbf-4432-ab12-b32efee6b440" />

Since IdsP = – IdsN, the PMOS load curve is relabeled with Vin values on the Y-axis instead of the internal –VgsP labels. The five curves now correspond to:
*	Vin = 0  →  (was –VgsP5 = –(–2) = 2V, PMOS strongly ON, highest current)
  
*	Vin = 0.5  →  (was –VgsP4)
  
*	Vin = 1  →  (was –VgsP3)
  
*	Vin = 1.5  →  (was –VgsP2)
  
*	Vin = 2  →  (was –VgsP1 = 0V, PMOS OFF, no current)

*The order of Vin values on the PMOS curve is reversed compared to NMOS. This is because lower Vin makes VgsP more negative, turning PMOS on harder.

# 2.2 L5 Step2 & Step3 – Convert PMOS and NMOS drain-source-voltage to vout 

<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/edd4f97c-03cd-4250-a57f-d45b19866869" />

The original PMOS characteristic curve uses (-VdsP) as the X-axis and (-IdsP) as the Y-axis, because PMOS operates with negative voltages. To compare it with the NMOS curve and find the inverter operating point, both curves must be plotted on the same axes: X = Vout and Y = IdsN. This requires an axis conversion for the PMOS curve, while the NMOS curve is already in the correct form.
pmos/...
<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/3fa49a0c-2c7b-4802-9e12-d095fb78eb78" />

X-axis Conversion:

We know from the circuit that VdsP = Vout - Vdd. Rearranging this gives:
Vout = Vdd + VdsP
The original PMOS X-axis runs from 0 to Vdd in the direction of -VdsP (left to right). After conversion, the X-axis runs from Vdd to 0 in the Vout direction. This is why the PMOS load curve runs from right to left on the Vout axis.
Y-axis Conversion:

We apply the current continuity condition derived earlier:
IdsP = -IdsN   =>   IdsN = -IdsP
The original PMOS Y-axis shows -IdsP (to make the values positive). After applying this relation, the Y-axis becomes IdsN directly .

*After conversion, the PMOS curves are labeled with Vin values. The Vin = 0 curve is the topmost curve (PMOS fully ON, maximum current). The Vin = 2 curve is the bottommost (PMOS fully OFF, zero current).

Step 3 — NMOS Load Curve (No Conversion Needed)
<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/bd5284d1-d703-4a37-a0c8-c7bbe8370c20" />

For NMOS, the terminal voltages are:
* VgsN = Vin

* VdsN = Vout

* Since VdsN is already equal to Vout and the Y-axis is already IdsN, no conversion is needed. The NMOS characteristic curve in its standard form is directly the NMOS Load Curve
# NMOS Vin Mapping
image 
NMOS Load Curve Behavior:
*	Vin = 0V: NMOS is OFF (VgsN = 0 < Vtn), entire curve at zero current
	
*	Vin = 2V: NMOS is fully ON, highest current curve
  
*	As Vout increases from 0 to Vdd: curve rises steeply in linear region, then flattens in saturation
  
*	Higher Vin gives higher curves (opposite to PMOS)
  
final comparision 
<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/f7fafe6d-fd4b-4aaf-ae6e-e0854719eb5f" />

*	Both load curves now share the same axes: X = Vout (0 to Vdd), Y = IdsN
  
*	For a given Vin, the NMOS and PMOS carry the same current in steady state
  
*	The intersection of the NMOS and PMOS load curves for the same Vin gives the operating point (Vout at that Vin)
  
*	Plotting these operating points for all Vin values gives the complete Voltage Transfer Characteristic (VTC)
	
# 2.2 L6 Merge PMOS – NMOS load curves and plot VTC

Before merging, we have two separate Id vs Vout load curves derived from the previous lectures:
NMOS Load Curve:
*	X-axis = VdsN = Vout, Y-axis = IdsN
  
*	Five curves for Vin = 0, 0.5, 1, 1.5, 2 V (bottom to top)
  
*	Vin = 0 → NMOS OFF → IdsN = 0 (flat line at X-axis)
  
*	Higher Vin → higher IdsN in saturation

<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/e423bcbf-ca1e-45d6-9962-635d7c47cdcf" />

PMOS Load Curve:
*	X-axis = Vout (mapped from VdsP), Y-axis = IdsN (= |IdsP|)
*	Five curves for Vin = 0, 0.5, 1, 1.5, 2 V (top to bottom)
*	Vin = 0 → PMOS strongly ON → highest IdsP (topmost curve)
*	Vin = 2 → PMOS OFF → IdsP = 0 (flat at X-axis)
*   Vin ordering is reversed compared to NMOS because lower Vin makes VgsP more negative
since Vin and Vout are common to both PMOS and NMOS in the inverter, these two sets of curves can be placed on the same graph to find the operating points

# Superimposing Load Curves – Finding Operating Points

<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/615b597a-ac0f-4124-a285-6e95c4224082" />

Both load curves are placed on the same IdsN vs Vout plot. This is valid because:
*	Vin is common to both PMOS and NMOS (both gates are tied together)
  
*	Vout is common to both drains
  
*	At steady state: IdsP = IdsN (current continuity at output node)

After superimposition, the corresponding Vin curves from PMOS and NMOS intersect each other. Each intersection point is the DC operating point (Vout) for that particular Vin value.

*	For each Vin, there is exactly one intersection point between the PMOS and NMOS curves
  
*	This intersection gives the unique Vout value for that Vin
  
*	These (Vin, Vout) pairs form the data points of the VTC curve
  
# VTC Point-by-Point Construction

Reading the five intersection points from the superimposed plot:
<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/4bcbe534-491d-41e4-b848-83cfa7a6dc12" />

Vin = 0 V:
*	NMOS: OFF (VgsN = 0 < Vtn) → IdsN = 0, curve is flat at zero
  
*	PMOS: strongly ON (VgsP = –Vdd, maximum drive)
  
*	Intersection at Vout = Vdd = 2 V
  
*	VTC point: (0 V, 2 V) | Transistor states: PMOS linear, NMOS off

Vin = 0.5 V:
*	NMOS barely ON (VgsN = 0.5 V, just above Vtn)
  
*	PMOS still strongly ON (VgsP = –1.5 V)
  
*	Intersection: 1.5 < Vout < 2 V
  
*	VTC point: (0.5 V, ~1.5–2 V) | Transistor states: PMOS linear, NMOS saturation

Vin = 1 V:
*	NMOS and PMOS have comparable drive strengths

*	Both transistors in saturation → maximum gain region (sharpest VTC slope)
  
*	Intersection near Vout ≈ 1 V (midpoint of supply)
  
*	VTC point: (1 V, ~1 V) | Transistor states: PMOS sat, NMOS sat

Vin = 1.5 V:
*	NMOS strongly ON (VgsN = 1.5 V)
  
*	PMOS barely ON (VgsP = –0.5 V, close to |Vtp|)
  
*	Output pulled low: Vout between 0 and 0.5 V
  
*	VTC point: (1.5 V, ~0.5 V) | Transistor states: PMOS sat, NMOS linear

Vin = 2 V (= Vdd):
*	PMOS: OFF (VgsP = 0 V, |VgsP| < |Vtp|) → IdsP = 0
  
*	NMOS strongly ON (VgsN = 2 V)
  
*	Output pulled all the way to 0 V
	
*	VTC point: (2 V, 0 V) | Transistor states: PMOS off, NMOS linear

# Complete VTC Curve

<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/633ad184-291e-49b0-ac95-88365d668696" />

The five plotted points form the characteristic S-shaped VTC. The three distinct regions of the VTC are:
*	Flat HIGH region (low Vin): Vout ≈ Vdd. PMOS is ON and supplies current; NMOS is OFF. Output stays at logic HIGH.
  
*	Transition region (mid Vin ≈ Vdd/2): Vout rapidly switches from HIGH to LOW. Both PMOS and NMOS are simultaneously in saturation — this gives the maximum gain and sharpest slope
  
*	Flat LOW region (high Vin): Vout ≈ 0 V. NMOS is ON and pulls output to ground; PMOS is OFF. Output stays at logic LOW.
  
*	This graphical method of VTC construction using load-line analysis is the foundation for understanding CMOS DC characteristics

# DAY 3

#  L1 VOLTAGE TRANSFER CHRACTERISTICS - SPICE SIMULATIONS 

<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/70e2bb4c-862a-4f21-b9ba-4aa022cb1251" />

Now we will write the SPICE deck for the CMOS inverter to simulate the Voltage Transfer Characteristic (VTC). A SPICE deck has three main parts:
•	Component connectivity
•	Component values
•	Identify 'nodes'

# Component Connectivity

The CMOS inverter circuit consists of:
*	M1 – PMOS transistor, source connected to Vdd

*	M2 – NMOS transistor, source connected to Vss (ground)
  
*	Gates of both M1 and M2 connected together at input node Vin
  
*	Drains of M1 and M2 connected together at output node Vout
  
*	Load capacitor cload connected from the output node to Vss

# Component Values
<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/049b105f-bbba-46d8-b5c7-aa1e4d6401fc" />

The component values for this simulation are:
•	M1 (PMOS): W = 0.375u, L = 0.25u
•	M2 (NMOS): W = 0.375u, L = 0.25u
•	cload = 10fF

The W/L ratio for both transistors is 0.375/0.25 = 1.5.

 # Adding Supply Voltage Sources

The supply voltage sources are added to the circuit:
*	Vdd = 2.5V connected from node vdd to Vss
  
*	Vin = 2.5V (input source) connected from node in to Vss

# Identifying Nodes

<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/b1744253-7384-42d7-af94-9ea9d1821b4d" />

A node means there is no obstruction between two points, i.e., if two terminals are directly connected by a wire, they belong to the same node.

The four nodes identified in this circuit are:
*	vdd – supply voltage node
  
*	in – input node (connected to gates of M1 and M2)
  
*	out – output node (connected to drains of M1 and M2 and top plate of cload)
  
*	0 (Vss) – ground node

SPICE Netlist Description

<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/00f3a380-fa5a-43fd-89a4-c1cf132d3bd1" />

The MOSFET is described in SPICE syntax as:

  M <name>  <drain>  <gate>  <source>  <substrate>  <model_name>  W=<value>  L=<value>

For the CMOS inverter, the two transistor lines in the netlist are:

M1  out  in  vdd  vdd  pmos  W=0.375u  L=0.25u
M2  out  in  0    0    nmos  W=0.375u  L=0.25u

Explanation:
*	M1: drain = out, gate = in, source = vdd, substrate = vdd, model = pmos
  
*	M2: drain = out, gate = in, source = 0 (GND), substrate = 0 (GND), model = nmos
  
*	The PMOS substrate is connected to vdd (highest potential) and the NMOS substrate is connected to 0 (ground) — this is standard CMOS practice

*	A SPICE deck for CMOS inverter requires: component connectivity, component values, and node identification
  
*	Both M1 (PMOS) and M2 (NMOS) have W = 0.375u, L = 0.25u giving W/L = 1.5 for both
	MOSFET SPICE syntax order is: drain, gate, source, substrate, model name, W, L

*	Four nodes are defined: vdd, in, out, and 0 (ground)
  
*	PMOS source and substrate are connected to vdd; NMOS source and substrate are connected to 0 (GND)

# L2 -SPICE simulation for CMOS inverter
<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/5a3ceb0a-653d-4f2d-8c04-2320c60b3580" />

The complete SPICE deck for simulating the Voltage Transfer Characteristic (VTC) of the CMOS inverter is built in the following sections:
*	 MODEL Descriptions
	
*	NETLIST Description
	
*	Component values (passive elements and sources)
  
*	 SIMULATION Commands
  
<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/35515b2d-c794-4142-8438-da9ff0c4277e" />

# SPICE Netlist – Transistors

The two transistor lines define the PMOS (M1) and NMOS (M2) devices:

M1  out  in  vdd  vdd  pmos  W=0.375u  L=0.25u
M2  out  in  0    0    nmos  W=0.375u  L=0.25u

M1 is the PMOS transistor: drain and gate at output (out) and input (in) nodes, source and substrate at vdd. M2 is the NMOS transistor: drain and gate at out and in, source and substrate at ground (0).

# SPICE Netlist – Passive Elements and Sources
<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/c8d0f2ba-f5a2-4a19-b10f-b62f435740ec" />

The passive elements and voltage sources are:

cload  out  0  10f
Vdd  vdd  0  2.5
Vin  in   0  2.5

cload is the load capacitor of value 10fF connected from output node to ground. Vdd is the supply voltage source of 2.5V. Vin is the input voltage source of 2.5V (it will be swept by the DC simulation command).

<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/f6f6775a-c991-4a87-9c70-66102310d4a6" />

# Simulation Commands

Two simulation commands are used:

.op
.dc  Vin  0  2.5  0.05

*	.op – Calculates the DC operating point of the circuit
*	.dc Vin 0 2.5 0.05 – Performs a DC sweep of Vin from 0V to 2.5V in steps of 0.05V

<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/598cab89-7c1a-4456-90ee-c461421ff024" />

The dc sweep allows us to observe how the output voltage Vout changes as the input voltage Vin is swept from 0 to Vdd, which directly gives us the VTC curve.

Including the Technology Model File

The technology model file is included in the SPICE deck to provide the foundry-specific MOSFET parameters. The syntax used is:

 * .LIB  "tsmc_025um_model.mod"  CMOS_MODELS
 *  .end

*	.LIB includes the model file and specifies the section name CMOS_MODELS
*	.end marks the end of the SPICE deck

# Technology Model File (tsmc_025um_model.mod)

The model file tsmc_025um_model.mod contains the SPICE model parameters for both NMOS and PMOS transistors from the TSMC 0.25um process. The file defines:
*	.MODEL nmos NMOS – NMOS model with all technology parameters
  
*	.MODEL pmos PMOS – PMOS model with all technology parameters

The PMOS model parameters include technology constants such as:
*	VERSION, TNOM, TOX (gate oxide thickness)
  
*	XJ (junction depth), NCH (channel doping), VTH0 (threshold voltage)
  
*	K1, K2, K3, K3B – body effect parameters
  
*	W0, NLX – narrow width and length parameters
  
*	DVT0W, DVT1W, DVT2W, DVT0, DVT1, DVT2 – short channel effect parameters
  
*	U0 (mobility), UA, UB, UC – mobility degradation parameters
  
*	VSAT – saturation velocity
  
*	AGS, B0, B1 – gate-induced drain leakage parameters
  
*	KETA, A1, A2, RDSW, PRWG, PRWB – additional parameters
  
<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/596432b8-bcc3-4daf-8a18-4e2529a30223" />

# Running the Simulation in ngspice

The simulation is run using ngspice (version 26). The steps to run the simulation are:

Step 1:
*	Open ngspice and navigate to the folder containing the SPICE deck file
  
*	Command: cd C:\VLSICADDevelopment\ngspice-26_140112\ForUdemy\CMOSVinVout

Step 2:
*	Source (load) the SPICE deck file:
ngspice 2 -> source cmosVTC_PMOSwidth_NMOSwidth.cir

Step 3:
*	Check the available simulation vectors using the display command:
ngspice 5 -> display
*	The display output shows vectors: in, out, v-sweep, vdd, vdd#branch, vin#branch — all of type voltage or current, 51 long (corresponding to 51 Vin sweep points from 0 to 2.5V in 0.05V steps)

Step 4:
•	Plot the output voltage vs input voltage to get the VTC:
plot out vs in

# SPICE Waveform Results – VTC

<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/f26609f3-0a6e-4e59-b9a8-df6a3f9c303b" />

SPICE waveform: Wn = Wp = 0.375u, Ln,p = 0.25u device (Wn/Ln = Wp/Lp = 1.5)

Two VTC plots are obtained from the simulation:

Case 1: Wn = Wp = 0.375u, Ln,p = 0.25u (W/L = 1.5 for both):
•	The VTC shows Vout vs Vin sweep from 0 to approximately 1.5V
•	Vout stays close to Vdd (2.5V) for low Vin, then drops sharply
•	The switching threshold (midpoint of VTC) occurs at a Vin value that is not exactly at Vdd/2 = 1.25V

Case 2: Wn = 0.375u, Wp = 0.9375u, Ln,p = 0.25u (Wn/Ln = 1.5, Wp/Lp = 2.5):
•	The PMOS W is increased to make the PMOS drive strength comparable to NMOS
•	The switching threshold shifts closer to Vdd/2 = 1.25V
•	The VTC becomes more symmetric around Vdd/2
The difference in switching threshold between the two cases arises because the PMOS mobility (µp) is approximately 2–3× lower than the NMOS mobility (µn). To compensate and balance the drive strength of PMOS and NMOS, the PMOS width (Wp) needs to be increased by the same factor

#  3.1 L3 Labs Sky130 SPICE simulation for CMOS
We now get the VTC characteristics
<img width="1366" height="768" alt="image" src="https://github.com/user-attachments/assets/0299dca6-26a7-4553-8aba-c74603bc6dbe" />

Now we need to know the Switching Threshold from this graph, it is the point when Vin=Vout.

<img width="1366" height="768" alt="image" src="https://github.com/user-attachments/assets/92844c1f-de96-4444-99fe-a43dc599a45c" />

<img width="1366" height="768" alt="image" src="https://github.com/user-attachments/assets/88308c66-64ce-4b8b-b1a1-f1676c0228da" />

<img width="280" height="30" alt="image" src="https://github.com/user-attachments/assets/8fbafb32-6de0-43b8-a00e-84f09068d1cb" />

So switching threshold for W/L=2.3 is around 0.876V

We can see that it is for typical corner as before and the W/L is also same. But now we taking transient pulse from 0v to 1V with shift of 0 with rise time and fall time being 0.1ns and 0.1ns respectively, pulse width of 2ns and total time period of 4ns. Let us run this.

 We will now see the transient analysis:
 
For that we will go inside the tansient SPICE file for day3
<img width="1600" height="858" alt="image" src="https://github.com/user-attachments/assets/52f52463-10a9-4835-aab5-0501768182fd" />

<img width="1600" height="892" alt="image" src="https://github.com/user-attachments/assets/e1fd6d3d-0bfb-42b3-8e20-aa2cc2cb2e72" />

<img width="1600" height="894" alt="image" src="https://github.com/user-attachments/assets/00d3617b-2bce-453f-a263-4535925aded1" />

RISE TIME 
<img width="1600" height="878" alt="image" src="https://github.com/user-attachments/assets/2526253a-feb0-43e6-b143-1b0a72de0888" />

<img width="623" height="306" alt="image" src="https://github.com/user-attachments/assets/9ea43e4b-89c0-4684-9cde-f13a0c5e8361" />
With output X0 = 2.48 and Input X = 2.15  Rise delay = 2.48 - 2.15 = 0.33

FALL TIME 

<img width="1600" height="898" alt="image" src="https://github.com/user-attachments/assets/f33c30e3-ef3e-46c5-9b27-646d40135194" />

<img width="426" height="85" alt="image" src="https://github.com/user-attachments/assets/cf7c8796-f7ab-4699-84f8-c8b5f0ad8c60" />

Output Xo = 4.33    input X = 4.05    Fall delay = 4.33 - 4.05 = 0.28

# 3.2 STATIC BEHAVIOUR EVALUATION -CMOS INVERTER ROUBSTNESS -SWITCHING THRESHOLD 

# 3.2  - L1 SPICE WAVEFORM RESULTS AND STATIC BEHAVIOR EVALUATION: SWITCHING THRESHOLD, Vm
SPICE Waveform Results – VTC
Two VTC plots are obtained from the simulation comparing different PMOS width configurations.

<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/f6a22cc8-58be-4227-be39-5486ddff40ea" />

SPICE waveform: Wn=0.375, Wp=0.9375u, Ln,p=0.25u device (Wn/Ln=1.5, Wp/Lp=3.75)
Case 1: Wn = Wp = 0.375u, Ln,p = 0.25u (Wn/Ln = Wp/Lp = 1.5)

<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/316a898c-1e3e-4212-a715-d2479d6a44f0" />

Both SPICE waveforms side by side - equal width vs increased PMOS width
•	The VTC shows Vout vs Vin sweep from 0 to approximately 1.5V
•	Vout stays close to Vdd (2.5V) for low Vin, then drops sharply
•	The switching threshold (midpoint of VTC) does not occur exactly at Vdd/2 = 1.25V
Case 2: Wn = 0.375u, Wp = 0.9375u, Ln,p = 0.25u (Wn/Ln = 1.5, Wp/Lp = 3.75)
•	PMOS W is increased to make the PMOS drive strength comparable to NMOS
•	The switching threshold shifts closer to Vdd/2 = 1.25V
•	The VTC becomes more symmetric around Vdd/2
The difference in switching threshold between the two cases arises because PMOS mobility (µp) is approximately 2–3x lower than NMOS mobility (µn). To compensate and balance the drive strength, Wp needs to be increased by the same factor.
Static behavior Evaluation: CMOS inverter Robustness
1. Switching Threshold, Vm
   <img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/dabb94fe-8df5-4eca-afc6-02544fdfd698" />

VTC with Vin=Vout diagonal line showing Vm - the switching threshold point
•	Vm is defined as the point where Vin = Vout
•	It is found by drawing the line Vin = Vout (a 45-degree diagonal) on the VTC graph and identifying where it intersects the VTC curve

<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/151570bc-7fb0-4a10-a8c7-4fd5d1e8ceca" />

Both VTC waveforms with Vm labeled for each case
•	For the symmetric case (Wn/Ln = Wp/Lp = 1.5): Vm ≈ 0.98V
•	For the balanced case (Wn/Ln = 1.5, Wp/Lp = 3.75): Vm ≈ 1.2V
•	Vm is the point where Vin = Vout

<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/9afb076e-0a2e-41ab-b011-bc7ba589dadc" />

VTC curve with transistor operating regions labeled at key points
The VTC operating regions at each point on the curve are:
•	At top-left (Vin low, Vout high): PMOS linear, NMOS off
•	As Vin increases slightly: PMOS linear, NMOS saturation
•	At midpoint (both in saturation): PMOS saturation, NMOS saturation — this is the maximum gain region
•	As Vin increases further: PMOS saturation, NMOS linear
•	At bottom-right (Vin high, Vout low): PMOS off, NMOS linear
CMOS inverter circuit with VGS=VDS condition and VTC curve showing IdsP = -IdsN

<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/72e4ba14-51e9-4bc8-b1d4-436c87a9f1d7" />

The key relationship used at the switching threshold is:
•	At Vm, the condition Vgs = Vds holds for the NMOS transistor
•	The current condition is: IdsP = - IdsN (current continuity at output node)
•	Both values of Vm (0.98V and 1.2V) confirm that by increasing Wp/Lp ratio, Vm shifts closer to Vdd/2 = 1.25V

#  3.2 L2 Analytical expression of Vm as a function of (W/L)p and (W/L)n
Static behavior Evaluation: CMOS inverter Robustness

<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/668c404d-4eb9-43f3-9cc8-84d92ff21c72" />

CMOS inverter circuit with VTC showing Vm~0.98v and Vm~1.2v for the two configurations
*	Vm is the point where Vin = Vout
  
*	From the two SPICE simulations: Vm ≈ 0.98V (symmetric sizing) and Vm ≈ 1.2V (balanced sizing)
  
*	The key condition: IdsP = - IdsN which means IdsP + IdsN = 0

# Deriving the Analytical Expression for Vm
Setting up the Current Equation

<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/030edf86-c4cc-4516-8553-659b2372c178" />

NMOS Id vs Vds characteristics with Vds = Vgs - Vt boundary shown
Starting from the current continuity condition at the output node:
•	IdsP + IdsN = 0
•	Both NMOS and PMOS are in saturation at Vm (both gates and drains have the same potential since Vgs = Vds at Vm)

Applying the Drain Current Equation
<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/391950a5-56f6-4f0f-8513-5d2929613f43" />

CMOS inverter circuit with IdsP = -IdsN condition and general drain current equation shown
The general drain current equation used for this derivation is:
Id = µn . Cox . (W/L) . [(Vgt . Vdsat) – Vdsat²/2] . [1 + λ Vds]
Where Vgt = (Vgs - Vt)

The channel length modulation term [1 + λ Vds] is ignored for this derivation

<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/c70bb7cc-9c1d-4309-9102-9773e9d6fe82" />

Simplified drain current equation without the lambda term
After ignoring the lambda term, the simplified equation becomes:
Id = µn . Cox . (W/L) . [(Vgs – Vt) . Vdsat – Vdsat²/2]

Writing Current Equations for NMOS and PMOS

<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/89cb5499-4507-4102-b6b3-a5092c97d02e" />

NMOS drain current equation with Vm substituted for Vgs
For NMOS (Vgs = Vm, Vds = Vm):
Idsn = kn . [([Vm – Vt] . Vdsatn) – Vdsatn²/2]

<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/4fa02eab-a81e-4ce3-b3d5-68ac3eb30fbd" />

PMOS drain current equation with Vm-Vdd substituted
For PMOS (Vgs = Vm – Vdd, Vds = Vm – Vdd):
Idsp = kp . [([Vm – Vdd – Vt] . Vdsatp) – Vdsatp²/2]

Combined Equation and Solution

<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/2532d70a-7583-4569-a4c1-9c9c2edefecc" />

Full combined equation with both NMOS and PMOS terms set to zero
Applying the condition IdsP + IdsN = 0:
kp . [([Vm – Vdd – Vt] . Vdsatp) – Vdsatp²/2] + kn . [([Vm – Vt] . Vdsatn) – Vdsatn²/2] = 0

Final Vm formula: Vm = R.Vdd/(1+R) where R = Kp.Vdsatp/Kn.Vdsatn
<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/85e8b9cb-a88a-429a-b817-8d92bb4989d7" />

Solving the above equation for Vm gives:
Vm = R . Vdd / (1+R)
Where:
R = Kp . Vdsatp / Kn . Vdsatn = (Wp/Lp) Kp’ . Vdsatp / (Wn/Ln) Kn’ . Vdsatn
•	R captures the ratio of PMOS to NMOS drive strength
•	Vm is directly controlled by the ratio of (Wp/Lp) to (Wn/Ln)
•	By changing the W/L ratio of either transistor, Vm can be shifted closer to or further from Vdd/2
•	This is the analytical formula that explains why the two SPICE simulations gave different values of Vm (0.98V and 1.2V)

# 3.2 L3 Analytical expression of (W/L)p and (W/L)n as a function of Vm

<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/3cdf9223-491e-41ed-8619-0c41291f5d2c" />

* Summary of Vm equation and key conditions: IdsP = -IdsN, IdsP + IdsN = 0
  
* The combined equation from the previous lecture is:
kp . [([Vm – Vdd – Vt] . Vdsatp) – Vdsatp²/2] + kn . [([Vm – Vt] . Vdsatn) – Vdsatn²/2] = 0

* And the Vm formula: Vm = R . Vdd / (1+R)
Where R = Kp . Vdsatp / Kn . Vdsatn = (Wp/Lp) Kp’ . Vdsatp / (Wn/Ln) Kn’ . Vdsatn

Deriving the Required PMOS/NMOS Size Ratio

The above Vm equation can also be used the other way — to find the required transistor size ratio to achieve a specific desired value of Vm.

<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/b177ee4c-f47a-408b-93a8-49b3238d925e" />

Rearranged equation: the required ratio of PMOS vs NMOS transistor size can be derived such that Vm is set
*	Alternatively, the required ratio of PMOS v/s NMOS transistor size can be derived, such that Vm is set to a desired value
Starting from the current balance equation and rearranging

<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/1bec9430-e92b-4ce9-9c23-af7497dbc597" />

Step 1: kn term moved to the right side of the equation
kn . [([Vm – Vt] . Vdsatn) – Vdsatn²/2] = - kp . [([Vm – Vdd – Vt] . Vdsatp) – Vdsatp²/2]

<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/9da75bcb-f0c8-4e35-ac0e-cd9d6c99fbd1" />

Dividing both sides: Kp.Vdsatp/Kn.Vdsatn = ([Vm-Vt] - Vdsatn/2) / ([-Vm+Vdd+Vt] + Vdsatp/2)
Dividing both sides:
Kp . Vdsatp / Kn . Vdsatn = ([Vm – Vt]) – Vdsatn/2) / ([-Vm + Vdd + Vt]) + Vdsatp/2)
Expanded form: (Wp/Lp)Kp’.Vdsatp / (Wn/Ln)Kn’.

<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/ab24ad61-3c42-4a42-856a-7379ce3bd0db" />

<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/095d1964-7630-4692-8e77-d0665151bedf" />

Final ratio form: Wp/Lp / Wn/Ln = right-hand side expression
The final expression gives the required (Wp/Lp) / (Wn/Ln) ratio directly in terms of a desired Vm value.

<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/e8777924-dd59-461c-8e6d-37bdc488cd5a" />

<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/8fe84faf-d092-4a21-81e8-bc7711bff15d" />

Table showing Wp/Lp vs x.Wn/Ln for 5 different ratio values (1x to 5x)

Table filled with Wn/Ln, 2Wn/Ln, 3Wn/Ln, 4Wn/Ln, 5Wn/Ln and the corresponding ratio formula
*	By plugging in different W/L ratios into the formula, the corresponding Vm can be calculated for each case
  
*	This table allows designers to directly read off what sizing is needed to achieve a target switching threshold
  
*	Vm is the point where Vin = Vout, and it shifts with the PMOS-to-NMOS size ratio
  
*	For Vm = Vdd/2 (ideal symmetric inverter), R must equal 1, which requires (Wp/Lp) Kp’ Vdsatp = (Wn/Ln) Kn’ Vdsatn

# 3.2 L4 Static and dynamic simulation of CMOS inverter

1. Switching Threshold, Vm

Vm is the point where Vin = Vout. It is the midpoint of the VTC where the inverter transitions from HIGH output to LOW output.

# Vm Equation

The switching threshold Vm is given by:
Vm = R · Vdd / (1 + R)
Where R is defined as:
R = (Kp · Vdsatp) / (Kn · Vdsatn) = ((Wp/Lp) · Kp' · Vdsatp) / ((Wn/Ln) · Kn' · Vdsatn)

The Wp/Lp to Wn/Ln ratio is:
(Wp/Lp) / (Wn/Ln) = [Kn' · Vdsatn · (Vm – Vt) – Vdsatn/2] / [Kp' · Vdsatp · (–Vm + Vdd + Vt) + Vdsatp/2]

 <img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/9b86b5ad-fa96-45a0-a870-dba2b8b60b56" />

Figure 1: Vm equation and expanded form (left), and Wp/Lp sweep table showing 5 cases from Wn/Ln to 5Wn/Ln (right)

Here we are going to find the value so SWITCHNG THRESHOLD by varying W/L ratios of NMOS. we did our SPICE simlation.

<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/70802caf-2d04-4a3e-9485-76695332c0c1" />

* To calculate switching threshold we will draw a line with slope 1 and find intersection point.This is Vm.

* From this we can ind dynamic simulation such as Rise and Fall delay.we identify what is Rsie and All and how doe sit vary with Vm.
* everything is same,we just change input to Pulse.This is known as Transient analysis.

<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/a45f6fc5-bcc5-44a5-a015-c6bf5ccb8ff3" />

* Pulse starts from Zero and ends at 2.5V with shit value zero.

* starts exactly ar=t time unit 0.

* rise time of 10ps and fall time of 10ps.

* complete cycle of 2ns with duty cycle of 1ns.

Results:
<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/081a7818-f017-4e27-93d8-b29e40c7e642" />


we can find rise delay from graph.
<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/bace45fd-b2dc-4b70-935a-aae5cbd41ead" />

Rise delay is difference between Vin at falling edge and Vout at raising point exactly at midpoint..

similarly for fall delay.It is dierence between the Voltage at raising of Vin and falling of Vout exactly at 50% value of Vin i.e 1.25V.

# 3.2 L5 Static and dynamic simulation of CMOS inverter with increased PMOS width

In previous lecture we did simulation for only one condition.Here we will do simulation s fror remaining conditions and we will compare results.

<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/33aca37a-8186-467d-9244-104300945fca" />

<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/22ad07dd-4b1c-4a9d-9301-1d8bc37b438f" />

<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/f5356d60-e5ab-4372-bae4-db9fcd20c447" />

<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/7a69f3ee-480a-4c68-a338-fe1ec1b20aeb" />

<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/55b57f96-b5cd-4cd4-b29a-6f202d0c70e8" />

<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/46b4c399-c451-4dc9-b03b-c1f48edfc202" />

From above simulation results we can observe that Rise delay is decreasing with ncrease in power of PMOS and all delay is incresing with decrease in power of CMOS.

# 3.2 L6 Applications of CMOS inverter in clock network and STA

The transient SPICE simulation is run for all five Wp/Lp cases. The complete results table from the ngspice simulation:

<img width="979" height="293" alt="image" src="https://github.com/user-attachments/assets/4048d25e-378e-49ff-a8b3-fc7833b1b38d" />

*	As Wp/Lp increases, Vm increases from 0.99V towards 1.4V

*	As Wp/Lp increases, Rise delay decreases (from 148ps to 37ps) — PMOS becomes stronger
  
*	As Wp/Lp increases, Fall delay increases (from 71ps to 88ps) — PMOS drives harder, load charges faster, output falls slower.

Case 2: Wp/Lp = 2Wn/Ln – Clock Inverter/Buffer

At Wp/Lp = 2Wn/Ln, the rise delay (80ps) and fall delay (76ps) are approximately equal. This is noted as:

*	Approximately equal rise-fall delay
  
*	Typical characteristics for a clock inverter/buffer

A clock inverter/buffer requires equal rise and fall delays to maintain a 50% duty cycle through the clock network. This is why Wp is typically sized to ~2x Wn for clock buffers

<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/9179d556-8c65-45bf-bae1-f7c2bf336776" />


Cases 3–5: Regular Inverter/Buffer – Preferred for Data Path

<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/3ad42b17-2430-40b9-9a71-5e219bf25460" />


For Wp/Lp = 3Wn/Ln, 4Wn/Ln, and 5Wn/Ln, the inverter is noted as:

*	Regular inverter/buffer

*	Preferred for data path

In these cases, the PMOS is stronger and Vm is above Vdd/2 = 1.25V. The rise delay is much smaller than fall delay. These are typical for standard cell data path inverters where drive strength needs to be high.

# Application in Clock Network – H-Tree Structure

The clock signal is distributed across the chip using an H-Tree structure. The clock inverter/buffer (Wp/Lp ≈ 2Wn/Ln) is used at each node of the H-Tree to ensure equal rise and fall delays. The H-Tree check-list for clock network design includes:

	1) SKEW – checked
	
	2) PULSE WIDTH – checked
	
    3) DUTY CYCLE
	
	4) LATENCY
	
	5) CLOCK TREE POWER
	
	6) SIGNAL INTEGRITY AND CROSSTALK

<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/5de867d2-61bc-4c0b-8188-7a17e8145e7c" />

Application in Static Timing Analysis (STA)

The delay values from the CMOS inverter simulation are used directly in Static Timing Analysis (STA). The setup analysis for a single clock domain is shown below.

Specifications:
•	Clock Frequency (F) = 1GHz
•	Clock Period (T) = 1/F = 1/1GHz = 1ns
•	Skew (S) = 10ps = 0.01ns
•	Uncertainty = 90ps = 0.09ns

The setup timing condition is:

(Theta + Delta1) < (T + Delta2 + 3x) – S – SU
Where:
•	Theta (Θ) = clock-to-Q delay of the Launch Flop
•	Delta1 (Δ1) = data path delay through combinational logic
•	T = clock period
•	Delta2 (Δ2) = clock network delay to Capture Flop
•	3x = uncertainty buffer
•	S = clock skew
•	SU = setup time of Capture Flop

The SLACK must be ≥ 0:

SLACK = Data Required Time – Data Arrival Time

<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/5692787c-9d61-4e89-a78f-4511cf0e221f" />

# NgspiceSky130-Day4-CMOS Noise Margin robustness evaluation

# DAY 4.1 L1 Introduction to Noise Margin

Static behavior evaluation focuses on the CMOS inverter robustness. In this lecture we look at Noise Margin, specifically NMH and NML.

<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/9fd817e3-17f9-4810-9f74-7dca22397370" />

Consider a CMOS inverter. Its function is:
•	Input 0 gives output 1
•	Input 1 gives output 0
The Ideal I/O characteristic of an inverter shows a perfect step: Vout stays at Vdd for all Vin below Vdd/2, and drops instantly to 0 for all Vin above Vdd/2. This ideal step transition happens exactly at Vin = Vdd/2.

# Ideal VTC with Infinite Slope

<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/04fc3bcf-8c85-4c41-95f7-0c3b1dbb813f" />

In the ideal case, the transition region has infinite slope. This means the inverter switches instantaneously between logic 0 and logic 1. There is no ambiguity in output for any input voltage
# Actual VTC with Finite Slope

<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/617e8b1d-6aed-472c-b5ec-a332342f8d3a" />

In a real inverter, the VTC has a finite slope in the transition region. The output does not switch instantly. Because of this finite slope, we need to define voltage levels that guarantee correct logic operation. These are called noise margin parameters. The four key parameters are:
•	VOH — Output High Voltage
•	VOL — Output Low Voltage
•	VIH — Input High Voltage
•	VIL — Input Low Voltage

VOH — Output High Voltage
<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/01eb308e-0854-4b1d-99d0-a8037af0a5bc" />

*	Any output voltage level between VOH and Vdd will be treated as logic '1'

*	VOH is found on the VTC at the point where slope = -1 on the upper part of the transition

*	VIL is the corresponding input voltage at this point (the lower transition boundary)

VOL is the Output Low Voltage.

<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/8b007321-3f1c-4f9b-a033-fda4094f016a" />

*	Any output voltage level between 0 and VOL will be treated as logic '0'
  
*	VOL is found on the VTC at the point where slope = -1 on the lower part of the transition
  
*	VIH is the corresponding input voltage at this point (the upper transition boundary)

# 4.1 L2 Noise margin voltage parameters

<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/e54acbf2-e228-47d4-89d9-b8c4bdff9b5a" />

Ideal Inverter VTC — Infinite Slope In an ideal inverter: 

*Vout = Vdd for all Vin < Vdd/2

*Vout switches instantly to 0 at Vin = Vdd/2 

*Vout = 0 for all Vin > Vdd/2

This gives a perfectly rectangular VTC with infinite slope at the switching point. No ambiguity — any input either produces exactly Vdd or exactly 0.

Actual Inverter VTC — Finite Slope In a real CMOS inverter the VTC has a finite slope. This means: 
*Vout starts near Vdd (but not exactly Vdd) for low Vin

* Vout falls gradually through a transition region around Vdd/2 
* Vout settles near 0 (but not exactly 0) for high Vin

We will define all four noise margin voltage parameters on the actual VTC of the CMOS inverter and explain how they are determined using the slope = −1 criterion .

# Actual I/O Characteristic of a CMOS Inverter

<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/b3774aad-ad07-4ca5-b37a-fdbb99b19a54" />

The actual VTC of a CMOS inverter has a finite slope transition region. In this transition region, the output switches from HIGH to LOW. To define the valid logic levels, we identify four key voltage parameters from the actual VTC.

 # Defining VIL and VIH from the Actual VTC
 
<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/ef686d19-29d4-4ee0-8edc-e38976dab140" />

The points VIL and VIH are determined by drawing tangent lines on the actual VTC curve at the points where the slope equals −1.
*	VIL (Input Low Voltage): the Vin value where the VTC slope first reaches −1 on the upper part of the curve. For any input below VIL, the output is guaranteed to be HIGH.

*	VIH (Input High Voltage): the Vin value where the VTC slope reaches −1 on the lower part of the curve. For any input above VIH, the output is guaranteed to be LOW.
  
* The region between VIL and VIH is the transition (undefined) region. Signals in this region do not guarantee a valid logic level at the output.

Defining VOH and VOL from the VTC
VOH and VOL are the output voltage levels corresponding to VIL and VIH respectively.
*	VOH (Output High Voltage): the output voltage when Vin = VIL. Any output between VOH and Vdd is treated as logic '1'.

*	VOL (Output Low Voltage): the output voltage when Vin = VIH. Any output between 0 and VOL is treated as logic '0'.

Slope = −1 Criterion
 
<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/08c57fe1-8b3b-4c27-a27f-79f5d4a9b123" />

The slope = −1 criterion is the standard method to determine the noise margin voltage parameters.
*	On the actual VTC curve, draw tangent lines at the two inflection points where the slope of the curve equals exactly −1

*	Upper inflection: where the curve just starts to fall steeply — this gives VIL (x-axis) and VOH (y-axis)

*	Lower inflection: where the curve is completing its fall — this gives VIH (x-axis) and VOL (y-axis)

This method is used because the slope of −1 represents the unity gain point. Any gain below this (magnitude < 1) means the inverter is in a stable region, and beyond it (magnitude > 1) the circuit is in the high-gain amplification region.

# 4.1  L3 Noise margin equation and summary

 we will derive the noise margin equations for NMH and NML,that  introduces the undefined region, and presents the full noise margin summary with noise-induced bump characteristics.

 I/O Characteristic Plotted to Scale
 
<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/2365e36c-0c49-4fa8-b818-3440cef3fcf3" />

The actual VTC is now plotted to scale with all four voltage parameters (VOH, VOL, VIH, VIL) marked. On the right side of the slide, a vertical scale from 0 to Vdd is drawn to show where each parameter falls and how the noise margins are derived from them.

NMH — Noise Margin High
<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/de0df71f-849e-4d67-9ff4-6545bf48a8bb" />

NMH (Noise Margin High) is defined as:
NMH = VOH - VIH
•	VOH is the minimum output voltage that counts as logic '1'
•	VIH is the minimum input voltage required to be recognised as logic '1'
•	NMH represents how much noise can be added to a logic '1' signal at the output before it is no longer recognised as logic '1' at the next stage's input
•	Any voltage in the NMH range (between VIH and VOH) will be detected as logic '1'
NML - NOISE MARGIN LOW 
<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/ea7c82a2-e950-4156-831a-1685909455fd" />

NML (Noise Margin Low) is defined as:
NML = VIL - VOL
•	VOL is the maximum output voltage that counts as logic '0'
•	VIL is the maximum input voltage that is recognised as logic '0'
•	NML represents how much noise can be added to a logic '0' signal at the output before it is no longer recognised as logic '0' at the next stage's input
•	Any voltage in the NML range (between VOL and VIL) will be detected as logic '0'

UNDEFINED REGION 

 <img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/4c10eeec-8545-494b-8292-0a0165129412" />

 Three regions visible on the voltage scale: NMH (logic '1'), Undefined Region, and NML (logic '0')
Between VIH and VIL there is a region that is not covered by either NMH or NML. This is called the Undefined Region.
*	The Undefined Region lies between VIL (top of NML) and VIH (bottom of NMH)

*	Any signal in the Undefined Region will produce an indefinite logic level at the 

*	The circuit behaviour is unpredictable for inputs in this range

*	A well-designed inverter minimises the width of this undefined region

Noise Margin Summary

<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/9db0cddf-231c-4a7f-b174-1af96a164aa7" />

The noise margin summary diagram shows a signal waveform on the time axis with three noise-induced bumps at different voltage levels:
*	a) Bump height lies between VOL and VIL — it is within NML range, so the output will be treated as logic '0'
  
*	b) Bump height lies between VIL and VIH — it is in the Undefined Region, so the output logic level is indefinite
  
*	c) Bump height lies between VIH and VOH — it is within NMH range, so the output will be treated as logic '1'
  
For any signal to be considered as logic '0' and logic '1', it should be in the NML and NMH ranges respectively.

# 4.1 L4 Noise margin variation with respect to PMOS width
we  will observe how the noise margins NMH and NML change as the PMOS width is varied from Wn/Ln to 5Wn/Ln while keeping NMOS width constant at Wp/Lp .

<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/ac22cbb4-6d3d-4c43-b52c-5fd19068b7c9" />

* SPICE simulation set up 

The SPICE simulation is run for five different PMOS width conditions. The table on the left shows the Wp/Lp value kept constant at Wp/Lp while x.Wn/Ln is varied from 1x to 5x. The NMH and NML columns at the bottom of the table track how the noise margins change with each condition.
•	Wp/Lp is kept constant
•	x.Wn/Ln is swept through five values: Wn/Ln, 2Wn/Ln, 3Wn/Ln, 4Wn/Ln, and 5Wn/Ln
•	For each case, the VTC is plotted and the NMH and NML values are read off

Case 1: Wp/Lp = Wn/Ln (x = 1)

<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/da9da85a-929a-46a9-b04b-3382db53866e" />

When the PMOS width equals the NMOS width (x = 1), the VTC is not symmetric. The switching threshold Vm = 0.99v which is below Vdd/2. The noise margins are equal in this case:
•	NMH = 0.3
•	NML = 0.3

Case 2: Wp/Lp = 2Wn/Ln (x = 2)

<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/0e22248b-5502-4833-87be-85458b3e60c6" />

When the PMOS width is doubled, the VTC shifts to the right. The switching threshold Vm increases to 1.2v. Notice that:
•	NMH = 0.35 — slightly improved compared to Case 1
•	NML = 0.3 — unchanged

Case 3: Wp/Lp = 3Wn/Ln (x = 3)

<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/096e4c58-4511-4225-8ca0-5c587ad7e014" />

When the PMOS width is tripled, the VTC shifts further right and the switching threshold increases further. The NMH continues to increase as the PMOS becomes stronger and drives VOH higher, while NML remains relatively unchanged.

Case 4: Wp/Lp = 4Wn/Ln (x = 4)

<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/1b06510b-0ca0-45c8-8410-50761b985c62" />

At x = 4, the PMOS is now considerably stronger than the NMOS. The VTC is shifted well to the right:
•	Vm = 1.35v
•	NMH = 0.42 — NMH has increased significantly
•	NML = 0.27 — NML has decreased slightly

Case 5: Wp/Lp = 5Wn/Ln (x = 5)

<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/d9ac6336-78bb-4e84-89cf-54bfa8e2b7e0" />

At x = 5, the VTC shifts even further right with Vm = 1.4v. Notice that NMH and NML are the same as Case 4 (NMH = 0.42, NML = 0.27), indicating that beyond a certain PMOS width the improvement in NMH saturates.

<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/70010580-c1e7-416b-9c30-1729345a51d6" />

From the table we can observe:
•	As PMOS width increases, NMH increases from 0.3 to 0.42
•	NML decreases slightly from 0.3 to 0.27 as PMOS becomes stronger
•	Vm increases from 0.99v to 1.4v as PMOS drive strength increases
•	The improvement in NMH saturates between x = 4 and x = 5

<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/6b4cec34-0f08-4497-946e-0d1305a6c96a" />

<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/1ea3b5e6-1917-46d5-9220-5d315e1216bd" />

As the PMOS width increases, the VTC curve shifts to the right. For digital design purposes, the ideal target is to have the switching threshold Vm as close to Vdd/2 as possible. From the simulation results:
*	At x = 1 (equal sizing), Vm = 0.99v which is below Vdd/2 — NMOS dominates

*	At x = 2 (Wp = 2Wn), Vm = 1.2v which is much closer to Vdd/2 = 1.25v — this is a balanced design

*	At x = 3 and above, Vm exceeds Vdd/2 and the VTC is shifted too far to the right for typical digital applications


# 4.1 L5 Sky130 Noise margin labs
We will now plot Noise margins

<img width="1366" height="768" alt="image" src="https://github.com/user-attachments/assets/1e36eab8-fe90-4a42-bac6-7798d1caa92c" />

<img width="1366" height="768" alt="image" src="https://github.com/user-attachments/assets/2e823e7a-4484-4699-b40a-b302f21f64be" />



We will take the point where the slope is -1 ; x axis will give VIL and VIH, whereas y axis will give VOH and VOL.

Noise margin NH = VOH - VIH = 1.70952-0.98778 = 0.72 
Noise margin NL = VIL - VOL = 0.7733-0.09523 = 0.67807


# DAY 5  NgspiceSky130-Day5-CMOS power supply and device variation robustness evaluation

# Static behaviour evaluation-CMOS inverter robustness-Power supply variation

 # 5.1L1  Smart SPICE simulation for power supply variations

While evaluating the robustness of CMOS inverter another factor is Power Supply Scaling. On reducing the gate length, the operating power is also reduced. On power scaling the Cmos characteristics should not change.

We will check by simulation, taking two case

<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/455b72ab-dd90-431e-9bcb-0f8731e6cf51" />

From above picture we can observe the inverter circuit used for this experiment. Here we took bigger PMOS compared to NMOS to match resistances. 
Circuit parameters are:
*Vdd = 2.5V (starting value, will be scaled down)

*Wp = 0.9375u (PMOS width) 

*Wn = 0.375u (NMOS width) 

*Wp is 2.5x Wn.This is the balanced sizing we learned in previous lecture to get Vm near Vdd/2.

<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/75b6acd9-56e4-435c-b3ee-7b9d653e4631" />

From above picture we can observe the VTC curve at Vdd = 2.5V with region labels. 
5 regions are visible on the curve: 
* PMOS linear, NMOS off - at very low Vin,output = Vdd 
* PMOS linear, NMOS sat - Vin just above Vtn,NMOS starts conducting 
* PMOS sat, NMOS sat - both in saturation,sharp transition region 
* PMOS sat, NMOS linear - Vin high,NMOS pulls output low
* PMOS off, NMOS linear - at very high Vin,output = 0 This is the full VTC at 2.5V.Now we want to see what happens at lower Vdd values.
  
The Smart SPICE Netlist - How the loop works Instead of writing 5 separate netlists,the instructor writes ONE netlist with a loop

<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/db92b57f-4d85-43da-a95a-3296e80dd2b9" />

<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/487eb4bb-423a-4acf-aca5-257441eb4ce4" />

<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/b8c1c726-d41b-49a7-b844-4f88066dd902" />

<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/8ca0a802-22c7-4385-95ca-61d0bdd59333" />

We will now plot the VTC charactersitics for Vdd= 2.5V, 2V, 1.5V, 1V, 0.5V 

<img width="970" height="688" alt="image" src="https://github.com/user-attachments/assets/bdf3a131-2617-47e0-89ed-8a46d97e0a09" />

 # 5.2 L2 ADVANTAGES AND DISADVANTAGES USING LOW SUPPLY VOLTAGE

Here we use SPICE simulation to evaluate the effect of power supply scaling on the CMOS inverter. We look at how reducing the supply voltage affects the gain, energy, and delay characteristics of the inverter.

<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/ad35e0e8-c59a-440d-81ce-ff55886cae41" />

SPICE Simulation — VTC at Different Supply Voltages
The SPICE simulation plots five VTC curves on the same graph. Each curve corresponds to a different supply voltage, from dc1 out (highest supply, green) down to dc5 out (lowest supply, purple). The X-axis is the input voltage and the Y-axis is the output voltage.
•	dc1 out (green) — highest supply voltage: VTC is widest, transition spans full range from near 2.5V to 0V
•	dc2 out (red) — second supply level: VTC is narrower, Vdd is about 2.0V
•	dc3 out (yellow) — mid supply: transition region is compressing
•	dc4 out (blue) — lower supply: VTC is further compressed
•	dc5 out (purple) — lowest supply (0.5V): VTC is very narrow and highly compressed

|gain| Observation from SPICE

<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/664e4f97-c9f1-4bc0-9f0a-31408ae7c132" />

The gain of the inverter at the switching threshold Vm is an important parameter. The gain magnitude |gain| is the slope of the VTC at the Vm point (where the VTC is steepest).
*	|gain| = 7.38 for the highest supply voltage (dc1 out, 2.5V)
Notice that the gain is measured by the steepness of the transition region. A higher gain means a sharper, more ideal transition from HIGH to LOW

56% Improvement in Gain at Low Supply Voltage
<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/f29f7f8c-50a7-497b-8b77-3af788c7ab02" />

* When the supply voltage is reduced to 0.5V (dc5 out, purple curve), the gain increases significantly.

*	|gain| = 11.53 at Vdd = 0.5V — a 56% improvement in gain
This is a key advantage of operating at low supply voltage. The gain improvement happens because at low Vdd, both PMOS and NMOS are operating closer to their threshold voltages, making the inverter behave more like a high-gain amplifier in the transition region

Energy Reduction at Low Supply Voltage
<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/45db24d8-acac-484b-9e92-168d24ac7b6b" />

<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/fb13821f-0140-4ddd-9c33-b4d611e78a01" />

*The energy consumed by a CMOS circuit is given by: Energy = ½ CV²
Where C is the load capacitance and V is the supply voltage. Substituting V = 0.5V:

* Energy = ½ C (0.5)²
Since energy depends on the square of the supply voltage, reducing Vdd from 2.5V to 0.5V gives a reduction factor of (0.5/2.5)² = 0.04, which is a close to 90% reduction in energy

# Advantages of using 0.5V Supply
<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/f88f3c96-6aae-4794-9d5b-0cdfead9bc58" />

From the SPICE simulation, the advantages of using a 0.5V supply are:
*	Increase in gain (close to 50% improvement) — |gain| improves from 7.38 to 11.53, a 56% improvement
  
*	Significant reduction in energy (close to 90% improvement) — Energy = ½CV² scales quadratically with Vdd

Transient Simulation — Rise Delay and Fall Delay
<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/53190c73-95e4-467d-a371-1dab3f828b14" />

In addition to the DC analysis, a transient simulation is performed to evaluate rise delay and fall delay at the low supply voltage condition.
*	The Y-axis is in mV units due to the very small Vdd = 0.5V supply
  
*	The green curve is the output waveform (out) and the red curve is the input (in)
  
*	The output transitions are slow compared to the input transitions because of the reduced drive strength at low Vdd

<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/93d40ad7-eadc-4275-afe0-2471b9552518" />

The rise delay is the time difference between:
*	The falling edge of Vin (at 50% of its amplitude) and the rising edge of Vout (at 50% of its amplitude)
  
The fall delay is the time difference between:

*	The rising edge of Vin (at 50% of its amplitude) and the falling edge of Vout (at 50% of its amplitude)

* at low supply voltage (0.5V), while gain and energy are improved, the delay increases significantly. This is the main disadvantage of low supply voltage operation.
  
* The reduced overdrive voltage at low Vdd means transistors take longer to switch, which increases both rise and fall delays.

# 5.1 L3 Sky130 Supply Variation Labs

We will calculate the supply variation.

<img width="1366" height="768" alt="image" src="https://github.com/user-attachments/assets/943cf16a-0bfc-43c7-a334-09db7eebaa1b" />

The initial supply voltage is 1.8V and we are reducing it with the step of 0.2V, so there will be 6 iterations.

<img width="1366" height="768" alt="image" src="https://github.com/user-attachments/assets/29a6428f-0775-4ec8-ae37-ff132b4cf097" />

# 5.2 L1 Sources of variation – Etching process

 Here we look at two sources of variation that affect the CMOS inverter: Etching Process Variation and Oxide Thickness Variation. These sources of variation cause the actual fabricated transistor dimensions to differ from the designed values, which in turn affects circuit performance.

Single Inverter — Layout and Circuit

<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/f469f178-962e-4a37-b8e1-0a498d8ecee5" />

Let us look at a single inverter to understand how it is represented at different levels of abstraction. The three representations shown are:
•	Circuit symbol (left) — standard inverter symbol with In, Out, Vdd and Vss connections
•	Transistor-level schematic (middle) — shows Poly Gate connected to both PMOS and NMOS, P Diffusion region for PMOS and N Diffusion region for NMOS
•	Layout view (right) — shows the physical placement of Poly (red), P Diff (green), N Diff (green), metal connections (blue), Vdd rail at top and Vss rail at bottom
<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/65b5b87b-e424-48a2-8f77-efaf5995f7ce" />

In the layout, the key physical parameters that control transistor behavior are:
•	L — channel length, which is the width of the Poly Gate stripe between source and drain diffusions
•	W — transistor width, which is the length of the overlap between Poly and the diffusion region

# Inverter Chain — Layout

<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/98578047-1c41-42c8-877c-bbf6a66d5deb" />

<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/6eb07a86-027b-403f-92e9-81fbae2ddfbf" />

When multiple inverters are placed in a chain, each inverter cell has the same layout structure. The Poly Gate stripes of all inverters run vertically, and the P Diff and N Diff regions alternate across the chain. The critical observation is:
•	Gates in the middle of the chain have the same structure on either side
•	The Vdd rail runs along the top and the Vss rail runs along the bottom for the entire chain
•	Each cell is a mirror image of the adjacent cell sharing the same diffusion regions

# Ideal Mask vs Actual Mask — Etching Process Variation
<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/6b73bd41-e4d0-4125-b59b-ea60e06121f0" />

<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/c6cd9256-0e5d-4971-8ed3-9556ab7d7720" />

During semiconductor fabrication, a mask is used to define the shape of each layer. The Ideal Mask defines a perfectly rectangular Poly stripe with exact L and W dimensions. However, during the etching process, the chemicals used to remove unwanted material do not always follow the mask edges perfectly. This causes the Actual Mask to have irregular, uneven boundaries.
•	The Ideal Mask produces a Poly stripe with uniform width L along its entire length
•	The Actual Mask produces a Poly stripe with non-uniform edges — the width varies along the length
•	This variation in the Poly dimensions directly translates to variation in the channel length L of the fabricated transistor

<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/5cbda179-d3e7-40e3-a8c3-a7be68ae1762" />

The etching process variation affects not just a single inverter but all inverters in the chain. Since the middle gates have the same structure on either side, any variation in the Poly shape during etching will affect all gates equally due to the uniform etch environment across the chip. This is called global variation or systematic variation

# Effect of Etching Variation on W/L Ratio

<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/7406ba1c-7929-4b44-af26-8ce2c4deb620" />

The etching variation changes the effective W/L ratio of the transistor. The drain current equation depends directly on W/L:
Id = u Cox (W/L) [(Vgs − Vt)Vds − Vds²/2]
•	If L increases due to extra Poly remaining (under-etch) — the W/L ratio decreases, reducing Id
•	If L decreases due to excess Poly removal (over-etch) — the W/L ratio increases, increasing Id
<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/19b920ce-1e42-4c43-875e-4882c592328e" />

•	Both cases cause the actual Id to differ from the designed Id, shifting the VTC and changing Vm, NMH, NML, and delay

<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/f5683cfe-9030-4416-903a-43f4654b47e7" />

Notice that in the drain current equation, Cox, u, Vgs, Vt, and Vds are all controlled by process parameters or applied voltages. The W/L ratio is the one parameter that is set by the mask dimensions. When etching variation occurs, W and L deviate from their designed values, making the actual Id different from the expected Id for every transistor on the chip

Oxide Thickness Variation
The gate oxide layer (SiO2) is grown on the substrate surface during fabrication. The thickness of this oxide layer, known as Tox (oxide thickness), determines the gate oxide capacitance per unit area Cox:
Cox = εox / Tox
Where εox is the permittivity of the gate oxide. During fabrication, the oxide growth process is not perfectly uniform across the wafer. This means Tox can vary from its designed value.
•	If Tox is thicker than designed — Cox decreases, which reduces the drain current Id and weakens the transistor
•	If Tox is thinner than designed — Cox increases, which increases the drain current Id and strengthens the transistor
•	This variation also affects the threshold voltage Vt through the body effect coefficient γ, since γ = (1/Cox) √(2qεsi NA)

Both etching process variation and oxide thickness variation are examples of device variation that affect the static and dynamic performance of the CMOS inverter. They cause spread in parameters like Vm, NMH, NML, rise delay, and fall delay across different chips and different dies on the same wafer.

# 5.2 L2 SOURCES OF VARIATION - OXIDE THICKNESS

 Here we look at oxide thickness as a source of variation in the CMOS inverter. The gate oxide layer grown during fabrication is not perfectly uniform, and this non-uniformity directly affects the Cox parameter in the drain current equation

Single Inverter
<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/6ee84560-fd30-4331-a09b-d4f1dbc3fa63" />

The  single inverter has:
•	PMOS connected to Vdd (Pull-up network)
•	NMOS connected to Vss (Pull-down network)
•	Gates of both transistors tied together at input (In)
•	Drains connected together at output (Out)

Inverter Chain
<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/91d3ac57-b168-4f9a-b254-e04ef01c9376" />

When multiple inverters are placed in a chain, each inverter cell has the same layout structure with Poly Gate stripes running vertically and P Diff and N Diff regions alternating across the chain.

<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/0cb0d68d-debe-4a50-9acf-d1516dc1e07a" />

Ideal Oxidation Process
<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/2452de41-a60f-45a8-b495-a3403456db58" />

The gate oxide layer (SiO2) is grown on the P-substrate surface during fabrication. In the ideal oxidation process, the oxide grows uniformly to a designed thickness tox. The cross-section shows:
•	tox — the gate oxide thickness, indicated at the top of the cross-section
•	Gate oxide — the thin SiO2 dielectric layer grown on the P-substrate between source and drain
•	Poly-Si or metal gate — deposited on top of the gate oxide to form the gate terminal
•	n+ diffusion regions — the source and drain regions on either side of the channel
•	P-substrate — the body of the transistor, connected to terminal B

Ideal vs Actual Oxidation Process

<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/bb5b8b06-b476-4719-bb98-7e3813089fb1" />


During the actual fabrication process, the oxidation is not perfectly uniform across the wafer. The actual oxidation process produces a gate oxide layer with non-uniform thickness. This means tox varies from its designed value at different points on the wafer or even within the same die:
•	Ideal Oxidation Process — tox is uniform and equals the designed value everywhere
•	Actual Oxidation Process — tox varies locally. Some regions may have a thicker oxide (over-oxidation) and some may have a thinner oxide (under-oxidation)
Effect of Oxide Thickness Variation on Drain Current

<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/f794c838-40c1-4833-baf3-3b6f75940fa0" />

The gate oxide capacitance per unit area Cox is given by: Cox = εox / tox
where εox is the permittivity of the gate oxide material. The drain current equation for a MOSFET in the linear region is:
Id = u Cox (W/L) [(Vgs - Vt)Vds - Vds²/2]
<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/a2ddf792-6637-4346-a6e3-6bcea0a11881" />

 we can observe that oxide thickness variation directly impacts Cox and therefore Id:
•	If tox is thicker than designed — Cox = εox/tox decreases, which reduces the drain current Id and weakens the transistor
•	If tox is thinner than designed — Cox = εox/tox increases, which increases the drain current Id and strengthens the transistor
•	This variation causes the actual Id to differ from the designed Id, shifting the VTC, changing Vm, NMH, NML, and delay

Oxide thickness variation is one of two main sources of device variation in CMOS fabrication. The other source is Etching Process Variation, which affects the W/L ratio. Both sources cause spread in the performance characteristics of the CMOS inverter across different chips and different dies on the same wafer.

# 5.2 L3 - SMART SPICE SIMULATIONS FOR DEVICE VARIATIONS 

Now we will be doing the SPICE simulation for device variations, and prove the robustness of CMOS inverter inspite of different extreme conditions.
We will see the characteristics for Strong PMOS and week NMOS, this means PMOS width is wider and it has least resistance. Also for weak PMOS and strong PMOS, that means the width of NMOS is more than PMOS and it has least resitance.
<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/0de59ef9-2ab3-45ab-af0a-c36564b79a9a" />

<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/e99efc46-46d3-4737-bb90-90d386b1602a" />

<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/b178d0e0-4eb1-40c0-91d2-423fbd8bd2b2" />

<img width="959" height="745" alt="image" src="https://github.com/user-attachments/assets/f8f1ff42-672a-4d60-8193-66296ce716d1" />

# 5.2 L4 CONCLUSION 

SPICE Simulation Setup — Strong PMOS and Strong NMOS Conditions
<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/dc13e14e-7497-4ed3-953f-858e4471a133" />

The SPICE simulation is set up to show the effect of device variation on the VTC. Five simulation runs are performed corresponding to different combinations of strong and weak PMOS and NMOS conditions:
•	dc1.out (green) — one device variation condition

•	dc2.out (red) — second device variation condition

•	dc3.out (blue) — third device variation condition

•	dc4.out (yellow) — fourth device variation condition

•	dc5.out (purple) — fifth device variation condition

The two device configurations shown are:
•	Strong PMOS — the PMOS is stronger than the NMOS. Wp = 0.375u (shown with the P block larger in the inverter icon on the left)
•	Strong NMOS — the NMOS is stronger than the PMOS. Wn = 1.875u (shown on the right with Wn highlighted in yellow)

VTC Curves with Vin = Vout Diagonal Line

<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/e4b8f25f-80ca-4976-8c5f-3e505ca619ba" />

The Vin = Vout diagonal line is drawn on the same graph as all five VTC curves. The point where each VTC curve intersects this diagonal gives the switching threshold Vm for that particular device variation condition. We can observe that:
•	The five VTC curves are spread across a wide range of input voltages
•	Each curve intersects the Vin = Vout diagonal at a different point, giving a different Vm
•	The leftmost curve (dc5.out, purple) has the lowest Vm — this is the Strong PMOS condition where the PMOS drives the output to ground much earlier
•	The rightmost curve (dc1.out, green) has the highest Vm — this is the Strong NMOS condition where the NMOS keeps the output high for longer

Shift in Vm due to Device Variation

<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/721de9b8-3eed-4ba5-bffd-02d28b287452" />
The annotation 'Shift in Vm' with a bracket on the left side of the plot shows the total range of Vm variation across all five conditions. The two yellow dashed lines mark:
•	Lower dashed line — the lowest Vm (Strong PMOS case), approximately 0.7v
•	Upper dashed line — the highest Vm (Strong NMOS case), approximately 1.4v
•	The shift in Vm is significant — device variation causes Vm to move by approximately 0.7v across the range of conditions

Variation in NMH and NML

<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/44e2de71-c456-4c41-a10b-6cc982154cff" />

In addition to the shift in Vm, device variation also causes variation in the noise margins:
•	Variation in NMH — the top yellow dashed lines show the spread of VOH values across all five VTCs. For the Strong PMOS case, VOH is lower. For the Strong NMOS case, VOH is higher
•	Variation in NML — the bottom yellow dashed lines show the spread of VOL values. For the Strong NMOS case, VOL is higher. For the Strong PMOS case, VOL is lower
•	This means that device variation affects NMH = VOH − VIH and NML = VIL − VOL for every transistor on the chip

CONCLUSION 

<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/8f0d2748-a3cb-4f88-b78d-a524fa5403cf" />

The important conclusion from the device variation simulation is that despite the spread in switching threshold Vm, noise margins NMH and NML across the five device variation conditions, the operation of the gate is intact:
•	All five VTC curves still show a valid transition from logic HIGH (Vout ≈ Vdd) to logic LOW (Vout ≈ 0V)
•	The inverter correctly inverts the input logic level (0/1 → 1/0) for all five conditions
•	The variation in Vm, NMH, and NML affects the performance of the inverter but does not cause a functional failure
•	The CMOS inverter is robust to device variation in terms of its basic logic operation .

# 5.2 L5 Sky130 Device Variation Labs

<img width="1366" height="768" alt="image" src="https://github.com/user-attachments/assets/5c941019-054c-4275-988c-acc49ad31b7a" />

We can see that the width of PMOS is quite large than that of NMOS. SO it is clearly strong PMOS and weak NMOS case. The Vm will be right shifted.

<img width="1366" height="768" alt="image" src="https://github.com/user-attachments/assets/02a843f8-ba9f-437f-a096-a54210e0cf51" />

