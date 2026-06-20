---
source: sources/wiki-Time_series.md
source_url: https://en.wikipedia.org/wiki/Time_series
---

## Time Series Analysis: Concepts, Methods, and Models

Time series analysis is the study of data points indexed in chronological order. This page covers the definition of time series, methods for analyzing them (frequency-domain vs. time-domain), classical and non-linear models (AR, ARMA, ARIMA, GARCH), and applications spanning forecasting, classification, segmentation, and clustering.

## Key Concepts

- A **time series** is a sequence of data points indexed in chronological order, typically at equally spaced intervals, representing discrete-time data
- **Time series analysis** extracts meaningful statistics and characteristics from temporal data; **time series forecasting** uses models to predict future values from past observations
- Time series data is generally modeled as a **stochastic process** — observations closer in time are more closely related than distant ones
- Time series analysis is distinct from **cross-sectional studies** (no natural ordering) and **spatial data analysis** (geographic ordering)
- A time series is a one-dimensional case of **panel data**; panel data requires both a time field and an additional identifier (e.g., stock symbol, country code)
- Time series can apply to real-valued continuous data, discrete numeric data, or discrete symbolic data (e.g., character sequences)
- Two foundational conditions: **stationarity** (statistical properties constant over time) and **ergodicity** (time averages equal ensemble averages); ergodicity implies stationarity but not vice versa
- Stationarity is classified into **strict stationarity** and **wide-sense (second-order) stationarity**

## Commands and Syntax

- **Notation**: A time series X indexed by natural numbers: X = (X₁, X₂, ...) or Y = (Yₜ : t ∈ T) where T is the index set
- **Software for forecasting**: Julia, Python, R, SAS, SPSS; large-scale forecasting via Apache Spark with the Spark-TS library; models collected in the Python package `sktime`

## Relationships

- **Analysis method taxonomy**:
  - **By domain**: Frequency-domain (spectral analysis, wavelet analysis) vs. time-domain (autocorrelation, cross-correlation, scaled correlation)
  - **By assumptions**: Parametric (assume structure, estimate parameters — e.g., AR, MA) vs. non-parametric (estimate covariance/spectrum directly)
  - **By linearity**: Linear vs. non-linear
  - **By dimensionality**: Univariate vs. multivariate
- **Classical linear models hierarchy**: AR → MA → ARMA → ARIMA → ARFIMA; extend with "V" prefix for vector (multivariate) variants (e.g., VAR), "X" suffix for exogenous inputs
- **TVAR models**: Time-varying autoregressive models generalize AR by allowing coefficients to change over time; estimated via kernel smoothing, recursive least squares, or Kalman filtering
- **Non-linear models**: ARCH/GARCH family models changing variance (heteroskedasticity); also nonlinear autoregressive exogenous (NARX) models; can produce chaotic behavior
- **Other modeling approaches**: Hidden Markov Models (HMMs, used in speech recognition), dynamic Bayesian networks, wavelet-based model-free methods, Markov switching multifractal (MSMF)
- **Analysis tasks**: Exploratory analysis, curve fitting (interpolation vs. smoothing vs. regression), function approximation, prediction/forecasting, classification, segmentation (change-point detection), clustering
- **Curve fitting subtleties**: Interpolation gives exact fit; smoothing gives approximate fit; regression focuses on statistical inference and uncertainty; extrapolation goes beyond observed range with higher uncertainty
- **Clustering caveat**: Subsequence time series clustering via sliding windows produces unstable/random clusters — cluster centers converge to arbitrary sine patterns regardless of dataset

## Exam-Relevant Points

- Know the distinction: time series vs. cross-sectional vs. panel data — differentiated by what makes a record unique (time alone = time series; time + identifier = panel; non-time identifier = cross-sectional)
- The model hierarchy AR → MA → ARMA → ARIMA → ARFIMA and when each applies (stationarity assumptions, integration order)
- Frequency-domain methods (spectral analysis, wavelet analysis) vs. time-domain methods (autocorrelation, cross-correlation) — two fundamental analysis classes
- Parametric vs. non-parametric: parametric assumes structure with few parameters; non-parametric estimates covariance/spectrum without structural assumptions
- Ergodicity implies stationarity, but stationarity does not imply ergodicity
- ARCH/GARCH models specifically address **time-varying variance** (heteroskedasticity), not level changes
- Interpolation = estimation between known points; extrapolation = estimation beyond known range (higher uncertainty)
- Subsequence clustering with sliding windows is fundamentally flawed — produces meaningless sine-wave cluster centers
- Kalman filter operates in the time domain and is equivalent to frequency-domain filtering/smoothing approaches
- Key investigative tools: autocorrelation function (ACF), spectral density function, Fourier transform, PCA/EOF analysis, singular spectrum analysis, dynamic time warping
