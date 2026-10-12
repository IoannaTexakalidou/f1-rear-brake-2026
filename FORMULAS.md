# Formulas used in the study

Every equation the model uses, in the order the model applies them, with a short note on what each one does.

## 1. Energy lost in each braking zone

**Speed energy lost** between the start speed $v_0$ and the end speed $v_1$ of a braking zone, for a car of mass $m$.

```math
\Delta KE = \frac{1}{2}\,m\,\big(v_0^2 - v_1^2\big)
```

**Air resistance and rolling resistance**, which take part of that energy for free. $\rho$ is the air density, $C_dA$ the drag area, $C_{rr}$ the rolling resistance coefficient.

```math
P_{drag} = \frac{1}{2}\,\rho\,C_dA\,v^3 \qquad P_{roll} = C_{rr}\,m\,g\,v
```

**Braking power at the wheels.** The deceleration $a$ comes from the speed trace, smoothed with a Savitzky Golay filter so that noise is not turned into braking.

```math
a = -\frac{dv}{dt} \qquad P_{wheel}(t) = m\,v\,a - P_{drag} - P_{roll}
```

The power is then scaled slightly so that over the whole braking zone it adds up exactly to the energy lost:

```math
\int P_{wheel}\,dt = \Delta KE - E_{drag} - E_{roll}
```

## 2. Front and rear

**Prescribed brake balance.** With a front balance $b$ (57%), the rear axle takes the rest.

```math
P_{rear} = (1 - b)\,P_{wheel}
```

**Grip proxy.** The rear axle can only brake as hard as the load on its tyres allows. The load on the rear tyres is the static weight share $s$, plus the rear share of the downforce, minus the weight that moves forward under braking ($h$ = centre of gravity height, $L$ = wheelbase).

```math
F_{z,rear} = s\,m\,g + (1 - a_f)\,\frac{1}{2}\,\rho\,C_lA\,v^2 - m\,a\,\frac{h}{L}
```

Grip falls slightly as the load rises (load sensitivity $k$), and the rear braking power is capped by that grip:

```math
\mu = \mu_{rear}\left(\frac{F_{z,rear}}{4000\ \text{N}}\right)^{-k} \qquad P_{rear} \le \mu\,F_{z,rear}\,v
```

## 3. Engine, MGU-K and rear friction brakes

**Engine braking** acts on the rear axle. $\tau_{eng}$ is the closed throttle torque, $\omega$ the engine speed from the lap data.

```math
P_{eng} = \min\big(\tau_{eng}\,\omega,\ P_{rear}\big)
```

**MGU-K.** It takes mechanical power from the rear axle, limited by three things: what is left of the rear braking, the electrical power limit (350 kW in 2026, 120 kW in 2025, converted with the efficiency $\eta$ = 90%), and the torque limit of 500 Nm at engine speed.

```math
P_{mech} = \min\left(P_{rear} - P_{eng},\ \frac{P_{elec,max}}{\eta},\ \tau_{max}\,\omega\right)
```

The electrical energy it stores over the lap may not pass the limit per lap (8.5 MJ in 2026, 2 MJ in 2025):

```math
E_{elec} = \eta\int P_{mech}\,dt \ \le\ E_{lap,max}
```

**Rear friction brakes** take whatever is left, shared between two rear discs:

```math
P_{fric,rear} = P_{rear} - P_{eng} - P_{mech} \qquad Q_{disc}(t) = \frac{P_{fric,rear}(t)}{2}
```

**The headline result**, the drop in rear friction brake heat per lap:

```math
\text{drop} = \left(1 - \frac{E_{fric,rear}^{2026}}{E_{fric,rear}^{2025}}\right)\times 100\%
```

## 4. Rear disc temperature

**Heat balance of the disc** at every time step of the lap: heat in from braking, heat out by air cooling and by radiation. $c$ is the specific heat, $\varepsilon$ the emissivity, $\sigma$ the Stefan Boltzmann constant, temperatures in kelvin for the radiation term.

```math
m_{disc}\,c\,\frac{dT}{dt} = Q_{disc}(t) - h(v)\,A_{conv}\,\big(T - T_{air}\big) - \varepsilon\,\sigma\,A_{rad}\,\big(T^4 - T_{air}^4\big)
```

**Air cooling.** It grows with car speed $v$ and with the duct inlet area $A_{duct}$ (relative to the baseline), in the way turbulent flow does ($\text{Re}^{0.8}$). A share $r$ of the cooling comes from the air around the wheel and does not depend on the duct.

```math
h(v) = h_{ref}\left(\frac{v}{60\ \text{m/s}}\right)^{0.8}\Big[\,r + (1 - r)\,A_{duct}^{0.8}\Big]
```

**Calibration.** $h_{ref}$ is chosen so that the 2025 disc peaks at 750 °C over a settled lap. The same $h_{ref}$ is then used for 2026, so only the braking heat changes.

**Disc mass and radiating area.** $D_o$ and $D_i$ are the outer and inner diameters, $t$ the thickness, $\phi$ the share of the volume taken by holes.

```math
m_{disc} = \rho_{disc}\,\frac{\pi}{4}\big(D_o^2 - D_i^2\big)\,t\,(1 - \phi) = 1.24\ \text{kg}
```

```math
A_{rad} = 2\cdot\frac{\pi}{4}\big(D_o^2 - D_i^2\big) + \pi\,D_o\,t = 0.097\ \text{m}^2
```

## 5. Ranges

**Monte Carlo.** All uncertain inputs are drawn at random within their ranges, 2,000 times for the energy and 600 times for energy and temperature together, every draw within 350 kW and 500 Nm. The range quoted is from the 5th to the 95th percentile of the results, the band that holds 90% of them.
