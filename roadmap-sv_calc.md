# Rapid Path to Mastery: Applied Single-Variable Calculus (5 Stages)

## 1) Foundations & Limits (intuitive → operational)

**Primary text (pick one):**

* Stewart, *Calculus: Early Transcendentals* — Ch. 1 “Functions and Models”, Ch. 2.1–2.6 “Limits & Continuity”
* Open alt: Strang, *Calculus* — Ch. 1 “Functions and Limits”, Ch. 2.1–2.2

**Must-know**

* Function types (poly/rational/exp/log/trig), domain/range, compositions, inverses
* Limit laws, one-sided limits, infinite limits, continuity, IVT
* Practical limit evaluation (algebraic simplification, rationalization)

**Nice-to-know**

* Formal ε–δ viewpoint (just the structure)
* Piecewise continuity and removable/essential discontinuities
* Asymptotes (horizontal/vertical/oblique) as limit statements

**Project**

* **Sensor model calibration.** Take a monotone dataset (e.g., thermistor or battery discharge). Fit exp/log models, estimate asymptotes via limits, and justify continuity assumptions. Deliver a short report with plots and a limit-based rationale for your chosen model.

---

## 2) Derivatives: Definitions, Rules, and Linearization

**Primary text (pick one):**

* Stewart — Ch. 2.7–2.9 “Derivative as a Function”, Ch. 3.1–3.9 “Differentiation Rules”
* Open alt: Strang — Ch. 2.3–2.6 (derivative), Ch. 3 (rules & rates)

**Must-know**

* Derivative as rate/slope and as linear approximation; differentiability ⇒ continuity
* Rules: power, product, quotient, chain; exp/log/trig & inverse-trig derivatives
* Implicit differentiation, related rates; differentials & linearization

**Nice-to-know**

* Sensitivity analysis with differentials (propagation of measurement error)
* Higher derivatives and jerk/curvature intuition
* Automatic differentiation vs. symbolic differentiation (conceptual)

**Project**

* **Optimization with constraints (single variable).** Model a cost/efficiency scenario (e.g., packaging with fixed material, or minimizing travel time with a speed profile). Use derivatives and linearization to quantify sensitivity to parameter changes. Provide first-order error bounds.

---

## 3) Applications of the Derivative: Graphing & Optimization at Scale

**Primary text (pick one):**

* Stewart — Ch. 4.1–4.6 “Applications of Differentiation”, 4.7–4.8 “Newton’s Method & Antiderivatives”, 4.10 “L’Hospital’s Rule”
* Open alt: Strang — Ch. 3 (applications), sections on Newton’s method

**Must-know**

* Extrema (local/global), first/second derivative tests, MVT & consequences
* Concavity/inflection, sketching from ( f', f'' )
* Newton’s method: derivation, convergence caveats
* L’Hospital’s Rule for 0/0 and ∞/∞

**Nice-to-know**

* Curvature and geometric interpretation of ( f', f'' )
* Robust root-finding (bracketing vs. Newton) and failure modes
* Nondifferentiable points in applied models (kinks, absolute value)

**Project**

* **Data-driven curve analysis.** From noisy ( (t, x(t)) ) data, build smoothed ( x(t) ), compute ( v(t)\approx x'(t) ), ( a(t)\approx x''(t) ). Identify extrema, inflection points, and use Newton’s method to find event times. Compare finite-difference vs. polynomial fit derivatives; report stability and error.

---

## 4) Integrals: Fundamentals, Techniques, and Numerical Methods

**Primary text (pick one):**

* Stewart — Ch. 5.1–5.5 “Definite Integral & FTC”, Ch. 6.1–6.5 “Applications”, Ch. 7.1–7.5 “Techniques”
* Open alt: Strang — Ch. 4 “Integrals”, Ch. 5 “Techniques”, Ch. 6 “Applications”

**Must-know**

* Riemann sums → definite integral; FTC I & II; ( \frac{d}{dx}\int_a^x f = f(x) )
* Substitution; integration by parts; basic trig patterns
* Numerical integration (rectangle/trapezoid/Simpson); error behavior
* Applications: area, average value, volumes (disk/washer/shell), work

**Nice-to-know**

* Partial fractions; improper integrals (comparison tests for convergence)
* Arc length & surface area integrals; centers of mass
* Adaptive quadrature ideas; composite rules and step-size control

**Project**

* **Energy and volume from real data.**
  (A) From a power-vs-time dataset, compute total energy via numerical integration; compare rules and estimate error.
  (B) Use cross-sectional profiles of an object to approximate its volume (shells or washers); validate against a 3-D approximation.

---

## 5) Differential Equations (Intro) & Series for Approximation

**Primary text (pick one):**

* Stewart — Ch. 9.1–9.3 “First-Order DEs (separable, linear, integrating factor)”, Ch. 11.1–11.11 “Sequences & Series, Power/Taylor Series”
* Open alt: Strang — Ch. 7 “Differential Equations”, Ch. 8 “Infinite Series”

**Must-know**

* Separable and first-order linear DEs; integrating factor; initial values
* Qualitative tools: slope fields, equilibria, stability (1-D)
* Series: tests (nth-term, comparison, ratio, integral, alternating), absolute vs conditional convergence
* Taylor polynomials/series; remainder/error bounds; using series to approximate integrals/solutions

**Nice-to-know**

* Logistic growth (separable DE) and parameter inference from data
* Series solutions near regular points (concept)
* Fourier series as an orthogonal expansion (basic statement & example)

**Project**

* **Model + Approximate.**
  (A) Fit a first-order model (cooling, RC discharge, or logistic growth) to real data; estimate parameters and assess residuals.
  (B) Build a Taylor-series approximator with certified remainder bounds to hit a target accuracy for ( \sin, \exp, \ln ) on specified intervals; compare with numerical quadrature where relevant.

---

## How to Execute Fast (suggested cadence)

* **Stage 1–2**: master routine skills and linearization (problem sets daily; brief applied write-ups).
* **Stage 3**: mix analytical with numerical differentiation/roots; stress-test with noisy data.
* **Stage 4**: emphasize FTC intuition + numerical integration accuracy/efficiency.
* **Stage 5**: tie modeling (DEs) to approximation (series) with explicit error control.

## Deliverables for Each Project

* Short technical memo (objective, model/derivation, method, results, error analysis)
* Reproducible notebook or program (Python/C++), plus plots/tables
* A one-page “lessons learned” focusing on assumptions and failure modes

If you’d like, I can turn this into a printable checklist or populate a reading plan with chapter-by-chapter exercises next.


https://chatgpt.com/s/t_691247350cd88191b416cbd035c18844
