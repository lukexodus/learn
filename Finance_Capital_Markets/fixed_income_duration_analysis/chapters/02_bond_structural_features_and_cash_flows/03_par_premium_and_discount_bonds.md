## Par, Premium, and Discount Bonds

### Core Definitions

A bond's classification as trading "at par," "at a premium," or "at a discount" is determined by the relationship between its market price and its face (par) value, which in turn is governed by the relationship between its coupon rate and the prevailing required yield (market discount rate) for bonds of comparable risk and maturity.

| Classification | Price vs. Par | Relationship |
| --- | --- | --- |
| Par bond | $P = F$ | Coupon rate = Required yield |
| Premium bond | $P > F$ | Coupon rate > Required yield |
| Discount bond | $P < F$ | Coupon rate < Required yield |

Where $P$ is market price and $F$ is face value.

### Why This Relationship Holds

A bond's price is the present value of its fixed cash flows discounted at the market-required yield:

$$P = \sum_{t=1}^{n} \frac{C}{(1+y)^t} + \frac{F}{(1+y)^n}$$

Since the coupon $C = c \times F$ is fixed at issuance (for a fixed-rate bond) but the required yield $y$ fluctuates with market conditions, the price must adjust to bring the bond's return in line with the market. If a bond promises a coupon rate higher than what new comparable bonds are offering, investors will bid its price up until its yield converges downward to match the market-required yield — and vice versa. The price is the mechanism that equalizes total return across bonds regardless of their stated coupon.

### Par Bond

**Condition:** Coupon rate = Yield to maturity (YTM)

**Example:**

A bond with a 5% annual coupon, $1,000 face value, 5 years to maturity, priced when the market-required yield is also 5%:

$$P = \sum_{t=1}^{5} \frac{50}{(1.05)^t} + \frac{1000}{(1.05)^5} = 1000$$

At issuance, most bonds are priced at or very near par, since issuers typically set the coupon rate close to prevailing market yields to ensure the offering sells at (or close to) face value.

### Premium Bond

**Condition:** Coupon rate > Required yield → Price > Par

**Mechanism:** The bond is paying more in coupons than the market currently demands for that risk/maturity profile, so investors are willing to pay more than face value to capture that above-market coupon stream. As the bond approaches maturity, this premium must decay — since the bond will only repay $F$ at maturity, not the premium price paid.

**Example:**

Same bond (5% coupon, $1,000 face, 5 years), but the market-required yield has fallen to 3%:

$$P = \sum_{t=1}^{5} \frac{50}{(1.03)^t} + \frac{1000}{(1.03)^5} \approx 1{,}091.59$$

The bond trades at a $91.59 premium because its 5% coupon exceeds the 3% rate now available in the market.

**[Inference] Common scenario:** Premium bonds typically arise when interest rates have declined since issuance, or when a bond was issued with an unusually generous coupon relative to its credit risk at the time.

### Discount Bond

**Condition:** Coupon rate < Required yield → Price < Par

**Mechanism:** The bond's coupon is below what the market now demands, so investors will only buy it if compensated via a lower purchase price — the capital appreciation from price-to-par at maturity supplements the below-market coupon to bring total return up to the required yield.

**Example:**

Same bond (5% coupon, $1,000 face, 5 years), but the market-required yield has risen to 7%:

$$P = \sum_{t=1}^{5} \frac{50}{(1.07)^t} + \frac{1000}{(1.07)^5} \approx 918.00$$

The bond trades at an $82.00 discount because its 5% coupon is below the 7% rate now required by the market.

**Special case — Zero-coupon bonds:** These always trade at a discount to face value (assuming positive yields), since with $C = 0$, the entire return to the investor comes from the difference between purchase price and the face value received at maturity:

$$P = \frac{F}{(1+y)^n}$$

### Price Convergence to Par ("Pull to Par")

Regardless of whether a bond begins at a premium or discount, as it approaches maturity, its price converges toward face value — this is known as the "pull to par" effect, because at maturity there are no further coupons to discount, and the only remaining cash flow is the repayment of face value itself.

### Diagram: Pull to Par (svg_diagram)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 700 320" font-family="Arial, sans-serif">
<text x="350" y="24" text-anchor="middle" font-size="15" font-weight="bold">Bond Price Convergence to Par Over Time (svg_diagram)</text>
<line x1="70" y1="270" x2="650" y2="270" stroke="black" stroke-width="1.5" />
<line x1="70" y1="30" x2="70" y2="270" stroke="black" stroke-width="1.5" />
<text x="360" y="300" text-anchor="middle" font-size="12">Time to Maturity →</text>
<text x="30" y="150" text-anchor="middle" font-size="12" transform="rotate(-90 30 150)">Bond Price</text>
<line x1="70" y1="150" x2="650" y2="150" stroke="gray" stroke-width="1.5" stroke-dasharray="6,4" />
<text x="655" y="154" font-size="11" fill="gray">Par (F)</text>
<path d="M 70 80 C 250 100, 450 130, 650 150" fill="none" stroke="#c0392b" stroke-width="2.5" />
<text x="120" y="72" font-size="11" fill="#c0392b">Premium Bond (P &gt; F)</text>
<path d="M 70 220 C 250 200, 450 170, 650 150" fill="none" stroke="#1a5fb4" stroke-width="2.5" />
<text x="120" y="240" font-size="11" fill="#1a5fb4">Discount Bond (P &lt; F)</text>
<circle cx="650" cy="150" r="4" fill="black" />
<text x="600" y="130" font-size="11">Maturity: P = F</text>
</svg>

### Relationship to Current Yield and YTM

For a fuller picture, three yield measures diverge predictably depending on bond classification:

| Bond Type | Coupon Rate | Current Yield | Yield to Maturity |
| --- | --- | --- | --- |
| Par | = | = | = |
| Premium | Highest | Middle | Lowest |
| Discount | Lowest | Middle | Highest |

Where current yield $= \dfrac{C}{P}$ (annual coupon ÷ market price). This ordering holds because:

- Premium bonds have $P > F$, so dividing the fixed coupon by a larger price than face value produces a current yield lower than the coupon rate, but YTM incorporates the capital *loss* pulling to par, pushing YTM below current yield.
- Discount bonds have $P < F$, so current yield exceeds coupon rate, and YTM incorporates the capital *gain* pulling to par, pushing YTM above current yield.

### Practical Implications

- **Premium bonds** return part of the investor's own invested capital back as "coupon" income each period — a portion of every coupon payment above the discount-equivalent yield is effectively a repayment of the premium originally paid. [Inference] This has tax implications in many jurisdictions (e.g., amortizable bond premium), though exact tax treatment is jurisdiction-specific and not addressed here.
- **Discount bonds** carry embedded price appreciation as part of total return, which in some tax regimes is treated as ordinary income or capital gains depending on the type of discount (market discount vs. original issue discount).
- **Callable premium bonds** carry elevated call risk: issuers are incentivized to call back high-coupon bonds when rates fall, since premium pricing signals the issuer is paying above-market coupons — the investor holding a premium bond is thus exposed to the possibility of early redemption at par, cutting off the premium's income advantage.

### Key Points

- Classification (par/premium/discount) is driven entirely by the coupon rate vs. required market yield comparison, not by any inherent quality of the bond.
- Premium: coupon > yield, price > par. Discount: coupon < yield, price < par. Par: coupon = yield, price = par.
- All bonds converge to face value at maturity ("pull to par"), which is a mechanical certainty stemming from the final cash flow being exactly $F$.
- Current yield sits between coupon rate and YTM for both premium and discount bonds, but on opposite sides.
- Zero-coupon bonds are a limiting case that is always priced at a discount (for positive yields).

**Related Topics**

- Yield to Maturity (YTM) Calculation and Assumptions
- Amortization of Bond Premium and Accretion of Discount
- Call Risk and Callable Bond Pricing Dynamics
- Original Issue Discount (OID) vs. Market Discount
- Realized vs. Expected Return and Reinvestment Risk
- Duration Differences Between Premium and Discount Bonds