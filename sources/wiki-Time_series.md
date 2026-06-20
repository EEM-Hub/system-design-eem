---
source: https://en.wikipedia.org/wiki/Time_series
fetched: 2026-06-19
---

Sequence of data points over time Not to be confused with [*Time* (Film and TV)](./Time_(disambiguation)#Film_and_television). 

 [![](//upload.wikimedia.org/wikipedia/commons/thumb/7/77/Random-data-plus-trend-r2.png/250px-Random-data-plus-trend-r2.png)](./File:Random-data-plus-trend-r2.png)Time series: random data plus trend, with best-fit line and different applied filters 

In [mathematics](./Mathematics), a **time series** is a sequence of [data points](./Data_point) indexed, listed, or graphed in chronological order. Most commonly, a time series consists of observations recorded at successive equally spaced points in time. Thus, it represents a form of [discrete-time](./Discrete-time) data. A time series may describe measurements collected over seconds, days, years, or even centuries. Common examples include heights of ocean [tides](./Tides), counts of [sunspots](./Sunspots), daily temperature readings, and the closing values of stock market indices such as the [Dow Jones Industrial Average](./Dow_Jones_Industrial_Average).

 

A time series is often visualized using a [run chart](./Run_chart) (a type of temporal [line chart](./Line_chart)), which helps identify patterns such as trends, seasonal effects, and irregular fluctuations. Time series are widely used in [statistics](./Statistics), [actuarial science](./Actuarial_science), [signal processing](./Signal_processing), [pattern recognition](./Pattern_recognition), [econometrics](./Econometrics), [mathematical finance](./Mathematical_finance), [weather forecasting](./Weather_forecasting), [earthquake prediction](./Earthquake_prediction), [electroencephalography](./Electroencephalography), [control engineering](./Control_engineering), [astronomy](./Astronomy), [communications engineering](./Communications_engineering), and many other areas of applied [science](./Applied_science) and [engineering](./Engineering) that involve temporal measurements.

 

**Time series *analysis*** comprises methods for analyzing time series data in order to extract meaningful statistics and other characteristics of the data. **Time series *forecasting*** is the use of a [model](./Model_(abstract)) to predict future values based on previously observed values. Generally, time series data is modeled as a [stochastic process](./Stochastic_process). While [regression analysis](./Regression_analysis) is often employed in such a way as to test relationships between one or more different time series, this type of analysis is not usually called "time series analysis", which refers in particular to relationships between different points in time within a single series.

 

Time series data have a natural temporal ordering. This makes time series analysis distinct from [cross-sectional studies](./Cross-sectional_study), in which there is no natural ordering of the observations (e.g. explaining people's wages by reference to their respective education levels, where the individuals' data could be entered in any order). Time series analysis is also distinct from [spatial data analysis](./Spatial_data_analysis) where the observations typically relate to geographical locations (e.g. accounting for house prices by the location as well as the intrinsic characteristics of the houses). A [stochastic](./Stochastic) model for a time series will generally reflect the fact that observations close together in time will be more closely related than observations further apart. In addition, time series models will often make use of the natural one-way ordering of time so that values for a given period will be expressed as deriving in some way from past values, rather than from future values (see [time reversibility](./Time_reversibility)).

 

Time series analysis can be applied to [real-valued](./Real_number), continuous data, [discrete](https://en.wiktionary.org/wiki/discrete) [numeric](./Data_type#Numeric_types) data, or discrete symbolic data (i.e. sequences of characters, such as letters and words in the [English language](./English_language)[[1]](./Time_series#cite_note-1)).

 

## Methods for analysis

 

Methods for time series analysis may be divided into two classes: [frequency-domain](./Frequency-domain) methods and [time-domain](./Time-domain) methods. The former include [spectral analysis](./Frequency_spectrum#Spectrum_analysis) and [wavelet analysis](./Wavelet_analysis); the latter include [auto-correlation](./Auto-correlation) and [cross-correlation](./Cross-correlation) analysis. In the time domain, correlation and analysis can be made in a filter-like manner using [scaled correlation](./Scaled_correlation), thereby mitigating the need to operate in the frequency domain.

 

 

Additionally, time series analysis techniques may be divided into [parametric](./Parametric_estimation) and [non-parametric](./Non-parametric_statistics) methods. The parametric approaches assume that the underlying [stationary stochastic process](./Stationary_process) has a certain structure which can be described using a small number of parameters (for example, using an [autoregressive](./Autoregressive) or [moving-average model](./Moving-average_model)). In these approaches, the task is to estimate the parameters of the model that describes the stochastic process. By contrast, non-parametric approaches explicitly estimate the [covariance](./Covariance) or the [spectrum](./Spectrum) of the process without assuming that the process has any particular structure.

 

Methods of time series analysis may also be divided into [linear](./Linear_regression) and [non-linear](./Nonlinear_regression), and [univariate](./Univariate_analysis) and [multivariate](./Multivariate_analysis).

 

## Panel data

 

A time series is one type of [panel data](./Panel_data). Panel data is the general class, a multidimensional data set, whereas a time series data set is a one-dimensional panel (as is a [cross-sectional dataset](./Cross-sectional_data)).  A data set may exhibit characteristics of both panel data and time series data.  One way to tell is to ask what makes one data record unique from the other records.  If the answer is the time data field, then this is a time series data set candidate.  If determining a unique record requires a time data field and an additional identifier which is unrelated to time (e.g. student ID, stock symbol, country code), then it is panel data candidate.  If the differentiation lies on the non-time identifier, then the data set is a cross-sectional data set candidate.

 

## Analysis

 

There are several types of motivation and data analysis available for time series which are appropriate for different purposes.

 

### Motivation

 

In the context of [statistics](./Statistics), [econometrics](./Econometrics), [quantitative finance](./Quantitative_finance), [seismology](./Seismology), [meteorology](./Meteorology), and [geophysics](./Geophysics) the primary goal of time series analysis is [forecasting](./Forecasting). In the context of [signal processing](./Signal_processing), [control engineering](./Control_engineering) and [communication engineering](./Communication_engineering) it is used for signal detection. Other applications are in [data mining](./Data_mining), [pattern recognition](./Pattern_recognition) and [machine learning](./Machine_learning), where time series analysis can be used for [clustering](./Cluster_analysis),[[2]](./Time_series#cite_note-2)[[3]](./Time_series#cite_note-3)[[4]](./Time_series#cite_note-4) [classification](./Statistical_classification),[[5]](./Time_series#cite_note-5) query by content,[[6]](./Time_series#cite_note-6) [anomaly detection](./Anomaly_detection) as well as [forecasting](./Forecasting).[[7]](./Time_series#cite_note-7)

 

### Exploratory analysis

 Further information: [Exploratory analysis](./Exploratory_analysis) [![](//upload.wikimedia.org/wikipedia/commons/thumb/e/e5/Time_series_TB_US.png/250px-Time_series_TB_US.png)](./File:Time_series_TB_US.png)Time series of tuberculosis deaths in the United States 1954–2021 

A simple way to examine a regular time series is manually with a [line chart](./Line_chart). The datagraphic shows tuberculosis deaths in the United States,[[8]](./Time_series#cite_note-8) along with the yearly change and the percentage change from year to year. The total number of deaths declined in every year until the mid-1980s, after which there were occasional increases, often proportionately - but not absolutely - quite large.

 

A study of corporate data analysts found two challenges to exploratory time series analysis: discovering the shape of interesting patterns, and finding an explanation for these patterns.[[9]](./Time_series#cite_note-9) Visual tools that represent time series data as [heat map matrices](./Heat_map) can help overcome these challenges.

 

### Estimation, filtering, and smoothing

 

This approach may be based on [harmonic analysis](./Harmonic_analysis) and filtering of signals in the [frequency domain](./Frequency_domain) using the [Fourier transform](./Fourier_transform), and [spectral density estimation](./Spectral_density_estimation). Its development was significantly accelerated during [World War II](./World_War_II) by mathematician [Norbert Wiener](./Norbert_Wiener), electrical engineers [Rudolf E. Kálmán](./Rudolf_E._Kálmán), [Dennis Gabor](./Dennis_Gabor) and others for filtering signals from noise and predicting signal values at a certain point in time. 

 

An equivalent effect may be achieved in the time domain, as in a [Kalman filter](./Kalman_filter); see [filtering](./Filter_(signal_processing)) and [smoothing](./Smoothing) for more techniques.

 

Other related techniques include:

 
- [Autocorrelation](./Autocorrelation) analysis to examine [serial dependence](./Serial_dependence)
- [Spectral analysis](./Frequency_spectrum#Spectrum_analysis) to examine cyclic behavior which need not be related to [seasonality](./Seasonality). For example, sunspot activity varies over 11 year cycles.[[10]](./Time_series#cite_note-10)[[11]](./Time_series#cite_note-11) Other common examples include celestial phenomena, weather patterns, neural activity, commodity prices, and economic activity.
- Separation into components representing trend, seasonality, slow and fast variation, and cyclical irregularity: see [trend estimation](./Trend_estimation) and [decomposition of time series](./Decomposition_of_time_series)

 

### Curve fitting

 Main article: [Curve fitting](./Curve_fitting) 

Curve fitting[[12]](./Time_series#cite_note-12)[[13]](./Time_series#cite_note-13) is the process of constructing a [curve](./Curve), or [mathematical function](./Function_(mathematics)), that has the best fit to a series of [data](./Data) points,[[14]](./Time_series#cite_note-14) possibly subject to constraints.[[15]](./Time_series#cite_note-15)[[16]](./Time_series#cite_note-16) Curve fitting can involve either [interpolation](./Interpolation),[[17]](./Time_series#cite_note-17)[[18]](./Time_series#cite_note-18) where an exact fit to the data is required, or [smoothing](./Smoothing),[[19]](./Time_series#cite_note-19)[[20]](./Time_series#cite_note-20) in which a "smooth" function is constructed that approximately fits the data.  A related topic is [regression analysis](./Regression_analysis),[[21]](./Time_series#cite_note-21)[[22]](./Time_series#cite_note-22) which focuses more on questions of [statistical inference](./Statistical_inference) such as how much uncertainty is present in a curve that is fit to data observed with random errors. Fitted curves can be used as an aid for data visualization,[[23]](./Time_series#cite_note-23)[[24]](./Time_series#cite_note-24) to infer values of a function where no data are available,[[25]](./Time_series#cite_note-25) and to summarize the relationships among two or more variables.[[26]](./Time_series#cite_note-26) [Extrapolation](./Extrapolation) refers to the use of a fitted curve beyond the [range](./Range_(statistics)) of the observed data,[[27]](./Time_series#cite_note-27) and is subject to a [degree of uncertainty](./Uncertainty)[[28]](./Time_series#cite_note-28) since it may reflect the method used to construct the curve as much as it reflects the observed data.

 [![](//upload.wikimedia.org/wikipedia/commons/thumb/6/6a/Growth_equations.png/250px-Growth_equations.png)](./File:Growth_equations.png)Growth equations 

For processes that are expected to generally grow in magnitude one of the curves in the graphic (and many others) can be fitted by estimating their parameters.

 

The construction of economic time series involves the estimation of some components for some dates by [interpolation](./Interpolation) between values ("benchmarks") for earlier and later dates. Interpolation is estimation of an unknown quantity between two known quantities (historical data), or drawing conclusions about missing information from the available information ("reading between the lines").[[29]](./Time_series#cite_note-29) Interpolation is useful where the data surrounding the missing data is available and its trend, seasonality, and longer-term cycles are known. This is often done by using a related series known for all relevant dates.[[30]](./Time_series#cite_note-30) Alternatively [polynomial interpolation](./Polynomial_interpolation) or [spline interpolation](./Spline_interpolation) is used where piecewise [polynomial](./Polynomial) functions are fitted in time intervals such that they fit smoothly together. A different problem which is closely related to interpolation is the approximation of a complicated function by a simple function (also called [regression](./Polynomial_regression)). The main difference between regression and interpolation is that polynomial regression gives a single polynomial that models the entire data set.  Spline interpolation, however, yield a piecewise continuous function composed of many polynomials to model the data set.

 

[Extrapolation](./Extrapolation) is the process of estimating, beyond the original observation range, the value of a variable on the basis of its relationship with another variable. It is similar to [interpolation](./Interpolation), which produces estimates between known observations, but extrapolation is subject to greater [uncertainty](./Uncertainty) and a higher risk of producing meaningless results.

 

### Function approximation

 Main article: [Function approximation](./Function_approximation) 

In general, a function approximation problem asks us to select a [function](./Function_(mathematics)) among a well-defined class that closely matches ("approximates") a target function in a task-specific way.
One can distinguish two major classes of function approximation problems: First, for known target functions, [approximation theory](./Approximation_theory)  is the branch of [numerical analysis](./Numerical_analysis) that investigates how certain known functions (for example, [special functions](./Special_function)) can be approximated by a specific class of functions (for example, [polynomials](./Polynomial) or [rational functions](./Rational_function)) that often have desirable properties (inexpensive computation, continuity, integral and limit values, etc.).

 

Second, the target function, call it *g*, may be unknown; instead of an explicit formula, only a set of points (a time series) of the form (*x*, *g*(*x*)) is provided.  Depending on the structure of the [domain](./Domain_of_a_function) and [codomain](./Codomain) of *g*, several techniques for approximating *g* may be applicable.  For example, if *g* is an operation on the [real numbers](./Real_number), techniques of [interpolation](./Interpolation), [extrapolation](./Extrapolation), [regression analysis](./Regression_analysis), and [curve fitting](./Curve_fitting) can be used.  If the [codomain](./Codomain) (range or target set) of *g* is a finite set, one is dealing with a [classification](./Statistical_classification) problem instead. A related problem of *online* time series approximation[[31]](./Time_series#cite_note-31) is to summarize the data in one-pass and construct an approximate representation that can support a variety of time series queries with bounds on worst-case error.

 

To some extent, the different problems ([regression](./Regression_analysis), [classification](./Statistical_classification), [fitness approximation](./Fitness_approximation)) have received a unified treatment in [statistical learning theory](./Statistical_learning_theory), where they are viewed as [supervised learning](./Supervised_learning) problems.

 

### Prediction and forecasting

 

In [statistics](./Statistics), [prediction](./Prediction) is a part of [statistical inference](./Statistical_inference). One particular approach to such inference is known as [predictive inference](./Predictive_inference), but the prediction can be undertaken within any of the several approaches to statistical inference. Indeed, one description of statistics is that it provides a means of transferring knowledge about a sample of a population to the whole population, and to other related populations, which is not necessarily the same as prediction over time. When information is transferred across time, often to specific points in time, the process is known as [forecasting](./Forecasting).

 
- Fully formed statistical models for [stochastic simulation](./Stochastic_simulation) purposes, so as to generate alternative versions of the time series, representing what might happen over non-specific time-periods in the future
- Simple or fully formed statistical models to describe the likely outcome of the time series in the immediate future, given knowledge of the most recent outcomes (forecasting).
- Forecasting on time series is usually done using automated statistical software packages and programming languages, such as [Julia](./Julia_(programming_language)), [Python](./Python_(programming_language)), [R](./R_(programming_language)), [SAS](./SAS_(software)), [SPSS](./SPSS) and many others.
- Forecasting on large scale data can be done with [Apache Spark](./Apache_Spark) using the Spark-TS library, a third-party package.[[32]](./Time_series#cite_note-32)

 

### Classification

 Main article: [Statistical classification](./Statistical_classification) 

Assigning time series pattern to a specific category, for example identify a word based on series of hand movements in [sign language](./Sign_language).

 

### Segmentation

 Main article: [Time-series segmentation](./Time-series_segmentation) 

Splitting a time-series into a sequence of segments. It is often the case that a time-series can be represented as a sequence of individual segments, each with its own characteristic properties. For example, the audio signal from a conference call can be partitioned into pieces corresponding to the times during which each person was speaking. In time-series segmentation, the goal is to identify the segment boundary points in the time-series, and to characterize the dynamical properties associated with each segment. One can approach this problem using [change-point detection](./Change_detection), or by modeling the time-series as a more sophisticated system, such as a Markov jump linear system.

 

### Clustering

 

Time series data may be clustered, however special care has to be taken when considering subsequence clustering.[[33]](./Time_series#cite_note-33)[[34]](./Time_series#cite_note-34)
Time series clustering may be split into 

 
- whole time series clustering (multiple time series for which to find a cluster)
- subsequence time series clustering (single timeseries, split into chunks using sliding windows)
- time point clustering

 

#### Subsequence time series clustering

 

Subsequence time series clustering resulted in unstable (random) clusters *induced by the feature extraction* using chunking with sliding windows.[[35]](./Time_series#cite_note-35) It was found that the cluster centers (the average of the time series in a cluster - also a time series) follow an arbitrarily shifted sine pattern (regardless of the dataset, even on realizations of a [random walk](./Random_walk)). This means that the found cluster centers are non-descriptive for the dataset because the cluster centers are always nonrepresentative sine waves.

 

## Models

 

### Classical models (AR, ARMA, ARIMA, and well-known variations)

 

Models for time series data can have many forms and represent different [stochastic processes](./Stochastic_processes). When modeling variations in the level of a process, three broad classes of practical importance are the *[autoregressive](./Autoregressive)* (AR) models, the *integrated* (I) models, and the *[moving-average](./Moving-average_model)* (MA) models. These three classes depend *linearly* on previous data points.[[36]](./Time_series#cite_note-linear_time_series-36) Combinations of these ideas produce [autoregressive moving-average](./Autoregressive_moving-average_model) (ARMA) and [autoregressive integrated moving-average](./Autoregressive_integrated_moving_average) (ARIMA) models. The [autoregressive fractionally integrated moving-average](./Autoregressive_fractionally_integrated_moving_average) (ARFIMA) model generalizes the former three. Another important generalization is the time-varying autoregressive (TVAR) model, in which the AR coefficients are allowed to change over time, enabling the model to capture evolving or non-stationary dynamics. Extensions of these classes to deal with vector-valued data are available under the heading of multivariate time-series models and sometimes the preceding acronyms are extended by including an initial "V" for "vector", as in VAR for [vector autoregression](./Vector_autoregression). An additional set of extensions of these models is available for use where the observed time-series is driven by some "forcing" time-series (which may not have a causal effect on the observed series): the distinction from the multivariate case is that the forcing series may be deterministic or under the experimenter's control. For these models, the acronyms are extended with a final "X" for "exogenous".

 

### Time-varying autoregressive (TVAR) models

 

Time-varying autoregressive (TVAR) models are especially useful for analyzing non-stationary time series in which the underlying dynamics evolve over time in complex ways, not limited to classical forms of variation such as trends or seasonal patterns. Unlike classical AR models with fixed parameters, TVAR models allow the autoregressive coefficients to vary as functions of time, typically represented through basis function expansions whose form and complexity are determined by the user, allowing for highly flexible modeling of time-varying behavior, which enables them to capture specific non-stationary patterns exhibited by the data. This flexibility makes them well suited to modeling structural changes, regime shifts, or gradual evolutions in a system's behavior. TVAR time-series models are widely applied in fields such as signal processing,[[37]](./Time_series#cite_note-37)[[38]](./Time_series#cite_note-38) economics,[[39]](./Time_series#cite_note-39) finance,[[40]](./Time_series#cite_note-40) reliability and [condition monitoring](./Condition_monitoring),[[41]](./Time_series#cite_note-41)[[42]](./Time_series#cite_note-42)[[43]](./Time_series#cite_note-43) telecommunications,[[44]](./Time_series#cite_note-44)[[45]](./Time_series#cite_note-45) neuroscience,[[46]](./Time_series#cite_note-46) climate sciences,[[47]](./Time_series#cite_note-47) and hydrology,[[48]](./Time_series#cite_note-48) where time series often display dynamics that traditional linear models cannot adequately represent. Estimation of TVAR models typically involves methods such as kernel smoothing,[[49]](./Time_series#cite_note-49) recursive least squares,[[50]](./Time_series#cite_note-50) or Kalman filtering.[[51]](./Time_series#cite_note-51)

 

### Non-linear models

 

Non-linear dependence of the level of a series on previous data points is of interest, partly because of the possibility of producing a [chaotic](./Chaos_theory) time series. However, more importantly, empirical investigations can indicate the advantage of using predictions derived from non-linear models, over those from linear models, as for example in [nonlinear autoregressive exogenous models](./Nonlinear_autoregressive_exogenous_model). Further references on nonlinear time series analysis: (Kantz and Schreiber),[[52]](./Time_series#cite_note-52) and (Abarbanel)[[53]](./Time_series#cite_note-53)

 

Among other types of non-linear time series models, there are models to represent the changes of variance over time ([heteroskedasticity](./Heteroskedasticity)). These models represent [autoregressive conditional heteroskedasticity](./Autoregressive_conditional_heteroskedasticity) (ARCH) and the collection comprises a wide variety of representation ([GARCH](./GARCH), TARCH, EGARCH, FIGARCH, CGARCH, etc.). Here changes in variability are related to, or predicted by, recent past values of the observed series. This is in contrast to other possible representations of locally varying variability, where the variability might be modeled as being driven by a separate time-varying process, as in a [doubly stochastic model](./Doubly_stochastic_model).

 

### Other modeling approaches

 

In a recent work on "model-free" analyses (a term often used to refer to analyses that do not rely on modeling the processes evolution over time with a parametric mathematical expression), wavelet transform based methods (for example locally stationary wavelets and wavelet decomposed neural networks) have gained favor.[[54]](./Time_series#cite_note-54) Multiscale (often referred to as multiresolution) techniques decompose a given time series, attempting to illustrate time dependence at multiple scales. See also [Markov switching multifractal](./Markov_switching_multifractal) (MSMF) techniques for modeling volatility evolution.

 

A [hidden Markov model](./Hidden_Markov_model) (HMM) is a statistical Markov model in which the system being modeled is assumed to be a Markov process with unobserved (hidden) states. An HMM can be considered as the simplest [dynamic Bayesian network](./Dynamic_Bayesian_network). HMM models are widely used in [speech recognition](./Speech_recognition), for translating a time series of spoken words into text.

 

Many of these models are collected in the python package [sktime](./Sktime?action=edit&redlink=1).

 

## Notation

 

A number of different notations are in use for time-series analysis. A common notation specifying a time series *X* that is indexed by the [natural numbers](./Natural_number) is written

 *X* = (*X*1, *X*2, ...). 

Another common notation is

 *Y* = (*Yt*: *t* ∈ *T*), 

where *T* is the [index set](./Index_set).

 

### Conditions

 

There are two sets of conditions under which much of the theory is built:

 
- [Stationary process](./Stationary_process)
- [Ergodic process](./Ergodic_process)

 

Ergodicity implies stationarity, but the converse is not necessarily the case. Stationarity is usually classified into [strict stationarity](./Strict_stationarity) and wide-sense or [second-order stationarity](./Stationary_process#Weaker_forms_of_stationarity). Both models and applications can be developed under each of these conditions, although the models in the latter case might be considered as only partly specified.

 

In addition, time-series analysis can be applied where the series are [seasonally stationary](./Cyclostationary_process) or non-stationary. Situations where the amplitudes of frequency components change with time can be dealt with in [time-frequency analysis](./Time-frequency_analysis) which makes use of a [time–frequency representation](./Time–frequency_representation) of a time-series or signal.[[55]](./Time_series#cite_note-55)

 

### Tools

 

Tools for investigating time-series data include:

 
- Consideration of the [autocorrelation function](./Autocorrelation) and the [spectral density function](./Spectral_density) (also [cross-correlation functions](./Cross-correlation_function) and cross-spectral density functions)
- [Scaled](./Scaled_correlation) cross- and auto-correlation functions to remove contributions of slow components[[56]](./Time_series#cite_note-Nikolicetal-56)
- Performing a [Fourier transform](./Fourier_transform) to investigate the series in the [frequency domain](./Frequency_domain)
- Performing a clustering analysis [[57]](./Time_series#cite_note-57)
- Discrete, continuous or mixed spectra of time series, depending on whether the time series contains a (generalized) harmonic signal or not
- Use of a [filter](./Digital_filter) to remove unwanted [noise](./Noise_(physics))
- [Principal component analysis](./Principal_component_analysis) (or [empirical orthogonal function](./Empirical_orthogonal_function) analysis)
- [Singular spectrum analysis](./Singular_spectrum_analysis)
- "Structural" models:

- General [state space models](./State_space_model)
- Unobserved components models

- [Machine learning](./Machine_learning) 
- [Artificial neural networks](./Artificial_neural_network)
- [Support vector machine](./Support_vector_machine)
- [Fuzzy logic](./Fuzzy_logic)
- [Gaussian process](./Gaussian_process)
- [Genetic programming](./Genetic_programming)
- [Gene expression programming](./Gene_expression_programming)
- [Hidden Markov model](./Hidden_Markov_model)
- [Multi expression programming](./Multi_expression_programming)

- [Queueing theory](./Queueing_theory) analysis
- [Control chart](./Control_chart) 
- [Shewhart individuals control chart](./Shewhart_individuals_control_chart)
- [CUSUM](./CUSUM) chart
- [EWMA chart](./EWMA_chart)

- [Detrended fluctuation analysis](./Detrended_fluctuation_analysis)
- [Nonlinear mixed-effects modeling](./Nonlinear_mixed-effects_model)
- [Dynamic time warping](./Dynamic_time_warping)[[58]](./Time_series#cite_note-Sakoe_1978-58)
- [Dynamic Bayesian network](./Dynamic_Bayesian_network)
- [Time-frequency analysis techniques:](./Time-frequency_representation) 
- [Fast Fourier transform](./Fast_Fourier_transform)
- [Continuous wavelet transform](./Continuous_wavelet_transform)
- [Short-time Fourier transform](./Short-time_Fourier_transform)
- [Chirplet transform](./Chirplet_transform)
- [Fractional Fourier transform](./Fractional_Fourier_transform)

- [Chaotic analysis](./Chaos_theory) 
- [Correlation dimension](./Correlation_dimension)
- [Recurrence plots](./Recurrence_plot)
- [Recurrence quantification analysis](./Recurrence_quantification_analysis)
- [Lyapunov exponents](./Lyapunov_exponent)
- [Entropy encoding](./Entropy_encoding)

 

### Measures

 

Time-series metrics or [features](./Features_(pattern_recognition)) that can be used for time series [classification](./Classification_(machine_learning)) or [regression analysis](./Regression_analysis):[[59]](./Time_series#cite_note-59)

 
- **Univariate linear measures** 
- [Moment (mathematics)](./Moment_(mathematics))
- [Spectral band power](./Spectral_band_power?action=edit&redlink=1)
- [Spectral edge frequency](./Spectral_edge_frequency)
- Accumulated [energy (signal processing)](./Energy_(signal_processing))
- Characteristics of the [autocorrelation](./Autocorrelation) function
- [Hjorth parameters](./Hjorth_parameters)
- [FFT](./Fast_Fourier_transform) parameters
- [Autoregressive model](./Autoregressive_model) parameters
- [Mann–Kendall test](./Mann–Kendall_test?action=edit&redlink=1)

- **Univariate non-linear measures** 
- Measures based on the [correlation](./Correlation) sum
- [Correlation dimension](./Correlation_dimension)
- [Correlation integral](./Correlation_integral)
- [Correlation density](./Correlation_density?action=edit&redlink=1)
- [Correlation entropy](./Correlation_entropy?action=edit&redlink=1)
- [Approximate entropy](./Approximate_entropy)[[60]](./Time_series#cite_note-60)
- [Sample entropy](./Sample_entropy)
- [Fourier entropy](./Fourier_entropy?action=edit&redlink=1) [[uk](https://uk.wikipedia.org/wiki/Ентропія%20Фур'є)]
- Wavelet entropy
- Dispersion entropy
- Fluctuation dispersion entropy
- [Rényi entropy](./Rényi_entropy)
- Higher-order methods
- [Marginal predictability](./Marginal_predictability?action=edit&redlink=1)
- [Dynamical similarity](./Dynamical_similarity?action=edit&redlink=1) index
- [State space](./State_space) dissimilarity measures
- [Lyapunov exponent](./Lyapunov_exponent)
- Permutation methods
- [Local flow](./Local_flow)

- **Other univariate measures** 
- [Algorithmic complexity](./Algorithmic_information_theory)
- [Kolmogorov complexity](./Kolmogorov_complexity) estimates
- [Hidden Markov model](./Hidden_Markov_model) states
- [Rough path signature](./Rough_path#Signature)[[61]](./Time_series#cite_note-61)
- Surrogate time series and surrogate correction
- Loss of recurrence (degree of non-stationarity)

- **Bivariate linear measures** 
- Maximum linear [cross-correlation](./Cross-correlation)
- Linear [Coherence (signal processing)](./Coherence_(signal_processing))

- **Bivariate non-linear measures** 
- Non-linear interdependence
- Dynamical Entrainment (physics)
- Measures for [phase synchronization](./Phase_synchronization)
- Measures for [phase locking](./Phase_locking)

- **Similarity measures**:[[62]](./Time_series#cite_note-62) 
- [Cross-correlation](./Cross-correlation)
- [Dynamic time warping](./Dynamic_time_warping)[[58]](./Time_series#cite_note-Sakoe_1978-58)
- [Hidden Markov model](./Hidden_Markov_model)
- [Edit distance](./Edit_distance)
- [Total correlation](./Total_correlation)
- [Newey–West estimator](./Newey–West_estimator)
- [Prais–Winsten transformation](./Prais–Winsten_estimation)
- Data as vectors in a metrizable space

- [Minkowski distance](./Minkowski_distance)
- [Mahalanobis distance](./Mahalanobis_distance)

- Data as time series with envelopes

- Global [standard deviation](./Standard_deviation)
- Local [standard deviation](./Standard_deviation)
- Windowed [standard deviation](./Standard_deviation)

- Data interpreted as stochastic series

- [Pearson product-moment correlation coefficient](./Pearson_product-moment_correlation_coefficient)
- [Spearman's rank correlation coefficient](./Spearman's_rank_correlation_coefficient)

- Data interpreted as a [probability distribution](./Probability_distribution) function

- [Kolmogorov–Smirnov test](./Kolmogorov–Smirnov_test)
- [Cramér–von Mises criterion](./Cramér–von_Mises_criterion)

 

## Visualization

 

Time series can be visualized with two categories of chart: Overlapping Charts and Separated Charts. Overlapping Charts display all-time series on the same layout while Separated Charts presents them on different layouts (but aligned for comparison purpose)[[63]](./Time_series#cite_note-63)

 

### Overlapping charts

 
- [Braided graphs](./Braided_graph?action=edit&redlink=1)
- Line charts
- Slope graphs
- [GapChart](./GapChart?action=edit&redlink=1) [[fr](https://fr.wikipedia.org/wiki/GapChart)]

 

### Separated charts

 
- [Horizon graphs](./Horizon_chart)
- Reduced line chart (small multiples)
- Silhouette graph
- Circular silhouette graph

 

## History

 

Jevons was the first to study times series.[[64]](./Time_series#cite_note-Jenrons1884-64) In his book he examined a number of weekly financial time series between the years 1825 to 1860 inclusive. These included times series of bankruptcies, currency circulation and discount rates.

 

## See also

  
- [Anomaly time series](./Anomaly_time_series)
- [Chirp](./Chirp)
- [Decomposition of time series](./Decomposition_of_time_series)
- [Detrended fluctuation analysis](./Detrended_fluctuation_analysis)
- [Digital signal processing](./Digital_signal_processing)
- [Distributed lag](./Distributed_lag)
- [Estimation theory](./Estimation_theory)
- [Forecasting](./Forecasting)
- [Frequency spectrum](./Frequency_spectrum)
- [Hurst exponent](./Hurst_exponent)
- [Least-squares spectral analysis](./Least-squares_spectral_analysis)
- [Monte Carlo method](./Monte_Carlo_method)
- [Panel analysis](./Panel_analysis)
- [Random walk](./Random_walk)
- [Scaled correlation](./Scaled_correlation)
- [Seasonal adjustment](./Seasonal_adjustment)
- [Sequence analysis](./Sequence_analysis)
- [Signal processing](./Signal_processing)
- [Time series database](./Time_series_database) (TSDB)
- [Trend estimation](./Trend_estimation)
- [Unevenly spaced time series](./Unevenly_spaced_time_series)

 

## References

  
1. [↑](./Time_series#cite_ref-1) Lin, Jessica; Keogh, Eamonn; Lonardi, Stefano; Chiu, Bill (2003). "A symbolic representation of time series, with implications for streaming algorithms". *Proceedings of the 8th ACM SIGMOD workshop on Research issues in data mining and knowledge discovery*. New York: ACM Press. pp. 2–11. [CiteSeerX](./CiteSeerX_(identifier)) [10.1.1.14.5597](https://citeseerx.ist.psu.edu/viewdoc/summary?doi=10.1.1.14.5597). [doi](./Doi_(identifier)):[10.1145/882082.882086](https://doi.org/10.1145%2F882082.882086). [ISBN](./ISBN_(identifier)) [978-1-4503-7422-4](./Special:BookSources/978-1-4503-7422-4). [S2CID](./S2CID_(identifier)) [6084733](https://api.semanticscholar.org/CorpusID:6084733).
2. [↑](./Time_series#cite_ref-2) Warren Liao, T. (November 2005). "Clustering of time series data—a survey". *Pattern Recognition*. **38** (11): 1857–1874. [Bibcode](./Bibcode_(identifier)):[2005PatRe..38.1857W](https://ui.adsabs.harvard.edu/abs/2005PatRe..38.1857W). [doi](./Doi_(identifier)):[10.1016/j.patcog.2005.01.025](https://doi.org/10.1016%2Fj.patcog.2005.01.025). [S2CID](./S2CID_(identifier)) [8973749](https://api.semanticscholar.org/CorpusID:8973749).
3. [↑](./Time_series#cite_ref-3) Aghabozorgi, Saeed; Seyed Shirkhorshidi, Ali; Ying Wah, Teh (October 2015). "Time-series clustering – A decade review". *Information Systems*. **53**: 16–38. [doi](./Doi_(identifier)):[10.1016/j.is.2015.04.007](https://doi.org/10.1016%2Fj.is.2015.04.007). [S2CID](./S2CID_(identifier)) [158707](https://api.semanticscholar.org/CorpusID:158707).
4. [↑](./Time_series#cite_ref-4) Li, Aimin; Siqi, Xiong; Junhuai, Li (April 2023). "AngClust: Angle Feature-Based Clustering for Short Time Series Gene Expression Profiles". *IEEE/ACM Transactions on Computational Biology and Bioinformatics*. **20** (2): 1574–1580. [Bibcode](./Bibcode_(identifier)):[2023ITCBB..20.1574L](https://ui.adsabs.harvard.edu/abs/2023ITCBB..20.1574L). [doi](./Doi_(identifier)):[10.1109/TCBB.2022.3192306](https://doi.org/10.1109%2FTCBB.2022.3192306). [PMID](./PMID_(identifier)) [35853049](https://pubmed.ncbi.nlm.nih.gov/35853049).
5. [↑](./Time_series#cite_ref-5) Keogh, Eamonn; Kasetty, Shruti (2002). "On the need for time series data mining benchmarks: A survey and empirical demonstration". *Proceedings of the eighth ACM SIGKDD international conference on Knowledge discovery and data mining*. pp. 102–111. [doi](./Doi_(identifier)):[10.1145/775047.775062](https://doi.org/10.1145%2F775047.775062). [ISBN](./ISBN_(identifier)) [1-58113-567-X](./Special:BookSources/1-58113-567-X).
6. [↑](./Time_series#cite_ref-6) Agrawal, Rakesh; Faloutsos, Christos; Swami, Arun (1993). "Efficient similarity search in sequence databases". [*Foundations of Data Organization and Algorithms*](https://figshare.com/articles/journal_contribution/6605123). Lecture Notes in Computer Science. Vol. 730. pp. 69–84. [doi](./Doi_(identifier)):[10.1007/3-540-57301-1_5](https://doi.org/10.1007%2F3-540-57301-1_5). [ISBN](./ISBN_(identifier)) [978-3-540-57301-2](./Special:BookSources/978-3-540-57301-2). [S2CID](./S2CID_(identifier)) [16748451](https://api.semanticscholar.org/CorpusID:16748451).
7. [↑](./Time_series#cite_ref-7) Chen, Cathy W. S.; Chiu, L. M. (4 September 2021). ["Ordinal Time Series Forecasting of the Air Quality Index"](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8469594). *Entropy*. **23** (9): 1167. [Bibcode](./Bibcode_(identifier)):[2021Entrp..23.1167C](https://ui.adsabs.harvard.edu/abs/2021Entrp..23.1167C). [doi](./Doi_(identifier)):[10.3390/e23091167](https://doi.org/10.3390%2Fe23091167). [PMC](./PMC_(identifier)) [8469594](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8469594). [PMID](./PMID_(identifier)) [34573792](https://pubmed.ncbi.nlm.nih.gov/34573792).
8. [↑](./Time_series#cite_ref-8) ["Table 1 | Reported TB in the US 2022| Data & Statistics | TB | CDC"](https://www.cdc.gov/tb/statistics/reports/2022/table1.htm). 27 August 2024.
9. [↑](./Time_series#cite_ref-9) Sarkar, Advait; Spott, Martin; Blackwell, Alan F.; Jamnik, Mateja (2016). ["Visual discovery and model-driven explanation of time series patterns"](https://www.repository.cam.ac.uk/handle/1810/260285). *2016 IEEE Symposium on Visual Languages and Human-Centric Computing (VL/HCC)*. pp. 78–86. [doi](./Doi_(identifier)):[10.1109/vlhcc.2016.7739668](https://doi.org/10.1109%2Fvlhcc.2016.7739668). [ISBN](./ISBN_(identifier)) [978-1-5090-0252-8](./Special:BookSources/978-1-5090-0252-8). [S2CID](./S2CID_(identifier)) [9787931](https://api.semanticscholar.org/CorpusID:9787931).
10. [↑](./Time_series#cite_ref-10) Bloomfield, Peter (1976). *Fourier Analysis of Time Series: An Introduction*. Wiley. [ISBN](./ISBN_(identifier)) [978-0-471-08256-9](./Special:BookSources/978-0-471-08256-9).[*[page needed](./Wikipedia:Citing_sources)*]
11. [↑](./Time_series#cite_ref-11) [Shumway, Robert H.](./Robert_H._Shumway) (1988). *Applied Statistical Time Series Analysis*. Prentice-Hall. [ISBN](./ISBN_(identifier)) [978-0-13-041500-4](./Special:BookSources/978-0-13-041500-4).[*[page needed](./Wikipedia:Citing_sources)*]
12. [↑](./Time_series#cite_ref-12) Arlinghaus, Sandra (1994). *Practical Handbook of Curve Fitting*. CRC Press. [ISBN](./ISBN_(identifier)) [978-0-8493-0143-8](./Special:BookSources/978-0-8493-0143-8).[*[page needed](./Wikipedia:Citing_sources)*]
13. [↑](./Time_series#cite_ref-13) Kolb, William M. (1984). *Curve Fitting for Programmable Calculators*. SYNTEC. [ISBN](./ISBN_(identifier)) [978-0-943494-02-9](./Special:BookSources/978-0-943494-02-9).[*[page needed](./Wikipedia:Citing_sources)*]
14. [↑](./Time_series#cite_ref-14) Halli, S. S.; Rao, K. V. (1992). *Advanced Techniques of Population Analysis*. Springer Science & Business Media. p. 165. [ISBN](./ISBN_(identifier)) [978-0-306-43997-1](./Special:BookSources/978-0-306-43997-1). functions are fulfilled if we have a good to moderate fit for the observed data.
15. [↑](./Time_series#cite_ref-15) Silver, Nate (2012). [*The Signal and the Noise: Why So Many Predictions Fail but Some Don't*](https://archive.org/details/signalnoisewhymo00silv). The Penguin Press. [ISBN](./ISBN_(identifier)) [978-1-59420-411-1](./Special:BookSources/978-1-59420-411-1).
16. [↑](./Time_series#cite_ref-16) Pyle, Dorian (1999). *Data Preparation for Data Mining*. Morgan Kaufmann. [ISBN](./ISBN_(identifier)) [978-1-55860-529-9](./Special:BookSources/978-1-55860-529-9).[*[page needed](./Wikipedia:Citing_sources)*]
17. [↑](./Time_series#cite_ref-17) Numerical Methods in Engineering with MATLAB. By [Jaan Kiusalaas](./Jaan_Kiusalaas?action=edit&redlink=1). Page 24.
18. [↑](./Time_series#cite_ref-18) Kiusalaas, Jaan (2013). *Numerical Methods in Engineering with Python 3*. Cambridge University Press. p. 21. [ISBN](./ISBN_(identifier)) [978-1-139-62058-1](./Special:BookSources/978-1-139-62058-1).
19. [↑](./Time_series#cite_ref-19) Guest, Philip George (2012). *Numerical Methods of Curve Fitting*. Cambridge University Press. p. 349. [ISBN](./ISBN_(identifier)) [978-1-107-64695-7](./Special:BookSources/978-1-107-64695-7).
20. [↑](./Time_series#cite_ref-20) See also: [Mollifier](./Mollifier)
21. [↑](./Time_series#cite_ref-21) Motulsky, Harvey; Christopoulos, Arthur (2004). *Fitting Models to Biological Data Using Linear and Nonlinear Regression: A Practical Guide to Curve Fitting*. Oxford University Press. [ISBN](./ISBN_(identifier)) [978-0-19-803834-4](./Special:BookSources/978-0-19-803834-4).[*[page needed](./Wikipedia:Citing_sources)*]
22. [↑](./Time_series#cite_ref-22) Regression Analysis By Rudolf J. Freund, William J. Wilson, Ping Sa. Page 269.[*[date missing](./Wikipedia:Citing_sources)*]
23. [↑](./Time_series#cite_ref-23) Daud, Hanita; Sagayan, Vijanth; Yahya, Noorhana; Najwati, Wan (2009). "Modeling of Electromagnetic Waves Using Statistical and Numerical Techniques". *Visual Informatics: Bridging Research and Practice*. Lecture Notes in Computer Science. Vol. 5857. pp. 686–695. [doi](./Doi_(identifier)):[10.1007/978-3-642-05036-7_65](https://doi.org/10.1007%2F978-3-642-05036-7_65). [ISBN](./ISBN_(identifier)) [978-3-642-05035-0](./Special:BookSources/978-3-642-05035-0).
24. [↑](./Time_series#cite_ref-24) Hauser, John R. (2009). *Numerical Methods for Nonlinear Engineering Models*. Springer Science & Business Media. p. 227. [ISBN](./ISBN_(identifier)) [978-1-4020-9920-5](./Special:BookSources/978-1-4020-9920-5).
25. [↑](./Time_series#cite_ref-25) William, Dudley, ed. (1976). "Nuclear and Atomic Spectroscopy". *Spectroscopy*. Methods in Experimental Physics. Vol. 13. pp. 115–346 [150]. [doi](./Doi_(identifier)):[10.1016/S0076-695X(08)60643-2](https://doi.org/10.1016%2FS0076-695X%2808%2960643-2). [ISBN](./ISBN_(identifier)) [978-0-12-475913-8](./Special:BookSources/978-0-12-475913-8).
26. [↑](./Time_series#cite_ref-26) Salkind, Neil J. (2010). [*Encyclopedia of Research Design*](https://books.google.com/books?id=HVmsxuaQl2oC&pg=PA266). SAGE. p. 266. [ISBN](./ISBN_(identifier)) [978-1-4129-6127-1](./Special:BookSources/978-1-4129-6127-1).
27. [↑](./Time_series#cite_ref-27) Klosterman, Richard E. (1990). *Community Analysis and Planning Techniques*. Rowman & Littlefield Publishers. p. 1. [ISBN](./ISBN_(identifier)) [978-0-7425-7440-3](./Special:BookSources/978-0-7425-7440-3).
28. [↑](./Time_series#cite_ref-28) Yoe, Charles E. (March 1996). An Introduction to Risk and Uncertainty in the Evaluation of Environmental Investments (Report). U.S. Army Corps of Engineers. p. 69. [DTIC](./DTIC_(identifier)) [ADA316839](https://apps.dtic.mil/sti/citations/tr/ADA316839).
29. [↑](./Time_series#cite_ref-29) Hamming, Richard (2012). *Numerical Methods for Scientists and Engineers*. Courier Corporation. [ISBN](./ISBN_(identifier)) [978-0-486-13482-6](./Special:BookSources/978-0-486-13482-6).[*[page needed](./Wikipedia:Citing_sources)*]
30. [↑](./Time_series#cite_ref-30) Friedman, Milton (December 1962). "The Interpolation of Time Series by Related Series". *Journal of the American Statistical Association*. **57** (300): 729–757. [doi](./Doi_(identifier)):[10.1080/01621459.1962.10500812](https://doi.org/10.1080%2F01621459.1962.10500812).
31. [↑](./Time_series#cite_ref-31) Gandhi, Sorabh; Foschini, Luca; Suri, Subhash (2010). "Space-efficient online approximation of time series data: Streams, amnesia, and out-of-order". *2010 IEEE 26th International Conference on Data Engineering (ICDE 2010)*. pp. 924–935. [doi](./Doi_(identifier)):[10.1109/ICDE.2010.5447930](https://doi.org/10.1109%2FICDE.2010.5447930). [ISBN](./ISBN_(identifier)) [978-1-4244-5445-7](./Special:BookSources/978-1-4244-5445-7). [S2CID](./S2CID_(identifier)) [16072352](https://api.semanticscholar.org/CorpusID:16072352).
32. [↑](./Time_series#cite_ref-32) Ryza, Sandy (2020-03-18). ["Time Series Analysis with Spark"](https://databricks.com/session/time-series-analysis-with-spark) (slides of a talk at Spark Summit East 2016). [Databricks](./Databricks). Retrieved 2021-01-12.
33. [↑](./Time_series#cite_ref-33) Zolhavarieh, Seyedjamal; Aghabozorgi, Saeed; Teh, Ying Wah (2014). ["A Review of Subsequence Time Series Clustering"](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC4130317). *The Scientific World Journal*. **2014** 312521. [doi](./Doi_(identifier)):[10.1155/2014/312521](https://doi.org/10.1155%2F2014%2F312521). [PMC](./PMC_(identifier)) [4130317](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC4130317). [PMID](./PMID_(identifier)) [25140332](https://pubmed.ncbi.nlm.nih.gov/25140332).
34. [↑](./Time_series#cite_ref-34) Li, Aimin; Siqi, Xiong; Junhuai, Li (April 2023). "AngClust: Angle Feature-Based Clustering for Short Time Series Gene Expression Profiles". *IEEE/ACM Transactions on Computational Biology and Bioinformatics*. **20** (2): 1574–1580. [Bibcode](./Bibcode_(identifier)):[2023ITCBB..20.1574L](https://ui.adsabs.harvard.edu/abs/2023ITCBB..20.1574L). [doi](./Doi_(identifier)):[10.1109/TCBB.2022.3192306](https://doi.org/10.1109%2FTCBB.2022.3192306). [PMID](./PMID_(identifier)) [35853049](https://pubmed.ncbi.nlm.nih.gov/35853049).
35. [↑](./Time_series#cite_ref-35) Keogh, Eamonn; Lin, Jessica (August 2005). "Clustering of time-series subsequences is meaningless: implications for previous and future research". *Knowledge and Information Systems*. **8** (2): 154–177. [doi](./Doi_(identifier)):[10.1007/s10115-004-0172-7](https://doi.org/10.1007%2Fs10115-004-0172-7).
36. [↑](./Time_series#cite_ref-linear_time_series_36-0) [Gershenfeld, N.](./Neil_Gershenfeld) (1999). [*The Nature of Mathematical Modeling*](https://archive.org/details/naturemathematic00gers_334). New York: Cambridge University Press. pp. [205](https://archive.org/details/naturemathematic00gers_334/page/n206)–208. [ISBN](./ISBN_(identifier)) [978-0-521-57095-4](./Special:BookSources/978-0-521-57095-4).
37. [↑](./Time_series#cite_ref-37) Baptista de Souza, Douglas; Kuhn, Eduardo Vinicius; Seara, Rui (January 2019). "A Time-Varying Autoregressive Model for Characterizing Nonstationary Processes". *IEEE Signal Processing Letters*. **26** (1): 134–138. [Bibcode](./Bibcode_(identifier)):[2019ISPL...26..134B](https://ui.adsabs.harvard.edu/abs/2019ISPL...26..134B). [doi](./Doi_(identifier)):[10.1109/LSP.2018.2880086](https://doi.org/10.1109%2FLSP.2018.2880086).
38. [↑](./Time_series#cite_ref-38) Kay, Steven (April 2008). ["A New Nonstationarity Detector"](https://digitalcommons.uri.edu/ele_facpubs/1320). *IEEE Transactions on Signal Processing*. **56** (4): 1440–1451. [Bibcode](./Bibcode_(identifier)):[2008ITSP...56.1440K](https://ui.adsabs.harvard.edu/abs/2008ITSP...56.1440K). [doi](./Doi_(identifier)):[10.1109/TSP.2007.909346](https://doi.org/10.1109%2FTSP.2007.909346).
39. [↑](./Time_series#cite_ref-39) Inayati, Syarifah; Iriawan, Nur (31 December 2024). ["Time-Varying Autoregressive Models for Economic Forecasting"](https://doi.org/10.11113%2Fmatematika.v40.n3.1654). *Matematika*: 131–142. [doi](./Doi_(identifier)):[10.11113/matematika.v40.n3.1654](https://doi.org/10.11113%2Fmatematika.v40.n3.1654).
40. [↑](./Time_series#cite_ref-40) Jia, Zhixuan; Li, Wang; Jiang, Yunlong; Liu, Xingshen (9 July 2025). ["The Use of Minimization Solvers for Optimizing Time-Varying Autoregressive Models and Their Applications in Finance"](https://doi.org/10.3390%2Fmath13142230). *Mathematics*. **13** (14): 2230. [doi](./Doi_(identifier)):[10.3390/math13142230](https://doi.org/10.3390%2Fmath13142230).
41. [↑](./Time_series#cite_ref-41) Souza, Douglas Baptista de; Leao, Bruno Paes (5 November 2024). "Data Augmentation of Multivariate Sensor Time Series using Autoregressive Models and Application to Failure Prognostics". *Annual Conference of the PHM Society*. **16** (1). [arXiv](./ArXiv_(identifier)):[2410.16419](https://arxiv.org/abs/2410.16419). [doi](./Doi_(identifier)):[10.36001/phmconf.2024.v16i1.4145](https://doi.org/10.36001%2Fphmconf.2024.v16i1.4145).
42. [↑](./Time_series#cite_ref-42) Souza, Douglas Baptista de; Leao, Bruno Paes (26 October 2023). ["Data Augmentation of Sensor Time Series using Time-varying Autoregressive Processes"](https://doi.org/10.36001%2Fphmconf.2023.v15i1.3565). *Annual Conference of the PHM Society*. **15** (1). [doi](./Doi_(identifier)):[10.36001/phmconf.2023.v15i1.3565](https://doi.org/10.36001%2Fphmconf.2023.v15i1.3565).
43. [↑](./Time_series#cite_ref-43) Lei, Huang; Yiming, Wang; Jianfeng, Qu; Hao, Ren (2020). ["A Fault Diagnosis Methodology Based on Non-Stationary Monitoring Signals by Extracting Features With Unknown Probability Distribution"](https://doi.org/10.1109%2FACCESS.2020.2978112). *IEEE Access*. **8**: 59821–59836. [Bibcode](./Bibcode_(identifier)):[2020IEEEA...859821L](https://ui.adsabs.harvard.edu/abs/2020IEEEA...859821L). [doi](./Doi_(identifier)):[10.1109/ACCESS.2020.2978112](https://doi.org/10.1109%2FACCESS.2020.2978112).
44. [↑](./Time_series#cite_ref-44) Wang, Shihan; Chen, Tao; Wang, Hongjian (17 March 2023). ["IDBD-Based Beamforming Algorithm for Improving the Performance of Phased Array Radar in Nonstationary Environments"](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC10052024). *Sensors*. **23** (6): 3211. [Bibcode](./Bibcode_(identifier)):[2023Senso..23.3211W](https://ui.adsabs.harvard.edu/abs/2023Senso..23.3211W). [doi](./Doi_(identifier)):[10.3390/s23063211](https://doi.org/10.3390%2Fs23063211). [PMC](./PMC_(identifier)) [10052024](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC10052024). [PMID](./PMID_(identifier)) [36991922](https://pubmed.ncbi.nlm.nih.gov/36991922).
45. [↑](./Time_series#cite_ref-45) Wu, Xiaorui; Wu, Chunling; Deng, Pei (23 February 2023). ["Prediction of Packet Loss Rate in Non-Stationary Networks Based on Time-Varying Autoregressive Sequences"](https://doi.org/10.3390%2Felectronics12051103). *Electronics*. **12** (5): 1103. [doi](./Doi_(identifier)):[10.3390/electronics12051103](https://doi.org/10.3390%2Felectronics12051103).
46. [↑](./Time_series#cite_ref-46) Gutierrez, D.; Salazar-Varas, R. (August 2011). "EEG signal classification using time-varying autoregressive models and common spatial patterns". *2011 Annual International Conference of the IEEE Engineering in Medicine and Biology Society*. pp. 6585–6588. [doi](./Doi_(identifier)):[10.1109/IEMBS.2011.6091624](https://doi.org/10.1109%2FIEMBS.2011.6091624). [ISBN](./ISBN_(identifier)) [978-1-4577-1589-1](./Special:BookSources/978-1-4577-1589-1). [PMID](./PMID_(identifier)) [22255848](https://pubmed.ncbi.nlm.nih.gov/22255848).
47. [↑](./Time_series#cite_ref-47) Diodato, Nazzareno; Di Salvo, Cristina; Bellocchi, Gianni (18 March 2025). ["Climate driven generative time-varying model for improved decadal storm power predictions in the Mediterranean"](https://doi.org/10.1038%2Fs43247-025-02196-2). *Communications Earth & Environment*. **6** (1): 212. [Bibcode](./Bibcode_(identifier)):[2025ComEE...6..212D](https://ui.adsabs.harvard.edu/abs/2025ComEE...6..212D). [doi](./Doi_(identifier)):[10.1038/s43247-025-02196-2](https://doi.org/10.1038%2Fs43247-025-02196-2).
48. [↑](./Time_series#cite_ref-48) Guo, Tianli; Song, Songbai; Yan, Yating (1 October 2022). "A time-varying autoregressive model for groundwater depth prediction". *Journal of Hydrology*. **613** 128394. [Bibcode](./Bibcode_(identifier)):[2022JHyd..61328394G](https://ui.adsabs.harvard.edu/abs/2022JHyd..61328394G). [doi](./Doi_(identifier)):[10.1016/j.jhydrol.2022.128394](https://doi.org/10.1016%2Fj.jhydrol.2022.128394).
49. [↑](./Time_series#cite_ref-49) Zhang, Ting; Wu, Wei Biao (1 June 2012). "Inference of time-varying regression models". *The Annals of Statistics*. **40** (3). [arXiv](./ArXiv_(identifier)):[1208.3552](https://arxiv.org/abs/1208.3552). [doi](./Doi_(identifier)):[10.1214/12-AOS1010](https://doi.org/10.1214%2F12-AOS1010).
50. [↑](./Time_series#cite_ref-50) Chu, Y. J.; Chan, S. C.; Zhang, Z. G.; Tsui, K. M. (May 2012). "A new recursive algorithm for time-varying autoregressive (TVAR) model estimation and its application to speech analysis". *2012 IEEE International Symposium on Circuits and Systems*. pp. 1026–1029. [doi](./Doi_(identifier)):[10.1109/ISCAS.2012.6271402](https://doi.org/10.1109%2FISCAS.2012.6271402). [ISBN](./ISBN_(identifier)) [978-1-4673-0219-7](./Special:BookSources/978-1-4673-0219-7).
51. [↑](./Time_series#cite_ref-51) Zhang, Z. G.; Chan, S. C.; Chen, X. (December 2013). "A new Kalman filter-based recursive method for measuring and tracking time-varying spectrum of nonstationary signals". *2013 9th International Conference on Information, Communications & Signal Processing*. pp. 1–4. [doi](./Doi_(identifier)):[10.1109/ICICS.2013.6782838](https://doi.org/10.1109%2FICICS.2013.6782838). [ISBN](./ISBN_(identifier)) [978-1-4799-0434-1](./Special:BookSources/978-1-4799-0434-1).
52. [↑](./Time_series#cite_ref-52) Kantz, Holger; Thomas, Schreiber (2004). *Nonlinear Time Series Analysis*. London: Cambridge University Press. [ISBN](./ISBN_(identifier)) [978-0-521-52902-0](./Special:BookSources/978-0-521-52902-0).
53. [↑](./Time_series#cite_ref-53) Abarbanel, Henry (Nov 25, 1997). *Analysis of Observed Chaotic Data*. New York: Springer. [ISBN](./ISBN_(identifier)) [978-0-387-98372-1](./Special:BookSources/978-0-387-98372-1).
54. [↑](./Time_series#cite_ref-54) Tomás, R.; Li, Z.; Lopez-Sanchez, J. M.; Liu, P.; Singleton, A. (June 2016). ["Using Wavelet Tools to Analyse Seasonal Variations from InSAR Time-Series Data: A Case Study of the Huangtupo Landslide"](http://link.springer.com/10.1007/s10346-015-0589-y). *Landslides*. **13** (3): 437–450. [Bibcode](./Bibcode_(identifier)):[2016Lands..13..437T](https://ui.adsabs.harvard.edu/abs/2016Lands..13..437T). [doi](./Doi_(identifier)):[10.1007/s10346-015-0589-y](https://doi.org/10.1007%2Fs10346-015-0589-y). [hdl](./Hdl_(identifier)):[10045/62160](https://hdl.handle.net/10045%2F62160). [ISSN](./ISSN_(identifier)) [1612-510X](https://search.worldcat.org/issn/1612-510X).
55. [↑](./Time_series#cite_ref-55) Boashash, B. (ed.), (2003) *Time-Frequency Signal Analysis and Processing: A Comprehensive Reference*, Elsevier Science, Oxford, 2003 [ISBN](./ISBN_(identifier)) [0-08-044335-4](./Special:BookSources/0-08-044335-4)
56. [↑](./Time_series#cite_ref-Nikolicetal_56-0) Nikolić, Danko; Mureşan, Raul C.; Feng, Weijia; Singer, Wolf (March 2012). "Scaled correlation analysis: a better way to compute a cross-correlogram". *European Journal of Neuroscience*. **35** (5): 742–762. [doi](./Doi_(identifier)):[10.1111/j.1460-9568.2011.07987.x](https://doi.org/10.1111%2Fj.1460-9568.2011.07987.x). [PMID](./PMID_(identifier)) [22324876](https://pubmed.ncbi.nlm.nih.gov/22324876). [S2CID](./S2CID_(identifier)) [4694570](https://api.semanticscholar.org/CorpusID:4694570).
57. [↑](./Time_series#cite_ref-57) Li, Aimin; Siqi, Xiong; Junhuai, Li (April 2023). "AngClust: Angle Feature-Based Clustering for Short Time Series Gene Expression Profiles". *IEEE/ACM Transactions on Computational Biology and Bioinformatics*. **20** (2): 1574–1580. [Bibcode](./Bibcode_(identifier)):[2023ITCBB..20.1574L](https://ui.adsabs.harvard.edu/abs/2023ITCBB..20.1574L). [doi](./Doi_(identifier)):[10.1109/TCBB.2022.3192306](https://doi.org/10.1109%2FTCBB.2022.3192306). [PMID](./PMID_(identifier)) [35853049](https://pubmed.ncbi.nlm.nih.gov/35853049).
58. [1](./Time_series#cite_ref-Sakoe_1978_58-0) [2](./Time_series#cite_ref-Sakoe_1978_58-1) Sakoe, H.; Chiba, S. (February 1978). "Dynamic programming algorithm optimization for spoken word recognition". *IEEE Transactions on Acoustics, Speech, and Signal Processing*. **26** (1): 43–49. [doi](./Doi_(identifier)):[10.1109/TASSP.1978.1163055](https://doi.org/10.1109%2FTASSP.1978.1163055). [S2CID](./S2CID_(identifier)) [17900407](https://api.semanticscholar.org/CorpusID:17900407).
59. [↑](./Time_series#cite_ref-59) Mormann, Florian; Andrzejak, Ralph G.; Elger, Christian E.; Lehnertz, Klaus (2007). ["Seizure prediction: the long and winding road"](https://doi.org/10.1093%2Fbrain%2Fawl241). *[Brain](./Brain_(journal))*. **130** (2): 314–333. [doi](./Doi_(identifier)):[10.1093/brain/awl241](https://doi.org/10.1093%2Fbrain%2Fawl241). [PMID](./PMID_(identifier)) [17008335](https://pubmed.ncbi.nlm.nih.gov/17008335).
60. [↑](./Time_series#cite_ref-60) Land, Bruce; Elias, Damian. ["Measuring the 'Complexity' of a time series"](https://web.archive.org/web/20150103050445/https://nbb.cornell.edu/neurobio/land/PROJECTS/Complexity). Archived from [the original](https://www.nbb.cornell.edu/neurobio/land/PROJECTS/Complexity/) on 2015-01-03.
61. [↑](./Time_series#cite_ref-61) Chevyrev, Ilya; Kormilitzin, Andrey (2016). "A Primer on the Signature Method in Machine Learning". [arXiv](./ArXiv_(identifier)):[1603.03788](https://arxiv.org/abs/1603.03788) [[stat.ML](https://arxiv.org/archive/stat.ML)].
62. [↑](./Time_series#cite_ref-62) Ropella, G.E.P.; Nag, D.A.; Hunt, C.A. (2003). "Similarity measures for automated comparison of in silico and in vitro experimental results". *Proceedings of the 25th Annual International Conference of the IEEE Engineering in Medicine and Biology Society (IEEE Cat. No. 03CH37439)*. pp. 2933–2936. [doi](./Doi_(identifier)):[10.1109/IEMBS.2003.1280532](https://doi.org/10.1109%2FIEMBS.2003.1280532). [ISBN](./ISBN_(identifier)) [978-0-7803-7789-9](./Special:BookSources/978-0-7803-7789-9). [S2CID](./S2CID_(identifier)) [17798157](https://api.semanticscholar.org/CorpusID:17798157).
63. [↑](./Time_series#cite_ref-63) Tominski, Christian; Aigner, Wolfgang. ["The TimeViz Browser:A Visual Survey of Visualization Techniques for Time-Oriented Data"](https://web.archive.org/web/20150212033542/http://survey.timeviz.net/). Archived from [the original](http://survey.timeviz.net/) on 2015-02-12. Retrieved 1 June 2014.
64. [↑](./Time_series#cite_ref-Jenrons1884_64-0) W. S. Jevons. Investigations in Currency and Finance. Macmillan, London, 1884

 

## Further reading

 
- De Gooijer, Jan G.; [Hyndman, Rob J.](./Rob_J._Hyndman) (2006). "25 Years of Time Series Forecasting". *International Journal of Forecasting*. Twenty Five Years of Forecasting. **22** (3): 443–473. [CiteSeerX](./CiteSeerX_(identifier)) [10.1.1.154.9227](https://citeseerx.ist.psu.edu/viewdoc/summary?doi=10.1.1.154.9227). [doi](./Doi_(identifier)):[10.1016/j.ijforecast.2006.01.001](https://doi.org/10.1016%2Fj.ijforecast.2006.01.001). [S2CID](./S2CID_(identifier)) [14996235](https://api.semanticscholar.org/CorpusID:14996235).
- [Box, George](./George_E._P._Box); Jenkins, Gwilym (1976), *Time Series Analysis: forecasting and control, rev. ed.*, Oakland, California: Holden-Day
- [Durbin J.](./James_Durbin), Koopman S.J. (2001), *Time Series Analysis by State Space Methods*, [Oxford University Press](./Oxford_University_Press).
- Gershenfeld, Neil (2000), *The Nature of Mathematical Modeling*, [Cambridge University Press](./Cambridge_University_Press), [ISBN](./ISBN_(identifier)) [978-0-521-57095-4](./Special:BookSources/978-0-521-57095-4), [OCLC](./OCLC_(identifier)) [174825352](https://search.worldcat.org/oclc/174825352)
- [Hamilton, James](./James_D._Hamilton) (1994), *Time Series Analysis*, [Princeton University Press](./Princeton_University_Press), [ISBN](./ISBN_(identifier)) [978-0-691-04289-3](./Special:BookSources/978-0-691-04289-3)
- [Priestley, M. B.](./Maurice_Priestley) (1981), *Spectral Analysis and Time Series*, [Academic Press](./Academic_Press). [ISBN](./ISBN_(identifier)) [978-0-12-564901-8](./Special:BookSources/978-0-12-564901-8)
- Shasha, D. (2004), *High Performance Discovery in Time Series*, [Springer](./Springer_Science+Business_Media), [ISBN](./ISBN_(identifier)) [978-0-387-00857-8](./Special:BookSources/978-0-387-00857-8)
- Shumway R. H., Stoffer D. S. (2017), *Time Series Analysis and its Applications: With R Examples (ed. 4)*, Springer, [ISBN](./ISBN_(identifier)) [978-3-319-52451-1](./Special:BookSources/978-3-319-52451-1)
- Weigend A. S., Gershenfeld N. A. (Eds.) (1994), *Time Series Prediction: Forecasting the Future and Understanding the Past*. Proceedings of the NATO Advanced Research Workshop on Comparative Time Series Analysis (Santa Fe, May 1992), [Addison-Wesley](./Addison-Wesley).
- [Wiener, Norbert](./Norbert_Wiener). [*Extrapolation, Interpolation, and Smoothing of Stationary Time Series: With Engineering Applications*](https://direct.mit.edu/books/oa-monograph/4361/Extrapolation-Interpolation-and-Smoothing-of). [MIT Press](./MIT_Press). [ISBN](./ISBN_(identifier)) [978-0-262-25719-0](./Special:BookSources/978-0-262-25719-0).
- Woodward, W. A., Gray, H. L. & Elliott, A. C. (2012), *Applied Time Series Analysis*, [CRC Press](./CRC_Press).
- Auffarth, Ben (2021). [*Machine Learning for Time-Series with Python: Forecast, predict, and detect anomalies with state-of-the-art machine learning methods*](https://www.packtpub.com/product/machine-learning-for-time-series-with-python/9781801819626) (1st ed.). Packt Publishing. [ISBN](./ISBN_(identifier)) [978-1-80181-962-6](./Special:BookSources/978-1-80181-962-6). Retrieved 5 November 2021.

 

## External links

   [![Wikimedia Commons logo](//upload.wikimedia.org/wikipedia/en/thumb/4/4a/Commons-logo.svg/40px-Commons-logo.svg.png)](./File:Commons-logo.svg) Wikimedia Commons has media related to [Time series](https://commons.wikimedia.org/wiki/Category:Time%20series).  
- [Introduction to Time series Analysis (Engineering Statistics Handbook)](http://www.itl.nist.gov/div898/handbook/pmc/section4/pmc4.htm) — A practical guide to time-series analysis

 
| vteStatistics |
| --- |
| OutlineIndex |
| Descriptive statisticsContinuous dataCenterMeanArithmeticArithmetic-GeometricContraharmonicCubicGeneralized/powerGeometricHarmonicHeronianHeinzLehmerMedianModeDispersionAverage absolute deviationCoefficient of variationInterquartile rangePercentileRangeStandard deviationVarianceShapeCentral limit theoremMomentsKurtosisL-momentsSkewnessCount dataIndex of dispersionSummary tablesContingency tableFrequency distributionGrouped dataDependencePartial correlationPearson product-moment correlationRank correlationKendall's τSpearman's ρScatter plotGraphicsBar chartBiplotBox plotControl chartCorrelogramFan chartForest plotHistogramPie chartQ–Q plotRadar chartRun chartScatter plotStem-and-leaf displayViolin plotHeatmapScatter Plot MatrixECDF plotLine chart | Descriptive statistics | Continuous dataCenterMeanArithmeticArithmetic-GeometricContraharmonicCubicGeneralized/powerGeometricHarmonicHeronianHeinzLehmerMedianModeDispersionAverage absolute deviationCoefficient of variationInterquartile rangePercentileRangeStandard deviationVarianceShapeCentral limit theoremMomentsKurtosisL-momentsSkewnessCount dataIndex of dispersionSummary tablesContingency tableFrequency distributionGrouped dataDependencePartial correlationPearson product-moment correlationRank correlationKendall's τSpearman's ρScatter plotGraphicsBar chartBiplotBox plotControl chartCorrelogramFan chartForest plotHistogramPie chartQ–Q plotRadar chartRun chartScatter plotStem-and-leaf displayViolin plotHeatmapScatter Plot MatrixECDF plotLine chart | Continuous data | CenterMeanArithmeticArithmetic-GeometricContraharmonicCubicGeneralized/powerGeometricHarmonicHeronianHeinzLehmerMedianModeDispersionAverage absolute deviationCoefficient of variationInterquartile rangePercentileRangeStandard deviationVarianceShapeCentral limit theoremMomentsKurtosisL-momentsSkewness | Center | MeanArithmeticArithmetic-GeometricContraharmonicCubicGeneralized/powerGeometricHarmonicHeronianHeinzLehmerMedianMode | Dispersion | Average absolute deviationCoefficient of variationInterquartile rangePercentileRangeStandard deviationVariance | Shape | Central limit theoremMomentsKurtosisL-momentsSkewness | Count data | Index of dispersion | Summary tables | Contingency tableFrequency distributionGrouped data | Dependence | Partial correlationPearson product-moment correlationRank correlationKendall's τSpearman's ρScatter plot | Graphics | Bar chartBiplotBox plotControl chartCorrelogramFan chartForest plotHistogramPie chartQ–Q plotRadar chartRun chartScatter plotStem-and-leaf displayViolin plotHeatmapScatter Plot MatrixECDF plotLine chart |
| Descriptive statistics |
| Continuous dataCenterMeanArithmeticArithmetic-GeometricContraharmonicCubicGeneralized/powerGeometricHarmonicHeronianHeinzLehmerMedianModeDispersionAverage absolute deviationCoefficient of variationInterquartile rangePercentileRangeStandard deviationVarianceShapeCentral limit theoremMomentsKurtosisL-momentsSkewnessCount dataIndex of dispersionSummary tablesContingency tableFrequency distributionGrouped dataDependencePartial correlationPearson product-moment correlationRank correlationKendall's τSpearman's ρScatter plotGraphicsBar chartBiplotBox plotControl chartCorrelogramFan chartForest plotHistogramPie chartQ–Q plotRadar chartRun chartScatter plotStem-and-leaf displayViolin plotHeatmapScatter Plot MatrixECDF plotLine chart | Continuous data | CenterMeanArithmeticArithmetic-GeometricContraharmonicCubicGeneralized/powerGeometricHarmonicHeronianHeinzLehmerMedianModeDispersionAverage absolute deviationCoefficient of variationInterquartile rangePercentileRangeStandard deviationVarianceShapeCentral limit theoremMomentsKurtosisL-momentsSkewness | Center | MeanArithmeticArithmetic-GeometricContraharmonicCubicGeneralized/powerGeometricHarmonicHeronianHeinzLehmerMedianMode | Dispersion | Average absolute deviationCoefficient of variationInterquartile rangePercentileRangeStandard deviationVariance | Shape | Central limit theoremMomentsKurtosisL-momentsSkewness | Count data | Index of dispersion | Summary tables | Contingency tableFrequency distributionGrouped data | Dependence | Partial correlationPearson product-moment correlationRank correlationKendall's τSpearman's ρScatter plot | Graphics | Bar chartBiplotBox plotControl chartCorrelogramFan chartForest plotHistogramPie chartQ–Q plotRadar chartRun chartScatter plotStem-and-leaf displayViolin plotHeatmapScatter Plot MatrixECDF plotLine chart |
| Continuous data | CenterMeanArithmeticArithmetic-GeometricContraharmonicCubicGeneralized/powerGeometricHarmonicHeronianHeinzLehmerMedianModeDispersionAverage absolute deviationCoefficient of variationInterquartile rangePercentileRangeStandard deviationVarianceShapeCentral limit theoremMomentsKurtosisL-momentsSkewness | Center | MeanArithmeticArithmetic-GeometricContraharmonicCubicGeneralized/powerGeometricHarmonicHeronianHeinzLehmerMedianMode | Dispersion | Average absolute deviationCoefficient of variationInterquartile rangePercentileRangeStandard deviationVariance | Shape | Central limit theoremMomentsKurtosisL-momentsSkewness |
| Center | MeanArithmeticArithmetic-GeometricContraharmonicCubicGeneralized/powerGeometricHarmonicHeronianHeinzLehmerMedianMode |
| Dispersion | Average absolute deviationCoefficient of variationInterquartile rangePercentileRangeStandard deviationVariance |
| Shape | Central limit theoremMomentsKurtosisL-momentsSkewness |
| Count data | Index of dispersion |
| Summary tables | Contingency tableFrequency distributionGrouped data |
| Dependence | Partial correlationPearson product-moment correlationRank correlationKendall's τSpearman's ρScatter plot |
| Graphics | Bar chartBiplotBox plotControl chartCorrelogramFan chartForest plotHistogramPie chartQ–Q plotRadar chartRun chartScatter plotStem-and-leaf displayViolin plotHeatmapScatter Plot MatrixECDF plotLine chart |
| Statistical data processingTransformationsData transformationLog transformationPower transformBox–Cox transformationYeo–Johnson transformationVariance-stabilizing transformationAnscombe transformFisher transformationScaling and normalizationFeature scalingNormalizationStandardization (z-score)Min–max normalizationUnit vector normalizationData cleaningData cleaningOutlierWinsorizingTruncationMissing dataData reductionDimensionality reductionPrincipal component analysisFactor analysisTime-series preprocessingDifferencingDetrendingSeasonal adjustmentStationarity transformation | Statistical data processing | TransformationsData transformationLog transformationPower transformBox–Cox transformationYeo–Johnson transformationVariance-stabilizing transformationAnscombe transformFisher transformationScaling and normalizationFeature scalingNormalizationStandardization (z-score)Min–max normalizationUnit vector normalizationData cleaningData cleaningOutlierWinsorizingTruncationMissing dataData reductionDimensionality reductionPrincipal component analysisFactor analysisTime-series preprocessingDifferencingDetrendingSeasonal adjustmentStationarity transformation | Transformations | Data transformationLog transformationPower transformBox–Cox transformationYeo–Johnson transformationVariance-stabilizing transformationAnscombe transformFisher transformation | Scaling and normalization | Feature scalingNormalizationStandardization (z-score)Min–max normalizationUnit vector normalization | Data cleaning | Data cleaningOutlierWinsorizingTruncationMissing data | Data reduction | Dimensionality reductionPrincipal component analysisFactor analysis | Time-series preprocessing | DifferencingDetrendingSeasonal adjustmentStationarity transformation |
| Statistical data processing |
| TransformationsData transformationLog transformationPower transformBox–Cox transformationYeo–Johnson transformationVariance-stabilizing transformationAnscombe transformFisher transformationScaling and normalizationFeature scalingNormalizationStandardization (z-score)Min–max normalizationUnit vector normalizationData cleaningData cleaningOutlierWinsorizingTruncationMissing dataData reductionDimensionality reductionPrincipal component analysisFactor analysisTime-series preprocessingDifferencingDetrendingSeasonal adjustmentStationarity transformation | Transformations | Data transformationLog transformationPower transformBox–Cox transformationYeo–Johnson transformationVariance-stabilizing transformationAnscombe transformFisher transformation | Scaling and normalization | Feature scalingNormalizationStandardization (z-score)Min–max normalizationUnit vector normalization | Data cleaning | Data cleaningOutlierWinsorizingTruncationMissing data | Data reduction | Dimensionality reductionPrincipal component analysisFactor analysis | Time-series preprocessing | DifferencingDetrendingSeasonal adjustmentStationarity transformation |
| Transformations | Data transformationLog transformationPower transformBox–Cox transformationYeo–Johnson transformationVariance-stabilizing transformationAnscombe transformFisher transformation |
| Scaling and normalization | Feature scalingNormalizationStandardization (z-score)Min–max normalizationUnit vector normalization |
| Data cleaning | Data cleaningOutlierWinsorizingTruncationMissing data |
| Data reduction | Dimensionality reductionPrincipal component analysisFactor analysis |
| Time-series preprocessing | DifferencingDetrendingSeasonal adjustmentStationarity transformation |
| Data collectionStudy designEffect sizeMissing dataOptimal designPopulationReplicationSample size determinationStatisticStatistical powerSurvey methodologySamplingClusterStratifiedOpinion pollQuestionnaireStandard errorControlled experimentsBlockingFactorial experimentInteractionRandom assignmentRandomized controlled trialRandomized experimentScientific controlAdaptive designsAdaptive clinical trialStochastic approximationUp-and-down designsObservational studiesCohort studyCross-sectional studyNatural experimentQuasi-experiment | Data collection | Study designEffect sizeMissing dataOptimal designPopulationReplicationSample size determinationStatisticStatistical powerSurvey methodologySamplingClusterStratifiedOpinion pollQuestionnaireStandard errorControlled experimentsBlockingFactorial experimentInteractionRandom assignmentRandomized controlled trialRandomized experimentScientific controlAdaptive designsAdaptive clinical trialStochastic approximationUp-and-down designsObservational studiesCohort studyCross-sectional studyNatural experimentQuasi-experiment | Study design | Effect sizeMissing dataOptimal designPopulationReplicationSample size determinationStatisticStatistical power | Survey methodology | SamplingClusterStratifiedOpinion pollQuestionnaireStandard error | Controlled experiments | BlockingFactorial experimentInteractionRandom assignmentRandomized controlled trialRandomized experimentScientific control | Adaptive designs | Adaptive clinical trialStochastic approximationUp-and-down designs | Observational studies | Cohort studyCross-sectional studyNatural experimentQuasi-experiment |
| Data collection |
| Study designEffect sizeMissing dataOptimal designPopulationReplicationSample size determinationStatisticStatistical powerSurvey methodologySamplingClusterStratifiedOpinion pollQuestionnaireStandard errorControlled experimentsBlockingFactorial experimentInteractionRandom assignmentRandomized controlled trialRandomized experimentScientific controlAdaptive designsAdaptive clinical trialStochastic approximationUp-and-down designsObservational studiesCohort studyCross-sectional studyNatural experimentQuasi-experiment | Study design | Effect sizeMissing dataOptimal designPopulationReplicationSample size determinationStatisticStatistical power | Survey methodology | SamplingClusterStratifiedOpinion pollQuestionnaireStandard error | Controlled experiments | BlockingFactorial experimentInteractionRandom assignmentRandomized controlled trialRandomized experimentScientific control | Adaptive designs | Adaptive clinical trialStochastic approximationUp-and-down designs | Observational studies | Cohort studyCross-sectional studyNatural experimentQuasi-experiment |
| Study design | Effect sizeMissing dataOptimal designPopulationReplicationSample size determinationStatisticStatistical power |
| Survey methodology | SamplingClusterStratifiedOpinion pollQuestionnaireStandard error |
| Controlled experiments | BlockingFactorial experimentInteractionRandom assignmentRandomized controlled trialRandomized experimentScientific control |
| Adaptive designs | Adaptive clinical trialStochastic approximationUp-and-down designs |
| Observational studies | Cohort studyCross-sectional studyNatural experimentQuasi-experiment |
| Statistical inferenceStatistical theoryPopulationStatisticProbability distributionSampling distributionOrder statisticEmpirical distributionDensity estimationStatistical modelModel specificationLpspaceParameterlocationscaleshapeParametric familyLikelihood(monotone)Location–scale familyExponential familyCompletenessSufficiencyStatistical functionalBootstrapUVOptimal decisionloss functionEfficiencyStatistical distancedivergenceAsymptoticsRobustnessFrequentist inferencePoint estimationEstimating equationsMaximum likelihoodMethod of momentsM-estimatorMinimum distanceUnbiased estimatorsMean-unbiased minimum-varianceRao–BlackwellizationLehmann–Scheffé theoremMedian unbiasedPlug-inInterval estimationConfidence intervalPivotLikelihood intervalPrediction intervalTolerance intervalResamplingBootstrapJackknifeTesting hypotheses1- & 2-tailsPowerUniformly most powerful testPermutation testRandomization testMultiple comparisonsParametric testsLikelihood-ratioScore/Lagrange multiplierWaldSpecific testsZ-test(normal)Student'st-testF-testGoodness of fitChi-squaredG-testKolmogorov–SmirnovAnderson–DarlingLillieforsJarque–BeraNormality(Shapiro–Wilk)Likelihood-ratio testModel selectionCross validationAICBICRank statisticsSignSample medianSigned rank(Wilcoxon)Hodges–Lehmann estimatorRank sum(Mann–Whitney)Nonparametricanova1-way(Kruskal–Wallis)2-way(Friedman)Ordered alternative(Jonckheere–Terpstra)Van der Waerden testBayesian inferenceBayesian probabilitypriorposteriorCredible intervalBayes factorBayesian estimatorMaximum posterior estimator | Statistical inference | Statistical theoryPopulationStatisticProbability distributionSampling distributionOrder statisticEmpirical distributionDensity estimationStatistical modelModel specificationLpspaceParameterlocationscaleshapeParametric familyLikelihood(monotone)Location–scale familyExponential familyCompletenessSufficiencyStatistical functionalBootstrapUVOptimal decisionloss functionEfficiencyStatistical distancedivergenceAsymptoticsRobustnessFrequentist inferencePoint estimationEstimating equationsMaximum likelihoodMethod of momentsM-estimatorMinimum distanceUnbiased estimatorsMean-unbiased minimum-varianceRao–BlackwellizationLehmann–Scheffé theoremMedian unbiasedPlug-inInterval estimationConfidence intervalPivotLikelihood intervalPrediction intervalTolerance intervalResamplingBootstrapJackknifeTesting hypotheses1- & 2-tailsPowerUniformly most powerful testPermutation testRandomization testMultiple comparisonsParametric testsLikelihood-ratioScore/Lagrange multiplierWaldSpecific testsZ-test(normal)Student'st-testF-testGoodness of fitChi-squaredG-testKolmogorov–SmirnovAnderson–DarlingLillieforsJarque–BeraNormality(Shapiro–Wilk)Likelihood-ratio testModel selectionCross validationAICBICRank statisticsSignSample medianSigned rank(Wilcoxon)Hodges–Lehmann estimatorRank sum(Mann–Whitney)Nonparametricanova1-way(Kruskal–Wallis)2-way(Friedman)Ordered alternative(Jonckheere–Terpstra)Van der Waerden testBayesian inferenceBayesian probabilitypriorposteriorCredible intervalBayes factorBayesian estimatorMaximum posterior estimator | Statistical theory | PopulationStatisticProbability distributionSampling distributionOrder statisticEmpirical distributionDensity estimationStatistical modelModel specificationLpspaceParameterlocationscaleshapeParametric familyLikelihood(monotone)Location–scale familyExponential familyCompletenessSufficiencyStatistical functionalBootstrapUVOptimal decisionloss functionEfficiencyStatistical distancedivergenceAsymptoticsRobustness | Frequentist inference | Point estimationEstimating equationsMaximum likelihoodMethod of momentsM-estimatorMinimum distanceUnbiased estimatorsMean-unbiased minimum-varianceRao–BlackwellizationLehmann–Scheffé theoremMedian unbiasedPlug-inInterval estimationConfidence intervalPivotLikelihood intervalPrediction intervalTolerance intervalResamplingBootstrapJackknifeTesting hypotheses1- & 2-tailsPowerUniformly most powerful testPermutation testRandomization testMultiple comparisonsParametric testsLikelihood-ratioScore/Lagrange multiplierWald | Point estimation | Estimating equationsMaximum likelihoodMethod of momentsM-estimatorMinimum distanceUnbiased estimatorsMean-unbiased minimum-varianceRao–BlackwellizationLehmann–Scheffé theoremMedian unbiasedPlug-in | Interval estimation | Confidence intervalPivotLikelihood intervalPrediction intervalTolerance intervalResamplingBootstrapJackknife | Testing hypotheses | 1- & 2-tailsPowerUniformly most powerful testPermutation testRandomization testMultiple comparisons | Parametric tests | Likelihood-ratioScore/Lagrange multiplierWald | Specific tests | Z-test(normal)Student'st-testF-testGoodness of fitChi-squaredG-testKolmogorov–SmirnovAnderson–DarlingLillieforsJarque–BeraNormality(Shapiro–Wilk)Likelihood-ratio testModel selectionCross validationAICBICRank statisticsSignSample medianSigned rank(Wilcoxon)Hodges–Lehmann estimatorRank sum(Mann–Whitney)Nonparametricanova1-way(Kruskal–Wallis)2-way(Friedman)Ordered alternative(Jonckheere–Terpstra)Van der Waerden test | Z-test(normal)Student'st-testF-test | Goodness of fit | Chi-squaredG-testKolmogorov–SmirnovAnderson–DarlingLillieforsJarque–BeraNormality(Shapiro–Wilk)Likelihood-ratio testModel selectionCross validationAICBIC | Rank statistics | SignSample medianSigned rank(Wilcoxon)Hodges–Lehmann estimatorRank sum(Mann–Whitney)Nonparametricanova1-way(Kruskal–Wallis)2-way(Friedman)Ordered alternative(Jonckheere–Terpstra)Van der Waerden test | Bayesian inference | Bayesian probabilitypriorposteriorCredible intervalBayes factorBayesian estimatorMaximum posterior estimator |
| Statistical inference |
| Statistical theoryPopulationStatisticProbability distributionSampling distributionOrder statisticEmpirical distributionDensity estimationStatistical modelModel specificationLpspaceParameterlocationscaleshapeParametric familyLikelihood(monotone)Location–scale familyExponential familyCompletenessSufficiencyStatistical functionalBootstrapUVOptimal decisionloss functionEfficiencyStatistical distancedivergenceAsymptoticsRobustnessFrequentist inferencePoint estimationEstimating equationsMaximum likelihoodMethod of momentsM-estimatorMinimum distanceUnbiased estimatorsMean-unbiased minimum-varianceRao–BlackwellizationLehmann–Scheffé theoremMedian unbiasedPlug-inInterval estimationConfidence intervalPivotLikelihood intervalPrediction intervalTolerance intervalResamplingBootstrapJackknifeTesting hypotheses1- & 2-tailsPowerUniformly most powerful testPermutation testRandomization testMultiple comparisonsParametric testsLikelihood-ratioScore/Lagrange multiplierWaldSpecific testsZ-test(normal)Student'st-testF-testGoodness of fitChi-squaredG-testKolmogorov–SmirnovAnderson–DarlingLillieforsJarque–BeraNormality(Shapiro–Wilk)Likelihood-ratio testModel selectionCross validationAICBICRank statisticsSignSample medianSigned rank(Wilcoxon)Hodges–Lehmann estimatorRank sum(Mann–Whitney)Nonparametricanova1-way(Kruskal–Wallis)2-way(Friedman)Ordered alternative(Jonckheere–Terpstra)Van der Waerden testBayesian inferenceBayesian probabilitypriorposteriorCredible intervalBayes factorBayesian estimatorMaximum posterior estimator | Statistical theory | PopulationStatisticProbability distributionSampling distributionOrder statisticEmpirical distributionDensity estimationStatistical modelModel specificationLpspaceParameterlocationscaleshapeParametric familyLikelihood(monotone)Location–scale familyExponential familyCompletenessSufficiencyStatistical functionalBootstrapUVOptimal decisionloss functionEfficiencyStatistical distancedivergenceAsymptoticsRobustness | Frequentist inference | Point estimationEstimating equationsMaximum likelihoodMethod of momentsM-estimatorMinimum distanceUnbiased estimatorsMean-unbiased minimum-varianceRao–BlackwellizationLehmann–Scheffé theoremMedian unbiasedPlug-inInterval estimationConfidence intervalPivotLikelihood intervalPrediction intervalTolerance intervalResamplingBootstrapJackknifeTesting hypotheses1- & 2-tailsPowerUniformly most powerful testPermutation testRandomization testMultiple comparisonsParametric testsLikelihood-ratioScore/Lagrange multiplierWald | Point estimation | Estimating equationsMaximum likelihoodMethod of momentsM-estimatorMinimum distanceUnbiased estimatorsMean-unbiased minimum-varianceRao–BlackwellizationLehmann–Scheffé theoremMedian unbiasedPlug-in | Interval estimation | Confidence intervalPivotLikelihood intervalPrediction intervalTolerance intervalResamplingBootstrapJackknife | Testing hypotheses | 1- & 2-tailsPowerUniformly most powerful testPermutation testRandomization testMultiple comparisons | Parametric tests | Likelihood-ratioScore/Lagrange multiplierWald | Specific tests | Z-test(normal)Student'st-testF-testGoodness of fitChi-squaredG-testKolmogorov–SmirnovAnderson–DarlingLillieforsJarque–BeraNormality(Shapiro–Wilk)Likelihood-ratio testModel selectionCross validationAICBICRank statisticsSignSample medianSigned rank(Wilcoxon)Hodges–Lehmann estimatorRank sum(Mann–Whitney)Nonparametricanova1-way(Kruskal–Wallis)2-way(Friedman)Ordered alternative(Jonckheere–Terpstra)Van der Waerden test | Z-test(normal)Student'st-testF-test | Goodness of fit | Chi-squaredG-testKolmogorov–SmirnovAnderson–DarlingLillieforsJarque–BeraNormality(Shapiro–Wilk)Likelihood-ratio testModel selectionCross validationAICBIC | Rank statistics | SignSample medianSigned rank(Wilcoxon)Hodges–Lehmann estimatorRank sum(Mann–Whitney)Nonparametricanova1-way(Kruskal–Wallis)2-way(Friedman)Ordered alternative(Jonckheere–Terpstra)Van der Waerden test | Bayesian inference | Bayesian probabilitypriorposteriorCredible intervalBayes factorBayesian estimatorMaximum posterior estimator |
| Statistical theory | PopulationStatisticProbability distributionSampling distributionOrder statisticEmpirical distributionDensity estimationStatistical modelModel specificationLpspaceParameterlocationscaleshapeParametric familyLikelihood(monotone)Location–scale familyExponential familyCompletenessSufficiencyStatistical functionalBootstrapUVOptimal decisionloss functionEfficiencyStatistical distancedivergenceAsymptoticsRobustness |
| Frequentist inference | Point estimationEstimating equationsMaximum likelihoodMethod of momentsM-estimatorMinimum distanceUnbiased estimatorsMean-unbiased minimum-varianceRao–BlackwellizationLehmann–Scheffé theoremMedian unbiasedPlug-inInterval estimationConfidence intervalPivotLikelihood intervalPrediction intervalTolerance intervalResamplingBootstrapJackknifeTesting hypotheses1- & 2-tailsPowerUniformly most powerful testPermutation testRandomization testMultiple comparisonsParametric testsLikelihood-ratioScore/Lagrange multiplierWald | Point estimation | Estimating equationsMaximum likelihoodMethod of momentsM-estimatorMinimum distanceUnbiased estimatorsMean-unbiased minimum-varianceRao–BlackwellizationLehmann–Scheffé theoremMedian unbiasedPlug-in | Interval estimation | Confidence intervalPivotLikelihood intervalPrediction intervalTolerance intervalResamplingBootstrapJackknife | Testing hypotheses | 1- & 2-tailsPowerUniformly most powerful testPermutation testRandomization testMultiple comparisons | Parametric tests | Likelihood-ratioScore/Lagrange multiplierWald |
| Point estimation | Estimating equationsMaximum likelihoodMethod of momentsM-estimatorMinimum distanceUnbiased estimatorsMean-unbiased minimum-varianceRao–BlackwellizationLehmann–Scheffé theoremMedian unbiasedPlug-in |
| Interval estimation | Confidence intervalPivotLikelihood intervalPrediction intervalTolerance intervalResamplingBootstrapJackknife |
| Testing hypotheses | 1- & 2-tailsPowerUniformly most powerful testPermutation testRandomization testMultiple comparisons |
| Parametric tests | Likelihood-ratioScore/Lagrange multiplierWald |
| Specific tests | Z-test(normal)Student'st-testF-testGoodness of fitChi-squaredG-testKolmogorov–SmirnovAnderson–DarlingLillieforsJarque–BeraNormality(Shapiro–Wilk)Likelihood-ratio testModel selectionCross validationAICBICRank statisticsSignSample medianSigned rank(Wilcoxon)Hodges–Lehmann estimatorRank sum(Mann–Whitney)Nonparametricanova1-way(Kruskal–Wallis)2-way(Friedman)Ordered alternative(Jonckheere–Terpstra)Van der Waerden test | Z-test(normal)Student'st-testF-test | Goodness of fit | Chi-squaredG-testKolmogorov–SmirnovAnderson–DarlingLillieforsJarque–BeraNormality(Shapiro–Wilk)Likelihood-ratio testModel selectionCross validationAICBIC | Rank statistics | SignSample medianSigned rank(Wilcoxon)Hodges–Lehmann estimatorRank sum(Mann–Whitney)Nonparametricanova1-way(Kruskal–Wallis)2-way(Friedman)Ordered alternative(Jonckheere–Terpstra)Van der Waerden test |
| Z-test(normal)Student'st-testF-test |
| Goodness of fit | Chi-squaredG-testKolmogorov–SmirnovAnderson–DarlingLillieforsJarque–BeraNormality(Shapiro–Wilk)Likelihood-ratio testModel selectionCross validationAICBIC |
| Rank statistics | SignSample medianSigned rank(Wilcoxon)Hodges–Lehmann estimatorRank sum(Mann–Whitney)Nonparametricanova1-way(Kruskal–Wallis)2-way(Friedman)Ordered alternative(Jonckheere–Terpstra)Van der Waerden test |
| Bayesian inference | Bayesian probabilitypriorposteriorCredible intervalBayes factorBayesian estimatorMaximum posterior estimator |
| CorrelationRegression analysisCorrelationPearson product-momentPartial correlationConfounding variableCoefficient of determinationRegression analysisErrors and residualsRegression validationMixed effects modelsSimultaneous equations modelsMultivariate adaptive regression splines (MARS)Template:Least squares and regression analysisLinear regressionSimple linear regressionOrdinary least squaresGeneral linear modelBayesian regressionNon-standard predictorsNonlinear regressionNonparametricSemiparametricIsotonicRobustHomoscedasticity and HeteroscedasticityGeneralized linear modelExponential familiesLogistic(Bernoulli)/Binomial/Poisson regressionsPartition of varianceAnalysis of variance (ANOVA, anova)Analysis of covarianceMultivariate ANOVADegrees of freedom | CorrelationRegression analysis | CorrelationPearson product-momentPartial correlationConfounding variableCoefficient of determinationRegression analysisErrors and residualsRegression validationMixed effects modelsSimultaneous equations modelsMultivariate adaptive regression splines (MARS)Template:Least squares and regression analysisLinear regressionSimple linear regressionOrdinary least squaresGeneral linear modelBayesian regressionNon-standard predictorsNonlinear regressionNonparametricSemiparametricIsotonicRobustHomoscedasticity and HeteroscedasticityGeneralized linear modelExponential familiesLogistic(Bernoulli)/Binomial/Poisson regressionsPartition of varianceAnalysis of variance (ANOVA, anova)Analysis of covarianceMultivariate ANOVADegrees of freedom | Correlation | Pearson product-momentPartial correlationConfounding variableCoefficient of determination | Regression analysis | Errors and residualsRegression validationMixed effects modelsSimultaneous equations modelsMultivariate adaptive regression splines (MARS)Template:Least squares and regression analysis | Linear regression | Simple linear regressionOrdinary least squaresGeneral linear modelBayesian regression | Non-standard predictors | Nonlinear regressionNonparametricSemiparametricIsotonicRobustHomoscedasticity and Heteroscedasticity | Generalized linear model | Exponential familiesLogistic(Bernoulli)/Binomial/Poisson regressions | Partition of variance | Analysis of variance (ANOVA, anova)Analysis of covarianceMultivariate ANOVADegrees of freedom |
| CorrelationRegression analysis |
| CorrelationPearson product-momentPartial correlationConfounding variableCoefficient of determinationRegression analysisErrors and residualsRegression validationMixed effects modelsSimultaneous equations modelsMultivariate adaptive regression splines (MARS)Template:Least squares and regression analysisLinear regressionSimple linear regressionOrdinary least squaresGeneral linear modelBayesian regressionNon-standard predictorsNonlinear regressionNonparametricSemiparametricIsotonicRobustHomoscedasticity and HeteroscedasticityGeneralized linear modelExponential familiesLogistic(Bernoulli)/Binomial/Poisson regressionsPartition of varianceAnalysis of variance (ANOVA, anova)Analysis of covarianceMultivariate ANOVADegrees of freedom | Correlation | Pearson product-momentPartial correlationConfounding variableCoefficient of determination | Regression analysis | Errors and residualsRegression validationMixed effects modelsSimultaneous equations modelsMultivariate adaptive regression splines (MARS)Template:Least squares and regression analysis | Linear regression | Simple linear regressionOrdinary least squaresGeneral linear modelBayesian regression | Non-standard predictors | Nonlinear regressionNonparametricSemiparametricIsotonicRobustHomoscedasticity and Heteroscedasticity | Generalized linear model | Exponential familiesLogistic(Bernoulli)/Binomial/Poisson regressions | Partition of variance | Analysis of variance (ANOVA, anova)Analysis of covarianceMultivariate ANOVADegrees of freedom |
| Correlation | Pearson product-momentPartial correlationConfounding variableCoefficient of determination |
| Regression analysis | Errors and residualsRegression validationMixed effects modelsSimultaneous equations modelsMultivariate adaptive regression splines (MARS)Template:Least squares and regression analysis |
| Linear regression | Simple linear regressionOrdinary least squaresGeneral linear modelBayesian regression |
| Non-standard predictors | Nonlinear regressionNonparametricSemiparametricIsotonicRobustHomoscedasticity and Heteroscedasticity |
| Generalized linear model | Exponential familiesLogistic(Bernoulli)/Binomial/Poisson regressions |
| Partition of variance | Analysis of variance (ANOVA, anova)Analysis of covarianceMultivariate ANOVADegrees of freedom |
| Categorical/multivariate/time-series/survival analysisCategoricalCohen's kappaContingency tableGraphical modelLog-linear modelMcNemar's testCochran–Mantel–Haenszel statisticsMultivariateRegressionManovaPrincipal componentsCanonical correlationDiscriminant analysisCluster analysisClassificationStructural equation modelFactor analysisMultivariate distributionsElliptical distributionsNormalTime-seriesGeneralDecompositionTrendStationaritySeasonal adjustmentExponential smoothingCointegrationStructural breakGranger causalitySpecific testsDickey–FullerJohansenQ-statistic(Ljung–Box)Durbin–WatsonBreusch–GodfreyTime domainAutocorrelation (ACF)partial (PACF)Cross-correlation (XCF)ARMA modelARIMA model(Box–Jenkins)Autoregressive conditional heteroskedasticity (ARCH)Vector autoregression (VAR)(Autoregressive model (AR))Frequency domainSpectral density estimationFourier analysisLeast-squares spectral analysisWaveletWhittle likelihoodSurvivalSurvival functionKaplan–Meier estimator (product limit)Proportional hazards modelsAccelerated failure time (AFT) modelFirst hitting timeHazard functionNelson–Aalen estimatorTestLog-rank test | Categorical/multivariate/time-series/survival analysis | CategoricalCohen's kappaContingency tableGraphical modelLog-linear modelMcNemar's testCochran–Mantel–Haenszel statisticsMultivariateRegressionManovaPrincipal componentsCanonical correlationDiscriminant analysisCluster analysisClassificationStructural equation modelFactor analysisMultivariate distributionsElliptical distributionsNormalTime-seriesGeneralDecompositionTrendStationaritySeasonal adjustmentExponential smoothingCointegrationStructural breakGranger causalitySpecific testsDickey–FullerJohansenQ-statistic(Ljung–Box)Durbin–WatsonBreusch–GodfreyTime domainAutocorrelation (ACF)partial (PACF)Cross-correlation (XCF)ARMA modelARIMA model(Box–Jenkins)Autoregressive conditional heteroskedasticity (ARCH)Vector autoregression (VAR)(Autoregressive model (AR))Frequency domainSpectral density estimationFourier analysisLeast-squares spectral analysisWaveletWhittle likelihoodSurvivalSurvival functionKaplan–Meier estimator (product limit)Proportional hazards modelsAccelerated failure time (AFT) modelFirst hitting timeHazard functionNelson–Aalen estimatorTestLog-rank test | Categorical | Cohen's kappaContingency tableGraphical modelLog-linear modelMcNemar's testCochran–Mantel–Haenszel statistics | Multivariate | RegressionManovaPrincipal componentsCanonical correlationDiscriminant analysisCluster analysisClassificationStructural equation modelFactor analysisMultivariate distributionsElliptical distributionsNormal | Time-series | GeneralDecompositionTrendStationaritySeasonal adjustmentExponential smoothingCointegrationStructural breakGranger causalitySpecific testsDickey–FullerJohansenQ-statistic(Ljung–Box)Durbin–WatsonBreusch–GodfreyTime domainAutocorrelation (ACF)partial (PACF)Cross-correlation (XCF)ARMA modelARIMA model(Box–Jenkins)Autoregressive conditional heteroskedasticity (ARCH)Vector autoregression (VAR)(Autoregressive model (AR))Frequency domainSpectral density estimationFourier analysisLeast-squares spectral analysisWaveletWhittle likelihood | General | DecompositionTrendStationaritySeasonal adjustmentExponential smoothingCointegrationStructural breakGranger causality | Specific tests | Dickey–FullerJohansenQ-statistic(Ljung–Box)Durbin–WatsonBreusch–Godfrey | Time domain | Autocorrelation (ACF)partial (PACF)Cross-correlation (XCF)ARMA modelARIMA model(Box–Jenkins)Autoregressive conditional heteroskedasticity (ARCH)Vector autoregression (VAR)(Autoregressive model (AR)) | Frequency domain | Spectral density estimationFourier analysisLeast-squares spectral analysisWaveletWhittle likelihood | Survival | Survival functionKaplan–Meier estimator (product limit)Proportional hazards modelsAccelerated failure time (AFT) modelFirst hitting timeHazard functionNelson–Aalen estimatorTestLog-rank test | Survival function | Kaplan–Meier estimator (product limit)Proportional hazards modelsAccelerated failure time (AFT) modelFirst hitting time | Hazard function | Nelson–Aalen estimator | Test | Log-rank test |
| Categorical/multivariate/time-series/survival analysis |
| CategoricalCohen's kappaContingency tableGraphical modelLog-linear modelMcNemar's testCochran–Mantel–Haenszel statisticsMultivariateRegressionManovaPrincipal componentsCanonical correlationDiscriminant analysisCluster analysisClassificationStructural equation modelFactor analysisMultivariate distributionsElliptical distributionsNormalTime-seriesGeneralDecompositionTrendStationaritySeasonal adjustmentExponential smoothingCointegrationStructural breakGranger causalitySpecific testsDickey–FullerJohansenQ-statistic(Ljung–Box)Durbin–WatsonBreusch–GodfreyTime domainAutocorrelation (ACF)partial (PACF)Cross-correlation (XCF)ARMA modelARIMA model(Box–Jenkins)Autoregressive conditional heteroskedasticity (ARCH)Vector autoregression (VAR)(Autoregressive model (AR))Frequency domainSpectral density estimationFourier analysisLeast-squares spectral analysisWaveletWhittle likelihoodSurvivalSurvival functionKaplan–Meier estimator (product limit)Proportional hazards modelsAccelerated failure time (AFT) modelFirst hitting timeHazard functionNelson–Aalen estimatorTestLog-rank test | Categorical | Cohen's kappaContingency tableGraphical modelLog-linear modelMcNemar's testCochran–Mantel–Haenszel statistics | Multivariate | RegressionManovaPrincipal componentsCanonical correlationDiscriminant analysisCluster analysisClassificationStructural equation modelFactor analysisMultivariate distributionsElliptical distributionsNormal | Time-series | GeneralDecompositionTrendStationaritySeasonal adjustmentExponential smoothingCointegrationStructural breakGranger causalitySpecific testsDickey–FullerJohansenQ-statistic(Ljung–Box)Durbin–WatsonBreusch–GodfreyTime domainAutocorrelation (ACF)partial (PACF)Cross-correlation (XCF)ARMA modelARIMA model(Box–Jenkins)Autoregressive conditional heteroskedasticity (ARCH)Vector autoregression (VAR)(Autoregressive model (AR))Frequency domainSpectral density estimationFourier analysisLeast-squares spectral analysisWaveletWhittle likelihood | General | DecompositionTrendStationaritySeasonal adjustmentExponential smoothingCointegrationStructural breakGranger causality | Specific tests | Dickey–FullerJohansenQ-statistic(Ljung–Box)Durbin–WatsonBreusch–Godfrey | Time domain | Autocorrelation (ACF)partial (PACF)Cross-correlation (XCF)ARMA modelARIMA model(Box–Jenkins)Autoregressive conditional heteroskedasticity (ARCH)Vector autoregression (VAR)(Autoregressive model (AR)) | Frequency domain | Spectral density estimationFourier analysisLeast-squares spectral analysisWaveletWhittle likelihood | Survival | Survival functionKaplan–Meier estimator (product limit)Proportional hazards modelsAccelerated failure time (AFT) modelFirst hitting timeHazard functionNelson–Aalen estimatorTestLog-rank test | Survival function | Kaplan–Meier estimator (product limit)Proportional hazards modelsAccelerated failure time (AFT) modelFirst hitting time | Hazard function | Nelson–Aalen estimator | Test | Log-rank test |
| Categorical | Cohen's kappaContingency tableGraphical modelLog-linear modelMcNemar's testCochran–Mantel–Haenszel statistics |
| Multivariate | RegressionManovaPrincipal componentsCanonical correlationDiscriminant analysisCluster analysisClassificationStructural equation modelFactor analysisMultivariate distributionsElliptical distributionsNormal |
| Time-series | GeneralDecompositionTrendStationaritySeasonal adjustmentExponential smoothingCointegrationStructural breakGranger causalitySpecific testsDickey–FullerJohansenQ-statistic(Ljung–Box)Durbin–WatsonBreusch–GodfreyTime domainAutocorrelation (ACF)partial (PACF)Cross-correlation (XCF)ARMA modelARIMA model(Box–Jenkins)Autoregressive conditional heteroskedasticity (ARCH)Vector autoregression (VAR)(Autoregressive model (AR))Frequency domainSpectral density estimationFourier analysisLeast-squares spectral analysisWaveletWhittle likelihood | General | DecompositionTrendStationaritySeasonal adjustmentExponential smoothingCointegrationStructural breakGranger causality | Specific tests | Dickey–FullerJohansenQ-statistic(Ljung–Box)Durbin–WatsonBreusch–Godfrey | Time domain | Autocorrelation (ACF)partial (PACF)Cross-correlation (XCF)ARMA modelARIMA model(Box–Jenkins)Autoregressive conditional heteroskedasticity (ARCH)Vector autoregression (VAR)(Autoregressive model (AR)) | Frequency domain | Spectral density estimationFourier analysisLeast-squares spectral analysisWaveletWhittle likelihood |
| General | DecompositionTrendStationaritySeasonal adjustmentExponential smoothingCointegrationStructural breakGranger causality |
| Specific tests | Dickey–FullerJohansenQ-statistic(Ljung–Box)Durbin–WatsonBreusch–Godfrey |
| Time domain | Autocorrelation (ACF)partial (PACF)Cross-correlation (XCF)ARMA modelARIMA model(Box–Jenkins)Autoregressive conditional heteroskedasticity (ARCH)Vector autoregression (VAR)(Autoregressive model (AR)) |
| Frequency domain | Spectral density estimationFourier analysisLeast-squares spectral analysisWaveletWhittle likelihood |
| Survival | Survival functionKaplan–Meier estimator (product limit)Proportional hazards modelsAccelerated failure time (AFT) modelFirst hitting timeHazard functionNelson–Aalen estimatorTestLog-rank test | Survival function | Kaplan–Meier estimator (product limit)Proportional hazards modelsAccelerated failure time (AFT) modelFirst hitting time | Hazard function | Nelson–Aalen estimator | Test | Log-rank test |
| Survival function | Kaplan–Meier estimator (product limit)Proportional hazards modelsAccelerated failure time (AFT) modelFirst hitting time |
| Hazard function | Nelson–Aalen estimator |
| Test | Log-rank test |
| ApplicationsBiostatisticsBioinformaticsClinical trials/studiesEpidemiologyMedical statisticsEngineering statisticsChemometricsMethods engineeringProbabilistic designProcess/quality controlReliabilitySystem identificationSocial statisticsActuarial scienceCensusCrime statisticsDemographyEconometricsJurimetricsNational accountsOfficial statisticsPopulation statisticsPsychometricsSpatial statisticsCartographyEnvironmental statisticsGeographic information systemGeostatisticsKriging | Applications | BiostatisticsBioinformaticsClinical trials/studiesEpidemiologyMedical statisticsEngineering statisticsChemometricsMethods engineeringProbabilistic designProcess/quality controlReliabilitySystem identificationSocial statisticsActuarial scienceCensusCrime statisticsDemographyEconometricsJurimetricsNational accountsOfficial statisticsPopulation statisticsPsychometricsSpatial statisticsCartographyEnvironmental statisticsGeographic information systemGeostatisticsKriging | Biostatistics | BioinformaticsClinical trials/studiesEpidemiologyMedical statistics | Engineering statistics | ChemometricsMethods engineeringProbabilistic designProcess/quality controlReliabilitySystem identification | Social statistics | Actuarial scienceCensusCrime statisticsDemographyEconometricsJurimetricsNational accountsOfficial statisticsPopulation statisticsPsychometrics | Spatial statistics | CartographyEnvironmental statisticsGeographic information systemGeostatisticsKriging |
| Applications |
| BiostatisticsBioinformaticsClinical trials/studiesEpidemiologyMedical statisticsEngineering statisticsChemometricsMethods engineeringProbabilistic designProcess/quality controlReliabilitySystem identificationSocial statisticsActuarial scienceCensusCrime statisticsDemographyEconometricsJurimetricsNational accountsOfficial statisticsPopulation statisticsPsychometricsSpatial statisticsCartographyEnvironmental statisticsGeographic information systemGeostatisticsKriging | Biostatistics | BioinformaticsClinical trials/studiesEpidemiologyMedical statistics | Engineering statistics | ChemometricsMethods engineeringProbabilistic designProcess/quality controlReliabilitySystem identification | Social statistics | Actuarial scienceCensusCrime statisticsDemographyEconometricsJurimetricsNational accountsOfficial statisticsPopulation statisticsPsychometrics | Spatial statistics | CartographyEnvironmental statisticsGeographic information systemGeostatisticsKriging |
| Biostatistics | BioinformaticsClinical trials/studiesEpidemiologyMedical statistics |
| Engineering statistics | ChemometricsMethods engineeringProbabilistic designProcess/quality controlReliabilitySystem identification |
| Social statistics | Actuarial scienceCensusCrime statisticsDemographyEconometricsJurimetricsNational accountsOfficial statisticsPopulation statisticsPsychometrics |
| Spatial statistics | CartographyEnvironmental statisticsGeographic information systemGeostatisticsKriging |
| CategoryMathematicsportalCommonsWikiProject |

 [Portal](./Wikipedia:Contents/Portals):
- [![icon](//upload.wikimedia.org/wikipedia/commons/thumb/3/3e/Nuvola_apps_edu_mathematics_blue-p.svg/20px-Nuvola_apps_edu_mathematics_blue-p.svg.png)](./File:Nuvola_apps_edu_mathematics_blue-p.svg) [Mathematics](./Portal:Mathematics)

 
| Authority control databases |
| --- |
| National | United StatesFranceBnF dataJapanIsrael |
| Other | Yale LUX |