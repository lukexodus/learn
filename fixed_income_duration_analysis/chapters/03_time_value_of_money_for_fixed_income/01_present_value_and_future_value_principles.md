## Present Value and Future Value Principles


### Core Concept

Time value of money (TVM) is the foundational principle underlying all fixed income valuation: a given sum of money available today is worth more than the same nominal sum available at a future date, because money available today can be invested to earn a return over the intervening period. Every bond pricing, yield, and duration calculation in fixed income analysis is, at its core, an application of present value and future value mechanics to a defined stream of cash flows.

### Future Value (FV)

**Definition:** The value that a present sum of money will grow to after a specified period, given a specified rate of return, assuming compounding.

**Single cash flow, annual compounding:**

$$FV = PV \times (1+r)^n$$

Where:

- $PV$ = present value (initial sum)
- $r$ = interest rate per period
- $n$ = number of periods

**Example:**

$10,000 invested today at 5% annually for 3 years:

$$FV = 10{,}000 \times (1.05)^3 = 10{,}000 \times 1.157625 = \$11{,}576.25$$

### Present Value (PV)

**Definition:** The current worth of a future sum of money (or stream of sums), discounted back at a specified rate that reflects the opportunity cost of capital or required return.

**Single cash flow:**

$$PV = \frac{FV}{(1+r)^n}$$

Present value is the inverse operation of future value — discounting rather than compounding. This is the mathematical backbone of bond pricing, since a bond's value is the sum of the present values of all its future promised cash flows.

**Example:**

What is the present value of $11,576.25 to be received in 3 years, given a 5% discount rate?

$$PV = \frac{11{,}576.25}{(1.05)^3} = \$10{,}000.00$$

This confirms the FV/PV relationship is perfectly reciprocal at a given rate and time horizon.

### Compounding Frequency

The stated annual rate does not fully describe an investment's growth unless the compounding frequency is also specified. More frequent compounding produces a higher effective return for the same nominal (stated) annual rate, because interest itself begins earning interest sooner.

$$FV = PV \times \left(1 + \frac{r}{m}\right)^{m \times n}$$

Where $m$ = number of compounding periods per year.

**Effective Annual Rate (EAR):**

$$EAR = \left(1 + \frac{r}{m}\right)^m - 1$$

**Example:** A nominal annual rate of 6% compounded at different frequencies:

| Compounding Frequency | $m$ | Effective Annual Rate |
| --- | --- | --- |
| Annual | 1 | 6.0000% |
| Semi-annual | 2 | 6.0900% |
| Quarterly | 4 | 6.1364% |
| Monthly | 12 | 6.1678% |
| Daily | 365 | 6.1831% |
| Continuous | $\to \infty$ | 6.1837% |

**Continuous compounding:**

$$FV = PV \times e^{r \times n}$$

[Inference] Continuous compounding is used more often as a theoretical/analytical convenience (e.g., in derivatives pricing and some academic fixed income models) than as a literal real-world payment convention, though it provides a useful mathematical limit case.

### Present Value of a Single Sum vs. an Annuity

Fixed income cash flows are rarely a single payment — a coupon-bearing bond generates a **series** of periodic payments (an annuity) plus a final lump-sum principal repayment. Understanding both building blocks is essential.

**Present Value of an Ordinary Annuity** (equal payments $PMT$ at the end of each period):

$$PV_{\text{annuity}} = PMT \times \frac{1 - (1+r)^{-n}}{r}$$

**Present Value of a Single Lump Sum (e.g., bond's face value at maturity):**

$$PV_{\text{lump sum}} = \frac{F}{(1+r)^n}$$

**Combined — this is precisely the bond pricing formula:**

$$P = \underbrace{C \times \frac{1 - (1+y)^{-n}}{y}}_{\text{PV of coupon annuity}} + \underbrace{\frac{F}{(1+y)^n}}_{\text{PV of face value}}$$

This decomposition makes explicit that **bond pricing is nothing more than the present value of an annuity (the coupon stream) plus the present value of a single future sum (the principal repayment)**.

### Worked Bond Pricing Example Using TVM Principles

A 4-year bond, $1,000 face value, 6% annual coupon, discounted at a required yield of 8%:

$$P = 60 \times \frac{1 - (1.08)^{-4}}{0.08} + \frac{1000}{(1.08)^4}$$



$$P = 60 \times 3.31213 + 1000 \times 0.73503$$



$$P = 198.73 + 735.03 = \$933.76$$

This confirms the bond trades at a discount, consistent with coupon rate (6%) < required yield (8%).

### Diagram: Present Value / Future Value Relationship (svg_diagram)

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 700 300" font-family="Arial, sans-serif">
<text x="350" y="24" text-anchor="middle" font-size="15" font-weight="bold">Present Value and Future Value on a Timeline (svg_diagram)</text>
<line x1="80" y1="150" x2="620" y2="150" stroke="black" stroke-width="2" />
<polygon points="620,150 610,145 610,155" fill="black" />
<line x1="120" y1="145" x2="120" y2="155" stroke="black" stroke-width="2" />
<text x="120" y="175" text-anchor="middle" font-size="12">t = 0</text>
<circle cx="120" cy="150" r="5" fill="#1a5fb4" />
<text x="120" y="110" text-anchor="middle" font-size="13" fill="#1a5fb4" font-weight="bold">PV</text>
<line x1="540" y1="145" x2="540" y2="155" stroke="black" stroke-width="2" />
<text x="540" y="175" text-anchor="middle" font-size="12">t = n</text>
<circle cx="540" cy="150" r="5" fill="#c0392b" />
<text x="540" y="110" text-anchor="middle" font-size="13" fill="#c0392b" font-weight="bold">FV</text>
<path d="M 130 130 Q 330 80, 530 130" fill="none" stroke="#c0392b" stroke-width="2" marker-end="url(#arrowFwd)" />
<text x="330" y="75" text-anchor="middle" font-size="12" fill="#c0392b">Compounding: FV = PV × (1+r)ⁿ</text>
<path d="M 530 195 Q 330 245, 130 195" fill="none" stroke="#1a5fb4" stroke-width="2" marker-end="url(#arrowBack)" />
<text x="330" y="260" text-anchor="middle" font-size="12" fill="#1a5fb4">Discounting: PV = FV / (1+r)ⁿ</text>
</svg>

### The Discount Rate: Central Role in Fixed Income

The discount rate $r$ (or $y$, when referred to as yield) used in TVM calculations is not an arbitrary input — in fixed income, it represents the market's required return for the risk, maturity, and liquidity profile of the specific cash flow being valued. Small changes in this rate produce an inverse, non-linear change in present value — the mathematical origin of the fundamental inverse price-yield relationship in bond markets:

$$\frac{\partial PV}{\partial r} < 0$$

This partial derivative relationship — present value falling as the discount rate rises, and vice versa — is the single most important TVM-derived fact in all of fixed income analysis, and is the conceptual root from which duration and convexity (the standardized measures of this sensitivity) are later derived.

### Rule of 72 (Quick Approximation Tool)

**[Inference] Heuristic, not exact:** A commonly used mental approximation for how long it takes an investment to double at a given annual rate:

$$n \approx \frac{72}{r \, (\text{as a percentage})}$$

**Example:** At 8% annual compounding, doubling time $\approx 72/8 = 9$ years. [Note: the Rule of 72 is an approximation most accurate for rates roughly between 6%–10%; it diverges more noticeably from the exact compound-growth answer at very low or very high rates.]

### Key Points

- Future value compounds a present sum forward in time; present value discounts a future sum back to today — they are mathematically reciprocal operations at a given rate and horizon.
- More frequent compounding periods produce a higher effective annual rate for the same stated nominal rate.
- Bond pricing is a direct, combined application of the present value of an annuity (coupon stream) and the present value of a single lump sum (principal repayment).
- The inverse relationship between discount rate and present value ($\partial PV/\partial r < 0$) is the mathematical origin of the inverse bond price-yield relationship.
- All subsequent fixed income valuation concepts (yield to maturity, duration, convexity) are extensions or refinements of these core TVM principles.

**Related Topics**

- Yield to Maturity: Definition, Calculation, and Assumptions
- Macaulay Duration and Modified Duration Derivation
- Term Structure of Interest Rates and the Yield Curve
- Effective Annual Rate vs. Nominal Rate Conventions in Bond Markets
- Annuities, Perpetuities, and Their Role in Fixed Income Cash Flow Modeling
- Continuous Compounding Applications in Derivatives and Bond Pricing Models