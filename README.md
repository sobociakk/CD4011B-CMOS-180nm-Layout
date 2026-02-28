# CD4011B-CMOS-180nm-Custom-Layout

## Overview
This repository contains a full-custom physical design of a CD4011B equivalent integrated circuit. The project was developed from schematic entry down to the physical layout and post-layout verification. 

*Note: Due to NDA restrictions, proprietary TSMC technology files are not included. This repository serves as a portfolio showcase of the design methodology, layout structures, and simulation results.*

## Technology & Tools
* **Process Node:** CMOS TSMC 180 nm 1P6M 1.8V
* **Layout & DRC:** Magic VLSI
* **Simulation:** LTSpice (Pre-layout and Post-layout parasitic extraction)

## Key Design Features
The layout includes physical protections required for reliable chip fabrication:
* **ESD Protection:** Implemented robust protection on all I/O and power pads.
* **Reliability:** Strict layout rules applied to prevent Latch-up and Electromigration.
* **I/O PADs:** Custom 60x70 µm pads designed with the "no-devices-under-pad" rule utilizing all available metal layers.

## Performance Specs
The scaled output buffers were rigorously verified across the following conditions:
* **Operating Voltage:** $V_{DD}$ = 1.8V ± 10%
* **Temperature Range:** -30°C to +125°C
* **Capacitive Load:** 25 pF

## IC diagram
![ic_diagram](img/ic_diagram.png)

## Proposed layout schematic and pre-extraction netlist
![schem_netlist](img/schem_netlist.png)

## Pre-extraction Waveforms & Verification

### Output buffer current drive capability
![cdc_vh](img/cdc_vh.png)
*At a current load of 15mA, with Vdd –10% and a maximum temperature of 125°C, the output high voltage drops to 1.476V.*
![cdc_vl](img/cdc_vl.png)
*At a current load of 15mA, Vdd –10% and a maximum temperature of 125°C, the output low voltage drops to 78.795 mV.*

### Signal rise and fall time
![s_rise](img/s_rise.png)
*The rise time is 0.86 ns.*
![s_fall](img/s_fall.png)
*The fall time is 0.65 ns.*

### Threshold voltage
![th_voltage](img/th_voltage.png)
*The threshold voltage is 697 mV.*

### DC current consumption
![idd_cons](img/idd_cons.png)
*Averge DC current consumption is 1.40 mA, with a peak of 50 mA.*

## Single gate layout
![gate_lay](img/gate_lay.png)

## Gate with buffer stages
![gateb_lay](img/gateb_lay.png)

## ESD protection + Pad
![esd_pad](img/esd_pad.png)

## Layout topography
![layout](img/layout.png)

## Post-extraction Waveforms & Verification

### Post-extraction Output buffer current drive capability
![cdc_vh_pe](img/cdc_vh_pe.png)
*At a current load of 15mA, with Vdd –10% and a maximum temperature of 125°C, the output high voltage drops to 1.476V.*
![cdc_vl_pe](img/cdc_vl_pe.png)
*At a current load of 15mA, Vdd –10% and a maximum temperature of 125°C, the output low voltage drops to 78.131 mV.*

### Post-extraction Signal rise and fall time
![s_rise_pe](img/s_rise_pe.png)
*The rise time is 0.87 ns.*
![s_fall_pe](img/s_fall_pe.png)
*The fall time is 0.65 ns.*

### Post-extraction Threshold voltage
![th_voltage_pe](img/th_voltage_pe.png)
*The threshold voltage is 697 mV.*

## Results Summary
The following table compares the theoretical requirements with the LTSpice simulation results, both pre-layout and post-layout (with extracted parasitics).

| Parameter | Target | Pre-Layout | Post-Layout (Extracted) |
| :--- | :--- | :--- | :--- |
| **Max Frequency** | $\ge$ 30 MHz | 30.00 MHz | 29.948 MHz |
| **Output Voltage High (15 mA load)** | $\ge$ 1.62 V (90% VDD) | 1.476 V | 1.476 V |
| **Output Voltage Low (15 mA load)** | $\le$ 0.18 V (10% VDD) | 78.795 mV | 78.131 mV |
| **Rise Time** | - | 0.856 ns | 0.87 ns |
| **Fall Time** | - | 0.649 ns | 0.656 ns |
| **Switching Voltage** | ~900 mV | 697 mV | 696 mV |

*Average power supply current consumption was measured at 1.40 mA with a peak of 50 mA.*

## Summary
The designed circuit has been optimized for the required temperature range, ensuring correct operation across the entire specified interval. At a minimum input signal frequency of 30 MHz, the output yields valid values. The design incorporates Electrostatic Discharge (ESD) protection on the inputs, and narrow spacing has been maintained between adjacent leads, islands, and the substrate to protect the circuit from the latch-up effect. Output pads measuring 60 × 70 µm are located in the pad layer around the perimeter of the structure. The system operates stably at a supply voltage of 1.8 V under the assumed load.

## Repository Contents
* `layout/` - Magic VLSI layouts
* `img/` - Screenshots of waveforms and layouts
* `sim/` - LTSpice waveform plots
