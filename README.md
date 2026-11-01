# ANSYS Simulation: Straight Pipe vs. Muffler Pipe Acoustic Analysis

## Overview

This project presents an ANSYS numerical simulation comparing the acoustic and flow performance of a simple straight pipe against a reactive expansion-chamber muffler system. The objective is to evaluate how the geometric expansion affects sound pressure level (SPL) attenuation, pressure drop, and acoustic performance (Transmission Loss).

## Audio Observations & Acoustic Perception

Listening to the simulated acoustic outputs (`No_Mufler_Sound.wav` vs. `Mufler_Sound.wav`) reveals clear perceptual differences caused by the acoustic expansion chamber:

* **Straight Pipe Audio (`No_Mufler_Sound.wav`):**
  * **Sound Profile:** Loud, harsh, and unfiltered continuous tone.
  * **Frequency Response:** Dominant high-frequency sound waves pass through without resistance, leading to a sharp, buzzing tone.
  * **Perceptual Volume:** Significantly higher Sound Pressure Level (SPL) with full sound transmission from source to outlet.

* **Muffler Pipe Audio (`Mufler_Sound.wav`):**
  * **Sound Profile:** Deep, muffled, and heavily attenuated tone.
  * **Frequency Response:** Higher frequencies and harsh upper harmonics are suppressed due to wave interference inside the expansion chamber.
  * **Perceptual Volume:** Noticeable reduction in overall perceived loudness (dB SPL drop), resulting in a smoother, low-pass filtered sound.

---

## Geometry Specifications

### 1. Straight Pipe Baseline

A uniform cylindrical pipe serving as the baseline for acoustic comparison.

* **Inner Diameter (**$d$**):** $50\text{ mm}$
* **Total Length (**$L_{total}$**):** $500\text{ mm}$
* **Cross-sectional Area (**$A_1$**):** $1963.5\text{ mm}^2$ ($\approx 1.9635 \times 10^{-3}\text{ m}^2$)

### 2. Pipe with Expansion Chamber Muffler

A three-stage expansion chamber assembly designed to attenuate noise via acoustic impedance mismatching.

* **Inlet Pipe:**
  * Diameter ($d_{in}$): $50\text{ mm}$
  * Length ($L_{in}$): $100\text{ mm}$
* **Muffler Chamber (Expansion Chamber):**
  * Diameter ($D_{muffler}$): $200\text{ mm}$
  * Length ($L_{muffler}$): $300\text{ mm}$
  * Cross-sectional Area ($A_2$): $31415.9\text{ mm}^2$ ($\approx 3.1416 \times 10^{-2}\text{ m}^2$)
* **Outlet Pipe:**
  * Diameter ($d_{out}$): $50\text{ mm}$
  * Length ($L_{out}$): $100\text{ mm}$
* **Total Length (**$L_{total}$**):** $100\text{ mm} + 300\text{ mm} + 100\text{ mm} = 500\text{ mm}$

---

## Geometric Comparison Matrix

| Parameter | Straight Pipe | Pipe with Muffler | Difference / Ratio | 
| ----- | ----- | ----- | ----- | 
| **Total Length (**$L$**)** | $500\text{ mm}$ | $500\text{ mm}$ | Identical ($1:1$) | 
| **Min. Diameter (**$d$**)** | $50\text{ mm}$ | $50\text{ mm}$ | Identical | 
| **Max. Diameter (**$D$**)** | $50\text{ mm}$ | $200\text{ mm}$ | $4\times$ increase in diameter | 
| **Expansion Ratio (**$m = \frac{A_2}{A_1}$**)** | $1.0$ | $16.0$ | $16\times$ cross-sectional area expansion | 
| **Internal Volume (**$V$**)** | $\approx 0.982\text{ L}$ | $\approx 9.817\text{ L}$ | $\approx 10\times$ volume expansion | 

---

## Theoretical & Simulation Background

### Acoustic Transmission Loss (TL)

The muffler operates on the principle of a **reactive expansion chamber**. When sound waves traveling through the inlet pipe encounter the sudden area expansion ($A_1 \rightarrow A_2$), a significant portion of the acoustic wave is reflected back toward the source due to the impedance mismatch.

The theoretical Transmission Loss ($TL$) for a simple expansion chamber is given by:

$$
TL = 10 \log_{10} \left[ 1 + \frac{1}{4} \left( m - \frac{1}{m} \right)^2 \sin^2(k L_{muffler}) \right]
$$

Where:

* $m = \frac{A_2}{A_1} = \left(\frac{D}{d}\right)^2 = \left(\frac{200}{50}\right)^2 = 16$
* $k = \frac{2\pi f}{c}$ is the acoustic wavenumber ($c \approx 343\text{ m/s}$ in air at room temperature).
* $L_{muffler} = 0.3\text{ m}$.

### Maximum Theoretical Attenuation

At resonant peak frequencies where $\sin^2(k L_{muffler}) = 1$:

$$
TL_{max} = 10 \log_{10} \left[ 1 + \frac{1}{4} \left( 16 - \frac{1}{16} \right)^2 \right] \approx 18.06\text{ dB}
$$

---

## ANSYS Simulation Results Comparison Summary

### 1. Acoustic / Sound Pressure Level (SPL)

* **Straight Pipe:** Sound waves propagate with minimal attenuation along the length. Acoustic pressure amplitude remains high at the exit.
* **Muffler Pipe:** High noise attenuation is achieved across periodic frequency bands. Destructive interference inside the $300\text{ mm}$ chamber significantly reduces downstream acoustic energy.

### 2. Fluid Dynamics & Pressure Drop ($\Delta P$)

* **Straight Pipe:** Low static pressure drop across the $500\text{ mm}$ length; smooth flow field without flow separation.
* **Muffler Pipe:** Higher static pressure drop (backpressure) due to recirculation zones, turbulent eddies, and sudden expansion/contraction loss coefficients ($K_{ex}$ and $K_{con}$).

