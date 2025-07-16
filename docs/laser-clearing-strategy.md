# Laser-Based Ion Clearing Strategy

To ensure sharp, high-contrast voxel activation in the Eletria system, we propose a method for **pre-clearing the electron beam path** using an **infrared (IR) laser pulse**. This prevents unwanted recombination events along the trajectory of the electron beam before it reaches the intended voxel.

---

## Objective

Enable the electron beam to interact **only at the target voxel**, by **removing or displacing ions** along its travel path, just before it arrives. This improves:

- Spatial precision of recombination,
- Image contrast,
- Energy efficiency,
- Beam targeting accuracy.

---

## Core Idea

Each electron beam is preceded by a **short, high-intensity infrared laser pulse** that travels the **same trajectory** and:

- Temporarily **displaces or neutralizes ions** along the path,
- Clears a **non-reactive corridor** for the electron beam,
- Allows recombination **only** where beams intersect (i.e. at the voxel).

### Timing Sequence

```text
[ IR Pulse ] ──────────► Clears ion path
                      [ Delay Δt ]
[ Electron Beam ] ────► Follows cleared path to voxel
````

Timing is controlled by the **SpinStep engine** and must be precise within **nanoseconds to microseconds**, depending on medium conditions.

---

## Mechanisms of Ion Clearing

Several possible physical mechanisms can contribute to this effect:

### ✴️ A. Thermal Displacement

* IR laser heats gas along the beamline.
* Heat causes local **ion diffusion**, lowering ion density.
* Reduces probability of recombination events outside the voxel.

### ✴️ B. Electric Field Displacement

* High-intensity pulses induce transient **electric fields** via nonlinear optical effects.
* These can **push ions aside** through ponderomotive or Coulomb forces.

### ✴️ C. Plasma Channel Steering

* IR laser may briefly **channel or modulate** plasma characteristics.
* Creates a **low-density “tunnel”** where the electron beam can pass unaffected.

---

## Interaction Model

Let:

* $n_i(\vec{r}, t)$: ion density as a function of position and time,
* $n_{e}(\vec{r})$: electron density from the beam,
* $R(\vec{r}) \propto \alpha(T) \cdot n_i(\vec{r}, t) \cdot n_e(\vec{r})$: recombination rate.

By firing the laser at $t_0$, and the electron beam at $t_0 + \Delta t$, we engineer:

$$
n_i(\vec{r}, t_0 + \Delta t) \approx
\begin{cases}
0 & \text{along the beam path} \\
n_{i,\text{ambient}} & \text{at voxel target}
\end{cases}
$$

Thus:

* $R(\vec{r}) \approx 0$ along beam,
* $R(\vec{v}) \gg 0$ at voxel $\vec{v}$, where beams intersect and ions remain.

---

## Benefits

| Advantage                  | Description                                       |
| -------------------------- | ------------------------------------------------- |
| ✔️ Suppresses beam glow    | Prevents visible emissions along beamline         |
| ✔️ Improves sharpness      | Voxels appear as discrete, bright points          |
| ✔️ Maintains gas stability | Ion density reset before each frame               |
| ✔️ Invisible operation     | IR laser doesn’t interfere with viewer perception |

---

## Implementation Considerations

* **Laser safety** and precision optics are required.
* **Timing control** must be nanosecond-accurate.
* **Ion clearing pulse** must be localized and reversible.
* Gas mixture and pressure must support fast ion re-population between refresh cycles.

---

## Future Work

* Simulate ion-clearing effectiveness in various gases (e.g., neon, argon, helium).
* Develop timing architecture with SpinStep for pulsed firing logic.
* Investigate filamentation and thermal lensing as possible control mechanisms.

---

**Next:** [System Architecture →](04_architecture.md)

```
