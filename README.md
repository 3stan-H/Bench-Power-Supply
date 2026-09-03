# Bench Power Supply

## Overview
A mains-powered, adjustable bench power supply designed in KiCad, converting 120V AC wall input into a regulated 1–30V DC output. The design integrates real-time voltage/current monitoring and follows mains electrical safety practices for isolating AC and low-voltage DC domains. The complete unit was built for approximately $75 in components — roughly 50% less than similarly-specced commercial digital bench supplies ($130–$200 retail).

## Objectives
- Design a safe, mains-powered adjustable DC power supply from raw 120V AC input
- Provide fine-grained, real-time output voltage adjustment
- Display live output voltage and current readings during use
- Follow mains electrical safety practices to protect against shock hazards
- Deliver the unit at a significant cost saving over comparable commercial supplies

## Key Components
- **AC Input Stage** — IEC inlet, fuse, step-down transformer, bridge rectifier
- **Buck Converter** — XL4016, regulating output to 2–5V DC
- **Feedback Network** — potentiometer + resistor divider on the buck converter's feedback pin, enabling 0.01V adjustment resolution
- **Current Sensing** — INA219 current-sensing IC
- **Display/Control** — Arduino Nano driving an LCD screen, showing live voltage/current accurate to 0.01V/0.01A

## Signal Chain
IEC Inlet → Fuse → Transformer → Bridge Rectifier → XL4016 Buck Converter → Regulated 2–5V DC Output

## Files
- `Bench_Power_Supply.kicad_pro` — project file
- `Bench_Power_Supply.kicad_sch` — full schematic (AC input stage, buck converter, feedback network, current-sensing and display circuitry)
- `Bench_Power_Supply.kicad_pcb` — PCB layout (AC-safety and low-voltage DC routing kept separate)
- `gerbers/` — fabrication output (Gerber, drill files)
- `firmware/` — Arduino Nano source code for the INA219 readout and LCD display
- `Bench_Power_Supply_3D.png` — 3D rendered board preview

## Design Notes
- **Voltage Regulation**: The XL4016 buck converter's feedback pin is tuned via a potentiometer/resistor-divider network, giving real-time output adjustment in 0.01V steps across the 2–5V range.
- **Monitoring**: An INA219 current-sensing IC feeds live voltage and current data to an Arduino Nano, which drives an LCD display accurate to 0.01V/0.01A for real-time monitoring during use.
- **Mains Safety**: The chassis (earth) ground is isolated from the circuit's PCB ground rail at the IEC inlet, protecting against electrical shock hazards. AC-safety and low-voltage DC routing are kept physically separated on the PCB layout.
- **Cost**: Total build cost was approximately $75 in components, roughly 50% less than similarly-specced commercial digital bench power supplies (typically $130–$200 retail).

## Status
Designed, laid out, and built as a complete working unit — power regulation, voltage adjustment, and live voltage/current monitoring were all implemented and verified in the final build.
