---
title: Module Bill of Materials
tags:
- tag1
- tag2
---

## Overview
The part includes, quantities, pricing, manufacturer details, and sourcing information to support procurement and assembly, this ensures traceability and repeatability for manufacturing, with all components selected for our project performance requirements and system integration needs.

## Bill of Materials

| **Part Name/Description** | **Qty** | **Unit Cost** | **Total Cost** | **Manufacture** | **Manufacturer #** | **Vendor Link** |**Datasheet Link** | **Schematic Reference Designators** |
|:--------------------|:----|:---------------|:-----|:--------|:-----|:-----|:----|:-----|
Brushed DC Motor, 12VDC, 12,800 RPM, 0.453" Shaft Length, Wire Leads | 1 | $5.95 | $ 5.95 | NMB |PAN14EE12MD | [DigiKey](https://www.digikey.com/short/rcrj5vvj) | [datasheet link](https://mm.digikey.com/Volume0/opasdata/d220001/medias/docus/4806/PAN14EE12MD%20data%20sheet.pdf) | M1 |



# Power Budget

| Component | Quantity | Voltage (V) | Current per Unit (mA) | Total Current (mA) | Total Power (mW) |
|-----------|----------|-------------|----------------------|--------------------|------------------|
| ESP32 | 1 | 3.3 | 80 (active) | 80 | 264 |
| IFX9201SG  | 1 | 12 | 5 | 5 | 60 |
| Motor's | 1 | 12 | 2000 | 2000 | 24000 |
| Voltage regulator (12V→3.3V efficiency 85%) | 1 | 12 | 31 (input) | 31 | 372 |
| Motor running | | | | **~2126 mA** | **~25.5 W** |
| Motor idle | | | | **~116 mA** | **~1.4 W** |

The 12V power supply must provide at least 2.1A continuously to handle both motors. The 3.3V regulator supplies around 80mA to the ESP32. Using a switching regulator with around 85% efficiency, the 12V input current for the logic side is approximately 31mA.

**Conclusion:** A 12V, 5A power supply is recommended for the final robot to provide margin for stall currents and both motors simultaneously.
