<!--
  Name     : README.md
  Purpose  : Overview of the UHF log-periodic antenna calculator (GitHub repository)
  Author   : Eric Perret (ericperret)
  Date     : 2026-10-27
  Version  : 1.7
  License  : CC BY-NC 4.0 — commercial use forbidden without the author's written permission (eperret@azs.fr)
-->

# UHF log-periodic dipole antenna (LPDA) — calculator and drilling plan

🇫🇷 [Version française : LISEZMOI.md](LISEZMOI.md)

▶️ **[Launch the calculator](https://ericperret.github.io/lpda/lpda_uhf.html)** — results update on every input.

![UHF LPDA calculator v1.7: summary, cut list, top views (assembled, upper boom, lower boom) and side view](screenshot.png)

A standalone calculator (one single HTML file) for a log-periodic antenna built on two square booms, for the UHF band.
From the wanted band and the number of dipoles, it gives the cut lengths, the optimum angle, the drilling positions and a scale plan ready to print.

User interface in French. No installation, no library, no network connection required.

## Usage

1. Open the link above, or download `lpda_uhf.html` and open it in a recent browser.
2. Enter the band (f_bas = low, f_haut = high), the number of pairs N and the mechanics (boom side, overhang, gap between booms, element Ø, total boom margin: half at the tip, half at the tail).
3. Results update on every input; **Imprimer le plan** (print the plan) prints the plan without the input fields.

## Features

| Feature | Description |
|---|---|
| Summary | τ (scale factor), σ (spacing), apex angle 2α, estimated gain, boom length to cut, longest element half |
| Cut and drilling list | For each position: orientation of the half-elements, resonant frequency, K factor, dipole length, cut length of one half (×2), spacing, position from the boom edge |
| Top view | Scale plan: red (upper boom) and green (lower boom) half-elements alternating at each position, dimensions, 100 mm scale bar |
| Side view | Two stacked booms, same mirrored drilling, gap |
| Printing | Dedicated layout: summary, list and plan only |
| Checks | Invalid inputs and σ ≤ 0 (too few elements for the band) are flagged |

## Method

- Scale factor: τ = (f_low / f_high)^(1/(N−1)).
- Spacing for maximum gain (Carrel): σ = 0.243·τ − 0.051.
- Apex half-angle: tan α = (1 − τ) / (4σ).
- Dipole length: L = K · λ/2, with K corrected for the slenderness L/Ø: K = 0.975 − 0.18/√(L/Ø), bounded between 0.90 and 0.98.
- Position of each element from the virtual apex: x = (L/2) / tan α.
- Cut length of one half = L/2 (measured from the boom centre) + half the boom side + overhang.
- Estimated gain: saturating rise with N, ceiling around 11 dBi (practical limit of a simple LPDA), slightly lower for a wide band.

## Limitations

Preliminary design tool. The gain is an estimate; the 50 Ω matching (stub at the rear) and the radiation pattern are not computed. Final tuning with an antenna analyser is still required.

## History

| Version | Change |
|---|---|
| 1.1 | Automatic K factor from L/Ø; top and side views, red / green booms |
| 1.5 | Gain estimated by a saturating rise with N; boom cutting margin; cut measured from the boom centre |
| 1.6 | AZS visual identity (dark theme on screen, AZS band linking back to www.azs.fr); the plan stays on a white sheet and printing is unchanged |
| 1.7 | Total boom margin split half at the tip, half at the tail and drawn on the plan; warning when less than 5 mm of metal remains between the hole and the boom end; separate top views of the upper (red) and lower (green) booms with each element's cut length and side; plan labels kept inside the frame |

## License

**Free for non-commercial use** — [CC BY-NC 4.0](https://creativecommons.org/licenses/by-nc/4.0/), with mandatory credit of the source and the author:

> lpda — Eric PERRET — https://github.com/ericperret/lpda

Any commercial use is forbidden without the author's written permission, requested by e-mail: **eperret@azs.fr**.
Full terms (French / English): [LICENSE](LICENSE).
