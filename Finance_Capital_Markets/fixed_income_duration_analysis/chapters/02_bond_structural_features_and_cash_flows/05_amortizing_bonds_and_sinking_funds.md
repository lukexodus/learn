## Amortizing Bonds and Sinking Funds

### Core Concept

Most plain-vanilla bonds are **bullet bonds** — the full face value is repaid in a single lump sum at maturity, with only interest (coupon) paid periodically until then. Amortizing bonds and sinking fund provisions are structural alternatives in which some or all of the principal is repaid *before* the final maturity date, according to a predetermined schedule. This fundamentally changes the cash flow profile, the effective life of the bond, and its interest rate risk characteristics relative to a bullet bond of the same stated maturity.

### Amortizing Bonds

**Definition:** A bond structure in which each periodic payment includes both an interest component and a principal repayment component, progressively reducing the outstanding principal balance over the life of the bond — analogous to a fully amortizing mortgage or auto loan.

**Two主要 structures:**

| Type | Principal Repayment Pattern | Coupon Payment Pattern |
| --- | --- | --- |
| Fully amortizing | Principal fully repaid by maturity via scheduled payments | Declines over time (as outstanding balance shrinks) |
| Partially amortizing | Only part of principal repaid via schedule; remainder due as balloon payment at maturity | Declines over time, then balloon at maturity |

**Level-payment amortization (most common for consumer-style structures):**

Each payment $A$ is constant in total, but its split between interest and principal shifts over time:

$$A = \frac{P_0 \times r}{1 - (1+r)^{-n}}$$

Where:

- $P_0$ = original principal
- $r$ = periodic interest rate
- $n$ = number of payment periods

At each period $t$, the interest portion is $r \times P_{t-1}$ (balance-dependent), and the principal portion is $A - r \times P_{t-1}$ — meaning early payments are interest-heavy and later payments are principal-heavy.

**Example:**

A $100,000 amortizing bond, 5-year term, annual payments, 6% annual rate:

$$A = \frac{100{,}000 \times 0.06}{1 - (1.06)^{-5}} \approx \$23{,}739.64$$

| Year | Beginning Balance | Payment | Interest | Principal | Ending Balance |
| --- | --- | --- | --- | --- | --- |
| 1 | 100,000.00 | 23,739.64 | 6,000.00 | 17,739.64 | 82,260.36 |
| 2 | 82,260.36 | 23,739.64 | 4,935.62 | 18,804.02 | 63,456.34 |
| 3 | 63,456.34 | 23,739.64 | 3,807.38 | 19,932.26 | 43,524.08 |
| 4 | 43,524.08 | 23,739.64 | 2,611.44 | 21,128.20 | 22,395.88 |
| 5 | 22,395.88 | 23,739.64 | 1,343.75 | 22,395.89 | ~0.00 |

**Why this matters for risk analysis:**

Because principal is returned progressively rather than in one lump sum at the end, an amortizing bond has a shorter effective (weighted-average) life and lower duration than a bullet bond with the same final maturity date — cash is returned to the investor earlier on average, reducing sensitivity to interest rate changes.

### Sinking Fund Provisions

**Definition:** A contractual requirement embedded in a bond indenture obligating the issuer to retire a portion of the bond issue's principal periodically before final maturity, typically by either (a) making cash payments into a fund used to redeem bonds, or (b) directly calling/repurchasing a specified percentage of the outstanding bonds each period.

**Mechanisms issuers use to satisfy sinking fund requirements:**

| Mechanism | Description |
| --- | --- |
| Cash payment to trustee | Issuer deposits funds; trustee retires bonds via lottery/pro-rata call at par (or a specified sinking fund call price) |
| Open-market purchase | Issuer buys back bonds in the secondary market to satisfy the requirement, especially attractive if bonds trade below the sinking fund call price |
| Delivery of bonds | Issuer physically delivers previously-acquired bonds to the trustee for cancellation |

**Purpose (why issuers include sinking funds):**

- Reduces credit risk to bondholders by ensuring gradual, orderly principal reduction rather than a single large repayment burden at maturity (reduces "refinancing risk" / "balloon risk" for the issuer, which in turn benefits credit quality)
- Signals financial discipline, often resulting in a lower required coupon rate at issuance
- Can create a support mechanism for the bond's secondary market price, since the issuer becomes a periodic buyer

**Key risk to investors — Lottery/Call risk:**

Under a mandatory sinking fund with random-lottery selection, an individual bondholder does not choose whether their specific bonds are called — a random subset of bondholders is selected pro-rata regardless of their preference to continue holding. This introduces uncertainty into any single investor's actual holding period, even though in aggregate the schedule is known.

**Sinking fund call price:**

Typically set at or near par (frequently par exactly), which means investors holding bonds that were purchased at a premium face a risk of loss if their bonds are called at par via the sinking fund lottery — this parallels ordinary call risk but is structurally mandatory rather than issuer-discretionary in timing (though issuers often retain discretion in *which* mechanism to use to satisfy it).

### Diagram: Bullet vs. Amortizing vs. Sinking Fund Principal Repayment Profiles (svg_diagram)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 720 340" font-family="Arial, sans-serif">
<text x="360" y="24" text-anchor="middle" font-size="15" font-weight="bold">Outstanding Principal Over Time (svg_diagram)</text>
<line x1="80" y1="290" x2="660" y2="290" stroke="black" stroke-width="1.5" />
<line x1="80" y1="40" x2="80" y2="290" stroke="black" stroke-width="1.5" />
<text x="370" y="315" text-anchor="middle" font-size="12">Time →</text>
<text x="35" y="165" text-anchor="middle" font-size="12" transform="rotate(-90 35 165)">Outstanding Principal</text>
<line x1="80" y1="60" x2="620" y2="60" stroke="#c0392b" stroke-width="2.5" />
<line x1="620" y1="60" x2="620" y2="290" stroke="#c0392b" stroke-width="2.5" />
<text x="300" y="52" font-size="11" fill="#c0392b">Bullet bond (full repayment at maturity)</text>
<path d="M 80 60 L 200 130 L 320 175 L 440 220 L 560 260 L 620 285" fill="none" stroke="#1a5fb4" stroke-width="2.5" />
<text x="130" y="150" font-size="11" fill="#1a5fb4">Fully amortizing</text>
<path d="M 80 60 L 200 100 L 320 140 L 440 180 L 560 220" fill="none" stroke="#27ae60" stroke-width="2.5" />
<line x1="560" y1="220" x2="620" y2="220" stroke="#27ae60" stroke-width="2.5" />
<line x1="620" y1="220" x2="620" y2="290" stroke="#27ae60" stroke-width="2" stroke-dasharray="5,3" />
<text x="440" y="200" font-size="11" fill="#27ae60">Sinking fund (staged, partial + balloon)</text>
</svg>

### Comparative Structure Table

| Feature | Bullet Bond | Amortizing Bond | Sinking Fund Bond |
| --- | --- | --- | --- |
| Principal repayment timing | 100% at maturity | Progressive, per schedule | Progressive, per schedule (often partial + balloon) |
| Coupon payment pattern | Constant (on full principal) | Declining (on shrinking balance) | Declining on retired portion; constant on remainder |
| Effective/weighted-average life | Equal to stated maturity | Shorter than stated maturity | Shorter than stated maturity |
| Selection of which bonds retired early | N/A | N/A (pro-rata to all holders via structure) | Often random lottery among holders |
| Typical credit impact | N/A baseline | Generally favorable (reduces principal risk) | Generally favorable (reduces refinancing/balloon risk) |
| Common in which markets | Sovereign, most corporate bonds | Mortgage-backed securities, asset-backed securities, some project finance/municipal bonds | Corporate bonds, some municipal issues |

### Duration and Convexity Implications

- **Weighted Average Life (WAL)** becomes the more informative maturity metric than stated final maturity for amortizing and sinking-fund bonds:

$$\text{WAL} = \sum_{t=1}^{n} t \times \frac{\text{Principal repaid at } t}{\text{Total principal}}$$

- Because cash flows return earlier, both **Macaulay duration** and **modified duration** are lower for amortizing/sinking-fund bonds than for a bullet bond of identical final maturity, coupon, and yield — all else equal, this reduces interest rate sensitivity.
- [Unverified as a strict universal rule] In practice, sinking fund bonds with random lottery selection introduce a form of "call-like" optionality for the issuer that can create negative convexity effects similar to callable bonds, particularly when the sinking fund call price is below current market price.

### Practical Example Context

Amortizing structures are the structural backbone of most **mortgage-backed securities (MBS)** and **asset-backed securities (ABS)**, where the underlying loan pool (mortgages, auto loans, etc.) is itself amortizing, and that cash flow profile passes through to the security holders — often layered with additional **prepayment risk**, since underlying borrowers may repay principal faster than scheduled.

### Key Points

- Amortizing bonds repay principal progressively through periodic payments alongside interest, unlike bullet bonds which repay 100% of principal at maturity.
- Sinking fund provisions contractually require periodic principal retirement, often via lottery-based calls at (or near) par, cash deposits to a trustee, or open-market purchases.
- Both structures reduce weighted-average life and duration relative to an equivalent bullet bond, lowering interest rate sensitivity.
- Sinking funds primarily serve to reduce issuer refinancing/balloon risk and enhance credit quality, often at the cost of introducing call-like uncertainty for individual bondholders.
- Weighted Average Life (WAL) is the appropriate maturity-equivalent metric for cash-flow analysis on amortizing and sinking-fund structures, rather than stated final maturity.

**Related Topics**

- Weighted Average Life (WAL) vs. Macaulay Duration
- Mortgage-Backed Securities and Prepayment Risk (PSA Benchmark)
- Effective Duration for Bonds with Uncertain Cash Flow Timing
- Asset-Backed Securities: Structural Tranching and Waterfall Mechanics
- Credit Enhancement Techniques in Structured Finance
- Refinancing Risk and Issuer Balance Sheet Management