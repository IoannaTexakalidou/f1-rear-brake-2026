# Technical data

Every input of the model, with where it comes from. Each value is marked as a regulation value, data, or an assumption. The assumptions are varied in the sensitivity study over the range shown.

Regulation source: FIA 2026 Formula 1 Technical Regulations, Section C, Issue 19, 25 June 2026. Article and page are given for each value.

## 1. The lap data

| Item | Value | Source |
|---|---|---|
| Main lap | Lando Norris, fastest lap of Monza 2024 qualifying | FastF1 (official F1 timing data) |
| Second track | fastest lap of Singapore 2024 qualifying | FastF1 |
| Signals used | speed, throttle, brake on/off, engine speed | FastF1, about 4 samples per second |
| Braking zones | Monza 6, Singapore 11 (speed drop of at least 40 km/h) | found by the model |
| Mean speed over the lap | Monza 261 km/h, Singapore 196 km/h | from the lap data |

## 2. What changes from 2025 to 2026

| | 2025 | 2026 | 2026 source |
|---|---|---|---|
| MGU-K maximum electrical power | 120 kW | 350 kW | C5.2.7, p.65 |
| Energy the MGU-K may recover per lap | 2 MJ | 8.5 MJ (can be reduced to 7 MJ, at least 5 MJ in qualifying) | C5.2.10, p.66 |
| MGU-K maximum torque | the 120 kW power limit always binds first | 500 Nm, referred to engine speed | C5.2.11, p.66 |
| Minimum car mass in qualifying, without fuel | 798 kg, including tyres | 726 kg plus the tyre mass | C4.1, p.60 |
| Tyre mass used for 2026 | included above | 44 kg, an assumption (the FIA publishes it separately), varied 40 to 48 kg | assumption |
| Fuel on board in qualifying | 10 kg | 10 kg | assumption |
| Mass used in the energy equations | 808 kg | 780 kg | derived |

The lap is from 2024. Its car ran under the same MGU-K rules as 2025 and a minimum mass of 798 kg. The 2025 minimum became 800 kg, a difference of 0.25% that does not change the results.

The 2026 rule that limits MGU-K power when it pushes the car (P = 1800 − 5 × speed, C5.2.8) applies only to propulsion, so it does not limit recovery under braking.

## 3. Rear brake disc

| Parameter | Value | Status |
|---|---|---|
| Material | carbon carbon | typical for F1 |
| Outer diameter | 278 mm | rule: rear discs 260 to 280 mm (C11.3.3, p.120) |
| Inner diameter | 170 mm | assumption, set by the CAD bell interface |
| Thickness | 24 mm | rule: at most 34 mm (C11.3.2, p.120) |
| Cooling holes | 800 radial holes of 2.5 mm | rule: at least 2.5 mm (C11.3.4, p.120) |
| Drive slots | 30 | CAD |
| Share of the disc volume that is holes | 22.3% | from the CAD geometry, varied 15% to 30% |
| Density | 1,750 kg/m³ | assumption, typical carbon carbon |
| Mass | 1.24 kg | from the CAD geometry |
| Specific heat | 900 J/(kg K) | assumption, varied 750 to 1,050 |
| Heat capacity of the disc | about 1,120 J/K | derived |
| Emissivity | 0.85 | assumption, varied 0.75 to 0.95 |
| Area that radiates heat | 0.097 m² (both faces plus the outer rim) | derived |
| Air temperature | 30 °C | assumption, varied 20 to 40 °C |
| Peak temperature set for 2025 | 750 °C | reference scenario, not a measurement, varied 650 to 850 °C |
| Working range assumed for carbon brakes | 400 to 900 °C | assumption, used only for comparison |
| Share of cooling not supplied by the duct | 10% | unknown, varied 0% to 30% |

## 4. The 2026 brake rules and how the design meets them

| Rule | Article | This design |
|---|---|---|
| Rear disc diameter 260 to 280 mm | C11.3.3 | 278 mm |
| Disc thickness at most 34 mm | C11.3.2 | 24 mm |
| Cooling holes at least 2.5 mm | C11.3.4 | 2.5 mm |
| One caliper per wheel, 1 to 4 pairs of opposing pistons, aluminium | C11.2.2, C11.2.4 | caliper modelled only as a space envelope |
| No liquid cooling of the brakes | C11.5 | air cooling through a duct |
| Rear brakes must give at least 2,500 Nm per wheel without the MGU-K | C11.1 | not checked in this study |

## 5. Car and model inputs

These are not published for any F1 car, so each is an assumption, varied over the range shown.

| Parameter | Value | Range | Note |
|---|---|---|---|
| Drag area CdA | 1.05 m² | 0.85 to 1.30 | Monza, low downforce |
| Downforce area ClA | 3.00 m² | 2.50 to 3.50 | Monza. Singapore uses 1.55 and 4.60 |
| Air density | 1.20 kg/m³ | 1.14 to 1.25 | Singapore 1.16 |
| Rolling resistance coefficient | 0.015 | fixed | |
| Engine braking torque | 35 Nm | 15 to 60 Nm | at the crankshaft, throttle closed |
| Front brake balance | 57% | 50% to 65% | |
| MGU-K efficiency, mechanical to electrical | 90% | 85% to 95% | |
| Centre of gravity height | 0.30 m | 0.25 to 0.35 m | |
| Wheelbase | 3.40 m | fixed | rule: at most 3,400 mm (C2.3.3, p.12) |
| Weight on the rear axle at rest | 55% | fixed | rule: rear at least 54%, front at least 44% (C4.2, p.60) |
| Front share of downforce | 45% | fixed | |
| Rear tyre grip coefficient (grip proxy only) | 1.55 | 1.30 to 1.80 | not a tyre model |
| Car running above the minimum mass | 0 kg | 0 to 14 kg | |
| MGU-K power the team chooses to use | 350 kW | 200 to 350 kW | team strategy, not uncertainty |
| MGU-K torque the team chooses to use | 500 Nm | 300 to 500 Nm | team strategy, not uncertainty |

## 6. Rear corner CAD (Fusion 360)

| Part | What it is |
|---|---|
| Brake disc | 278 mm carbon disc with drilled faces and internal drive splines, built from the same parameters as the thermal model |
| Disc bell | splined bell that carries the disc and connects it to the hub |
| Caliper | space envelope, 150 × 42 × 58 mm (assumed) |
| Wheel | 18 inch rim (457 mm), wheel barrel kept as a clearance envelope |
| Upright and suspension | keep out volumes for packaging |
| Brake duct | three concepts: baseline, reduced inlet (60% to 80%), and one body with interchangeable inserts (50% to 100% inlet) |

The baseline duct inlet is 90 × 60 mm (5,400 mm²), the 100% point of the duct study. Its real size has to come from CFD.
