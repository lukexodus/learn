## The Displacement Current

### Motivation: The Inconsistency in Ampère's Law

The original form of Ampère's law relates the circulating magnetic field around a closed loop to the current passing through any surface bounded by that loop:

$$\oint \vec{B}\cdot d\vec{l} = \mu_0 I_{enc}$$

This law works correctly for steady (DC) currents, but Maxwell recognized a fundamental problem when applied to *time-varying* currents, particularly in circuits containing capacitors. Ampère's law requires that $I_{enc}$ be the same regardless of which surface (bounded by the same loop) is chosen for evaluation — but for a charging capacitor, this consistency breaks down.

### The Charging Capacitor Paradox

**Example**

Consider a circuit charging a parallel-plate capacitor, with an Amperian loop encircling the connecting wire.

- **Surface 1**: a flat disk that intersects the wire directly. Current $I$ flows through this surface, so Ampère's law gives $\oint\vec{B}\cdot d\vec{l} = \mu_0 I$.
- **Surface 2**: a "balloon-shaped" surface bulging between the capacitor plates, bounded by the same loop but passing *between* the plates rather than through the wire. No conduction current crosses this surface (the plates are separated by an insulating gap), so Ampère's law would give $\oint\vec{B}\cdot d\vec{l} = 0$.

Both surfaces share the identical boundary loop, so Ampère's law must give the same result for both — yet naively it does not. This contradiction reveals that the original Ampère's law is incomplete for non-steady-state situations.

### Maxwell's Resolution: The Displacement Current

Maxwell proposed that a *changing electric field* between the capacitor plates acts as a source of magnetic field, just as conduction current does — even though no actual charge crosses the gap. He introduced the **displacement current** $I_d$, defined via the rate of change of electric flux $\Phi_E$ through the surface:

$$I_d = \epsilon_0 \frac{d\Phi_E}{dt} = \epsilon_0 \frac{d}{dt}\int \vec{E}\cdot d\vec{A}$$

This term is added to the conduction current in Ampère's law, giving the **Ampère–Maxwell law**:

$$\oint \vec{B}\cdot d\vec{l} = \mu_0 I_{enc} + \mu_0\epsilon_0\frac{d\Phi_E}{dt}$$

or equivalently:

$$\oint \vec{B}\cdot d\vec{l} = \mu_0(I_{enc} + I_d)$$

### Resolving the Paradox

**Example (continued)**

Between the capacitor plates, the electric field is $E = \sigma/\epsilon_0 = Q/(\epsilon_0 A)$, where $Q$ is the instantaneous plate charge and $A$ is the plate area. The electric flux through the bulging surface (area $A$, field uniform and perpendicular) is:

$$\Phi_E = EA = \frac{Q}{\epsilon_0}$$

The displacement current through this surface is:

$$I_d = \epsilon_0\frac{d\Phi_E}{dt} = \epsilon_0 \cdot \frac{1}{\epsilon_0}\frac{dQ}{dt} = \frac{dQ}{dt}$$

Since $dQ/dt$ is exactly the conduction current $I$ charging the capacitor, we find $I_d = I$. Thus:

- Surface 1 (through the wire): $\oint\vec{B}\cdot d\vec{l} = \mu_0 I_{enc} = \mu_0 I$
- Surface 2 (between the plates): $\oint\vec{B}\cdot d\vec{l} = \mu_0 I_d = \mu_0 I$

Both surfaces now give identical results, and the contradiction is resolved. The magnetic field circulating around the wire connects smoothly and consistently to the field circulating around the region between the plates.

### Displacement Current Density

It is often convenient to define a displacement current *density*, analogous to conduction current density $\vec{J}$:

$$\vec{J}_d = \epsilon_0\frac{\partial \vec{E}}{\partial t}$$

so that $I_d = \int \vec{J}_d \cdot d\vec{A}$. This allows the Ampère–Maxwell law to be written in differential (point) form:

$$\nabla\times\vec{B} = \mu_0\vec{J} + \mu_0\epsilon_0\frac{\partial\vec{E}}{\partial t}$$

**Key Points**

- The displacement current is *not* a flow of charge — no actual charges move across the capacitor gap. It is a mathematical and physical construct representing how a changing electric field generates a magnetic field, symmetric to how a changing magnetic field generates an electric field (Faraday's law).
- $\vec{J}_d$ has the same units as conduction current density (A/m²) and enters Ampère's law with exactly the same weighting ($\mu_0$), meaning it is equally effective at producing magnetic fields.
- In a good conductor carrying a time-varying current, the conduction current density typically vastly exceeds the displacement current density at low frequencies, so $I_d$ is only significant in specific circumstances (vacuum/dielectric gaps, high-frequency fields, wave propagation).

### Why This Was a Landmark Theoretical Step

**Key Points**

- The displacement current term was not required by any pre-existing experimental discrepancy in the 1860s; Maxwell introduced it on grounds of mathematical and physical consistency (charge conservation, continuity equation) rather than from a direct new measurement forcing the correction.
- Taking the divergence of the Ampère–Maxwell law and combining with Gauss's law shows the modified equation is fully consistent with the continuity equation $\nabla\cdot\vec{J} + \frac{\partial\rho}{\partial t} = 0$, which express local conservation of electric charge — whereas the original Ampère's law (without $I_d$) violates this consistency in time-varying situations.
- This addition completed the set of four Maxwell's equations, and critically, it is the term that permits self-sustaining electromagnetic wave propagation: a changing $\vec{E}$ creates a $\vec{B}$ (via displacement current), and a changing $\vec{B}$ creates an $\vec{E}$ (via Faraday's law), allowing the fields to regenerate each other and propagate through empty space without any charges or currents present at all.

### Connection to Electromagnetic Waves

Without the displacement current term, Maxwell's equations in vacuum (no charges, no currents) would reduce to $\nabla\times\vec{B} = 0$, which cannot support wave propagation. With the displacement current included, the coupled curl equations in vacuum become:

$$\nabla\times\vec{E} = -\frac{\partial\vec{B}}{\partial t}, \qquad \nabla\times\vec{B} = \mu_0\epsilon_0\frac{\partial\vec{E}}{\partial t}$$

Combining these (via the vector identity for the curl of a curl) yields a wave equation for $\vec{E}$ (and similarly for $\vec{B}$):

$$\nabla^2\vec{E} = \mu_0\epsilon_0\frac{\partial^2\vec{E}}{\partial t^2}$$

Comparing to the standard wave equation $\nabla^2\vec{E} = \frac{1}{v^2}\frac{\partial^2\vec{E}}{\partial t^2}$ identifies the wave speed:

$$v = \frac{1}{\sqrt{\mu_0\epsilon_0}} = c$$

Substituting known values of $\mu_0 = 4\pi\times10^{-7}\ \text{T·m/A}$ and $\epsilon_0 = 8.854\times10^{-12}\ \text{F/m}$ gives $v \approx 3\times10^8\ \text{m/s}$ — the speed of light. This was one of the most significant theoretical results in physics: it showed that light itself is an electromagnetic wave, unifying optics with electricity and magnetism.

### Field Lines Between Capacitor Plates (svg_diagram)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 500 260">
<text x="250" y="24" font-size="16" text-anchor="middle" fill="#222">Displacement Current Between Capacitor Plates (svg_diagram)</text>
<line x1="150" y1="60" x2="150" y2="200" stroke="#1a5276" stroke-width="6" />
<line x1="350" y1="60" x2="350" y2="200" stroke="#1a5276" stroke-width="6" />
<text x="150" y="215" font-size="12" text-anchor="middle" fill="#1a5276">+Q</text>
<text x="350" y="215" font-size="12" text-anchor="middle" fill="#1a5276">−Q</text>
<line x1="170" y1="90" x2="330" y2="90" stroke="#a04000" stroke-width="2" marker-end="url(arrowE)" />
<line x1="170" y1="130" x2="330" y2="130" stroke="#a04000" stroke-width="2" marker-end="url(arrowE)" />
<line x1="170" y1="170" x2="330" y2="170" stroke="#a04000" stroke-width="2" marker-end="url(arrowE)" />
<text x="250" y="115" font-size="12" text-anchor="middle" fill="#a04000">E increasing (dE/dt)</text>
<ellipse cx="250" cy="130" rx="80" ry="45" fill="none" stroke="#27ae60" stroke-width="2" stroke-dasharray="5,4" />
<text x="250" y="70" font-size="12" text-anchor="middle" fill="#27ae60">Amperian loop (bulging surface)</text>
<text x="90" y="90" font-size="12" fill="#333">→ I (wire)</text>
<line x1="60" y1="95" x2="145" y2="95" stroke="#333" stroke-width="3" marker-end="url(arrowI)" />
<text x="250" y="245" font-size="13" text-anchor="middle" fill="#333">I_d = ε₀ dΦ_E/dt produces B field consistent with I in the wire</text>
</svg>

### Worked Numerical Example

**Example**

A parallel-plate capacitor with circular plates of radius $R = 3\ \text{cm}$ is being charged such that the electric field between the plates increases at a rate $dE/dt = 1\times10^{12}\ \text{V/(m·s)}$. Find the magnetic field at radius $r = 2\ \text{cm}$ from the central axis, inside the plate region.

Since $r < R$, only the enclosed fraction of displacement current contributes. Using the symmetry of the Ampère–Maxwell law (analogous to a uniform current density case):

$$I_{d,enc} = \epsilon_0\frac{dE}{dt}\pi r^2$$



$$I_{d,enc} = (8.854\times10^{-12})(1\times10^{12})\pi(0.02)^2 \approx 1.113\times10^{-2}\ \text{A}$$

Applying Ampère's law with cylindrical symmetry, $B(2\pi r) = \mu_0 I_{d,enc}$:

$$B = \frac{\mu_0 I_{d,enc}}{2\pi r} = \frac{(4\pi\times10^{-7})(1.113\times10^{-2})}{2\pi(0.02)} \approx 1.11\times10^{-7}\ \text{T}$$

This confirms that a changing electric field alone, with no conduction current present at that location, produces a genuine, measurable magnetic field — precisely Maxwell's prediction.

### Common Pitfalls

**Key Points**

- Interpreting displacement current as literal moving charge between capacitor plates — it is not; it is a flux-based term standing in for the physical effect of $I_{enc}$ in regions with no actual current flow.
- Forgetting to include $I_d$ when applying Ampère's law to any surface not pierced by a physical wire, especially inside capacitors or in free space — leads to inconsistent/wrong results if the chosen surface passes through a region of changing $E$.
- Assuming displacement current is negligible in *all* practical circuits: while true in typical low-frequency conduction wires (where $J \gg J_d$), it becomes essential and dominant in capacitor gaps, dielectrics, and at optical/RF frequencies, and is indispensable for electromagnetic wave propagation in vacuum where $J = 0$ everywhere.
- Confusing the displacement current's role in generating $\vec{B}$ (Ampère–Maxwell law) with Faraday's law's role in generating $\vec{E}$ from changing $\vec{B}$ — the two are complementary, not interchangeable, halves of the electromagnetic wave mechanism.

**Next Steps**

- Maxwell's Equations: Integral and Differential Forms
- Faraday's Law and Induced Electric Fields
- The Electromagnetic Wave Equation and Derivation
- Poynting Vector and Electromagnetic Energy Flow
- Boundary Conditions for E and B Fields at Interfaces
- Electromagnetic Waves in Dielectric and Conducting Media
- Radiation from Oscillating Charges and Antennas
- Gauss's Law for Electric and Magnetic Fields