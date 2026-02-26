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

  #  L1 NMOS RESISTIVE OPERATION WITH SMALL DRAIN TO SOURCE VOLTAGE 

* It is also known as the Linear Region of operation
*  observe changes when Vgs > Vt .
*  Induced charges (Qi) α (Vgs-Vt) .
*  when vt = 0.45v ,vgs = 1v, vgs > vt transitor turn on and conducting channel is present between source and drain and we can see  source is connected to ground and drain  is connected to some potential ,there will be a voltage gradient present across the channel . Also effective length is less than actual channel length .
  
*  <img width="965" height="620" alt="image" src="https://github.com/user-attachments/assets/234eceb1-96ff-43f3-be5d-e809891c1a38" />

*  lets plot a graph ,'x' is along the channel and 'y' is perpendicular to channel , y axis represents width , when x=0,1,2,3...,n  at every point v1,v2 ,..,vn the voltage will be different ,all values are different because of small voltage applied ie vds . Every point on x axis will vary w.r.t to Vgs-V(x), this will decide the current equation. where V(x) be the voltage at any point 'x' along the channel and  Vgs-V(x) is the gate-to-channel voltage at that point .
  
# L2 Drift current theory 
We know the effective channel voltage will vary w.r.t x, for example at x=0, Vgs=1V and V(x)=0, So the Vgs-Vx=1V. At x=Vds=0.05V, Vgs-Vx=0.95V. 
 * The induced charge at any point 'x' is  Qi(x) α - ((Vgs-V(x))-Vt) ie  Qi(x) = -cox ((Vgs-V(x))-Vt)
   
<img width="531" height="553" alt="image" src="https://github.com/user-attachments/assets/17a4710e-94a3-41df-9917-05ba8d561fff" />

From device point of view ,we have  2 kinds of currents in 
** drift current : current due to potential differnce 

**diffusion current : current due to difference in carrier concentration

<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/ebdef17f-9787-45a7-9983-db3b7aa98fdc" />

# L3 Drain current model for linear region of operation 

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

# L4 SPICE conclusion to resistive operation 

<img width="729" height="221" alt="image" src="https://github.com/user-attachments/assets/1154ef38-6afa-4269-ad46-ae8e95a3263a" />

We need to find the impact of Vgs and Vds on the drain current equation using diffferent values of vgs and vds . If we consider different values of Vgs, under what condition the device will remain in Linear region depends on (Vgs-Vt) should be greater than Vds.

A MOSFET operates in the linear (resistive) region when: Vds < (Vgs − Vt) ,Where:
* Vt = 0.45 V
  
* Vgs = 0.5 V, 1 V, 1.5 V, 2 V, 2.5 V
  
* (Vgs − Vt) = 0.05 V, 0.55 V, 1.05 V, 1.55 V, 2.05 V
  
For each Vgs value, Vds is swept from 0 to (Vgs − Vt) to maintain linear operation.
SPICE simulation is performed to sweep Vds, calculate Id, and verify resistive behavior of the MOSFET.

#  L5 SATURATION REGION 

when Drain-source voltage exceeds the value (Vgs-Vt), the region of operation is called "Saturation Region" .

<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/1ece8121-74c0-49ac-b831-3694ebcb7674" />

* vgs is constant at 1v , vt is constant at 0.45 v and vds is increased gradually from 0.05 v to observe vgs-vds ie channel voltage .

  <img width="1600" height="650" alt="image" src="https://github.com/user-attachments/assets/48234bd7-17e6-430e-8e2a-190b17e82bdc" />

* When Vgs-Vds is greater than Vt, there will be a conducting channel.
  
* When Vgs-Vds is equal to Vt,  Inversion has happened at drain side and it is equal to Vt, therefore channel will start disappearing at drain side.
  
<img width="1600" height="659" alt="image" src="https://github.com/user-attachments/assets/4763e7f7-c3ed-49fd-b555-9ee35a8c43f6" />

* The phenomenon where channel gets disapper is called PINCH -OFF phenomenon .
  
* When Vgs-Vds<=Vt, there is no channel present near the Drain terminal, this region is saturation region .
  
# L6 DRAIN CURRENT MODEL FOR SATURATION REGION OF OPERATION 

<img width="734" height="640" alt="image" src="https://github.com/user-attachments/assets/584a15e7-c939-4509-b667-ef66dcc1eeb0" />

In saturation region the channel voltage remains constant = vgs-vt . Drain current was  linear function of  vds .

*To get drain current equation in saturation region we will replace Vds as Vgs-Vt.

<img width="637" height="366" alt="image" src="https://github.com/user-attachments/assets/ef922a68-4d9f-4c5c-96ed-20aaff2621a3" />

At first , the MOSFET seems to act like a perfect current source. But in reality, when we increase vds
,the depletion region at the drain gets larger, which shortens the effective channel. This causes the drain current Id to slightly depend on vds . 

<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/d89ec2eb-b8cf-4020-8d8d-36125c4dca3e" />

The drain current equation is given below and  λ is  called channel length modulation .

 <img width="1600" height="312" alt="image" src="https://github.com/user-attachments/assets/e74e9892-b699-4538-a243-136d19bd378a" />

# Introduction to spice 

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

# Circuit description in SPICE syntax
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

# Define technology parameters 

Here we will see how to model this NMOS transistor. The model parameters are already given, so it is easy to create the model using them. These parameters are available in the technology file. The NMOS model can be found in the file with the same or a similar model name.

<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/f40003ca-92b5-4312-8754-1f44a99fd391" />

<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/caa8aca2-0f21-4554-b652-2c4307daacd4" />

These are the parameters coming from foundry ,we can use it in spice by .MODEL as stated above .Here we can state parameters in its respective positions as it has predeined positions for diffrent values.
we just plug in this packaged file in .mod file and call this file in top level SPICE netlist.

<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/7a4e702d-f360-42af-a02e-9f3be1fdf454" />

* All these models can be stored in .lib format .This can be used in spice console .

2 VDS ARE LEFT 

# DAY -2  L1 SPICE SIMULATIONS FOR LOWER NODES AND VELOCITY SATURATION 

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

# L2 Drain current vs gate voltage for long and short channel device 

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

# L3 velocity saturation at lower and higher electric fields 

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

# L4 velocity saturation drain current 

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

  # cmos voltage transfer characteristrics
  
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
   
# L2 INTRODUCTION TO STANDARD MOS VOLTAGE CURRENT PARAMETERS 

  CASE 1: Vin =Vdd  
  
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
* 
* Since the only path from the output node is through Rn to ground, the output voltage Vout is pulled down to 0 V. The load capacitor CL also discharges to 0 V through Rn.

* When Vin = Vdd → Vout = 0 (Output is LOW). This is the inverting property of the CMOS inverter.

<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/7e0cf1ab-a9fc-4fa7-8986-2d926c80831e" />

  case 2:

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















#  L3 PMOS/NMOS drain current v/s drain voltage
<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/76e1b909-4bf9-41c8-8486-34a6a8131ea7" />

The CMOS inverter consists of two transistors:
•	PMOS: source connected to Vdd, gate connected to Vin, drain connected to Vout
•	NMOS: source connected to Vss (GND), gate connected to Vin, drain connected to Vout
•	Load capacitor CL is present at the output node
Terminal Voltage Derivation
We derive the Vgs and Vds expressions for each transistor by observing circuit connections.

<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/13c4e841-4ca4-4b4c-a240-0436a649bd34" />

For NMOS (source = Vss = 0V):
•	VgsN = Vin – Vss = Vin
•	VdsN = Vout – Vss = Vout
•	So, IdsN is a function of Vin and Vout

* The gate-to-source voltage of the NMOS is directly equal to the input voltage Vin, and the drain-to-source voltage is equal to the output voltage Vout. So, the NMOS drain current IdsN is a function of both Vin and Vout.
  
For PMOS (source = Vdd):
•	VgsP = Vin – Vdd
•	VdsP = Vout – Vdd
•	Both are negative (since Vin ≤ Vdd and Vout ≤ Vdd), which is consistent with PMOS operation

* Both VgsP and VdsP are negative values since Vin and Vout are always less than or equal to Vdd. This is consistent with PMOS operation, which requires negative gate-to-source voltage to turn on.

* Since both transistors share the same output drain node, the current flowing through PMOS must equal the current flowing through NMOS. The sign difference occurs due to the direction of current flow:
IdsP = – IdsN .This equation is very important. It means that whatever current the PMOS supplies (charging CL), the NMOS must sink (discharging CL) in steady state. In transient conditions, the difference in these currents determines how quickly the output node charges or discharges
* NMOS IdsN vs VdsN Characteristic Curve
  
* The Id vs Vds characteristic curve for the NMOS transistor, the curve is plotted with IdsN on the Y-axis and VdsN on the X-axis, with multiple curves corresponding to different values of VgsN.

Since VgsN = Vin and VdsN = Vout, each curve on the graph corresponds to a fixed input voltage, and the X-axis represents the output voltage Vout. The curve shows:

•	At lower values of VdsN, the NMOS operates in the linear (resistive) region where IdsN increases almost linearly with VdsN .

•	Beyond the pinch-off point (VdsN = VgsN – Vtn), the NMOS enters saturation and the current flattens out

•	Higher values of VgsN (Vin) result in higher saturation currents – represented by the curves VgsN1 through VgsN5 from bottom to top

<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/bc8ac3cc-0f0e-4c6a-bbcf-1b157fee02d2" />

PMOS IdsP vs VdsP Characteristic Curve

Since PMOS operates with negative voltages:
•	The X-axis is plotted as –VdsP (which corresponds to Vdd – Vout)
•	The Y-axis is plotted as –IdsP (because PMOS current flows in the opposite direction)
•	Multiple curves are drawn for –VgsP1 through –VgsP5 representing different input voltage conditions

* The shape of the PMOS curve is similar to the NMOS curve but mirrored, since PMOS is structurally a complementary device.

<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/0b51c4f8-2ca3-4b9c-83ea-c3ddbbea0274" />



