# All figures explained

Every figure of the study with a short explanation. The main results are summarised in the [README](README.md).

## Brake heat per lap, front and rear

![Rear friction brake heat per lap, 2025 vs 2026](figures/01_headline_front_vs_rear.png)

Each pair of bars is the heat that goes into the front (purple) and rear (red) friction brakes on one lap, pale for 2025 and dark for 2026. The rear brakes drop by about half, the front brakes almost not at all.

The left and right groups are two ways of dividing the braking between front and rear. "Prescribed brake balance" keeps the split the driver sets, 57% front. "Grip proxy" lets the rear take only as much braking as its tyres can carry, which depends on how much weight is on them. The truth is probably somewhere in between, which is why I report both.

## Where the braking energy goes

![Energy balance per lap](figures/02_energy_balance.png)

Each bar is all the speed energy the car loses under braking in one lap (about 10.4 to 10.8 MJ), split by where it goes: air resistance (blue), engine braking (yellow), the MGU-K (green), the front brakes (purple) and the rear brakes (red). From 2025 to 2026 the green part more than doubles and the red part shrinks.

## Each braking zone

![Rear brake heat per braking zone](figures/03_per_corner_rear.png)

The rear brake heat in each of the six braking zones of the Monza lap. The drop is different in each zone because the MGU-K is limited by its maximum power. In a short, light braking zone (zone 3) it can take everything and the rear friction brakes do nothing at all. In a long, hard stop from top speed (zones 1 and 2) it can only take part of it.

## How sensitive the result is

![Sensitivity](figures/04_sensitivity.png)

The left two panels change one input at a time, from its lowest to its highest plausible value, and show how the drop in rear brake heat moves. The inputs at the top matter most: how much MGU-K power the team uses, and the front to rear brake balance. The right panel changes all inputs together 2,000 times. Green is with the MGU-K used to its full legal power, grey is when the team also chooses to recover less.

## Rear disc temperature over one lap

![Disc temperature over one lap](figures/05_disc_temperature_lap.png)

The temperature of one rear disc over a lap at Monza. The disc heats up sharply in each braking zone and cools down on the straights. Red is 2025, set to peak at 750 °C. Blue is 2026 with the same cooling, peaking at 341 °C. The blue band shows the range when the disc's material properties, the air temperature and the cooling are varied. The green area is the 400 °C to 900 °C range I assumed carbon brakes like to work in. The speed trace below shows where the braking zones are.

## Smaller cooling duct

![Duct inlet area sweep](figures/06_duct_sweep.png)

What happens to the 2026 peak temperature if the cooling duct inlet is made smaller (left to right), for different amounts of cooling the disc gets anyway from the air around the wheel (bottom to top). Bold numbers reach 400 °C. Halving the inlet brings the disc into the range, but the exact size needed depends on how much cooling the disc gets anyway, which only CFD or testing can tell.

## Monza and Singapore

![Monza vs Singapore](figures/07_monza_vs_singapore.png)

The same model on a second, much slower track. Singapore has 11 braking zones and lower speeds, so the MGU-K can take a bigger share of each stop and the rear disc runs even cooler. This is a second scenario, not a check of the model, because the cooling was set again for this track.

## Energy recovery against brake temperature

![Energy recovery versus brake temperature](figures/08_ers_thermal_tradeoff.png)

The main result in one picture. Across, how much electrical energy the MGU-K recovers per lap. Up, the peak rear disc temperature. Each point is a different MGU-K power limit, from 60 kW to the legal 350 kW. The more energy the car recovers, the colder the rear brake runs. The orange line is the same with half the duct inlet, and the thin lines show other brake balances and motor efficiencies. A team has to choose a point on this line.
