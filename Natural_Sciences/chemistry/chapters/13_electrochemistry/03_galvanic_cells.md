## Galvanic Cells


### Definition and Core Concept

A galvanic cell (also called a voltaic cell) is an electrochemical device that converts spontaneous chemical energy from a redox reaction into electrical energy. The defining feature is the physical separation of oxidation and reduction half-reactions into two compartments (half-cells), forcing electrons to flow through an external circuit rather than transferring directly between species in solution.

Because the underlying reaction is spontaneous, a galvanic cell has a positive cell potential ($E^\circ_{cell} > 0$) and can perform electrical work without an external power source.

### Structure of a Galvanic Cell

**Components:**

- **Anode**: the electrode where oxidation occurs; electrons are released into the external circuit. In a galvanic cell, the anode is the negative terminal.
- **Cathode**: the electrode where reduction occurs; electrons are consumed from the external circuit. In a galvanic cell, the cathode is the positive terminal.
- **Electrolyte**: an ionic solution surrounding each electrode that maintains electrical neutrality and allows ion conduction
- **Salt bridge**: a tube containing an inert electrolyte (e.g., $KNO_3$, $KCl$) connecting the two half-cells; it allows ion migration to balance charge without allowing the solutions to mix directly
- **External wire**: conducts electrons from anode to cathode, powering an external load (light bulb, voltmeter, motor)

**Mnemonic**: **A**node = **A**lphabetically first = **O**xidation (AnOx); **C**athode = **R**eduction (RedCat). Also: electrons flow from anode to cathode through the external circuit ("Red Cat, An Ox").

### Example: The Daniell Cell

The classic zinc-copper galvanic cell:

**Half-reactions:**

$$\text{Anode (oxidation): } Zn(s) \rightarrow Zn^{2+}(aq) + 2e^-$$



$$\text{Cathode (reduction): } Cu^{2+}(aq) + 2e^- \rightarrow Cu(s)$$

**Overall reaction:**

$$Zn(s) + Cu^{2+}(aq) \rightarrow Zn^{2+}(aq) + Cu(s)$$

As the reaction proceeds, the zinc electrode loses mass (dissolves into solution as $Zn^{2+}$), while the copper electrode gains mass (as $Cu^{2+}$ ions deposit as solid $Cu$). Electrons flow through the external wire from the zinc electrode to the copper electrode, and the salt bridge allows anions to migrate toward the anode compartment and cations toward the cathode compartment, preventing charge buildup.

### Cell Notation (Line Notation)

A standardized shorthand represents the cell configuration without drawing the full diagram.

**Convention:**

$$\text{Anode} \, | \, \text{Anode solution} \, || \, \text{Cathode solution} \, | \, \text{Cathode}$$

- Single vertical line ($|$) represents a phase boundary (e.g., solid–solution interface)
- Double vertical line ($||$) represents the salt bridge
- Species within the same phase are separated by commas
- Concentrations are typically specified in parentheses if non-standard

**Example (Daniell cell):**

$$Zn(s) \, | \, Zn^{2+}(aq, 1M) \, || \, Cu^{2+}(aq, 1M) \, | \, Cu(s)$$

**Example with an inert electrode** (e.g., a hydrogen half-cell using platinum, since $H_2$ gas is not itself conductive as a solid electrode):

$$Pt(s) \, | \, H_2(g, 1 atm) \, | \, H^+(aq, 1M) \, || \, Cu^{2+}(aq, 1M) \, | \, Cu(s)$$

### Standard Reduction Potentials

Each half-reaction has an associated standard reduction potential ($E^\circ$), measured in volts, relative to the standard hydrogen electrode (SHE), which is defined as exactly $0 V$.

$$2H^+(aq, 1M) + 2e^- \rightarrow H_2(g, 1 atm) \quad E^\circ = 0.00\,V$$

**Calculating standard cell potential:**

$$E^\circ_{cell} = E^\circ_{cathode} - E^\circ_{anode}$$

where both values are taken from a standard reduction potential table (i.e., both are looked up as *reduction* potentials, regardless of which electrode is actually undergoing oxidation in the cell).

**Worked example:** Given $E^\circ(Cu^{2+}/Cu) = +0.34\,V$ and $E^\circ(Zn^{2+}/Zn) = -0.76\,V$, calculate $E^\circ_{cell}$ for the Daniell cell.

Copper is reduced (cathode), zinc is oxidized (anode):

$$E^\circ_{cell} = E^\circ_{cathode} - E^\circ_{anode} = (+0.34\,V) - (-0.76\,V) = +1.10\,V$$

A positive $E^\circ_{cell}$ confirms the reaction is spontaneous under standard conditions, consistent with a functioning galvanic cell.

### Relationship to Gibbs Free Energy and Equilibrium Constant

Standard cell potential connects directly to thermodynamic spontaneity and equilibrium.

$$\Delta G^\circ = -nFE^\circ_{cell}$$

where $n$ = moles of electrons transferred, $F$ = Faraday constant ($96{,}485\,C/mol$).

$$\Delta G^\circ = -RT\ln K$$

Combining these relationships:

$$E^\circ_{cell} = \frac{RT}{nF}\ln K$$

At $298\,K$, this simplifies (using $\log_{10}$) to:

$$E^\circ_{cell} = \frac{0.0592\,V}{n}\log K$$

**Worked example:** For the Daniell cell ($n=2$, $E^\circ_{cell}=1.10\,V$), estimate $\Delta G^\circ$.

$$\Delta G^\circ = -nFE^\circ_{cell} = -(2)(96{,}485\,C/mol)(1.10\,V) \approx -212{,}267\,J/mol \approx -212.3\,kJ/mol$$

The large negative $\Delta G^\circ$ confirms strong spontaneity, and by extension a large equilibrium constant favoring products.

### Nernst Equation — Non-Standard Conditions

Real cells rarely operate under standard 1 M, 1 atm, 25°C conditions. The Nernst equation adjusts cell potential for actual concentrations and pressures.

$$E_{cell} = E^\circ_{cell} - \frac{RT}{nF}\ln Q$$

At $298\,K$, using $\log_{10}$:

$$E_{cell} = E^\circ_{cell} - \frac{0.0592\,V}{n}\log Q$$

where $Q$ is the reaction quotient for the overall cell reaction.

**Worked example:** Calculate $E_{cell}$ for the Daniell cell if $[Zn^{2+}] = 0.010\,M$ and $[Cu^{2+}] = 2.0\,M$.

$$Q = \frac{[Zn^{2+}]}{[Cu^{2+}]} = \frac{0.010}{2.0} = 0.005$$



$$E_{cell} = 1.10\,V - \frac{0.0592}{2}\log(0.005)$$



$$E_{cell} = 1.10\,V - (0.0296)(-2.301) \approx 1.10\,V + 0.068\,V \approx 1.168\,V$$

Lower product-ion concentration and higher reactant-ion concentration relative to standard conditions increases the cell potential above $E^\circ_{cell}$, consistent with Le Chatelier's principle favoring forward reaction.

### Galvanic Cell Diagram (svg_diagram)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 700 380">
<text x="350" y="26" text-anchor="middle" font-size="17" font-weight="bold" fill="#1a1a1a">Daniell Cell — Galvanic Cell Structure (svg_diagram)</text>
<rect x="60" y="70" width="220" height="220" fill="#e0f2fe" stroke="#0369a1" stroke-width="2" />
<text x="170" y="60" text-anchor="middle" font-size="13" fill="#1a1a1a">Anode Half-Cell</text>
<rect x="150" y="90" width="40" height="160" fill="#94a3b8" stroke="#334155" stroke-width="2" />
<text x="170" y="270" text-anchor="middle" font-size="13" fill="#1a1a1a">Zn(s)</text>
<text x="170" y="200" text-anchor="middle" font-size="12" fill="#1a1a1a" transform="rotate(-90 170 200)">Zn electrode</text>
<text x="170" y="310" text-anchor="middle" font-size="12" fill="#1a1a1a">ZnSO₄ solution</text>
<rect x="420" y="70" width="220" height="220" fill="#fef3c7" stroke="#b45309" stroke-width="2" />
<text x="530" y="60" text-anchor="middle" font-size="13" fill="#1a1a1a">Cathode Half-Cell</text>
<rect x="510" y="90" width="40" height="160" fill="#f97316" stroke="#7c2d12" stroke-width="2" />
<text x="530" y="270" text-anchor="middle" font-size="13" fill="#1a1a1a">Cu(s)</text>
<text x="530" y="310" text-anchor="middle" font-size="12" fill="#1a1a1a">CuSO₄ solution</text>
<path d="M 280 180 Q 350 130 420 180" stroke="#374151" stroke-width="8" fill="none" />
<text x="350" y="130" text-anchor="middle" font-size="12" fill="#1a1a1a">Salt Bridge (KNO₃)</text>
<line x1="170" y1="90" x2="170" y2="40" stroke="#000" stroke-width="2" />
<line x1="530" y1="90" x2="530" y2="40" stroke="#000" stroke-width="2" />
<line x1="170" y1="40" x2="530" y2="40" stroke="#000" stroke-width="2" marker-end="url(#arrowE)" />
<circle cx="350" cy="40" r="14" fill="#fff" stroke="#000" stroke-width="2" />
<text x="350" y="45" text-anchor="middle" font-size="12" font-weight="bold" fill="#1a1a1a">V</text>
<text x="250" y="30" text-anchor="middle" font-size="12" fill="#1a1a1a">e⁻ flow</text>

<text x="170" y="330" text-anchor="middle" font-size="13" font-weight="bold" fill="`#1a1a1a`">Oxidation: Zn → Zn²⁺ + 2e⁻</text>

<text x="530" y="330" text-anchor="middle" font-size="13" font-weight="bold" fill="`#1a1a1a`">Reduction: Cu²⁺ + 2e⁻ → Cu</text>

<text x="170" y="355" text-anchor="middle" font-size="12" fill="`#1a1a1a`">(−) Negative terminal</text>

<text x="530" y="355" text-anchor="middle" font-size="12" fill="`#1a1a1a`">(+) Positive terminal</text>

</svg>

### Galvanic vs. Electrolytic Cells (Comparison)

| Property | Galvanic Cell | Electrolytic Cell |
| --- | --- | --- |
| Reaction spontaneity | Spontaneous ($\Delta G < 0$) | Non-spontaneous ($\Delta G > 0$) |
| $E_{cell}$ | Positive | Negative (requires applied voltage to overcome) |
| Energy conversion | Chemical → Electrical | Electrical → Chemical |
| Anode charge | Negative | Positive |
| Cathode charge | Positive | Negative |
| Example | Battery, fuel cell | Electrolysis of water, electroplating |

Note: in both cell types, oxidation always occurs at the anode and reduction always occurs at the cathode — only the terminal polarity and spontaneity direction differ.

### Practical Applications

- **Primary (disposable) batteries**: alkaline cells, zinc-carbon cells — single-use galvanic cells
- **Secondary (rechargeable) batteries**: lead-acid batteries, lithium-ion cells — galvanic during discharge, electrolytic during recharge
- **Fuel cells**: continuous-feed galvanic cells (e.g., hydrogen-oxygen fuel cells) that convert fuel and oxidant directly to electricity
- **Corrosion protection**: sacrificial anode systems exploit galvanic principles, using a more easily oxidized metal (e.g., $Mg$ or $Zn$) to protect a structural metal (e.g., $Fe$)
- **Reference electrodes**: standardized half-cells (e.g., SHE, calomel electrode) used for potentiometric measurements in analytical chemistry

### Common Errors and Misconceptions

- Reversing anode/cathode polarity — remembering that the galvanic cell anode is negative (opposite of the electrolytic cell convention) is a frequent source of confusion
- Forgetting that the salt bridge conducts ions, not electrons — electron flow is confined to the external circuit only
- Misapplying the Nernst equation by using concentrations of pure solids or liquids (these are omitted from $Q$, as their activity is defined as 1)
- Calculating $E^\circ_{cell}$ as a simple sum instead of $E^\circ_{cathode} - E^\circ_{anode}$
- Assuming $E^\circ_{cell}$ changes with the stoichiometric coefficients used to balance the equation — $E^\circ$ is an intensive property and is unaffected by multiplying the reaction through by an integer (only $n$ in $\Delta G^\circ = -nFE^\circ$ scales)

**Related Topics**

- Standard reduction potentials and the electrochemical series
- Nernst equation applications (concentration cells, pH measurement)
- Electrolytic cells and Faraday's laws of electrolysis
- Battery technology (lead-acid, lithium-ion, fuel cells)
- Corrosion and cathodic protection
- Relationship between $\Delta G^\circ$, $E^\circ_{cell}$, and equilibrium constant $K$