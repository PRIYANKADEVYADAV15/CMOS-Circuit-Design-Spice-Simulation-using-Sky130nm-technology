# CMOS-Circuit-Design-Spice-Simulation-using-Sky130nm-technology

## Table Of Contents
- [NgspiceSky130-Day1-Basics of NMOS Drain Current(Id) vs Drain-to-source Voltage(Vds)](#NgspiceSky130-Day1-Basics-of-NMOS-Drain-Current(Id)-vs-Drain-to-source-Voltage(Vds))
  - [Introduction to Circuit Design and Spice Simulations](#Introduction-to-Circuit-Design-and-Spice-Simulations)
    - [L1 Why do we need SPICE simulations?](#L1-Why-do-we-need-SPICE-simulations?)
    - [L2 Introduction to basic element in circuit design-NMOS](#L2-Introduction-to-basic-element-in-circuit-design-NMOS)
    - [L3 Strong inversion and threshold voltage](#L3-Strong-inversion-and-threshold-voltage)
    - [L4 Threshold voltage with positive substrate potential](#L4-Threshold-voltage-with-positive-substrate-potential)
  - [NMOS resistive region and Saturation region of operation](#NMOS-resistive-region-and-Saturation-region-of-operation)
  - [Introduction to SPICE](#Introduction-to-SPICE)


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





