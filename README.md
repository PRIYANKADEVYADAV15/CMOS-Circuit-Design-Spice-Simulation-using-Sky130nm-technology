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

**WHy do we need SPICE?**
The clock Tree synthesis, crosstalks, and timing are built on SPICE

