# TheError
L(M) = φ(M) · φ(M+1) / (M+1)


### Lift Survival Function — W. Getachew · math.NT · 2026

**Live site:** https://wessengetachew.github.io/TheError/

# The Lift Survival Function
### Wessen Getachew · math.NT · 2026

**L(M) = φ(M) · φ(M+1) / (M+1)**

A geometric prime sieve built around modular arithmetic and consecutive coprimality.


Four interactive pages, all computed live in the browser:

| Page | File | Description |
|---|---|---|
| Opener | `index.html` | Framework introduction, 8 live chart previews, Prime Checker, benchmark table |
| Explorer | `EN_explorer-1-2.html` | 9 interactive charts probing E(N) = R(N) − C convergence |
| Deep Analysis | `EN_explorer-updated.html` | Four analytical panels: Lift Friction, Ghost Residues, Sign-Change Gaps, Parity Obstruction |
| Geometric Canvas | `zmmz_explorer-1.html` | WebGL ring explorer for (ℤ/Mℤ)* with lift lines, prime spirals, AI probes |

---

## The Core Object

For each integer M, the **lift weight** is:

```
L(M) = φ(M) · φ(M+1) / (M+1)
```

The **lift ratio** accumulates these weights:

```
R(N) = Σ_{m=1}^{N} L(m) / Σ_{m=1}^{N} φ(m)
```

**Theorem (proved).** R(N) → C as N → ∞, where:

```
C = ∏_p (p²−2)/(p²−1) = ζ(2) · d_FT ≈ 0.530711806246
```

This is the **Lift Survival Constant** — the long-run fraction of coprime residues that survive the lift from ring M to ring M+1.

**Conjecture (numerical).** The error term E(N) = R(N) − C satisfies:

```
E(N) = O(1/N)
```

Verified to N = 2,000,000: max|E(N)·N| < 0.929, OLS regression slope = −0.998 over 200,000 sample points. This rate is faster than the naive O(1/log N) prediction — the ratio structure of R(N) produces extra cancellation.

---

## The Jump Theorem

The log-derivative D(x) = d/dx log C(x) is smooth everywhere except at the primes. At x = p−1 for each prime p, D(x) jumps by exactly:

```
Δ = 1 / (p(p−1))
```

Composites pass in silence. Given a jump size s, the prime is recovered exactly:

```
p = (1 + √(1 + 4/s)) / 2
```

The discriminant 1 + 4p(p−1) = (2p−1)² is always a perfect square for integer primes. The golden ratio φ is the **supremum of the jump spectrum** — s = 1 is the unique value no integer prime reaches.

---

## The Four Constants

| Constant | Value | Status |
|---|---|---|
| C = ∏_p (p²−2)/(p²−1) | 0.530711806246… | Known (Tóth–Sándor 1989); new geometric interpretation |
| J = Σ_p 1/(p(p−1)) = Σ_{k≥2} P(k) | 0.773154968933… | Appears original |
| D₀ = Σ_p 1/(p²−1) | 0.551691597558… | Appears original |
| T = Σ_p 1/(p(p²−1)) | 0.221463371375… | Appears original |

**Identity (exact algebraic).** J = D₀ + T. Proof: partial fraction 1/(p(p−1)) = 1/(p²−1) + 1/(p(p²−1)), sum over all primes. ∎

---

## Benchmark — E(N) = O(1/N) to N = 2,000,000

| N | E(N) | \|E(N)\| | \|E\|·N | SC count |
|---|---|---|---|---|
| 50,000 | −1.1989e−06 | 1.1989e−06 | 0.0599 | 35,163 |
| 100,000 | +4.1882e−06 | 4.1882e−06 | 0.4188 | 70,178 |
| 500,000 | −3.9158e−08 | 3.9158e−08 | 0.0196 | 351,879 |
| 1,000,000 | +3.8650e−07 | 3.8650e−07 | 0.3865 | 704,986 |
| 2,000,000 | −1.0496e−07 | 1.0496e−07 | 0.2099 | 1,416,927 |

Regression slope: **−0.9979** (O(1/N) predicts exactly −1.0).

---

## RH Connection

Sign changes of E(N) accumulate at nearly every step (1,416,927 in 2M steps). Infinitely many sign changes is proved — the lift factor φ(M+1)/((M+1)·C) crosses 1 infinitely often because φ is unboundedly variable. This is consistent with ζ(s) having zeros on Re(s) = 1/2 and not elsewhere, i.e., consistent with RH.

The framework does **not** prove RH. Closing the gap would require an explicit formula linking the oscillations of E(N) to the imaginary parts of the non-trivial zeros of ζ(s).

Under GRH the error in the character sums that control E(N) is O(d√N log N), giving E(N) = O(log N / N^{3/2}) conditionally.

---

## What Each Page Does

### index.html — Opener
- Animated hero with live R(N) convergence canvas
- 8 interactive chart previews with play animation and auto-zoom at 75%
- Send-to-Canvas: any chart point opens the geometric ring viewer
- Jump Theorem Prime Checker with jump spectrum visualization
- Benchmark table with live verification button (runs in browser to N=5,000)
- Direction cards (6 open problems) with proved/conjectured/heuristic status badges

### EN_explorer-1-2.html — Explorer
- 9 live-computed charts (N up to 500,000 via linear sieve)
- Chart 01–03: convergence rate (3 views)
- Chart 04: signed E(N) with adaptive prime tick density
- Chart 05: SC(N)/π(N) ratio growth
- Chart 06: sign-change gap histogram
- Chart 07: local lift factor (asymptotic direction predictor)
- Chart 08: χ₄-restricted E(N) (Franel–Landau probe)
- Chart 09: prime-at-SC running fraction (open question)
- Play animation with adaptive step size and auto-zoom at 75% convergence
- Live OLS regression slope stat card
- Full data tables in collapsible drawers
- Jump Theorem verifier in the theorems section

### EN_explorer-updated.html — Deep Analysis
- Panel 01: Lift Friction Map — f(M) = L(M)/C − 1 deviation landscape
- Panel 02: Ghost Residues — stable primes (large dot) vs ghost composites (medium) vs transients (small)
- Panel 03: Sign-Change Waiting Time — log-scale gaps with Skewes context and live ratio stat
- Panel 04: Parity Obstruction — Liouville function and prime-factor parity balance
- Panel 05: Jump Theorem Prime Checker (fully interactive)
- PNG export button on each panel

### zmmz_explorer-1.html — Geometric Canvas
- WebGL point cloud renderer for (ℤ/Mℤ)* up to M=512
- Views: Concentric, Fermat Spiral, Farey Half-Plane, Unfolded Strip
- Color modes: Angle, Prime Ring, φ/M Density, Lift ✓/✗, Modular Entropy, Mod-6, Primorial, Gap Class
- Lift lines, broken lift lines, prime spiral paths, (M±n)/2 left-side paths
- Chain n=1..6 survival filter (chain n=2 uses Fermat spiral to show Hardy–Littlewood clustering)
- Residue path animator: input r and target mod M, watch the path animate ring by ring
- AI Probe tab: 12 named geometric probes with animations and persistent observation card
- Send-to-Canvas: receives commands from the Explorer page
- 4K export with title, legend, and stats panel
- Index Chart → Canvas bridge via localStorage

---

## Files

```
index.html                  — Opener (landing page)
EN_explorer-1-2.html        — Explorer (9 live charts)
EN_explorer-updated.html    — Deep Analysis (4 panels + checker)
zmmz_explorer-1.html        — Geometric Canvas (WebGL ring explorer)
README.md                   — This file
```

---

## Mathematical Attribution

- **C = ζ(2)·d_FT**: Known as the density of consecutive squarefree pairs (Tóth–Sándor 1989, OEIS A065469). The geometric interpretation as a lift survival rate and the identity C = F(2) appear to be new.
- **J, D₀, T, F(u)**: Appear original. The decomposition J = D₀ + T is an exact algebraic identity.
- **Jump Theorem**: The exact formula Δ = 1/(p(p−1)) and φ as spectrum supremum appear original in this framing.
- **E(N) = O(1/N)**: Numerical conjecture. Not claimed as proved.
- **Boikova (2025)**: Independently derives related error coefficient via sinc-function analysis (Preprints.org, doi:10.20944/preprints202512.0862.v1).

---

## Contact

Wessen Getachew · [@7dview](https://twitter.com/7dview) · GetachewWessen@gmail.com

*All computations run live in the browser. No server, no backend, no dependencies.*
