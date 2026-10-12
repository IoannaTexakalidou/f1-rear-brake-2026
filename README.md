# F1 Rear Brake Energy and Thermal Study, 2026 Regulations

Ioanna Texakalidou, independent project, 2026

## The question

From 2026, the electric motor on an F1 car's rear axle (the MGU-K) almost triples in power, from 120 kW to 350 kW. Under braking it slows the rear wheels and turns that energy into electricity. So the rear brakes have less to do and run colder.

But carbon brakes only grip well when they are hot. How much colder will the rear brakes run in 2026, and is that a problem?

## The answer

| | 2025 | 2026 |
|---|---|---|
| Heat into the rear brakes per lap (Monza qualifying) | 1.9 to 2.7 MJ | 0.7 to 1.3 MJ, 51% to 63% less |
| Rear disc peak temperature | 750 °C (reference) | 341 to 412 °C |
| Front brakes | | almost unchanged |

The rear disc ends up close to or below 400 °C, the lower end of the range I assumed carbon brakes need. So in 2026 there is a real trade-off: the more energy the car recovers, the colder its rear brakes run. A team cannot fix this with the cooling duct alone. It has to choose how much energy to recover.

![Energy recovery versus brake temperature](figures/08_ers_thermal_tradeoff.png)

*Each point is a different MGU-K power setting. Left: little recovery, hot brakes. Right: the full legal 350 kW, cold brakes.*

## The two main figures behind it

![Rear friction brake heat per lap, 2025 vs 2026](figures/01_headline_front_vs_rear.png)

*Heat into the brakes per lap. The rear (red) drops by about half, the front (purple) barely moves. The two groups are two ways of splitting braking between front and rear.*

![Disc temperature over one lap](figures/05_disc_temperature_lap.png)

*Rear disc temperature over one Monza lap. It jumps at every braking zone. Red is 2025, blue is 2026, the green area is the assumed working range.*

All eight figures, each with a short explanation, are in [FIGURES.md](FIGURES.md).

## How I did it

1. Took Lando Norris's pole lap at Monza 2024 from public F1 timing data (FastF1).
2. For every braking zone, worked out where the energy goes: air resistance, engine, MGU-K, front brakes, rear brakes.
3. Applied the 2026 limits from the official FIA rules, article by article.
4. Modelled how the rear disc heats up and cools down through the lap.
5. Varied every uncertain input thousands of times, so the results are ranges, not single guesses.

## What it does not claim

There is no public brake temperature data, so nothing here is validated. The 750 °C for 2025 and the 400 to 900 °C working range are assumptions used only for comparison. The exact duct size would need CFD or testing.

## Rear corner CAD (in progress)

A parametric Fusion 360 model of the rear corner, built from the same numbers as the thermal model and within the 2026 brake rules.

| Disc | Disc on its bell | Assembled corner |
|---|---|---|
| ![](figures/cad_disc.png) | ![](figures/cad_disc_bell.png) | ![](figures/cad_rear_corner.png) |

## More detail

- [FIGURES.md](FIGURES.md): every figure explained
- [TECHNICAL_DATA.md](TECHNICAL_DATA.md): the disc, the 2026 rules and every model input
- [FORMULAS.md](FORMULAS.md): the equations
- [HOW_IT_WAS_BUILT.md](HOW_IT_WAS_BUILT.md): the code and how I used AI

Python (NumPy, SciPy, pandas, Matplotlib, pytest), FastF1, Fusion 360. The code is private. I'm happy to walk through it on a call.

Contact: j.texakalidou@gmail.com | [Portfolio](https://ioannatexakalidou.github.io)
