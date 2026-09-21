## Mandatory Convertibles and Exchangeables


### Overview

Mandatory convertibles and exchangeables are equity-linked instruments that, unlike standard convertible bonds, do not give the holder discretion over whether to convert — conversion into shares is compulsory at or before maturity, according to a predetermined formula. Mandatory convertibles convert into the *issuer's own* shares, while exchangeables (in the mandatory context) convert into shares of a *different* company, typically a subsidiary, affiliate, or strategic holding of the issuer. Both instruments are commonly used as equity or equity-linked capital-raising tools where the issuer wants near-certainty that the instrument will convert to equity on the balance sheet, rather than remaining outstanding as debt.

### Mandatory Convertibles: Core Structure

**Defining Feature: Compulsory Conversion**

Unlike a standard convertible bond where the investor chooses whether to convert, a mandatory convertible automatically converts into common stock at maturity (or a specified mandatory conversion date), regardless of the stock price at that time. The investor's optionality is therefore about the initial investment decision, not an ongoing conversion choice.

**Conversion Ratio Collar**

Because conversion is compulsory, mandatory convertibles are structured with a **variable conversion ratio** between two bounds — a maximum and minimum number of shares per unit — to shape the payoff and share the risk of stock price moves between issuer and investor within a defined band:

$$\text{Conversion Ratio} = \begin{cases} \text{Ratio}_{max} = \dfrac{\text{Par}}{K_1} & S_T \le K_1 \\[6pt] \dfrac{\text{Par}}{S_T} & K_1 < S_T < K_2 \\[6pt] \text{Ratio}_{min} = \dfrac{\text{Par}}{K_2} & S_T \ge K_2 \end{cases}$$

where $K_1$ is the lower conversion price (also called the "threshold" or "initial" price) and $K_2$ is the upper conversion price (also called the "cap" or "threshold appreciation" price), and $S_T$ is the stock price at the mandatory conversion date.

### Payoff Decomposition

The mandatory convertible's payoff can be decomposed as a package of standard option positions, which is the standard framework for understanding its risk/return profile:

$$\text{Payoff} = S_T - \max(S_T - K_1, 0) + \max(S_T - K_2, 0)$$

Equivalently, this is economically similar to:

1. A **long position in the stock** (full downside exposure below $K_1$)
2. **Short a call option** struck at $K_1$ (capping upside participation at the threshold price — the investor effectively sold this call to the issuer in exchange for the enhanced coupon)
3. **Long a call option** struck at $K_2$ (returning some upside above the cap price)

This is often described as being economically equivalent to holding the stock plus a **short collar** (short a lower-struck call, long a higher-struck call), and the structure is the reason mandatory convertibles are sometimes called "PERCS," "DECS," "PRIDES," "ACES," or similar proprietary trade names historically used by different underwriters for economically similar structures. [Inference — exact naming conventions and minor structural variations differ by issuing bank and era, and are largely marketing/branding distinctions over an economically similar core payoff]

### Payoff Diagram at Mandatory Conversion (svg_diagram)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 640 380">
<rect width="640" height="380" fill="#ffffff" />
<text x="320" y="24" font-family="sans-serif" font-size="15" font-weight="bold" text-anchor="middle" fill="#1a1a1a">Mandatory Convertible Payoff at Conversion Date (svg_diagram)</text>
<line x1="70" y1="320" x2="600" y2="320" stroke="#333" stroke-width="1.5" />
<line x1="70" y1="320" x2="70" y2="40" stroke="#333" stroke-width="1.5" />
<text x="335" y="355" font-family="sans-serif" font-size="12" text-anchor="middle" fill="#333">Stock Price at Conversion (S_T)</text>
<text x="30" y="180" font-family="sans-serif" font-size="12" text-anchor="middle" fill="#333" transform="rotate(-90 30 180)">Value Received</text>

<line x1="150" y1="300" x2="530" y2="60" stroke="#cccccc" stroke-width="1.5" stroke-dasharray="4,4" />
<text x="500" y="80" font-family="sans-serif" font-size="11" fill="#999">Straight Equity (reference)</text>

<path d="M 150,300 L 260,220 L 400,220 L 530,110" fill="none" stroke="#228833" stroke-width="3" />
<line x1="260" y1="320" x2="260" y2="220" stroke="#8888aa" stroke-width="1" stroke-dasharray="3,3" />
<line x1="400" y1="320" x2="400" y2="220" stroke="#8888aa" stroke-width="1" stroke-dasharray="3,3" />
<text x="245" y="335" font-family="sans-serif" font-size="11" fill="#5555aa">K1 (lower)</text>
<text x="385" y="335" font-family="sans-serif" font-size="11" fill="#5555aa">K2 (upper)</text>

<text x="160" y="290" font-family="sans-serif" font-size="11" fill="#666">Full downside participation</text>

<text x="270" y="210" font-family="sans-serif" font-size="11" fill="#666">Capped participation zone</text>

<text x="440" y="130" font-family="sans-serif" font-size="11" fill="#666">Reduced-ratio upside above K2</text>

</svg>

### Yield Enhancement

To compensate the investor for the capped upside (the short call struck at $K_1$), mandatory convertibles typically pay a **higher coupon or dividend rate** than the issuer's common stock dividend yield and often higher than an equivalent-tenor standard convertible bond's coupon — this "yield enhancement" is the primary carry benefit investors receive in exchange for surrendering unlimited upside participation and, in most structures, without the downside protection of a bond floor (since conversion at maturity is compulsory regardless of how far the stock has fallen).

**Key distinction from standard convertibles**: mandatory convertibles typically do **not** have a meaningful bond floor at maturity in the way a standard optional convertible does, because there is no option to instead redeem for par — the holder is compelled to take shares (or share-equivalent value) even if the stock has declined sharply, making the instrument considerably more equity-like in downside risk than a standard convertible bond, despite still being structured with debt-like or preferred-stock-like periodic distributions prior to conversion.

### Legal Form

Mandatory convertibles may be issued as:

- **Mandatory convertible notes/bonds**: structured as debt instruments prior to conversion
- **Mandatory convertible preferred stock**: structured as preferred equity prior to conversion, which is common because preferred stock classification can offer favorable treatment for certain regulatory capital or credit rating agency equity-content purposes, and avoids some debt covenant/leverage-ratio implications that a note structure would carry [Inference — the relative prevalence of note vs. preferred structuring varies by market, jurisdiction, and issuer sector]

### Exchangeable Bonds (Mandatory and Optional Variants)

**Core Distinction from Convertibles**: An exchangeable bond converts into shares of a company *other than the issuer* — most commonly, the issuer holds a stake in another (often publicly listed) company and issues a bond exchangeable into that stake.

**Typical Use Cases**

- **Monetizing a strategic stake**: A company holding a large equity position in another firm (e.g., from a prior M&A transaction, spin-off retained stake, or cross-holding) issues an exchangeable bond to raise cash while deferring the outright sale of the stake, potentially for tax, strategic, or market-timing reasons, and often at a premium to the current market price of the held shares
- **Subsidiary equity monetization**: A parent company issues bonds exchangeable into shares of a partially-owned subsidiary, raising capital at the parent level while using the subsidiary's (potentially higher-multiple or more liquid) equity as the reference asset

**Mandatory vs. Optional Exchangeables**

- **Optional exchangeable**: structured like a standard optional convertible bond, but exchange is investor's choice and the reference share is a third party's stock rather than the issuer's own
- **Mandatory exchangeable**: structured like a mandatory convertible (collared conversion ratio, compulsory exchange at maturity), but into the third-party reference shares

**Key Risk Distinction from Convertibles**: Because the underlying share is not the issuer's own stock, exchangeable bondholders bear equity risk on a *different* company than the one bearing the credit risk of the bond — the issuer's credit risk and the reference stock's equity risk are decoupled, which is a materially different risk profile than a standard convertible where credit risk and equity-option risk both relate to the same entity. From the issuer's perspective, an exchangeable also typically does **not** dilute the issuer's own share count upon conversion (since shares of the third-party company are delivered, not newly issued issuer shares), distinguishing its balance sheet and EPS impact from both standard and mandatory convertibles issued on the company's own stock.

### Comparison Table

| Feature | Standard Convertible | Mandatory Convertible | Exchangeable Bond |
| --- | --- | --- | --- |
| Conversion decision | Investor's option | Compulsory at maturity | Investor's option (or compulsory, if mandatory exchangeable) |
| Underlying shares | Issuer's own stock | Issuer's own stock | Third-party company's stock |
| Issuer dilution | Yes, upon conversion | Yes, upon conversion | No (typically holds/delivers existing shares) |
| Downside protection | Bond floor | Limited/minimal | Bond floor (if optional) or limited (if mandatory) |
| Typical legal form | Debt | Debt or preferred stock | Debt |
| Coupon/yield level | Below straight debt | Enhanced (above stock dividend yield) | Below straight debt (if optional) |

### Use Cases and Issuer Rationale

- **Deleveraging / capital raising with certainty of equity conversion**: Issuers seeking a guaranteed increase in common equity (useful for credit rating agency equity-credit purposes, regulatory capital objectives for financial institutions, or balance sheet deleveraging commitments) prefer mandatory structures since conversion is not contingent on investor discretion or stock price performance
- **Rating agency and covenant treatment**: Mandatory convertible preferred stock in particular may receive partial or full "equity credit" from rating agencies, improving credit metrics relative to straight debt issuance of the same size
- **Monetizing non-core equity stakes (exchangeables)**: Provides liquidity from a strategic holding without an immediate outright block sale, which could otherwise pressure the reference stock's price or trigger unfavorable tax consequences

### Risk Factors

- **Equity-like Downside Exposure**: Mandatory convertible holders bear most of the downside of holding the stock outright below $K_1$, without the debt-like protection a standard convertible's bond floor provides
- **Capped Upside**: Return is structurally limited above $K_1$ within the collar range, and only partially participates above $K_2$
- **Reference Asset / Issuer Decoupling Risk (Exchangeables)**: The bond's credit risk (tied to the issuer) and its equity-linked payoff (tied to the reference company) can move independently, complicating risk assessment relative to a standard convertible
- **Dividend/Coupon Suspension Risk**: If structured as preferred stock, dividend payments may be subject to standard preferred stock discretion/deferral provisions depending on the specific instrument's terms

### **Related Topics**

- Convertible Bond Structure and Terms
- Convertible Bond Valuation Models (Binomial Trees, AFV Jump-Diffusion, Monte Carlo)
- Collar Option Strategies (Protective Collars, Zero-Cost Collars)
- Equity Monetization Strategies for Strategic Stakes
- Preferred Stock Structures and Rating Agency Equity Credit
- Contingent Convertible Bonds and Loss Absorption