---
source: sources/wiki-Downsampling_signal_processing.md
source_url: https://en.wikipedia.org/wiki/Downsampling_(signal_processing)
---

## Downsampling and Decimation in Digital Signal Processing

This page covers the process of reducing the sample rate of a digital signal, known as downsampling or decimation. It explains the two-step process (anti-aliasing filtering followed by sample-rate reduction), the mathematical foundations via the DTFT, efficient implementation using polyphase filters, and extension to rational rate conversion factors.

## Key Concepts

- **Downsampling, subsampling, compression, decimation** are related terms for reducing sample rate in a multi-rate DSP system
- **Decimation by factor M** means keeping only every Mth sample — this divides the sampling rate by M (or equivalently multiplies the sampling interval by M)
- **Two-step process for integer downsampling**: (1) lowpass filter to remove high-frequency components, then (2) keep every Mth sample
- **Aliasing** occurs if step 2 is performed without the anti-aliasing filter — high-frequency components fold into the lower frequency band
- **Anti-aliasing filter cutoff**: must be below 0.5/(M·T) to prevent spectral overlap after decimation, where T is the original sampling interval and M is the decimation factor
- **FIR vs IIR implementation**: FIR filters allow computing only every Mth output directly (efficient); IIR filters require computing every output due to feedback dependencies
- **Polyphase filter**: the FIR filter's impulse response is decomposed into M subsequences (phases); each phase filters a demultiplexed stream of the input independently, and outputs are summed — enables parallel/multi-processor implementations
- **Half-band filter**: when M=2, nearly half the filter coefficients are zero, reducing computation
- **First Noble identity**: the mathematical equivalence between the polyphase implementation and the naive zero-stuffing approach; used in derivations but not practical implementations
- **Decimation reduces DTFT periodicity and amplitude by factor M** — the periodic summation of the spectrum becomes M times less frequent

## Commands and Syntax

- **Decimating FIR filter computation** (dot product for nth output sample):
  ```
  y[n] = Σ(k=0 to K-1) x[nM - k] · h[k]
  ```
  where h[k] is the impulse response of length K, x[·] is the input sequence, and M is the decimation factor

- **Anti-aliasing filter cutoff condition**:
  ```
  B < 0.5/T · 1/M
  ```
  where B is the signal bandwidth, T is the original sampling period, M is the decimation factor

- **Rational rate conversion (M/L, where M > L)**:
  1. Upsample (interpolate) by factor L
  2. Decimate by factor M
  3. Use a single lowpass filter with cutoff = 0.5/M cycles per intermediate sample (the lower of the two required cutoffs)

- **Example**: CD audio at 44,100 samples/sec decimated by 5/4 yields 35,280 samples/sec

## Relationships

- **Upsampling/Interpolation**: the inverse operation — increases sample rate; combined with downsampling enables rational rate conversion
- **Anti-aliasing filter**: essential preprocessing step; connects to lowpass filter design theory
- **Aliasing**: the artifact that decimation without filtering produces; central motivation for the anti-aliasing step
- **Sample-rate conversion**: the general category encompassing both upsampling and downsampling
- **Multi-rate digital signal processing**: the broader field in which decimation is a fundamental operation
- **Polyphase filters**: an efficient implementation structure derived from the decimation process; connects to filter bank theory
- **Nyquist-Shannon sampling theorem**: theoretical foundation — decimation effectively resamples at a lower rate, so Nyquist conditions must be maintained
- **Wavelets and filter banks**: polyphase decomposition connects directly to wavelet filter bank structures (Strang & Nguyen)
- **Bandpass decimation / undersampling**: related technique for decimating bandpass signals rather than baseband

## Exam-Relevant Points

- Decimation by M keeps every Mth sample and **divides** the sampling rate by M
- The two-step decimation process is: **(1) lowpass filter, (2) downsample** — order matters; filtering must come first
- Anti-aliasing filter maximum cutoff frequency: **B < 0.5/(M·T)** — know this formula
- FIR filters are preferred for decimation because only every Mth output needs to be computed, saving computation
- **Polyphase decomposition** splits a length-K FIR filter into M sub-filters operating on demultiplexed input streams — key efficiency technique
- For M=2, a **half-band filter** has approximately half zero-valued coefficients
- **Rational rate conversion M/L**: upsample by L first, then decimate by M; a single filter at the lower cutoff frequency (0.5/M) handles both anti-imaging and anti-aliasing
- The **First Noble identity** establishes equivalence between polyphase filtering and the naive (inefficient) zero-padded approach
- Decimation reduces the DTFT's periodicity by factor M — spectral copies move closer together, which is why aliasing becomes a risk
- Realizable filters have a transition band ("skirt"), so practical cutoff must be placed **below** the theoretical maximum to ensure adequate alias suppression
