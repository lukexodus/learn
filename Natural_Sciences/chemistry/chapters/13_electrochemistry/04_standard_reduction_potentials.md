## Standard Reduction Potentials


### Definition and Core Concept

A standard reduction potential ($E^\circ$) is a quantitative measure of the tendency of a chemical species to be reduced (gain electrons), measured under standard conditions: $1\,M$ concentration for solutes, $1\,atm$ pressure for gases, pure solids/liquids at unit activity, and typically $25°C$ ($298\,K$). It is measured in volts ($V$) and is always reported as a reduction half-reaction, by convention, even for species more commonly encountered as oxidants in practice.

A higher (more positive) $E^\circ$ indicates a greater tendency for the species to be reduced — i.e., it is a stronger oxidizing agent. A lower (more negative) $E^\circ$ indicates a weaker tendency to be reduced — i.e., the reduced form is a stronger reducing agent.

### The Standard Hydrogen Electrode (SHE)

Because absolute electrode potentials cannot be measured directly (only potential *differences* between two electrodes are measurable), all standard reduction potentials are defined relative to a reference: the standard hydrogen electrode.

$$2H^+(aq, 1M) + 2e^- \rightarrow H_2(g, 1\,atm) \quad E^\circ = 0.00\,V \text{ (by definition)}$$

**SHE construction:** a platinum electrode (chemically inert, catalytically active) immersed in $1\,M\,H^+(aq)$ solution, with $H_2$ gas bubbled over the electrode at $1\,atm$ pressure. Platinum is coated with platinum black to increase surface area and catalytic efficiency.

Every other standard reduction potential in reference tables is measured by constructing a galvanic cell pairing the species of interest against the SHE and measuring the resulting cell voltage.

### The Electrochemical Series

The electrochemical series (activity series) is a ranked table of standard reduction potentials, ordered from most positive (strongest oxidizing agents / most easily reduced) to most negative (strongest reducing agents / most easily oxidized, or equivalently, their reduced/metallic forms are the strongest reducing agents).

**Representative values (standard reduction potentials, $25°C$):**

| Half-Reaction | $E^\circ$ (V) |
| --- | --- |
| $F_2(g) + 2e^- \rightarrow 2F^-(aq)$ | $+2.87$ |
| $MnO_4^-(aq) + 8H^+ + 5e^- \rightarrow Mn^{2+}(aq) + 4H_2O$ | $+1.51$ |
| $Cl_2(g) + 2e^- \rightarrow 2Cl^-(aq)$ | $+1.36$ |
| $O_2(g) + 4H^+ + 4e^- \rightarrow 2H_2O$ | $+1.23$ |
| $Ag^+(aq) + e^- \rightarrow Ag(s)$ | $+0.80$ |
| $Cu^{2+}(aq) + 2e^- \rightarrow Cu(s)$ | $+0.34$ |
| $2H^+(aq) + 2e^- \rightarrow H_2(g)$ | $0.00$ (reference) |
| $Pb^{2+}(aq) + 2e^- \rightarrow Pb(s)$ | $-0.13$ |
| $Fe^{2+}(aq) + 2e^- \rightarrow Fe(s)$ | $-0.44$ |
| $Zn^{2+}(aq) + 2e^- \rightarrow Zn(s)$ | $-0.76$ |
| $Al^{3+}(aq) + 3e^- \rightarrow Al(s)$ | $-1.66$ |
| $Na^+(aq) + e^- \rightarrow Na(s)$ | $-2.71$ |
| $Li^+(aq) + e^- \rightarrow Li(s)$ | $-3.04$ |

[Unverified: precise tabulated values vary slightly (typically ±0.01–0.02 V) between reference sources depending on measurement methodology and activity coefficient conventions]

**Key interpretive rules:**

- Species at the top of the table (most positive $E^\circ$, e.g., $F_2$) are the strongest oxidizing agents
- Species at the bottom of the table (most negative $E^\circ$, e.g., $Li^+$) have reduced forms (e.g., $Li$ metal) that are the strongest reducing agents
- Any species on the left side of a half-reaction can spontaneously oxidize any species on the right side of a half-reaction with a *more negative* $E^\circ$

### Using the Table to Predict Spontaneity

A reaction combining two half-reactions is spontaneous under standard conditions if the resulting $E^\circ_{cell}$ is positive.

$$E^\circ_{cell} = E^\circ_{cathode(reduction)} - E^\circ_{anode(oxidation)}$$

The half-reaction with the higher (more positive) $E^\circ$ proceeds as written (reduction, cathode); the half-reaction with the lower (more negative) $E^\circ$ is reversed (oxidation, anode).

**Worked example:** Will silver ions spontaneously oxidize copper metal?

$$Ag^+ + e^- \rightarrow Ag \quad E^\circ = +0.80\,V$$



$$Cu^{2+} + 2e^- \rightarrow Cu \quad E^\circ = +0.34\,V$$

Since $Ag^+/Ag$ has the higher $E^\circ$, it acts as the cathode (reduction); $Cu/Cu^{2+}$ is reversed as the anode (oxidation):

$$Cu(s) \rightarrow Cu^{2+}(aq) + 2e^- \quad (\times 1)$$



$$Ag^+(aq) + e^- \rightarrow Ag(s) \quad (\times 2, \text{ to balance electrons})$$



$$Cu(s) + 2Ag^+(aq) \rightarrow Cu^{2+}(aq) + 2Ag(s)$$



$$E^\circ_{cell} = (+0.80\,V) - (+0.34\,V) = +0.46\,V$$

Positive $E^\circ_{cell}$ confirms the reaction is spontaneous — copper metal reduces silver ions.

**Important:** $E^\circ$ is an intensive property and does not depend on the stoichiometric coefficients used. Multiplying the silver half-reaction by 2 (to balance electrons) does *not* double its $E^\circ$ value — it remains $+0.80\,V$.

### Relationship to Thermodynamics

Standard reduction potentials connect directly to Gibbs free energy and equilibrium constants via the relationships established in galvanic cell theory:

$$\Delta G^\circ = -nFE^\circ_{cell}$$



$$E^\circ_{cell} = \frac{RT}{nF}\ln K = \frac{0.0592\,V}{n}\log K \quad (\text{at } 298\,K)$$

A large positive $E^\circ_{cell}$ corresponds to a large negative $\Delta G^\circ$ and a large equilibrium constant $K \gg 1$, meaning the reaction proceeds essentially to completion.

### Predicting Reaction Feasibility (Activity Series Applications)

The electrochemical series directly explains and predicts single-replacement (displacement) reactions:

**Metal displacement:** a metal will displace a less active metal from solution if its $E^\circ$ (reduction) is more negative (i.e., it is more easily oxidized).

$$Fe(s) + CuSO_4(aq) \rightarrow FeSO_4(aq) + Cu(s) \quad \text{(spontaneous, since } E^\circ_{Fe^{2+}/Fe} < E^\circ_{Cu^{2+}/Cu}\text{)}$$



$$Cu(s) + FeSO_4(aq) \rightarrow \text{no reaction} \quad \text{(non-spontaneous, reverse direction)}$$

**Halogen displacement:** more oxidizing halogens (higher $E^\circ$) displace less oxidizing halide ions from solution.

$$Cl_2(g) + 2NaBr(aq) \rightarrow 2NaCl(aq) + Br_2(l) \quad \text{(spontaneous, } E^\circ_{Cl_2/Cl^-} > E^\circ_{Br_2/Br^-}\text{)}$$

**Reactivity with acids:** metals with $E^\circ < 0$ (more negative than the $H^+/H_2$ reference) can typically reduce $H^+$ from dilute acids, releasing $H_2$ gas; metals with $E^\circ > 0$ generally cannot.

$$Zn(s) + 2HCl(aq) \rightarrow ZnCl_2(aq) + H_2(g) \quad \text{(spontaneous, } E^\circ_{Zn^{2+}/Zn} = -0.76\,V < 0\text{)}$$



$$Cu(s) + HCl(aq) \rightarrow \text{no reaction} \quad \text{(} E^\circ_{Cu^{2+}/Cu} = +0.34\,V > 0\text{)}$$

### Electrochemical Series Diagram (svg_diagram)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 600 420">
<text x="300" y="26" text-anchor="middle" font-size="17" font-weight="bold" fill="#1a1a1a">Standard Reduction Potential Scale (svg_diagram)</text>
<line x1="150" y1="50" x2="150" y2="390" stroke="#000" stroke-width="2" />
<line x1="140" y1="65" x2="160" y2="65" stroke="#000" stroke-width="2" />
<text x="170" y="70" font-size="12" fill="#1a1a1a">+2.87 V — F₂ (strongest oxidizer)</text>
<line x1="140" y1="110" x2="160" y2="110" stroke="#000" stroke-width="2" />
<text x="170" y="115" font-size="12" fill="#1a1a1a">+1.36 V — Cl₂</text>
<line x1="140" y1="155" x2="160" y2="155" stroke="#000" stroke-width="2" />
<text x="170" y="160" font-size="12" fill="#1a1a1a">+0.80 V — Ag⁺</text>
<line x1="140" y1="200" x2="160" y2="200" stroke="#000" stroke-width="2" />
<text x="170" y="205" font-size="12" fill="#1a1a1a">+0.34 V — Cu²⁺</text>
<line x1="140" y1="245" x2="160" y2="245" stroke="#b91c1c" stroke-width="3" />
<text x="170" y="250" font-size="12" font-weight="bold" fill="#b91c1c">0.00 V — H⁺ (reference, SHE)</text>
<line x1="140" y1="290" x2="160" y2="290" stroke="#000" stroke-width="2" />
<text x="170" y="295" font-size="12" fill="#1a1a1a">−0.76 V — Zn²⁺</text>
<line x1="140" y1="335" x2="160" y2="335" stroke="#000" stroke-width="2" />
<text x="170" y="340" font-size="12" fill="#1a1a1a">−2.71 V — Na⁺</text>
<line x1="140" y1="378" x2="160" y2="378" stroke="#000" stroke-width="2" />
<text x="170" y="383" font-size="12" fill="#1a1a1a">−3.04 V — Li⁺ (weakest oxidizer)</text>
<path d="M 60 60 L 60 385" stroke="#7c2d12" stroke-width="3" marker-end="url(#arrowDown)" />
<text x="30" y="220" font-size="12" fill="#7c2d12" transform="rotate(-90 30 220)">Increasing reducing strength</text>
</svg>

### Limitations of Standard Reduction Potential Predictions

- **Thermodynamic vs. kinetic feasibility**: a positive $E^\circ_{cell}$ predicts thermodynamic spontaneity but says nothing about reaction rate — some thermodynamically favorable reactions proceed too slowly to observe (kinetic inhibition, e.g., high activation energy)
- **Non-standard conditions**: real systems rarely match $1\,M$/$1\,atm$/$25°C$ exactly; the Nernst equation must be applied for accurate predictions under actual conditions
- **Overpotential**: in practice (especially electrolysis), the voltage required to drive a reaction can exceed the theoretical $E^\circ$ value due to kinetic barriers at the electrode surface [Inference: this is a well-documented phenomenon in electrochemistry, particularly relevant to gas-evolving electrode reactions such as $O_2$ and $H_2$ formation]
- **Concentration and pH dependence**: many half-reactions involve $H^+$ or $OH^-$ explicitly, so actual potential shifts significantly with pH, as captured by the Nernst equation

### Common Errors and Misconceptions

- Treating $E^\circ$ as additive when combining half-reactions in series (it is not — only $\Delta G^\circ$ values are additive; $E^\circ$ requires the cathode-minus-anode formula)
- Multiplying $E^\circ$ by stoichiometric coefficients when balancing electron transfer (never scale $E^\circ$ itself)
- Confusing standard reduction potential with standard oxidation potential — always look up and use reduction values, reversing the sign only when explicitly writing the reverse (oxidation) half-reaction
- Assuming a very negative $E^\circ$ reaction cannot occur at all — it simply means the reverse (oxidation) direction is favored; both directions are chemically possible, just not both spontaneous under standard conditions simultaneously
- Ignoring that solid/liquid/pure-phase species do not appear in the Nernst equation's reaction quotient, even though their identity affects which half-reaction applies

**Related Topics**

- Nernst equation and potential under non-standard conditions
- Galvanic cells and standard cell potential calculations
- Relationship between $E^\circ_{cell}$, $\Delta G^\circ$, and equilibrium constant $K$
- Electrolytic cells and overpotential
- Activity series and predicting displacement reactions
- Concentration cells