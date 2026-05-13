# Mini Encabulator - PCB Design Project

A complete PCB design exercise demonstrating schematic capture, component selection, and board layout using KiCAD. This project implements a simple LED blinker with user-controllable blink rate.

![PCB Layout](images/layout.png)
*Final PCB layout with component placement and routing*

## 📋 Project Overview

The Mini Encabulator is a microcontroller-based device that:
- **Blinks an LED** when a button is pressed
- **Controls blink rate** via potentiometer position
- Demonstrates **complete PCB design workflow** from schematic to manufacturing files

This project was designed as a learning exercise for PCB design fundamentals, including proper power delivery, signal conditioning, and mechanical integration with an enclosure.

## 🎯 Features

- **Microcontroller-based control** using ATTiny85
- **Hardware debouncing** for reliable button input
- **Analog input** from potentiometer for variable timing
- **Regulated 5V power supply** from 7-12V input
- **In-circuit programming** via ISP header
- **Enclosure-ready design** with precise mounting holes
- **Two-layer PCB** with ground planes for noise immunity

## 🔧 Hardware Components

### Main Components

| Component | Part Number | Package | Purpose | Quantity |
|-----------|-------------|---------|---------|----------|
| Microcontroller | ATTiny85-20S | SOIC-8 | Main processor | 1 |
| Voltage Regulator | LM1117MP-5.0 | SOT-223 | 5V power supply | 1 |
| Protection Diode | MBR0520 | SOD-123 | Reverse current protection | 1 |

### Passive Components

| Component | Value | Package | Purpose | Quantity |
|-----------|-------|---------|---------|----------|
| Resistor | 10kΩ | 0805 | RESET pull-up | 1 |
| Resistor | 10kΩ | 0805 | Button debounce | 1 |
| Resistor | 1kΩ | 0805 | LED current limit | 1 |
| Capacitor | 1µF | 0805 | Power decoupling | 1 |
| Capacitor | 1µF | 0805 | Button debounce | 1 |

### Connectors

| Connector | Type | Pitch | Purpose | Quantity |
|-----------|------|-------|---------|----------|
| Power Input | Molex KK-254 2-pin | 2.54mm | External power | 1 |
| Button | Molex KK-254 2-pin | 2.54mm | User input | 1 |
| LED | Molex KK-254 2-pin | 2.54mm | Indicator output | 1 |
| Potentiometer | Molex KK-254 3-pin | 2.54mm | Analog input | 1 |
| ISP Header | IDC 2x3 | 2.54mm | Programming interface | 1 |

### Mechanical

- **Mounting Holes**: 4× M3 (3.2mm diameter)
- **Potential Compatible Enclosure**: Polycase SN25 or similar

## 📐 Technical Specifications

### Electrical Characteristics

- **Input Voltage**: 7-12V DC
- **Regulated Output**: 5V @ 800mA max (LM1117)
- **Microcontroller**: 20MHz max, 8KB Flash, 512B SRAM
- **Power Consumption**: ~50mA typical
- **LED Current**: 4mA @ 5V with 1kΩ resistor

### Design Rules

- **Minimum Trace Width**: 10 mil (0.254mm)
- **Power Trace Width**: 20 mil (0.508mm)
- **Minimum Clearance**: 10 mil (0.254mm)
- **Via Size**: 31.5 mil pad / 15.7 mil drill
- **Mounting Hole Spacing**: 1.575" × 1.260" (exact)


## 🔌 Pinout & Connections

### ATTiny85 Pin Assignment

| Pin | Function | Connected To |
|-----|----------|--------------|
| 1 (PB5) | RESET | Pull-up resistor, ISP header |
| 2 (PB3) | Potentiometer | J5 (POT wiper) |
| 3 (PB4) | Button Input | J3 (BUTTON) through RC filter |
| 4 (GND) | Ground | Ground plane |
| 5 (PB0) | MOSI/LED | R4 → J4 (LED) |
| 6 (PB1) | MISO | ISP header |
| 7 (PB2) | SCK | ISP header |
| 8 (VCC) | Power | +5V rail, C1 decoupling |

### External Connections

**J1 (Button)**: Momentary Switch
- Pin 1: Ground
- Pin 2: Switch terminal

**J3 (Vin)**: Power Input
- Pin 1: Ground
- Pin 2: +7-12V DC

**J4 (LED)**: Indicator LED
- Pin 1: Anode (+)
- Pin 2: Cathode (-)

**J5 (Pot)**: Potentiometer (10kΩ recommended)
- Pin 1: +5V
- Pin 2: Wiper (ADC input)
- Pin 3: Ground

## 🛠️ Design Methodology

### Power Distribution

1. **Input Protection**: Reverse polarity protection via Schottky diode
2. **Regulation**: LM1117 drops 7-12V input to stable 5V
3. **Decoupling**: 1µF capacitor near microcontroller VCC pin
4. **Ground Plane**: Solid copper pour on both layers for low impedance return path

### Signal Conditioning

1. **Button Debouncing**: Hardware RC filter (τ = 10ms) eliminates mechanical bounce 
2. **RESET Pull-up**: 10kΩ resistor prevents accidental resets from floating pin 
3. **LED Current Limiting**: 1kΩ resistor limits current to safe 4mA

### Layout Strategy

1. **Component Grouping**: Functional blocks grouped as in schematic
2. **Trace Routing**: 
   - Power traces: 20 mil width
   - Signal traces: 10 mil width
3. **Via Placement**: Ground stitching vias connect top/bottom planes
4. **Clearances**: 10 mil minimum trace-to-trace spacing


## 🤝 Contributing

Contributions are welcome! Please feel free to submit issues or pull requests.

### Areas for Improvement

- [ ] Add firmware source code
- [ ] Create 3D render of assembled board
- [ ] Design custom enclosure (OpenSCAD/FreeCAD)
- [ ] Add test points for debugging
- [ ] Implement sleep mode for power saving
- [ ] Create assembly video tutorial


## 🙏 Acknowledgments

- **KiCAD** - Open-source EDA tool
- **ZJUI ECE 445 / ME 470** - Course structure inspiration
- **Atmel/Microchip** - ATTiny85 datasheet and resources

## 📧 Contact

**Drias Imad Eddine** -  drias.imad2006@gmail.com


---

⭐ **If you found this project helpful, please consider giving it a star!**
