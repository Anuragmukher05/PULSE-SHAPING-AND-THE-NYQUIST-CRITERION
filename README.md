# PULSE-SHAPING-AND-THE-NYQUIST-CRITERION

Experiment 7 — Pulse Shaping and the Nyquist Criterion

   

A Digital Communication Laboratory experiment that demonstrates and compares Rectangular, Sinc, Raised-Cosine (RC), and Root-Raised-Cosine (RRC) pulse shaping and verifies the Nyquist zero-ISI criterion.

This repository contains implementations for both MATLAB and Python/Google Colab.


---

📌 Objectives

The main objectives of this experiment are:

Generate a rectangular pulse.

Generate an ideal sinc pulse.

Generate Raised-Cosine (RC) pulses.

Generate Root-Raised-Cosine (RRC) pulses.

Study the effect of the roll-off factor α.

Analyze the frequency response of RC and RRC filters.

Generate a BPSK symbol sequence.

Perform RC pulse shaping.

Verify the Nyquist zero-crossing condition.

Demonstrate RRC transmitter and receiver matched filtering.

Study the relationship between bandwidth and roll-off factor.



---

📂 Repository Structure

experiment-7-pulse-shaping-nyquist/
│
├── README.md
├── LICENSE
├── requirements.txt
├── .gitignore
│
├── matlab/
│   └── EXP7_Pulse_Shaping_Nyquist.m
│
├── colab/
│   ├── Experiment_7_Pulse_Shaping_Nyquist.ipynb
│   └── experiment_7_pulse_shaping.py
│
└── figures/
    ├── 01_raised_cosine.png
    ├── 02_root_raised_cosine.png
    ├── 03_pulse_comparison.png
    ├── 04_rc_frequency_response.png
    ├── 05_rrc_frequency_response.png
    ├── 06_rc_bpsk_pulse_shaping.png
    ├── 07_rrc_tx_rx_cascade.png
    └── 08_bandwidth_vs_rolloff.png


---

⚙️ Simulation Parameters

Parameter	Value

Symbol period Ts	1 s
Samples per symbol	16
Sampling frequency Fs	16 Hz
Filter span	±8 symbols
Roll-off factors α	0, 0.25, 0.5, 1
Number of BPSK symbols	20
FFT size	8192
Test roll-off factor	0.5



---

📐 Theory

1. Sinc Pulse

The ideal Nyquist pulse is given by:

\[
h(t)=\operatorname{sinc}\left(\frac{t}{T_s}\right)
\]

or

\[
h(t)=
\frac{\sin(\pi t/T_s)}
{\pi t/T_s}
\]

The sinc pulse has zero crossings at integer multiples of the symbol period:

\[
t=nT_s,\quad n\neq0
\]

This makes it an ideal zero-ISI pulse.


---

2. Raised-Cosine Pulse

The Raised-Cosine pulse is defined as:

\[
h_{RC}(t)=
\operatorname{sinc}\left(\frac{t}{T_s}\right)
\frac{\cos(\pi\alpha t/T_s)}
{1-(2\alpha t/T_s)^2}
\]

where:

\(T_s\) = symbol period

\(\alpha\) = roll-off factor


The roll-off factor satisfies:

\[
0\leq\alpha\leq1
\]

Effect of α

α = 0 → minimum theoretical bandwidth

α = 0.25 → small excess bandwidth

α = 0.5 → commonly used practical value

α = 1 → maximum roll-off


Increasing α increases bandwidth but makes the time-domain pulse more localized.


---

3. Root-Raised-Cosine Pulse

The RRC pulse used in this experiment is:

\[
h_{RRC}(t)=
\frac{
\sin[\pi t(1-\alpha)/T_s]
+
4\alpha(t/T_s)
\cos[\pi t(1+\alpha)/T_s]
}
{
\pi(t/T_s)
[1-(4\alpha t/T_s)^2]
}
\]

The RRC filter is commonly divided between the transmitter and receiver.

Ideally:

\[
H_{RRC}(f)H_{RRC}(f)=H_{RC}(f)
\]

Therefore:

\[
RRC * RRC \rightarrow RC
\]


---

📡 Nyquist Criterion

For zero inter-symbol interference, the overall pulse response must satisfy:

\[
h(nT_s)=
\begin{cases}
1, & n=0\\
0, & n\neq0
\end{cases}
\]

In this experiment, the RC pulse with:

\[
\alpha=0.5
\]

is sampled at:

\[
n=-5,-4,\ldots,0,\ldots,+4,+5
\]

The expected result is approximately:

n = 0       h(nTs) ≈ 1
n ≠ 0       h(nTs) ≈ 0

This verifies the Nyquist zero-ISI criterion.


---

📊 Results

1. Raised-Cosine Impulse Response

The experiment generates RC impulse responses for:

α = 0
α = 0.25
α = 0.5
α = 1




---

2. Root-Raised-Cosine Impulse Response

The RRC impulse response is generated for the same roll-off factors.




---

3. Pulse Shape Comparison

The experiment compares:

Rectangular pulse

Sinc pulse

RC pulse

RRC pulse





---

4. Raised-Cosine Frequency Response

The frequency response demonstrates the effect of roll-off factor on bandwidth.




---

5. Root-Raised-Cosine Frequency Response

The RRC frequency response is also analyzed for different values of α.




---

6. BPSK Pulse Shaping

A random BPSK sequence is generated and shaped using an RC pulse.




---

7. RRC Transmitter and Receiver

The experiment demonstrates matched filtering using:

BPSK symbols
      ↓
RRC Transmitter
      ↓
Channel
      ↓
RRC Receiver
      ↓
Overall RC Response




---

8. Bandwidth vs Roll-Off Factor

The theoretical bandwidth of a Raised-Cosine filter is:

\[
B=\frac{1+\alpha}{2T_s}
\]

Therefore, bandwidth increases linearly with the roll-off factor.




---

🖥️ MATLAB Implementation

The MATLAB implementation is located at:

matlab/EXP7_Pulse_Shaping_Nyquist.m

Running the MATLAB Code

1. Open MATLAB.


2. Open EXP7_Pulse_Shaping_Nyquist.m.


3. Run the script.


4. The program generates the required plots and displays the Nyquist verification results in the Command Window.



Important

The MATLAB implementation is written as a single script without local function definitions.

This avoids the MATLAB error:

Function definitions are not permitted in this context.

The RC and RRC equations are implemented directly inside the script.


---

☁️ Google Colab Implementation

The Google Colab notebook is located at:

colab/Experiment_7_Pulse_Shaping_Nyquist.ipynb

The Python implementation uses:

NumPy

Matplotlib


Running in Google Colab

1. Open Google Colab.


2. Upload the .ipynb file.


3. Run the notebook.


4. The plots and numerical verification will be generated automatically.



A standalone Python file is also provided:

colab/experiment_7_pulse_shaping.py


---

📦 Requirements

For the Python implementation:

numpy>=1.23
matplotlib>=3.6

Install using:

pip install -r requirements.txt

Google Colab normally already includes these libraries.


---

🔬 Key Observations

Observation 1 — Roll-off factor

Increasing α increases the occupied bandwidth.

Observation 2 — Zero ISI

The RC pulse has zero crossings at integer multiples of Ts, except at the central sampling point.

Observation 3 — RRC matched filtering

Two matched RRC filters produce an overall response approaching the RC response.

Observation 4 — Bandwidth

The theoretical bandwidth is:

\[
B=\frac{1+\alpha}{2T_s}
\]

Thus, bandwidth increases linearly with α.


---

✅ Conclusion

This experiment demonstrates the importance of pulse shaping in digital communication systems.

The following conclusions are obtained:

1. The sinc pulse is the ideal Nyquist pulse.

2. Raised-Cosine filtering provides a practical method for achieving zero ISI.

3. The roll-off factor controls the trade-off between bandwidth and time-domain characteristics.

4. Increasing the roll-off factor increases the required bandwidth.

5. RRC filtering can be divided between transmitter and receiver.

6. Cascaded RRC filters produce an overall RC response.

7. The RC pulse satisfies the Nyquist zero-ISI criterion at integer symbol intervals.




---

🧰 Technologies Used

MATLAB

Python

NumPy

Matplotlib

Google Colab

Digital Communication Theory





This project is provided for educational and laboratory purposes.

Released under the MIT License.
