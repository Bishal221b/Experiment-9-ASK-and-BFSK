# Experiment 9 — ASK and BFSK (coherent vs noncoherent detection)

Toolbox-free simulation of binary ASK (on-off keying) and binary FSK over AWGN. Modulation, channel, correlators,
envelope/energy detectors, BER, FFT spectra and the orthogonality check are all implemented by hand with NumPy.
SciPy is only used for `erfc` (Q-function) and the scaled Bessel function `ive` (theoretical noncoherent-ASK BER).

## Run
* **Colab:** upload `Exp9_ASK_BFSK_Colab.ipynb`, then *Runtime → Run all* (about 1 minute).
* **Local:** `pip install -r requirements.txt && python exp9_ask_bfsk.py`

Outputs: console results table and `fig01…fig11 *.png` (waveforms, correlator outputs, spectra, histograms,
BER curves, orthogonality / inner products, BER vs tone spacing, phase sensitivity).

## What it covers
| Task | Where |
|---|---|
| 32 passband ASK / BFSK | `generate_ask`, `generate_bfsk`, Fig. 1–2 |
| 33 correlator (coherent) detection | `coherent_ask_detector`, `coherent_bfsk_detector`, Fig. 3–4 |
| 34 energy / envelope (noncoherent) detection | `noncoherent_ask_detector`, `noncoherent_bfsk_detector` |
| 35 tone-spacing vs BER | section 9, Fig. 9 |
| Mandatory inner products | section 4 (printed Gram matrix), Fig. 10 |

Design: Tb = 1 ms, Fs = 80 kHz, fc = 5 kHz, f1 = 4 kHz, f2 = 5 kHz (integer cycles per bit, Δf·Tb = 1).
Eb/N0 uses the average bit energy for both schemes; sample noise variance is N0·Fs/2. Seed fixed (`default_rng(1)`).

Note: this is the Python port of the MATLAB lab script; its numbers are Python results, not MATLAB results.
