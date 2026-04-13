# TheError
L(M) = φ(M) · φ(M+1) / (M+1)
https://github.com/wessengetachew/TheError/

# TheError
### Lift Survival Function — W. Getachew · math.NT · 2026

**Live site:** https://wessengetachew.github.io/TheError/

---

## The Mathematics

For each positive integer M, define the **lift weight**:

```
L(M) = φ(M) · φ(M+1) / (M+1)
```

This is the local joint coprimality density of the consecutive pair (M, M+1).
The formula follows from the multiplicativity of Euler's φ across coprime moduli,
since gcd(M, M+1) = 1 always holds.

The **lift ratio** accumulates these weights:

```
R(N) = Σ_{M=1}^{N} L(M)  /  Σ_{M=1}^{N} φ(M)
```

As N → ∞, R(N) converges to the **Lift Survival Constant**:

```
C = ∏_{p prime} (p² − 2) / (p² − 1)
```

The **error term** and its asymptotic expansion:

```
E(N) = R(N) − C  =  c₁ / log N  +  O(1 / log² N)

c₁ = −C · Σ_p  log p / (p² − 2)
```

### Connection to the Riemann Hypothesis

Restricting the sum to integers r with gcd(r, 4) = 1 — i.e. r ≡ 1 or 3 (mod 4),
the support of the Dirichlet character χ₄ — and scaling by the conductor ×4,
produces a discrepancy function equivalent to the Farey sequence discrepancy
twisted by χ₄. This is a genuine Franel–Landau criterion for L(s, χ₄), not
merely an analogy. Sign changes of E(N) on this sublattice are a direct
numerical probe of the zeros of L(s, χ₄).

---

## Files

| File | Description |
|------|-------------|
| `index.html` | Landing page — animated R(N) hero, mathematical introduction, three chart previews, mod-4 RH panel |
| `EN_explorer-1-2.html` | Interactive explorer — three live convergence charts, adjustable N, performance warnings |
| `README.md` | This file |

---

## Navigation

- **index.html → EN_explorer-1-2.html** via the "Open Explorer →" button
- **EN_explorer-1-2.html → index.html** via the "◁ Main" back button or the Opener tab

---

## Explorer Charts

| Chart | Plots | Confirms |
|-------|-------|---------|
| 01 | \|E(N)\| with A/log N envelope | 1/log N convergence rate |
| 02 | E(N) · log N | Flattens to constant c₁ |
| 03 | log\|E(N)\| vs log(log N) | Slope → −1 |

Default N = 500 (safe for all devices). Performance warnings appear at:
- **Mobile:** ⚠ N > 1,000 · ⛔ N > 2,500
- **Desktop:** ⚠ N > 6,000 · ⛔ N > 12,000

---

## Performance

Both pages are mobile-optimized:
- Single merged RAF loop (was 4 separate loops)
- `ctx.shadowBlur` removed (primary GPU killer on mobile)
- 30 fps cap on touch devices
- 60 stars on mobile, 140 on desktop
- Static grid pre-drawn to offscreen canvas and blitted each frame
- Custom cursor and its loop disabled on touch devices
- Animations pause via Page Visibility API when tab is backgrounded

---

## Related Repositories

| Repo | Content |
|------|---------|
| [Sierpi-ski](https://wessengetachew.github.io/Sierpi-ski/) | Jump Theorem — modular ring structure, derivation of C |
| [Zeta](https://wessengetachew.github.io/Zeta/) | Zeta connection — Euler products, Dirichlet characters, GRH |
| [Primes](https://wessengetachew.github.io/Primes/) | Prime visualizations — D(x), twin prime filtering |

---

`E(N) = R(N) − C = O(1 / log N)`
