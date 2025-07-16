## Each Beam Contributes Part of the Energy

The **intersection point** of two beams becomes a **local energy concentration**. Each beam contributes a share of the necessary conditions for a photon emission event (e.g., via recombination, excitation, or collision-induced emission):

* **Electron Beam A** brings half the required **electron flux** (and energy density),
* **Electron Beam B** brings the other half,
* **Their product — not just their sum — determines the local activation rate**.

So the voxel “lights up” **only** where their **combined energy density** exceeds a **threshold for recombination** or **excitation**.

---

## Wavelength (Color) Depends on Interaction Energy

Yes — the **color of the emitted photon** depends on:

* The **type of ion** (e.g., H⁺, He⁺, Ne⁺),
* The **energy transferred** in the recombination/excitation,
* The **final energy state** of the ionized atom or molecule.

If you're targeting specific visible wavelengths:

* You may choose a **gas mixture** where recombination yields light in **RGB bands**,
* Or, in future versions, **modulate the energy of the beams** to adjust the emission line (if feasible).

In either case, the **intersection intensity (e.g., keV/cm²)** must be high enough to ensure photon emission, but **precisely controlled** to hit the right energy transition.

---

## Simplified Model

Let’s say a certain voxel requires a **recombination event** that emits green light (wavelength ≈ 550 nm). The corresponding photon energy is:

$$
E_{\gamma} = \frac{hc}{\lambda} ≈ \frac{(6.626×10^{-34} \cdot 3×10^8)}{550×10^{-9}} ≈ 2.25 \text{ eV}
$$

To reliably trigger this emission:

* The **total energy density at the voxel** must enable an **electron-ion recombination event** that can drop an electron into the correct state.
* If each beam is tuned to deliver \~**half the required flux or excitation probability**, then **only at their crossing point** does the necessary condition arise.
---

## **Nonlinear Interaction Thresholds**

We're essentially relying on a **nonlinear threshold effect**:

> The voxel only emits light when the **local interaction rate** exceeds a critical threshold, and this happens **only where both beams overlap**.

This is common in high-energy physics, nonlinear optics, and plasma physics.

---

## Recombination Rate Depends on Product of Densities

A key relationship from **plasma physics** is the **recombination rate equation**:

$$
R(\vec{r}) = \alpha(T) \cdot n_e(\vec{r}) \cdot n_i(\vec{r})
$$

Where:

* $R(\vec{r})$ is the **recombination rate** per unit volume at position $\vec{r}$,
* $\alpha(T)$ is the **recombination coefficient**, dependent on temperature,
* $n_e(\vec{r})$: **electron density**
* $n_i(\vec{r})$: **ion density**

This is **multiplicative**, not additive — so you can think of it as a **logical AND** gate:

> If either $n_e$ or $n_i$ is low, no significant light is emitted.

---

## Applying It to Our Two-Beam Model

Imagine both beams are focused on a point $\vec{v}$, and that each provides a spatially localized **electron density distribution**:

* Beam A contributes $n_{eA}(\vec{r})$
* Beam B contributes $n_{eB}(\vec{r})$

If the **ions are uniformly distributed** ($n_i = \text{constant}$), then:

$$
R(\vec{r}) = \alpha(T) \cdot [n_{eA}(\vec{r}) + n_{eB}(\vec{r})] \cdot n_i
$$

But this assumes **linear superposition** of electron densities — a good first approximation **if the beams are not interfering** quantum-mechanically.

If we instead model it more conservatively — especially when using short pulses or tightly focused beams — then **only where both beams exist** does the **effective local density spike**:

$$
R(\vec{r}) \sim \alpha(T) \cdot n_{eA}(\vec{r}) \cdot n_{eB}(\vec{r}) \cdot n_i
$$

This product-based form is more in line with **NIT's**, as used in:

* Two-photon excitation microscopy
* Cross-beam energy deposition
* Laser-induced breakdown
* Nonlinear ionization in femtosecond plasmas

---

## Reference Analogy: Two-Photon Absorption

In **nonlinear optics**, something very similar happens:

> A molecule only fluoresces when it simultaneously absorbs **two lower-energy photons** from crossing laser beams.

The probability is proportional to the **square of the light intensity**:

$$
P_{\text{2photon}} \propto I_1(\vec{r}) \cdot I_2(\vec{r})
$$

In fact, w’re building a **particle-based analog**:

> Emission occurs **only where electron flux A × electron flux B × ion density** is high enough.

---

## Equation

> **The local visible-light emission rate** at a voxel $\vec{r}$ is approximated by:

$$
R_{\text{emit}}(\vec{r}) \propto \alpha(T) \cdot n_{eA}(\vec{r}) \cdot n_{eB}(\vec{r}) \cdot n_i(\vec{r})
$$

> Where:
>
> * $\alpha(T)$: recombination coefficient (gas-dependent),
> * $n_{eA}, n_{eB}$: electron flux density from each beam,
> * $n_i$: local ion density (set by pre-ionization or ambient plasma),
> * Significant emission occurs **only where both beams intersect** and exceed an energy threshold.

---

## Summary

* ✔️ Each beam contributes part of the **energy density** required for activation.
* ✔️ The voxel **only lights up** when both beams overlap in space and time.
* ✔️ The **emitted color** depends on interaction physics — primarily the **type of ionized gas** and **recombination energy**.
