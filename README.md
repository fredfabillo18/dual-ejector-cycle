# Multi-Pressure Dual Ejector Vapor Compression Cycle Simulation

The project contains MATLAB simulation programs that investigates the thermodynamic performance of a **multi-pressure vapor compression cycle (VCC)** and a **dual ejector-assisted VCC**, including energy and exergy analysis.

The goal of the study is to evaluate how incorporating **dual ejectors** can improve system efficiency compared to a conventional multi-pressure refrigeration cycle.

---

## Repository Contents

This repository contains two MATLAB simulation codes:

### 1. Standard Multi-Pressure Vapor Compression Cycle

A baseline refrigeration cycle that includes:

* **Flash tank**
* **Intercooler**
* Multi-stage compression

This model is used as the **reference system** to compare performance improvements when ejectors are introduced.

<img width="1643" height="535" alt="image" src="https://github.com/user-attachments/assets/99cfb3e4-25ba-4d21-90e5-117fa66cf584" />

---

### 2. Multi-Pressure Dual Ejector Vapor Compression Cycle

An enhanced cycle that incorporates **two ejectors** based on the design methodology proposed by:

**Mendoza et al. (2020)** – Novel Dual-Ejector Vapor Compression Cycle.

<img width="1278" height="658" alt="image" src="https://github.com/user-attachments/assets/246b7e76-d50a-4e86-9480-b6b630f5cfb6" />

The ejectors are modeled with:

* Nozzle efficiency
* Suction chamber efficiency
* Mixing section efficiency
* Diffuser efficiency

The simulation iteratively solves for:

* Entrainment ratios
* Intermediate pressures
* Mass flow balances
* Thermodynamic state points

The model also performs:

* **Energy analysis**
* **Exergy analysis**
* **COP calculations (cooling, heating, combined)**

---

## Dependencies

This simulation requires **NIST REFPROP** for thermodynamic property calculations.

MATLAB accesses REFPROP using the `refpropm` interface.

### Required Software

* MATLAB
* **NIST REFPROP**

---

## REFPROP Setup

The easiest setup is to place the MATLAB scripts inside your REFPROP directory.

Typical location:

```
C:\Program Files (x86)\REFPROP\
```

Inside the code, the path is added using:

```matlab
addpath('C:\Program Files (x86)\REFPROP\')
```

Make sure MATLAB can locate:

```
refpropm.m
```

You can verify by running:

```matlab
which refpropm
```

---

## Refrigerant Used

The simulations currently use:

```
R1234yf
```

However, this can be easily changed in the code:

```matlab
refrigerant = 'R1234yf';
```

REFPROP will handle the property calculations for any supported refrigerant.

---

## Key Simulation Features

The model calculates:

### Thermodynamic Properties

* Enthalpy
* Entropy
* Pressure
* Vapor quality

### Performance Metrics

* Evaporator cooling capacity
* Condenser heat rejection
* Compressor work
* Coefficient of Performance (COP)

```
COPcooling
COPheating
COPcombined
```

### Exergy Analysis

Component-level exergy destruction is computed for:

* Compressors
* Condenser
* Evaporator
* Expansion valve
* Ejector 1
* Ejector 2

Overall exergy efficiency is also calculated.

---

## Iterative Solver

The dual ejector model uses **nested iterative loops** to solve for:

* Ejector entrainment ratios
* Pressure convergence
* Mixing and diffuser conditions

A **secant method** is used for solving the entrainment ratio.

---

## Outputs

The code calculates:

* Refrigeration capacity
* Compressor work
* Total power input
* COP values
* Exergy destruction
* Exergy efficiency

Optional lines are included in the code to export results to CSV for further analysis.

---

## Example Operating Conditions

Default conditions in the simulation:

| Parameter              | Value   |
| ---------------------- | ------- |
| Evaporator Temperature | −40°C   |
| Condenser Temperature  | 30°C    |
| Dead State Temperature | 25°C    |
| Refrigerant            | R1234yf |

These can be modified directly in the parameter section of the script.

---

## Academic Context

This simulation was developed as part of an **undergraduate mechanical engineering thesis** investigating advanced refrigeration cycle configurations and their thermodynamic performance.

---

## Key Results

From the simulation under baseline conditions:

- The dual ejector configuration improved COP compared to the standard multi-pressure cycle.
- Compressor work was reduced due to pressure recovery in the ejectors.
- Exergy destruction was significantly reduced in the expansion process by replacing the throttling valve with ejector expansion.

These results highlight the potential of ejector-assisted refrigeration cycles for improving thermodynamic efficiency in low-temperature applications.

---

## Notes

* The code prioritizes **thermodynamic modeling clarity** over computational speed.
* It is intended for **cycle analysis and academic exploration**.

---
