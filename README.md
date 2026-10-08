# Bosons and Fermions, Interactively

An interactive, single-page web demo of quantum statistics for identical particles: why counting states changes when particles are indistinguishable, when that starts to matter, and how it leads to the Fermi–Dirac and Bose–Einstein distributions.

Created by **Claude Opus 5.5**, based on the lecture notes by **Sang Hoon Lee** (Chapter 7, Quantum Statistics; Section 7.2, Bosons and Fermions). It is a companion to the grand canonical ensemble demo for Section 7.1.

## What's inside

**Counting states.** Place *N* noninteracting particles in *Z*<sub>1</sub> single-particle states of zero energy, so the partition function simply counts system states. Switch between distinguishable particles, bosons, and fermions and see every system state drawn as a row of boxes. The default reproduces the lecture example of 2 particles in 5 states:

| Counting | Formula | 2 particles, 5 states |
| --- | --- | --- |
| Distinguishable | Z<sub>1</sub><sup>N</sup> | 25 = 10 × 2 + 5 × 1 |
| The 1/N! shortcut | Z<sub>1</sub><sup>N</sup>/N! | 12.5 = 10 + 5 × ½ |
| Bosons | C(Z<sub>1</sub> + N − 1, N) | 15 |
| Fermions | C(Z<sub>1</sub>, N) | 10 |

The decomposition under the boxes shows exactly where the 1/*N*! shortcut goes wrong: it counts states with all particles in different single-particle states correctly but gives doubly occupied ones a fractional weight. A log-scale chart shows the boson and fermion counts converging to the shortcut as *Z*<sub>1</sub> ≫ *N*.

**Who may share a state.** Bosons (integer spin) versus fermions (half-integer spin), and the Pauli exclusion principle, which crosses out every doubly occupied state.

**When does it matter?** The quantum volume v<sub>Q</sub> = ℓ<sub>Q</sub><sup>3</sup> = (h/√(2πm k<sub>B</sub>T))<sup>3</sup> and the condition V/N ≫ v<sub>Q</sub>. Particles are drawn at their average spacing with halos the size of their de Broglie wavelength. Presets cover air at room temperature (spacing about 3 nm, wavelength about 0.02 nm, as in the lecture), liquid helium-4, conduction electrons in copper, and a neutron star; sliders let you vary the particle, temperature, and density.

**The distribution functions.** The derivation treating one single-particle state as the system and all other states as the reservoir, leading to

```
n̄_FD        = 1 / (exp[(ε − μ)/k_B T] + 1)     Fermi–Dirac
n̄_BE        = 1 / (exp[(ε − μ)/k_B T] − 1)     Bose–Einstein (ε > μ only)
n̄_Boltzmann = exp[−(ε − μ)/k_B T]
```

An interactive chart plots all three against energy, with sliders for μ and k<sub>B</sub>T and a movable probe energy. A second chart shows the probe state's occupation probabilities *P*(*n*): empty or full for fermions, geometric for bosons. A logarithmic axis makes the classical limit, ε − μ ≫ k<sub>B</sub>T, easy to see.

## Running it

There is nothing to build or install. The whole demo is one self-contained file, `index.html`, with all CSS and JavaScript inline.

Open it locally by double-clicking `index.html`, or serve the folder:

```bash
python3 -m http.server 8000
# then visit http://localhost:8000
```

### Publishing with GitHub Pages

1. Push this repository to GitHub.
2. Go to **Settings → Pages**.
3. Under **Build and deployment**, choose **Deploy from a branch**, select your main branch and the `/ (root)` folder, then save.
4. After a minute or so, the demo will be live at `https://<your-username>.github.io/<repository-name>/`.

## Technical notes

- Plain HTML, CSS, and vanilla JavaScript drawn on `<canvas>`. No frameworks, no build step.
- Equations are typeset with [MathJax 3](https://www.mathjax.org/) (SVG output, loaded from cdnjs), so they need no extra web fonts.
- The only other external resources are the Newsreader and Instrument Sans fonts from Google Fonts, with system font fallbacks if they fail to load.
- Opening the page requires an internet connection for MathJax; offline, the equations appear as raw TeX.
- Supports light and dark mode: it follows `prefers-color-scheme`, and a sun/moon button in the top-right corner switches by hand (the choice is remembered across pages); and is responsive down to phone widths.
- Constants used: h = 6.626 × 10<sup>−34</sup> J s, k<sub>B</sub> = 1.381 × 10<sup>−23</sup> J/K.

## Caveats

- Material values in the presets are representative: liquid helium-4 at 2 K with density 145 kg/m³, copper with 8.49 × 10<sup>28</sup> conduction electrons per m³, and a neutron star interior at about 10<sup>8</sup> K and nuclear density.
- Photons are quantum too, but they are massless, so the quantum-volume formula doesn't apply to them; they are treated separately later in the chapter.
- The energy scale in the distribution chart (in eV) is illustrative; the shapes depend only on (ε − μ)/k<sub>B</sub>T.

## Credits

- Demo: Claude Opus 5.5
- Physics content and examples: lecture notes by Sang Hoon Lee
- The lecture follows Daniel V. Schroeder, *An Introduction to Thermal Physics* (Problems 6.44 and 7.6 are referenced).

## License

No license has been chosen yet. Add a `LICENSE` file (for example, MIT or CC BY 4.0) before sharing or reusing this project publicly, and confirm that any use of the lecture material is permitted by its author.
