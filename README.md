# TheError
L(M) = φ(M) · φ(M+1) / (M+1)
https://github.com/wessengetachew/TheError/

# Lift Survival Function
### Wessen. Getachew · Number Theory · math.NT · 2026

---

## What This Is

An original research project in analytic number theory studying how quickly
the **Lift Ratio R(N)** converges to its limiting constant C, and what that
convergence reveals about the zeros of Dirichlet L-functions. The project
combines rigorous mathematics with interactive browser-based visualization.

---

## The Mathematics

### The Lift Weight

For each positive integer M, define the **lift weight**:

```
L(M) = φ(M) · φ(M+1) / (M+1)
```

This is the local joint coprimality density of the consecutive pair (M, M+1)
— the proportion of integers up to M expected to survive coprimality with
both. The formula follows from the multiplicativity of Euler's φ function
across coprime moduli, and gcd(M, M+1) = 1 always holds for consecutive
integers.

Note: L(M) is a density weight, not an exact integer count. The true
integer count differs by a floor-function correction bounded by 2^ω(M) per
term. These corrections cancel in the cumulative average, leaving the ratio
R(N) and its limit C well-defined.

### The Lift Ratio

```
R(N) = Σ_{M=1}^{N} L(M)  /  Σ_{M=1}^{N} φ(M)
```

This accumulates the lift density weights against the raw totient weights.
As N → ∞, R(N) converges to a definite constant C.

### The Lift Survival Constant

```
C = ∏_{p prime} (p² − 2) / (p² − 1)
```

An Euler product over all primes. Converges absolutely. Related to ζ(2) =
π²/6 via the normalisation 3/π² = 1/ζ(2), and listed in OEIS A065469.

### The Error Term

```
E(N) = R(N) − C  =  c₁ / log N  +  O(1 / log² N)
```

The convergence rate is 1/log N — the same slow logarithmic rate seen across
prime number theorem type results. The leading coefficient is explicitly:

```
c₁ = −C · Σ_{p prime}  log p / (p² − 2)
```

This sum over primes converges. The sign of c₁ is negative, meaning R(N)
approaches C from below.

### The Mod-4 / Farey / χ₄ Connection to RH

The route to the Riemann Hypothesis runs through the mod-4 residue
structure. Integers r with gcd(r, 4) = 1 — that is r ≡ 1 or 3 (mod 4) —
are exactly the support of the Dirichlet character χ₄. Restricting the Lift
Survival sum to this sublattice and scaling by a factor of 4 (the conductor)
produces a discrepancy function formally equivalent to the Farey sequence
discrepancy twisted by χ₄.

Under this ×4 normalisation, the completed L-function Λ(s, χ₄) satisfies
the functional equation Λ(s, χ₄) = Λ(1−s, χ₄), forcing the ξ-function to
be real-valued on the critical line. The non-trivial zeros of L(s, χ₄)
therefore appear as literal real numbers (values of the imaginary part t).
The mod-4 restriction selects χ₄ over ζ(s), and the ×4 conductor scaling
is what makes the zeros real in this sense.

Sign changes of E(N) restricted to gcd(r, 4) = 1 are therefore a direct
numerical probe of the zeros of L(s, χ₄) via a genuine Franel–Landau
criterion — not merely an analogy with it.

---

## Three Convergence Tests (Explorer Charts)

| Chart | What it plots | What it confirms |
|-------|--------------|-----------------|
| 01 | \|E(N)\| with A/log N envelope | Convergence rate is 1/log N |
| 02 | E(N) · log N | Flattens toward constant c₁ |
| 03 | log\|E(N)\| vs log(log N) | Slope → −1 confirms 1/log N |

---

## Files

| File | Description |
|------|-------------|
| `EN_opener-1.html` | Landing page — mathematical introduction, animated R(N) hero, three chart previews, mod-4 RH panel, project links |
| `EN_explorer-1.html` | Interactive explorer — full three-chart engine with adjustable N range *(linked, not yet in this repo)* |

### Companion Pages (hosted)

| URL | Content |
|-----|---------|
| `wessengetachew.github.io/Sierpi-ski/` | The Jump Theorem — modular ring structure and derivation of C |
| `wessengetachew.github.io/Zeta/` | Zeta connection — C within Euler products, Dirichlet characters, GRH |
| `wessengetachew.github.io/Primes/` | Prime visualizations — D(x), twin prime filtering, Euler product convergence |

---

## Performance Notes

The opener page has been optimized for mobile:

- All canvas animations run in a **single merged RAF loop** (was 4 separate loops)
- `ctx.shadowBlur` removed — it is the single most expensive canvas operation
  on mobile GPUs and was causing processor crashes on devices such as the
  Galaxy S10
- **30 fps cap on touch devices**, 60 fps on desktop
- Stars reduced to **60 on mobile**, 140 on desktop
- Static grid pre-drawn to an **offscreen canvas** and blitted each frame
- Custom cursor and its RAF loop are **disabled on touch devices**
- Animation **pauses automatically** when the tab is backgrounded
  (Page Visibility API)



## How to Run

Open `TheError` in any modern browser. No build step, no server, no
dependencies to install. Works fully offline after the initial Google Fonts
request (fonts degrade gracefully if offline).

---

## Author

**Wessen Getachew** · 2026  
`E(N) = R(N) − C = O(1 / log N)`
