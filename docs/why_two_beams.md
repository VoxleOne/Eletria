---
# 🎯 Why Two Electron Beams Are Needed to Activate a Voxel

In the Eletria system, visible voxels are created by the **recombination of electrons and ions** within a low-pressure gas chamber. A natural question arises:

> Why do we need **two intersecting electron beams** to activate a voxel in space?

This page explains the reasoning from both a **physical** and **engineering** perspective.

---

## 📍 1. The Problem with a Single Beam

An electron beam traveling through an ionized gas will **interact with ions along its entire path** — not just at a specific point. That means:

- Electrons may recombine with ions **anywhere** along the beamline.
- This creates a **line of unintended emissions**, not a single glowing voxel.
- Precision is lost — you cannot uniquely target one point in 3D space.

### 🔬 Mathematical View

Let’s define:

- \( \vec{r}_e(t) \): the position of an electron along its beam path.
- \( \rho_i(\vec{r}) \): ion density in the gas medium.

The **recombination probability** at any point \( \vec{r} \) is proportional to:

\[
P(\vec{r}) \propto \rho_e(\vec{r}) \cdot \rho_i(\vec{r})
\]

Where:
- \( \rho_e(\vec{r}) \) is the local electron density (spread along the beam).
- For a single beam, \( \rho_e(\vec{r}) \) is **nonzero** along a line → light is emitted **everywhere** along that line.

---

## ✨ 2. Beam Intersection: Localizing Recombination

By crossing **two focused electron beams** at a desired voxel coordinate \( \vec{v} \), we concentrate electron density:

- Both beams have high \( \rho_e \) only where they **intersect**.
- This makes \( P(\vec{r}) \) strongly peaked at \( \vec{v} \) — the voxel point.

### 📐 Geometry

Let two electron beams follow paths:

- Beam A: \( \vec{r}_A(t) = \vec{p}_A + \vec{v}_A t \)
- Beam B: \( \vec{r}_B(s) = \vec{p}_B + \vec{v}_B s \)

The voxel is activated at the **intersection point** \( \vec{v} \) where:

\[
\vec{r}_A(t_0) = \vec{r}_B(s_0) = \vec{v}
\]

The **intersection of two beams** defines a unique 3D coordinate, and only there do the electron densities from both beams overlap maximally.

---

## 🎯 3. Maximizing Recombination Efficiency

Recombination events that emit **visible photons** require:

- Sufficient energy
- Local ion presence
- High **electron density** at a precise point

Intersecting beams achieve this by:

- **Multiplying electron densities** at a single voxel
- Reducing interactions elsewhere (because density \( \rho_e \to 0 \) off-axis)

This boosts the **local probability of visible emission**:

\[
P_{\text{voxel}} \propto \rho_{eA}(\vec{v}) \cdot \rho_{eB}(\vec{v}) \cdot \rho_i(\vec{v})
\]

Outside the voxel, \( \rho_{eA} \cdot \rho_{eB} \approx 0 \), and no light is emitted.

---

## 🚫 4. Avoiding Background Glow

If a single beam were used, unintended recombination along its path would cause:

- **Line-like glow** instead of a point voxel
- **Image noise** and poor contrast
- **Low-resolution artifacts**

Using **beam intersections**, Eletria ensures:

- Voxel brightness is **localized**
- Only the **target voxel emits**
- Image quality and contrast are preserved

---

## 🧠 5. Optional: Pulse Timing & Beam Modulation

In advanced designs, SpinStep could:

- **Pulse beams** for just nanoseconds at the voxel site
- **Modulate beam intensity** based on voxel brightness
- **Use staged recombination** (e.g., pre-ionize with laser, then hit with beam)

---

## ✅ Summary: Why Two Beams?

| Factor                     | Single Beam | Dual Beams |
|----------------------------|-------------|------------|
| 3D Targeting Precision     | ❌ Poor      | ✅ Excellent |
| Recombination Localization | ❌ Spread    | ✅ Point-specific |
| Visual Contrast            | ❌ Blurry    | ✅ Sharp |
| Energy Efficiency          | ❌ Wasted    | ✅ Focused |

By requiring two beams to intersect at a voxel, Eletria creates a **physically clean, optically precise, and controllable light voxel** in free space — forming the foundation for a true 3D display.

---

**Next:** [System Architecture →](04_architecture.md)
```
