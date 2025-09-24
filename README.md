# CMOS-Circuit-Design-Spice-Simulation-using-Sky130nm-technology

## Table Of Contents
- [NgspiceSky130-Day1-Basics of NMOS Drain Current(Id) vs Drain-to-source Voltage(Vds)](#NgspiceSky130-Day1-Basics-of-NMOS-Drain-Current(Id)-vs-Drain-to-source-Voltage(Vds))
  - [Introduction to Circuit Design and Spice Simulations](#Introduction-to-Circuit-Design-and-Spice-Simulations)
    - [L1 Why do we need SPICE simulations?](#L1-Why-do-we-need-SPICE-simulations?)
    - [L2 Introduction to basic element in circuit design-NMOS](#L2-Introduction-to-basic-element-in-circuit-design-NMOS)
    - [L3 Strong inversion and threshold voltage](#L3-Strong-inversion-and-threshold-voltage)
    - [L4 Threshold voltage with positive substrate potential](#L4-Threshold-voltage-with-positive-substrate-potential)
  - [NMOS resistive region and Saturation region of operation](#NMOS-resistive-region-and-Saturation-region-of-operation)
    - [L1 Resistive region of operation with small drain-source voltage](#L1-Resistive-region-of-operation-with-small-drain-source-voltage)
    - [L2 Drift current theory](#L2-Drift-current-theory)
    - [L3 Drain current model for Linear region of operation](#L3-Drain-current-model-for-Linear-region-of-operation)
    - [L4 SPICE conclusion to resistive operation](#L4-SPICE-conclusion-to-resistive-operation)
    - [L5 Pinch-off region condition](#L5-Pinch-off-region-condition)
    - [L6 Drain current model for saturation region of operation](#L6-Drain-current-model-for-saturation-region-of-operation)
  - [Introduction to SPICE](#Introduction-to-SPICE)
    - [L1 Basic SPICE setup](#L1-Basic-SPICE-setup)
    - [L2 Circuit description in SPICE syntax](#L2-Circuit-description-in-SPICE-syntax)
    - [L3 Define Technology parameters](#L3-Define-Technology-parameters)
    - [L4 First SPICE simulation](#L4-First-SPICE-simulation)
    - [L5 SPICE lab with Sky130 models](#L5-SPICE-lab-with-Sky130-models)

# NgspiceSky130-Day1-Basics of NMOS Drain Current(Id) vs Drain-to-source Voltage(Vds)

## Introduction to Circuit Design and Spice Simulations

### L1 Why do we need SPICE simulations?
A circuit design includes PMOS and NMOS tied together in such a fashion that they result into logic gates such as NAND, NOR, OR, AND etc.</br>

<img width="542" height="526" alt="image" src="https://github.com/user-attachments/assets/bf9b9eed-3cf4-41be-bcfe-8b3ea7eadcb0" />

The above inverter will have the following charactersitics, we will do the SPICE simulations to find the delay and so we will get the W/L ratio of the particular transistor.</br>

<img width="965" height="695" alt="image" src="https://github.com/user-attachments/assets/e2264a62-e4b1-4506-bb0f-eded09d303f3" />

**WHy do we need SPICE?**</br>
The clock Tree synthesis, crosstalks, and timing are built on SPICE (Simulation Program with Integrated Circuit Emphasis), without SPICE there won't be delays and if there are no delays physical design flow, crosstalk won't make any sense.</br>

Let us say we have done some Clock Tree Synthesis of the circuit shown below with bufffers with different capacitive load at the output.</br>

<img width="1206" height="392" alt="image" src="https://github.com/user-attachments/assets/a0dbe0ed-6981-4966-8d1d-7bf4d223ef61" />

After the SPICE simulation we get a "Delay Table", which includes input slew and output load. The intersection value of Input slew and Output load is considered as Delay. Delay tables for both level 1 and level 2 buffers have been shown. This is calculated by circuit design and simulation</br>

<img width="1410" height="668" alt="image" src="https://github.com/user-attachments/assets/422a8a28-f4e6-469a-97d4-535f02762e3d" />

The source of the above Delay Tables comes from circuit design using SPICE simulations. SPICE simulations involves characterisation of any CMOS logic.</br>

### L2 Introduction to basic element in circuit design-NMOS
An NMOS transistor consist of P-type substrate, heavily doped with n+ region. There is an isolated region which isolates the transistor from other transistors. The n+regions are Source and Drain. Above itthere is an oxide layer, and top of it is metal deposition which is the GAte termianal.</br>

<img width="1195" height="507" alt="image" src="https://github.com/user-attachments/assets/fafb4e04-8d70-42dd-bae3-7570c38be028" />

**Threshold Voltage**
This is a very important term, all the characterisation depends on threshold voltage.</br>
At first we will keep the Vgs=0, means source and drain terminal both are grounded. Body is also ground. P-substrate and n+ act as PN junction diode and as there is no potential so there is a high resistance. No channel formation is there.</br>

<img width="1322" height="528" alt="image" src="https://github.com/user-attachments/assets/8e2fee4c-8616-4886-859c-d6c08d166541" />

Now we will apply a positive potential; Vgs>0. We will see gate is now positively charged and due to this there will be Accumulation of negative charges at the surface of substrate.</br>

<img width="1345" height="555" alt="image" src="https://github.com/user-attachments/assets/ef79f61f-5540-4ffb-aec8-06fa9354759a" />

### L3 Strong inversion and threshold voltage
Due to Accumulation of negatuve charges, there will be formation of Depletion Region, depleting of it's majority carriers i.e positive carriers here.</br>

<img width="831" height="402" alt="image" src="https://github.com/user-attachments/assets/335a3525-699e-4c66-8161-2201df2b9070" />

Now we will increase the Gate voltage further, we will see that the positive charge carriers will be repelled and there will be increase of Depletion Width. On further increase of Gate voltage we will reach at a point where the surface gets inverted into an n-type material, this is called "Surface Inversion" or "Stronf Inversion". The gate voltage of Vgs voltage where Strong Inversion happens is called "Threshold Voltage".</br>

<img width="1332" height="551" alt="image" src="https://github.com/user-attachments/assets/03776359-fd17-4e04-9fd5-9212422217df" />

What will happen if we further increase Vgs? As there are no more negative charges that will be attracted towards the positive Vgs, The negative charges from n+ region will get attracted and so there will be a formation of channel at the surface.</br>

<img width="1358" height="573" alt="image" src="https://github.com/user-attachments/assets/f8c47353-dbf7-4026-b4d9-89ebff6cd24d" />

<img width="1350" height="618" alt="image" src="https://github.com/user-attachments/assets/183a52c0-755d-43c6-9731-9043b047e679" />

Now there is a possibility of current from Source to Drain. The channel has bridged the gap between source to drain regions. But as there is no Drain voltage so the elctrons will not move, this is "Cut Off Region" now.</br>

We will see what happens when we change the potential of Body terminal.</br>

<img width="1311" height="532" alt="image" src="https://github.com/user-attachments/assets/0aa83b1f-12c2-4765-bd3f-caa35daac877" />

There will be increase in depletion region between source and body terminal. </br>

<img width="1283" height="607" alt="image" src="https://github.com/user-attachments/assets/1dd9f64e-5345-4dc9-98b2-6dcde19765ef" />

### L4 Threshold voltage with positive substrate potential
If we increase Vgs, we will see that the depletion region increase in both the cases. But, in second case as there is Vsb +ve, few charges from channel will be pulled towards the source.</br>

<img width="1247" height="617" alt="image" src="https://github.com/user-attachments/assets/65d128ea-03af-4dd4-af13-28b261e0fe66" />

Due to this the surface inversion will be slower in second case. Therefore some extra potential has to be apllied in second case to create inversion.</br>

<img width="1356" height="658" alt="image" src="https://github.com/user-attachments/assets/98b3483c-2c33-4244-b96d-6098ee9b0163" />

<img width="632" height="235" alt="image" src="https://github.com/user-attachments/assets/8025a009-e2dd-4e83-a4d6-c1725668e6fc" />

The parameters such as Gamma comes from foundaries after simulation of which in SPICE we get the value for Vt (Threshold Voltage).</br>

<img width="1327" height="643" alt="image" src="https://github.com/user-attachments/assets/8955fdc9-1230-4562-b513-4eca06eb5d3c" />

## NMOS resistive region and Saturation region of operation

### L1 Resistive region of operation with small drain-source voltage
Previously, we saw Cut Off region operation, now we will see the "Resistive region"/"Linear Region" of operation by applying Drain-source voltage.
If we keep on increasing the Gate-source voltage, the channel width keeps on increasing.</br>

<img width="1305" height="508" alt="image" src="https://github.com/user-attachments/assets/29f349a8-c77e-4d13-a323-82b1fa6bfb74" />

This shows that the net Induced charges is propotional to (Vgs-Vt). Now let's apply very small Vds at start. And keep Vt=0.45V, Vgs also small initially.</br>

<img width="1317" height="567" alt="image" src="https://github.com/user-attachments/assets/aed1572f-fd2b-492d-82ca-bd1ce4a94b1e" />

We can see that the source is grounded and Drain is at some potential, so there will be a voltage gradient accross the channel.</br>

<img width="1318" height="577" alt="image" src="https://github.com/user-attachments/assets/bf52a8c7-5553-4c74-888c-cdb43b09e3bc" />

Also, the Effective channel length is much lesser than the original channel length.</br>

<img width="797" height="510" alt="image" src="https://github.com/user-attachments/assets/c35a777b-b625-495c-bb37-9f92dfd92a64" />

Here, y axis represents the width of transistor and x axis is the voltage across the channel.</br>
On applying Vds, every point on x axis will vary w.r.t to Vgs-V(x), this will decide the current equation.</br>

<img width="817" height="558" alt="image" src="https://github.com/user-attachments/assets/a472661e-b9bd-4cfb-8437-ea5be2474fe2" />

### L2 Drift current theory
We know the effective channel voltage will vary w.r.t x, for example at x=0, Vgs=1V and V(x)=0, So the Vgs-Vx=1V. At x=Vds=0.05V, Vgs-Vx=0.95V. Now if we see the induced chagre equation, it is proportional to the effective channel voltage.</br>

<img width="411" height="150" alt="image" src="https://github.com/user-attachments/assets/f303fe6e-388f-4395-9650-e7121cd5aff4" />

<img width="390" height="451" alt="image" src="https://github.com/user-attachments/assets/14f8c404-0d02-4d21-8d67-b20ff1801eae" />

There are two types of currents; Dift and Diffusion current, Here there is Drift current as there is potential difference across the channel.</br>

<img width="1285" height="618" alt="image" src="https://github.com/user-attachments/assets/e1ba1c63-b342-4377-9fe8-1a2e58c93e02" />

To get the drain current, we will see the top view of transistor.</br>

<img width="1311" height="687" alt="image" src="https://github.com/user-attachments/assets/6c473806-a163-4120-974a-73e11da97839" />

### L3 Drain current model for Linear region of operation
As there is change of voltage across the channel length, this will result in change of velocity which is a function of mobility and electrci field.</br>

<img width="448" height="651" alt="image" src="https://github.com/user-attachments/assets/6518460a-1e4c-481f-8341-d99a1fa9a376" />

We will integrate the above equation, where limits of dV will be from 0 to Vds and limits of dx will be from 0 to L.</br>

<img width="442" height="428" alt="image" src="https://github.com/user-attachments/assets/382f07af-71b5-4f00-894d-bdab05e92d0e" />

<img width="377" height="48" alt="image" src="https://github.com/user-attachments/assets/f6f5158c-850f-4272-b381-0b57dc30e7a9" />

Here, Cox, W/L, Vgs, un and Vt are the 'technology parameters', we will simulate usinf SPICE and find out the characteristics.</br>

<img width="387" height="211" alt="image" src="https://github.com/user-attachments/assets/ee457e12-6af7-4389-a11a-036ba5a4b652" />

But, here we cannot say that it is in Linear region, since the Drain current is the quadratic function of Vds. We will calculate the Id with the given values.</br>

<img width="708" height="432" alt="image" src="https://github.com/user-attachments/assets/853ed5fa-0257-4a73-91dd-09007f16d273" />

When (Vgs-Vt)>=Vds, It is in "Linear region".</br>

<img width="683" height="443" alt="image" src="https://github.com/user-attachments/assets/bdfa5383-5b3b-452f-b437-0768814f2551" />

### L4 SPICE conclusion to resistive operation
We need to find the impact of Vgs and Vds on the drain current equation. We will consider different values of Vgs and Vds. If we consider different values of Vgs, under what condition the device will remain in Linear region depends on (Vgs-Vt) should be greater than Vds.</br>

<img width="591" height="172" alt="image" src="https://github.com/user-attachments/assets/d9735c9f-3a26-49aa-bc9b-62e64d65babe" />

Now the main question arises, How do we calculate Id for different values of 'Vgs' and at every value of 'Vgs', sweep Vds till (Vgs-Vt) using linear equation for Id?</br>
For this we need to do SPICE simulations.</br>

### L5 Pinch-off region condition
There is also a Region of operation when Drain-source voltage exceeds the value (Vgs-Vt), the region of operation is called "Saturation Region".
We know the channel voltage is Vgs-Vds. Now, we will increase the Vds.</br>

<img width="1367" height="625" alt="image" src="https://github.com/user-attachments/assets/d29ecff9-3641-49c7-9348-fa7537ff7118" />

When Vgs-Vds is greater than Vt, there will be a conducting channel.</br>
When Vgs-Vds is equal to Vt, we will see at drain side, just Inversion has happened as it is equal to Vt, so channel will start disappearing at drain side.</br>

<img width="1380" height="611" alt="image" src="https://github.com/user-attachments/assets/b51e39ef-093f-463d-8faa-7c6bb23cc68d" />
<img width="1352" height="621" alt="image" src="https://github.com/user-attachments/assets/8d325d80-10d4-47e3-aed0-2caaf0715a36" />

Now when the channel starts to disappear, is termed as "Pinch off region"</br>

<img width="1492" height="602" alt="image" src="https://github.com/user-attachments/assets/40146460-641e-4f89-a950-acebeba103e3" />

When Vgs-Vds<Vt, we will not see any channel present at drain side.</br>

<img width="1310" height="582" alt="image" src="https://github.com/user-attachments/assets/e62baac0-53e1-4c61-a9d6-e26a0a4b8ec1" />

This condition is termed as "Saturation region", when the mosfet is saturated and cannot do anything further.</br>

<img width="391" height="102" alt="image" src="https://github.com/user-attachments/assets/4c0aca6a-e230-47d1-9e30-9416785487be" />

### L6 Drain current model for saturation region of operation
In saturation region, the channel voltage will remain constant as 'Vgs-Vt', and the drain current will not depend on Vds.</br>
To get drain current equation in saturation region we will replace Vds as Vgs-Vt.</br>

<img width="467" height="360" alt="image" src="https://github.com/user-attachments/assets/3df0adef-9616-499c-97de-477da403178b" />

We can now see that according to the equation, the mosfet acts as perfect current source. But this is not true, when we increase Vds we will that Depletion region at drain increases and so channel length further reduces.Therefore, we see a slight dependency of Vds over Id</br>

<img width="1476" height="586" alt="image" src="https://github.com/user-attachments/assets/899bf2cb-f752-43ad-8750-5fc9d6b62f50" />

This is called "Channel Length Modulation".</br>

<img width="876" height="168" alt="image" src="https://github.com/user-attachments/assets/b3d388c1-7074-49c9-a019-7d0ff212271f" />

## Introduction to SPICE

### L1 Basic SPICE setup
First let us look into the SPICE setup.</br>

<img width="1412" height="611" alt="image" src="https://github.com/user-attachments/assets/5872cd9a-70d1-46cf-9fe4-f5247f8d3415" />

Some parameters are constant, and directly coming from the foundaries we don't have to derive them. These are circiled in yellow.</br>

<img width="1313" height="591" alt="image" src="https://github.com/user-attachments/assets/c7f8c503-a596-40a7-85e8-b00b1eef4cf9" />

<img width="922" height="536" alt="image" src="https://github.com/user-attachments/assets/260175cb-7abc-4fc6-a332-6b73b7954cae" />

So, when we feed the SPICE model parameters and SPICE netlist intp the SPICE software, we get the device characteristics in terms of Id vs Vds with different values of Vgs.</br>

**SPICE Netlist**
We need to feed the device into SPICE engine in certain manner, the circuit equivalent of given mosfet is as shown below. </br>

<img width="1262" height="585" alt="image" src="https://github.com/user-attachments/assets/ec870ea4-f7ce-4e99-939a-d6e8646c499e" />

### L2 Circuit description in SPICE syntax
Now we will write the syntax for this particular circuit in SPICE netlist. To do that we need to follow some steps-
* **Define Nodes**
  
  <img width="653" height="410" alt="image" src="https://github.com/user-attachments/assets/726a94e6-1333-41dc-a4c0-d9c766b00f9b" />

* **Give names to the node**
* **Write the code**
  `since modfet has 4 terminals, it is lying between 4 different nodes, similarly resistor is lying between 2 nodes.`

<img width="1307" height="418" alt="image" src="https://github.com/user-attachments/assets/fe360627-afb9-41d7-917d-95b7ac8ca6b7" />
<img width="1211" height="371" alt="image" src="https://github.com/user-attachments/assets/5d8f624b-296a-499a-9cc2-c9fd0946fb52" />
<img width="1213" height="412" alt="image" src="https://github.com/user-attachments/assets/c7d30d08-94c4-4891-95b3-4fc8c95fa3c9" />
<img width="1132" height="381" alt="image" src="https://github.com/user-attachments/assets/b9dad3c6-2cc6-48a5-9409-a7eb90f39301" />
<img width="1197" height="385" alt="image" src="https://github.com/user-attachments/assets/e091f59b-d7b8-4913-9ee3-0a2cc5d324f0" />

The fashion in which it is written is "Drain", "Gate", "Source", and "Substrate" (DGSS).</br>

<img width="1252" height="471" alt="image" src="https://github.com/user-attachments/assets/f9599207-d326-4da5-b92b-53d80a85c4cb" />
<img width="1172" height="406" alt="image" src="https://github.com/user-attachments/assets/15ce1ea6-b8d3-47f6-9ef9-978ddd83bbc6" />
<img width="1242" height="402" alt="image" src="https://github.com/user-attachments/assets/36660836-b886-4c2e-9649-d13863d65f7f" />

this is a long channel mosfet.

Similarly we can write for Resistor.</br>
<img width="1263" height="416" alt="image" src="https://github.com/user-attachments/assets/880832b5-5f1b-49f3-9c01-25ef9bdc55c4" />
<img width="1247" height="463" alt="image" src="https://github.com/user-attachments/assets/1d36164e-cf12-49e3-84b5-8f2928f4a8b9" />
<img width="1345" height="370" alt="image" src="https://github.com/user-attachments/assets/fb1e6449-cf20-48d7-9888-eadc40c5319c" />
<img width="1342" height="422" alt="image" src="https://github.com/user-attachments/assets/53c100fd-845e-474d-b3a3-9a53bfc0ee45" />
<img width="637" height="308" alt="image" src="https://github.com/user-attachments/assets/6498b3c6-8eda-40ee-adf7-c9a6e332675f" />











































































