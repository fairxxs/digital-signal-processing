# 📡 Digital Signal Processing - Python & Jupyter
**Gaukhar Assyrzhanova** | Hochschule Schmalkalden, Germany (Academic Mobility 2025–2026)

DSP laboratory work completed during academic exchange at **Hochschule Schmalkalden (HSM), Germany**. All experiments implemented in **Python** using NumPy, SciPy, and Matplotlib inside Jupyter Notebook. Hardware measurements verified with an **Agilent Technologies oscilloscope**.

---

## 🛠 Tools & Technologies
| Tool | Purpose |
|------|---------|
| Python (Jupyter Notebook) | Signal generation, filtering, visualization |
| NumPy | Array operations, FFT computation |
| SciPy (`scipy.signal`) | FIR/IIR filter design and application |
| Matplotlib | Spectrum and waveform plotting |
| Agilent Oscilloscope | Hardware signal verification |
| `.wav` file processing | Real-world audio signal analysis |

---

## 📁 Lab Reports

---

### 🔬 Lab 1 - Function Generator & Oscilloscope
**File:** `LabworkDSPGAD.pdf` / `DSPLabw_GAUKHAR_group_proj.pdf`

**What it covers:**
- Measured signal parameters (Vpp, Vrms, dBV) using Agilent oscilloscope at 25 kHz sampling
- Calculated FFT frequencies for aliased signals: fs–f0 and fs+f0
- Verified results with oscilloscope screenshots (ΔX = 25 kHz, ΔY measurements in dBV)

---

### 🎵 Lab 2 - Sine & Dual Tone Signal Generation + FFT Analysis

**What it covers:**
- Generated 1 kHz sine wave at fs = 8000 Hz using NumPy
- Created dual-tone signal: `sin(2π·1000·t) + 0.5·sin(2π·1700·t)` with Gaussian noise
- Computed and plotted FFT magnitude spectrum in dB
- Implemented custom `plot_spectrum()` function for one-sided DFT visualization
- Played signals as audio with IPython `Audio()`

**Key code:**
```python
fs = 8000
f1, f2 = 1000, 1700
sine_dual = np.sin(2*np.pi*f1*t) + 0.5*np.sin(2*np.pi*f2*t)
spec = abs(np.fft.fft(sine_dual))
```

---

### 🔧 Lab 3 - FIR Filter Design (Lowpass, Highpass, Bandpass)

**What it covers:**
- Designed 3 FIR filters using `scipy.signal.firwin()` with 33 coefficients
- Lowpass (f0 = 0.125), Highpass (f0 = 0.175), Bandpass (0.125–0.225 normalized)
- Applied filters to noisy dual-tone signal with `lfilter()`
- Plotted frequency responses and filtered spectra for all 3 filters
- Audio output of each filtered signal for perceptual evaluation

**Key code:**
```python
b_lp = scs.firwin(33, 0.125)
b_hp = scs.firwin(33, 0.175, pass_zero=False)
b_bp = scs.firwin(33, [0.125, 0.225], pass_zero=False)
filtered = scs.lfilter(b_lp, 1, signal)
```

---

### 📻 Lab 4 - Real Audio Signal Processing & IIR Notch Filter

**What it covers:**

**Sputnik Beep Signal (`Sputnik.wav`):**
- Loaded and normalized real historical audio (fs = 11025 Hz, 10.58 s)
- Plotted waveform and spectrogram (NFFT = 1024, overlap = 512)
- Zoomed into first beep onset (~20 ms window)
- Detected dominant interference frequency using FFT peak detection
- Designed IIR notch filter (`iirnotch`, Q = 2000) and removed interference
- Compared original vs filtered spectrum visually and aurally

**Zarathustra Signal (`zarathustra.wav`):**
- Loaded stereo audio (fs = 16000 Hz, 29.93 s)
- Detected interference frequency: **1700.0 Hz**
- Applied IIR notch filter to suppress the interference tone
- Visualized before/after spectra for comparison

**Bandpass filtering of Sputnik:**
- Designed 101-coefficient FIR bandpass filter (800–2000 Hz)
- Applied to isolate the core Sputnik beep frequency range

**Key code:**
```python
# Notch filter to remove interference
b_notch, a_notch = scs.iirnotch(interference_freq, Q=2000, fs=fs)
filtered = scs.lfilter(b_notch, a_notch, audio)
```

---

## 📊 Skills Demonstrated
- **Signal generation** - sine, dual-tone, noisy signals in Python
- **FFT analysis** - magnitude spectrum, one-sided DFT, dB scaling
- **FIR filter design** - lowpass, highpass, bandpass via `firwin()`
- **IIR filter design** - notch filter via `iirnotch()` for interference removal
- **Real audio processing** -`.wav` file loading, normalization, spectrogram
- **Hardware verification** - Agilent oscilloscope measurements
- **Data visualization** - waveforms, spectra, spectrograms with Matplotlib

---

## 👩‍💻 About
**Gaukhar Assyrzhanova**
Industrial Engineering (IIoT) Student - Astana IT University

Academic Mobility: Hochschule Schmalkalden, Germany (Oct 2025 – Feb 2026)

📧 gokass111@gmail.com
