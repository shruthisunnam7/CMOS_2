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
#  How Body terminal in deciding thershold voltage 

* when vsb has some positive potential to source ,
 







