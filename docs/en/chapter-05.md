# Chapter 5 — Understanding Modern Heat Pumps

## Introduction

The thermodynamic principles of a heat pump have not changed since the 1980s. What has changed radically is the way these principles are implemented: power electronics, microcontrollers, and new refrigerants have transformed a relatively simple mechanical machine into a complex, high-performance system.

This chapter is aimed at readers who want to understand what actually happens inside a modern heat pump — not to reproduce Suominen's work, but to be able to discuss with an installer, read technical documentation, or approach the diagnosis of a fault with confidence.

---

## The refrigeration cycle: the foundation of everything

A heat pump is a thermodynamic machine that moves heat from a cold medium to a warm one — the opposite of the natural direction of heat transfer. To do this, it uses a **refrigerant** that changes state, absorbing or releasing heat in the process.

The basic cycle has four stages:

**1. Evaporation** — The refrigerant, under low pressure, absorbs heat from the cold source (outdoor air, ground, water) and vaporises. This is the role of the evaporator.

**2. Compression** — The compressor draws in the vapour and raises it to high pressure and temperature. This is the stage that consumes electrical energy.

**3. Condensation** — The hot, pressurised fluid transfers its heat to the building's heating circuit and liquefies. This is the role of the condenser (or indoor heat exchanger).

**4. Expansion** — The liquid refrigerant passes through an expansion valve that sharply reduces its pressure, causing significant cooling. The cycle can begin again.

> **The key point**: the heat delivered to the building is the sum of the heat extracted from outside *and* the electrical energy consumed by the compressor. This is why the COP[^1] is greater than 1 — we are not creating energy, we are moving it.

[^1]: **COP** (*Coefficient of Performance*): the ratio between thermal energy delivered and electrical energy consumed. A COP of 4 means that for every 1 kWh of electricity consumed, the machine produces 4 kWh of heat — of which 3 kWh are drawn freely from the environment.

---

## Direct expansion (DX) vs intermediate circuit

There are two main architectures for geothermal heat pumps, which correspond exactly to the debate that Suominen had opened in the 1980s.

### Intermediate circuit (glycol water)

This is the most widespread architecture today for geothermal systems:
- A circuit of buried collectors contains glycol water (antifreeze)
- This glycol water circulates between the ground and a heat exchanger in the heat pump
- The exchanger transfers heat to the refrigerant circuit

**Advantage**: safety (the refrigerant remains confined within the machine), ease of maintenance.  
**Disadvantage**: double heat exchange = additional losses = slightly reduced COP.

### Direct expansion (DX — *Direct eXpansion*)

This is the principle that Suominen recommended:
- The refrigerant circulates directly in the buried collectors
- Evaporation takes place in the ground itself
- One heat exchange instead of two

**Advantage**: better COP, shorter collectors (the exchange is more efficient).  
**Disadvantage**: larger quantity of refrigerant in circulation, stricter safety constraints, more complex maintenance.

Direct expansion remains a technical niche — used by a few specialist manufacturers — but it confirms forty years later that Suominen had identified the thermodynamically optimal solution.

---

## The Inverter compressor: the heart of the modern heat pump

### How the inverter drive works

An Inverter compressor is a compressor whose rotation speed is variable, controlled by an electronic **inverter drive** (or *variable frequency drive*).

The inverter operates in three stages:
1. **Rectification**: the alternating current from the mains (120/240 V AC) is converted to direct current (170–400 V DC depending on supply voltage)
2. **Filtering**: high-capacity capacitors smooth the DC bus voltage
3. **Switching**: power transistors (IGBTs) reconstruct an alternating current of variable frequency to drive the compressor motor

It is this DC bus at 170–400 V that is the point of vigilance during maintenance — exactly like the high-voltage capacitors in a valve amplifier or cathode-ray TV set, they remain charged for several minutes after the mains supply is cut.

> **Note for North American readers**: single-phase residential supplies in North America are typically 120 V or 240 V AC split-phase. The DC bus voltage on 240 V systems is similar to European 230 V systems (around 340 V DC peak). The same safety rules apply: wait, then measure before touching.

### Why it matters

A fixed-speed compressor runs at full power or stops — this is the on/off approach that Suominen criticised. An Inverter compressor can run at 30%, 60%, 100% of its rated output, and any point in between.

Direct consequences:
- **COP maximised at all times**: the machine operates at its optimal efficiency point
- **Improved comfort**: indoor temperature is stable, without oscillations
- **Reduced wear**: fewer full-load starts, increased service life
- **Operation at very low temperatures**: the machine can run slowly rather than stopping

---

## Controls: the brain of the system

### General architecture

A modern heat pump has two levels of control:

**Internal control** (outdoor unit electronic board):
- Inverter compressor management
- Defrost management
- Component protection (pressures, temperatures, currents)
- Communication with the indoor unit

**System control** (thermostat or control panel):
- Weather compensation curve — flow temperature calculated as a function of outdoor temperature
- Mode management (heating, domestic hot water, cooling)
- User interface
- Home automation connectivity

### The weather compensation curve

This is the most important control principle to understand. Instead of reacting to an indoor temperature (like a simple thermostat), the heat pump *anticipates* demand based on outdoor temperature.

A typical weather compensation curve might be:
- At +50 °F (10 °C) outdoor → circuit flow at 95 °F (35 °C)
- At +32 °F (0 °C) outdoor → circuit flow at 113 °F (45 °C)
- At +14 °F (−10 °C) outdoor → circuit flow at 131 °F (55 °C)

This curve is adjustable according to the type of emitters (underfloor heating, low-temperature radiators, standard radiators) and the building's insulation level. Incorrect weather compensation settings are one of the most frequent causes of underperformance in an otherwise well-sized installation.

### Communication protocols

The indoor and outdoor units communicate via proprietary or standardised serial protocols. A few examples:
- **Daikin**: S21 or D-BUS protocol
- **Mitsubishi**: CN105 protocol
- **Atlantic / Hitachi**: proprietary protocols

These protocols are increasingly documented by the open source community, opening up interesting possibilities for home automation integration — in particular via ESP32 gateways that allow reading the heat pump's data and integrating it into Home Assistant, Node-RED, or MQTT.

---

## Refrigerants: evolution and constraints

| Refrigerant | Era | GWP[^2] | Note |
|--------|--------|---------|----------|
| R22 | 1980s–2000s | 1810 | Banned since 2010 (ozone layer destruction) |
| R410A | 2000s–2020s | 2088 | Being phased out (GWP too high) |
| R32 | 2015– | 675 | Predominant today, mildly flammable |
| R290 (propane) | 2020– | 3 | Excellent thermodynamically, flammable |
| R454B | 2023– | 466 | Likely successor to R410A |

[^2]: **GWP** (*Global Warming Potential*): the refrigerant's climate warming potential, expressed as CO₂ equivalent over 100 years. R290 (propane) has a GWP of 3 — nearly neutral — but its flammability requires specific installation constraints.

The trend is clear: tomorrow's refrigerants will have low GWP, at the cost of increased flammability that imposes new safety rules for installers and maintenance technicians.

---

## What a Papy Maker should remember

- The refrigeration cycle is unchanging — what evolves is how it is controlled
- The Inverter is the key to modern performance — understanding how it works means understanding 80% of electronic faults
- The weather compensation curve is the most impactful setting — a well-sized but poorly set heat pump will systematically underperform
- Communication protocols are increasingly accessible — an ESP32 can read and control a modern heat pump
- The inverter DC bus remains live after shutdown — same reflex as with a valve amplifier: wait, then measure before touching

The next chapter addresses diagnosis and troubleshooting — with the necessary safety precautions.
