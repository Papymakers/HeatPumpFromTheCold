# Chapter 3 — Suominen's Four Principles: from intuition to global standard

## Introduction

The failures of the PERCHE programme were not caused by a flaw in the thermodynamics of heat pumps. They resulted from four specific engineering problems, which Professor Suominen had identified and addressed from the early 1980s — while France was drawing hasty conclusions about the technology as a whole.

These four principles form a coherent system: each addresses a specific flaw in the machines of the time, and together they define what an effective cold-weather heat pump looks like. Forty years later, they have become the foundations of the entire global industry.

![The four technical principles explained by Professor Suominen](../../assets/images/quatre_principes.png)
*Illustration of the four principles identified by Professor Suominen for a high-performance cold-weather heat pump. Illustration created for this project.*

---

## Principle 1 — An oversized evaporator

### What Suominen recommended

At low outdoor temperatures, the available energy in the air drops. Cold air contains less thermal energy per unit volume, and the evaporator — the component that extracts this energy — must compensate for this scarcity with a larger exchange surface.

The French machines of the time were sized to operate in a range of +5 °C to +15 °C. Below that, their evaporator became insufficient: the machine was thermally "starved", its COP[^1] collapsed, and it would shut down on a safety fault.

Suominen recommended sizing the evaporator for the worst-case conditions — that is, for −20 °C — even if this meant oversizing it at mild temperatures. A generous evaporator at +10 °C is simply very efficient; the same undersized evaporator at −20 °C produces an unusable machine.

### How it evolved

The principle remained, but the means evolved considerably:

- **Fin geometry**: modern evaporators use variable-pitch fins, microstructured surfaces, and helical geometries that maximise heat transfer without excessively increasing volume.
- **Variable-flow fans**: coupled to EC (electronically commutated) motors, they adapt airflow to outdoor temperature, continuously optimising exchange without overconsumption.
- **Adapted refrigerants**: modern refrigerants (R32, R290) have better thermodynamic properties at low temperatures than the R22 used in the 1980s, improving exchange efficiency even on comparable surfaces.

> **In summary**: Suominen was right on the principle — more exchange surface. The industry added forty years of aerodynamic and thermodynamic optimisation.

---

## Principle 2 — Controlled and effective defrost

### What Suominen recommended

Below 0 °C, water vapour in the air deposits on the evaporator and freezes. This layer of frost acts as a thermal insulator: it progressively reduces the exchange between the air and the refrigerant, degrading the COP until the machine becomes ineffective.

Defrost is therefore unavoidable — but it has an energy cost. During the defrost phase, the heat pump no longer provides heating; it consumes energy to warm itself up. Poorly managed defrost can negate much of the gains achieved elsewhere.

Suominen's solution was based on **cycle reversal**: the machine is briefly switched to cooling mode, sending warm refrigerant into the evaporator. The frost melts rapidly, and the machine resumes normal operation within minutes. This defrost must be triggered at the right moment — neither too early (pointless) nor too late (the frost layer is too thick).

### How it evolved

Cycle reversal remained the reference method, but its management became far more intelligent:

- **On-demand defrost**: modern machines no longer defrost on a fixed timer, but in response to sensors measuring differential pressure or evaporator temperature. Defrost is only triggered when truly necessary.
- **Hot gas bypass defrost**: in some systems, warm refrigerant is injected directly into the evaporator without reversing the full cycle, reducing the heating interruption.
- **Predictive algorithms**: top-of-range heat pumps now incorporate models that anticipate frost build-up based on humidity and outdoor temperature, optimising defrost frequency.
- **Targeted auxiliary heaters**: some models combine cycle reversal with localised electric heating on the most sensitive points (drain pan, pipework), reducing cycle duration.

> **In summary**: Suominen set the right principle — defrost quickly and at the right moment by cycle reversal. The industry transformed this intuition into sophisticated control systems that minimise energy losses from defrosting.

---

## Principle 3 — Controls adapted to cold

### What Suominen recommended

A heat pump with on/off control — stopping when the setpoint is reached and restarting when it drops — has two major flaws in cold weather:

- **Short cycling**: the machine stops and restarts frequently, which is mechanically damaging and thermodynamically inefficient (each start consumes a burst of energy without immediately producing useful heat).
- **Power/demand mismatch**: at −20 °C, the building's demand is at its maximum, but a fixed-output machine tuned for +5 °C may be unable to meet it — or, conversely, too powerful at +10 °C and therefore constantly short-cycling.

Suominen recommended *modulating* control: the machine's output must continuously follow the building's demand, as a function of outdoor temperature. The graph in the original article clearly shows the difference between a well-controlled heat pump — whose output follows the demand curve — and a poorly controlled one, whose stepped output generates incessant cycling and poor comfort.

### How it evolved

This is probably the area where the most spectacular technological progress has been made since the 1980s:

- **Weather compensation control**: the heating circuit flow temperature is continuously calculated as a function of outdoor temperature, according to an adjustable curve. The machine anticipates demand rather than reacting after the fact.
- **Inverter compressor** (see Principle 4): it makes continuous power modulation possible, which was technically impossible with a fixed-speed compressor.
- **Home automation integration**: modern heat pumps communicate with connected thermostats, outdoor sensors, and even weather forecasts, to optimise operation over several hours.
- **Occupancy detection and learning**: some systems adapt their control to the occupants' habits, reducing consumption during absence without compromising comfort on return.

> **In summary**: Suominen described the ideal behaviour — modulating output that follows demand. Power electronics and embedded computing have made this behaviour not only possible, but standard.

---

## Principle 4 — A two-speed compressor

### What Suominen recommended

Instead of the traditional on/off operation, Suominen recommended a compressor capable of working at **two distinct speeds**:

- **Low speed** in mid-season, when demand is moderate and outdoor temperatures are still positive: the machine runs continuously at low output, which is thermodynamically far more efficient than repeated full-load starts.
- **High speed** in deep cold, when maximum demand must be met despite very low outdoor temperatures.

This principle may seem simple, but it represented an important conceptual break at the time: it acknowledged that a heat pump could not be optimised for a single operating point. It had to be designed for a *range* of conditions.

### How it evolved

Suominen's two-speed compressor was a first step. The industry went much further:

- **Inverter compressor** (late 1990s): thanks to an electronic variable frequency drive, the compressor speed becomes *continuous* rather than binary. The machine can operate at 30%, 60%, 100% of its rated output — and any point in between. The COP is maximised at every instant.
- **Scroll compressor**: dominant from the 2000s, it offers better volumetric efficiency than the piston compressor used in the 1980s, less mechanical wear, and quieter operation.
- **Twin rotary compressor**: used in high-performance splits, it further reduces vibration and improves efficiency at low loads.
- **Vapour injection**: an advanced technique that injects additional refrigerant into the compressor at mid-compression, significantly increasing the power available at very low temperatures (down to −25 °C and beyond) without oversizing the compressor.

> **In summary**: Suominen established the fundamental principle — variable output is essential. Power electronics transformed this principle into continuous modulation, making the very notion of "fixed speed" obsolete.

---

## Conclusion — A coherent vision, a gradual realisation

What strikes one on re-reading Suominen's work is its systemic coherence. The four principles are not four independent recipes: they form a whole. An oversized evaporator only makes sense if defrost is effective. Modulating control is only possible if the compressor can vary its output. And the whole system only works correctly if the controls can drive the compressor based on actual outdoor conditions.

Suominen had described, from the early 1980s, the architecture of a modern heat pump. What he lacked — and what forty years of technological progress have provided — is affordable power electronics, new refrigerants, optimised heat exchange materials, and microcontrollers capable of managing all of this in real time.

The idea was right. The technology simply took forty years to catch up.

[^1]: **COP** (*Coefficient of Performance*): ratio between thermal energy delivered and electrical energy consumed. A COP of 3 means that for every 1 kWh of electricity consumed, the machine produces 3 kWh of heat. In deep cold, the COP of poorly designed machines sometimes fell below 1 — less efficient than a simple electric radiator.
