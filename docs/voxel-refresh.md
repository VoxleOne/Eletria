## **Continuous Voxel Refresh via Beam Steering**

We're designing a real-time volumetric display system where voxel activation must occur continuously and rapidly to create the perception of a dynamic, persistent 3D image in space. Here's how that concept scales up:

### Conceptual Model

* The system **scans** voxels at **high frequency**, refreshing each visible point fast enough for **persistence of vision** (at least \~24–60 Hz per voxel, depending on display density).
* **Electron beams** are **swept through the voxel space** in coordinated, controlled trajectories.
* **SpinStep** acts as the central controller for:

  * **Voxel sequencing**
  * **Gimbal/quaternion steering**
  * **Beam firing timing**

---

### Beam Steering Mechanism

To scan across thousands of voxels in 3D space:

* **Electron beam emiters** (emitters) are mounted on a **gimbal-like mechanism**, capable of steering the beam along arbitrary orientations.
* Using **quaternion math** (which SpinStep already supports), the emitters can smoothly rotate in 3D without gimbal lock or discontinuities.
* **Gimbal + fine deflection coils** (electromagnetic beam steering) = coarse + fine beam control.

---

### Voxel Activation Loop (Per Frame)

1. **SpinStep calculates** the quaternion rotation + beam parameters for each target voxel in a frame.
2. **Beam steering** hardware orients emitters (via servo/motor or coil adjustments).
3. **Beams fire briefly** to intersect at the voxel point — just long enough to induce visible recombination.
4. System **moves on to the next voxel** rapidly.

This continues for **tens of thousands** of voxels per second — not unlike how CRTs swept beams to form 2D images.

---

### Refresh Rate and Perceived Stability

* **Perception requires stability**: Each voxel must be re-lit before its glow fades (which is typically <1ms for most recombination emissions).
* Therefore, the system must **loop through the active voxel set at 1–5 kHz** to maintain stable images.

This is **well within the realm of possibility**, especially with modern high-speed microcontrollers, FPGAs, or GPUs orchestrating beam paths and emitter control.

---

## System Diagram (Conceptually)

```
               +-----------------------------+
               |       SpinStep Engine       |
               |  (quaternion beam control)  |
               +-------------+---------------+
                             |
      +----------------------+----------------------+
      |                                             |
+-----------+                             +----------------+
| Electron  |                             | Electron       |
| Beam A    |<-- Quaternion Steering -->--| Beam B (or C…) |
+-----------+                             +----------------+
      \                                             /
       \                                           /
        +------------- Target Point -------------+
                         (Voxel)
                         ↙   ↓   ↘
          Visible photon emission via recombination

Environment: Low-pressure ionized gas in sealed vacuum chamber
```

---
