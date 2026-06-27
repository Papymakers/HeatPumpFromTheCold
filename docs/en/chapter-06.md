# Chapter 6 — Diagnosing and Troubleshooting Modern Heat Pumps

## Safety warning

> ⚠️ **Read before any intervention**
>
> A modern heat pump contains dangerous voltages. The inverter DC bus reaches 170–400 V DC depending on your mains supply voltage. The filter capacitors remain charged **for several minutes after the mains supply is cut** — exactly like the capacitors in a valve amplifier or cathode-ray television set.
>
> **Absolute rule: switch off, wait 10 minutes, measure before touching.**
>
> Above 50 V DC, the current passing through the body can be fatal. Measuring the DC bus with a voltmeter before any intervention is not a precaution — it is an obligation.
>
> **Note for North American readers**: the same rules apply whether your supply is 120 V or 240 V. The DC bus on a 240 V system reaches approximately 340 V DC — as dangerous as a European system.
>
> Handling the refrigerant circuit (refrigerant, fittings, valves) is legally restricted to technicians holding the relevant certification (EPA 608 in the USA, equivalent certifications elsewhere). This chapter does not cover these interventions.

---

## What a Papy Maker can do

Diagnosing a faulty heat pump naturally divides into two zones:

**Green zone — accessible without certification:**
- Reading error codes
- Diagnosing temperature sensors (NTC probes)
- Checking low-voltage power supplies
- Diagnosing control boards
- Checking wiring and connectors
- Home automation integration and monitoring

**Orange zone — feasible with precautions:**
- Diagnosing the Inverter board (after confirmed capacitor discharge)
- Measuring voltages on the DC bus
- Replacing the Inverter board

**Red zone — certification required:**
- Anything involving the refrigerant circuit
- Handling refrigerants
- Refrigerant pipework connections

---

## Reading error codes

This is always the first step. Every manufacturer has an error code system displayed on the indoor unit or accessible via the control interface.

### Accessing the codes

Depending on the machine:
- **Direct display** on the control panel (codes such as E1, F3, P8...)
- **Flashing LEDs** on the outdoor unit's electronic board — the number of flashes encodes the error code
- **Mobile app** or proprietary web interface
- **Diagnostic mode** accessible via a button sequence on the remote control

### Decoding the codes

Manufacturers' technical manuals are generally available online and document all error codes. Some common codes across many brands:

| Code type | Frequent cause |
|---|---|
| Temperature sensor error | Defective or disconnected NTC probe |
| High pressure error | Fouled condenser, failed fan, overcharged refrigerant |
| Low pressure error | Refrigerant leak, frosted evaporator, failed expansion valve |
| Communication error | Defective inter-unit cable or incorrect configuration |
| Inverter error | Defective Inverter board, faulty compressor motor |
| Defrost error | Defective defrost probe, stuck defrost cycle |

---

## Diagnosing temperature sensors (NTC probes)

NTC (*Negative Temperature Coefficient*) probes are thermistors whose resistance decreases as temperature increases. They are ubiquitous in a heat pump: outdoor temperature, flow temperature, return temperature, evaporator temperature, condenser temperature...

### Measuring an NTC probe

An NTC probe can be measured simply with a multimeter in resistance mode, **with the power off**:

| Temperature | Typical resistance (NTC 10kΩ at 25°C / 77°F) |
|---|---|
| −4 °F (−20 °C) | ~67 kΩ |
| 32 °F (0 °C) | ~27 kΩ |
| 77 °F (+25 °C) | ~10 kΩ |
| 122 °F (+50 °C) | ~4 kΩ |

A probe measuring 0 Ω (short circuit) or ∞ (open circuit) is defective. A probe giving a value inconsistent with the ambient temperature is also suspect.

### Replacement

NTC probes are standard components, often interchangeable between brands for common values (10 kΩ at 25 °C, standard B coefficient). The connector may be proprietary but the sensor itself is generic.

---

## Diagnosing the control board

The control board (control unit) is the brain of the heat pump. It manages communication between units, drives the Inverter, monitors sensors, and protects components.

### Check points

**Power supplies** — check the board's supply voltages with a multimeter:
- 12 V DC or 24 V DC depending on the manufacturer
- 5 V DC for logic circuits
- An absent or out-of-tolerance voltage (± 10%) indicates a power supply problem to investigate before suspecting the board itself

**Connectors** — small-section connectors are a frequent source of problems:
- Oxidised contacts (common in damp outdoor environments)
- Poorly seated connectors after a previous intervention
- Wires pulled off probe connectors

**Electrolytic capacitors** — as with any electronic equipment, electrolytic capacitors age and may bulge or leak. A visual inspection is essential before any measurement.

### Inter-board communication

The cable linking the indoor and outdoor units is a frequent and often overlooked source of faults:
- Insufficient cross-section for the cable run length
- Reversed polarity during installation or repair
- Mechanically damaged cable (rodents, pinching)
- Electromagnetic interference if the cable runs close to a power cable

---

## Diagnosing the Inverter board

### Mandatory preliminary precautions

1. Switch off the mains supply at the dedicated circuit breaker
2. Wait **at least 10 minutes**
3. Measure the voltage on the DC bus (terminals marked P and N on the board, or bus capacitors) — it must be below 50 V before any handling
4. Work with one hand behind your back where possible — standard electrician's safety reflex

### Visual inspection

Before any electrical measurement, a careful visual inspection is essential:
- Burn marks or flashover on the IGBTs
- Bulging or leaking bus capacitors
- Burnt bus discharge resistors
- Burnt or lifted PCB tracks

### Inverter board replacement

Inverter boards are available as spare parts from specialist distributors and increasingly from online marketplaces. Replacement is often the most economical solution for a defective board — component-level repair is feasible for an experienced electronics engineer, but power IGBTs require appropriate soldering equipment.

---

## Home automation integration and monitoring

This is a particularly interesting area for Papy Makers: several manufacturers allow access to the heat pump's data via documented or community-reverse-engineered protocols.

### ESP32 gateways

Open source projects allow connecting a heat pump to a home automation system via an ESP32:

- **ESPAltherma** (Daikin Altherma) — reading and control via the X10A connector on the indoor unit
- **CN105** (Mitsubishi Electric) — documented serial interface, many Arduino/ESP32 projects
- **MQTT integration** — the data read can be published to an MQTT broker and integrated into Node-RED, Home Assistant, or any other system

These gateways allow real-time monitoring of COP, temperatures, consumed and produced power — valuable data for optimising the installation and detecting gradual performance degradation before it becomes an outright failure.

### What can be monitored

- Outdoor temperature and flow temperature
- Electrical power consumed (Wh)
- Thermal power produced (calculated)
- Instantaneous COP and seasonal average COP (SCOP)
- Number and duration of defrost cycles
- Error codes in real time

---

## Resources and documentation

### Technical manuals

Most manufacturers publish their installation and maintenance manuals on their professional websites. Some require an installer account, but complete service manuals circulate widely on specialist forums.

### Online communities

- **Heat pump forums** — installer and owner feedback
- **Home Assistant Community** — heat pump home automation integration
- **GitHub** — ESPAltherma, CN105, and other open source gateway projects
- **Reddit r/heatpumps** — active English-language community

### Minimum recommended tools

| Tool | Use |
|---|---|
| True RMS multimeter | Voltage, resistance, current measurements |
| Clamp ammeter | Current measurement without breaking circuit |
| IR thermometer | Surface temperature checks |
| Oscilloscope (optional) | Inverter control signal diagnosis |
| ESP32 + adapter cable | Home automation integration and monitoring |

---

## What a Papy Maker should remember

- **Always start with the error codes** — they guide the diagnosis and avoid searching in the wrong place
- **NTC probes are often the culprit** — easy to measure, inexpensive to replace
- **The DC bus remains dangerous after shutdown** — 10 minutes' wait and measurement before working on the Inverter
- **The control board is diagnosed at low voltage** — power supplies, connectors, capacitors
- **An ESP32 can turn a heat pump into a data source** — monitoring prevents failures and optimises performance
- **The refrigerant circuit remains out of scope** — this is not a technical limitation, it is a regulatory requirement
