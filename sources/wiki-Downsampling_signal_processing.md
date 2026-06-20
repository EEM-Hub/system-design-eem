---
source: https://en.wikipedia.org/wiki/Downsampling_(signal_processing)
fetched: 2026-06-19
---

Resampling method 

In [digital signal processing](./Digital_signal_processing), **downsampling**, **subsampling**, **compression**, and **decimation** are terms associated with the process of [*resampling*](./Sample_rate_conversion) in a [multi-rate digital signal processing](./Multi-rate_digital_signal_processing) system. Both *downsampling* and *decimation* can be synonymous with *compression*, or they can describe an entire process of bandwidth reduction ([filtering](./Lowpass_filter)) and sample-rate reduction.[[1]](./Downsampling_(signal_processing)#cite_note-Oppenheim-1)[[2]](./Downsampling_(signal_processing)#cite_note-LiTan-2) When the process is performed on a sequence of samples of a *signal* or a continuous function, it produces an approximation of the sequence that would have been obtained by sampling the signal at a lower rate (or [density](./Dots_per_inch), as in the case of a photograph).

 

*Decimation* is a term that historically means the *[removal of every tenth one](./Decimation_(punishment))*.[[a]](./Downsampling_(signal_processing)#cite_note-3) But in signal processing, *decimation by a factor of 10* actually means *keeping* only every tenth sample. This factor multiplies the sampling interval or, equivalently, divides the sampling rate. For example, if [compact disc](./Compact_disc) audio at 44,100 samples/second is *decimated* by a factor of 5/4, the resulting sample rate is 35,280. A system component that performs decimation is called a *decimator*. Decimation by an integer factor is also called *compression*.[[3]](./Downsampling_(signal_processing)#cite_note-Crochiere-4)[[4]](./Downsampling_(signal_processing)#cite_note-Poularikas-5)

 

## Downsampling by an integer factor

 

Rate reduction by an integer factor *M* can be explained as a two-step process, with an equivalent implementation that is more efficient:[[5]](./Downsampling_(signal_processing)#cite_note-f.harris-6)

 
1. Reduce high-frequency signal components with a digital [lowpass filter](./Lowpass_filter).
2. *Decimate* the filtered signal by *M*; that is, keep only every *M*th sample.

 

Step 2 alone creates undesirable [aliasing](./Aliasing) (i.e. high-frequency signal components will copy into the lower frequency band and be mistaken for lower frequencies). Step 1, when necessary, suppresses aliasing to an acceptable level. In this application, the filter is called an [anti-aliasing filter](./Anti-aliasing_filter), and its design is discussed below. Also see [undersampling](./Undersampling) for information about decimating [bandpass](./Bandpass) functions and signals.

 

When the anti-aliasing filter is an [IIR](./Infinite_impulse_response) design, it relies on feedback from output to input, prior to the second step. With [FIR filtering](./FIR_filter), it is an easy matter to compute only every *M*th output. The calculation performed by a decimating FIR filter for the *n*th output sample is a [dot product](./Dot_product):[[b]](./Downsampling_(signal_processing)#cite_note-7)

     y [ n ] =  ∑ ∑   k = 0   K − −  1   x [ n M − −  k ] ⋅ ⋅  h [ k ] ,   {\displaystyle y[n]=\sum _{k=0}^{K-1}x[nM-k]\cdot h[k],}  ![{\displaystyle y[n]=\sum _{k=0}^{K-1}x[nM-k]\cdot h[k],}](https://wikimedia.org/api/rest_v1/media/math/render/svg/71d3756569db36dcd0f869fb9acb8a24781041fc) 

where the *h*[•] sequence is the impulse response, and *K* is its length. *x*[•] represents the input sequence being downsampled. In a general purpose processor, after computing *y*[*n*], the easiest way to compute *y*[*n*+1] is to advance the starting index in the *x*[•] array by *M*, and recompute the dot product. In the case *M*=2, *h*[•] can be designed as a [half-band filter](./Half-band_filter), where almost half of the coefficients are zero and need not be included in the dot products.

 

Impulse response coefficients taken at intervals of *M* form a subsequence, and there are *M* such subsequences (phases) multiplexed together. The dot product is the sum of the dot products of each subsequence with the corresponding samples of the *x*[•] sequence. Furthermore, because of downsampling by *M*, the stream of *x*[•] samples involved in any one of the *M* dot products is never involved in the other dot products. Thus *M* low-order FIR filters are each filtering one of *M* multiplexed *phases* of the input stream, and the *M* outputs are being summed. This viewpoint offers a different implementation that might be advantageous in a multi-processor architecture. In other words, the input stream is demultiplexed and sent through a bank of M filters whose outputs are summed. When implemented that way, it is called a **polyphase** filter.

 

For completeness, we now mention that a possible, but unlikely, implementation of each phase is to replace the coefficients of the other phases with zeros in a copy of the *h*[•] array, process the original *x*[•] sequence at the input rate (which means multiplying by zeros), and decimate the output by a factor of *M*. The equivalence of this inefficient method and the implementation described above is known as the *first Noble identity*.[[6]](./Downsampling_(signal_processing)#cite_note-Strang-8)[[c]](./Downsampling_(signal_processing)#cite_note-9) It is sometimes used in derivations of the polyphase method.

 [![](//upload.wikimedia.org/wikipedia/commons/thumb/7/76/Spectral_effects_of_decimation.svg/500px-Spectral_effects_of_decimation.svg.png)](./File:Spectral_effects_of_decimation.svg)Fig 1: These graphs depict the spectral distributions of an oversampled function and the same function sampled at 1/3 the original rate. The bandwidth, B, in this example is just small enough that the slower sampling does not cause overlap (aliasing). Sometimes, a sampled function is resampled at a lower rate by keeping only every Mth sample and discarding the others, commonly called "decimation". Potential aliasing is prevented by lowpass-filtering the samples before decimation. The maximum filter bandwidth is tabulated in the bandwidth units used by the common filter design applications. 

### Anti-aliasing filter

 

Let *X*(*f*) be the [Fourier transform](./Continuous_Fourier_transform) of any function, *x*(*t*), whose samples at some interval, *T*, equal the *x*[*n*] sequence. Then the [discrete-time Fourier transform](./Discrete-time_Fourier_transform) (DTFT) is a [Fourier series](./Fourier_series) representation of a [periodic summation](./Periodic_summation) of *X*(*f*):[[d]](./Downsampling_(signal_processing)#cite_note-10)

          ∑ ∑   n = − −  ∞ ∞    ∞ ∞        x ( n T )  ⏞ ⏞     x [ n ]       e   − −   i  2 π π  f n T    ⏟ ⏟     DTFT   =   1 T    ∑ ∑   k = − −  ∞ ∞    ∞ ∞    X   (   f − −    k T     )   .   {\displaystyle \underbrace {\sum _{n=-\infty }^{\infty }\overbrace {x(nT)} ^{x[n]}\ \mathrm {e} ^{-\mathrm {i} 2\pi fnT}} _{\text{DTFT}}={\frac {1}{T}}\sum _{k=-\infty }^{\infty }X{\Bigl (}f-{\frac {k}{T}}{\Bigr )}.}  ![{\displaystyle \underbrace {\sum _{n=-\infty }^{\infty }\overbrace {x(nT)} ^{x[n]}\ \mathrm {e} ^{-\mathrm {i} 2\pi fnT}} _{\text{DTFT}}={\frac {1}{T}}\sum _{k=-\infty }^{\infty }X{\Bigl (}f-{\frac {k}{T}}{\Bigr )}.}](https://wikimedia.org/api/rest_v1/media/math/render/svg/f0f042baeec78e1fbce45dd46dff9e0077503392) 

When *T* has units of seconds,     f   {\displaystyle f}  ![{\displaystyle f}](https://wikimedia.org/api/rest_v1/media/math/render/svg/132e57acb643253e7810ee9702d9581f159a1c61) has units of [hertz](./Hertz). Replacing *T* with *MT* in the formulas above gives the DTFT of the decimated sequence, *x*[*nM*]:

      ∑ ∑   n = − −  ∞ ∞    ∞ ∞    x ( n ⋅ ⋅  M T )     e   − −   i  2 π π  f n ( M T )   =   1  M T     ∑ ∑   k = − −  ∞ ∞    ∞ ∞    X  (  f − −     k  M T      )  .   {\displaystyle \sum _{n=-\infty }^{\infty }x(n\cdot MT)\ \mathrm {e} ^{-\mathrm {i} 2\pi fn(MT)}={\frac {1}{MT}}\sum _{k=-\infty }^{\infty }X\left(f-{\tfrac {k}{MT}}\right).}  ![{\displaystyle \sum _{n=-\infty }^{\infty }x(n\cdot MT)\ \mathrm {e} ^{-\mathrm {i} 2\pi fn(MT)}={\frac {1}{MT}}\sum _{k=-\infty }^{\infty }X\left(f-{\tfrac {k}{MT}}\right).}](https://wikimedia.org/api/rest_v1/media/math/render/svg/ce6e88a638f4a33511701aec6d7f0610c93abd75) 

The periodic summation has been reduced in amplitude and periodicity by a factor of *M*. An example of both these distributions is depicted in the two traces of Fig 1.[[e]](./Downsampling_(signal_processing)#cite_note-11)[[f]](./Downsampling_(signal_processing)#cite_note-12)[[g]](./Downsampling_(signal_processing)#cite_note-13)
Aliasing occurs when adjacent copies of *X*(*f*) overlap. The purpose of the anti-aliasing filter is to ensure that the reduced periodicity does not create overlap. The condition that ensures the copies of *X*(*f*) do not overlap each other is:     B <    0.5 T    ⋅ ⋅     1 M    ,   {\displaystyle B<{\tfrac {0.5}{T}}\cdot {\tfrac {1}{M}},}  ![{\displaystyle B<{\tfrac {0.5}{T}}\cdot {\tfrac {1}{M}},}](https://wikimedia.org/api/rest_v1/media/math/render/svg/2896494dd21f04ec1c421fbd5447165d2745a547) so that is the maximum [cutoff frequency](./Cutoff_frequency) of an *ideal* anti-aliasing filter.[[A]](./Downsampling_(signal_processing)#cite_note-14)

 

## By a rational factor

 

Let *M/L* denote the decimation factor,[[B]](./Downsampling_(signal_processing)#cite_note-16) where: M, L ∈      Z    {\displaystyle \mathbb {Z} }  ![{\displaystyle \mathbb {Z} }](https://wikimedia.org/api/rest_v1/media/math/render/svg/449494a083e0a1fda2b61c62b2f09b6bee4633dc); M > L.

 
1. Increase (resample) the sequence by a factor of *L*. This is called [Upsampling](./Upsampling), or *interpolation*.
2. Decimate by a factor of *M*

 

Step 1 requires a lowpass filter after increasing (*expanding*) the data rate, and step 2 requires a lowpass filter before decimation. Therefore, both operations can be accomplished by a single filter with the lower of the two cutoff frequencies. For the *M* > *L* case, the anti-aliasing filter cutoff,        0.5 M      {\displaystyle {\tfrac {0.5}{M}}}  ![{\displaystyle {\tfrac {0.5}{M}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/f24f180c8a2ed12c0d454a2c8bfb33af1b6a44c9) *cycles per intermediate sample*, is the lower frequency.

 

## See also

 
- [Upsampling](./Upsampling)
- [Posterization](./Posterization)
- [Sample-rate conversion](./Sample-rate_conversion)
- [Aliasing](./Aliasing)
- [Visvalingam–Whyatt algorithm](./Visvalingam–Whyatt_algorithm)

 

## Notes

 
1. [↑](./Downsampling_(signal_processing)#cite_ref-14) Realizable low-pass filters have a "skirt", where the response diminishes from near one to near zero. In practice the cutoff frequency is placed far enough below the theoretical cutoff that the filter's skirt is contained below the theoretical cutoff.
2. [↑](./Downsampling_(signal_processing)#cite_ref-16) General techniques for sample-rate conversion by factor R ∈       R   +     {\displaystyle \mathbb {R} ^{+}}  ![{\displaystyle \mathbb {R} ^{+}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/97dc5e850d079061c24290bac160c8d3b62ee139) include [polynomial interpolation](./Polynomial_interpolation) and the Farrow structure.[[7]](./Downsampling_(signal_processing)#cite_note-Milic-15)

 

## Page citations

 
1. [↑](./Downsampling_(signal_processing)#cite_ref-3) [Harris 2004](./Downsampling_(signal_processing)#f.harris). "6.1". p 128.

2. [↑](./Downsampling_(signal_processing)#cite_ref-7) [Crochiere and Rabiner](./Downsampling_(signal_processing)#Crochiere) "2". p 32. eq 2.55a.

3. [↑](./Downsampling_(signal_processing)#cite_ref-9) [Harris 2004](./Downsampling_(signal_processing)#f.harris). "2.2.1". p 25.

4. [↑](./Downsampling_(signal_processing)#cite_ref-10) [Oppenheim and Schafer](./Downsampling_(signal_processing)#Oppenheim). "4.2". p 143. eq 4.6, where**:**      Ω Ω  ≜ ≜  2 π π  f ,   {\displaystyle \Omega \triangleq 2\pi f,}  ![{\displaystyle \Omega \triangleq 2\pi f,}](https://wikimedia.org/api/rest_v1/media/math/render/svg/668996ec825cc28bb3b2de0485ebb6ef790c99aa)       X  s   ( i Ω Ω  ) ≜ ≜   ∑ ∑   n = − −  ∞ ∞    ∞ ∞    x ( n T )     e   − −   i  Ω Ω  n T   ,   {\displaystyle X_{s}(i\Omega )\triangleq \sum _{n=-\infty }^{\infty }x(nT)\ \mathrm {e} ^{-\mathrm {i} \Omega nT},}  ![{\displaystyle X_{s}(i\Omega )\triangleq \sum _{n=-\infty }^{\infty }x(nT)\ \mathrm {e} ^{-\mathrm {i} \Omega nT},}](https://wikimedia.org/api/rest_v1/media/math/render/svg/02a443ceed6fe7d2c36216db41088741b0bfbeca)  and       X  c   ( i 2 π π  f ) ≜ ≜  X ( f ) .   {\displaystyle X_{c}(i2\pi f)\triangleq X(f).}  ![{\displaystyle X_{c}(i2\pi f)\triangleq X(f).}](https://wikimedia.org/api/rest_v1/media/math/render/svg/5ebf5a19bd65c238aece852df45d5353a2eb8864) 
5. [↑](./Downsampling_(signal_processing)#cite_ref-11) [Harris 2004](./Downsampling_(signal_processing)#f.harris). "2.2". p 22. fig 2.10.

6. [↑](./Downsampling_(signal_processing)#cite_ref-12) [Oppenheim and Schafer](./Downsampling_(signal_processing)#Oppenheim). "4.6". p 171. fig 4.22.

7. [↑](./Downsampling_(signal_processing)#cite_ref-13) [Tan 2008](./Downsampling_(signal_processing)#LiTan). "1.2.1". fig 12.2.

 

## References

 
1. [↑](./Downsampling_(signal_processing)#cite_ref-Oppenheim_1-0)  [Oppenheim, Alan V.](./Alan_V_Oppenheim); Schafer, Ronald W.; Buck, John R. (1999). "4". [*Discrete-Time Signal Processing*](https://archive.org/details/discretetimesign00alan) (2nd ed.). Upper Saddle River, N.J.: Prentice Hall. p. [168](https://archive.org/details/discretetimesign00alan/page/168). [ISBN](./ISBN_(identifier)) [0-13-754920-2](./Special:BookSources/0-13-754920-2). 
2. [↑](./Downsampling_(signal_processing)#cite_ref-LiTan_2-0)  Tan, Li (2008-04-21). ["Upsampling and downsampling"](http://www.eetimes.com/document.asp?doc_id=1275556). *eetimes.com*. EE Times. Retrieved 2017-04-10. The process of reducing a sampling rate by an integer factor is referred to as *downsampling* of a data sequence.  We also refer to downsampling as *decimation*. The term *decimation* used for the downsampling process has been accepted and used in many textbooks and fields.
3. [↑](./Downsampling_(signal_processing)#cite_ref-Crochiere_4-0)  Crochiere, R.E.; [Rabiner, L.R.](./Lawrence_Rabiner) (1983). "2". [*Multirate Digital Signal Processing*](https://kupdf.net/download/multirate-digital-signal-processing-crochiere-rabiner_58a7065b6454a7e80bb1e993_pdf). Englewood Cliffs, NJ: Prentice-Hall. p. 32. [ISBN](./ISBN_(identifier)) [0136051626](./Special:BookSources/0136051626).
4. [↑](./Downsampling_(signal_processing)#cite_ref-Poularikas_5-0)  Poularikas, Alexander D. (September 1998). *Handbook of Formulas and Tables for Signal Processing* (1 ed.). CRC Press. pp. 42–48. [ISBN](./ISBN_(identifier)) [0849385792](./Special:BookSources/0849385792).
5. [↑](./Downsampling_(signal_processing)#cite_ref-f.harris_6-0)  [Harris, Frederic J.](./Fredric_J._Harris) (2004-05-24). "2.2". *Multirate Signal Processing for Communication Systems*. Upper Saddle River, NJ: Prentice Hall PTR. pp. 20–21. [ISBN](./ISBN_(identifier)) [0131465112](./Special:BookSources/0131465112). The process of down sampling can be visualized as a two-step progression. The process starts as an input series x(n) that is processed by a filter h(n) to obtain the output sequence y(n) with reduced bandwidth. The sample rate of the output sequence is then reduced Q-to-1 to a rate commensurate with the reduced signal bandwidth.  In reality the processes of bandwidth reduction and sample rate reduction are merged in a single process called a multirate filter.
6. [↑](./Downsampling_(signal_processing)#cite_ref-Strang_8-0)  [Strang, Gilbert](./Gilbert_Strang); Nguyen, Truong (1996-10-01). [*Wavelets and Filter Banks*](https://archive.org/details/waveletsfilterba00stra) (2 ed.). Wellesley, MA: Wellesley-Cambridge Press. pp. [100](https://archive.org/details/waveletsfilterba00stra/page/100)–101. [ISBN](./ISBN_(identifier)) [0961408871](./Special:BookSources/0961408871). No sensible engineer would do that.
7. [↑](./Downsampling_(signal_processing)#cite_ref-Milic_15-0)  Milić, Ljiljana (2009). *Multirate Filtering for Digital Signal Processing*. New York: Hershey. p. 192. [ISBN](./ISBN_(identifier)) [978-1-60566-178-0](./Special:BookSources/978-1-60566-178-0). Generally, this approach is applicable when the ratio Fy/Fx is a rational, or an irrational number, and is suitable for the sampling rate increase and for the sampling rate decrease.

 

## Further reading

 
- Proakis, John G. (2000). *Digital Signal Processing: Principles, Algorithms and Applications* (3rd ed.). India: Prentice-Hall. [ISBN](./ISBN_(identifier)) [8120311299](./Special:BookSources/8120311299).
- Lyons, Richard (2001). *Understanding Digital Signal Processing*. Prentice Hall. p. 304. [ISBN](./ISBN_(identifier)) [0-201-63467-8](./Special:BookSources/0-201-63467-8). Decreasing the sampling rate is known as decimation.
- Antoniou, Andreas (2006). [*Digital Signal Processing*](https://archive.org/details/digitalsignalpro00anto_617). McGraw-Hill. p. [830](https://archive.org/details/digitalsignalpro00anto_617/page/n855). [ISBN](./ISBN_(identifier)) [0-07-145424-1](./Special:BookSources/0-07-145424-1). Decimators can be used to reduce the sampling frequency, whereas interpolators can be used to increase it.
- Milic, Ljiljana (2009). *Multirate Filtering for Digital Signal Processing*. New York: Hershey. p. 35. [ISBN](./ISBN_(identifier)) [978-1-60566-178-0](./Special:BookSources/978-1-60566-178-0). Sampling rate conversion systems are used to change the sampling rate of a signal. The process of sampling rate decrease is called decimation, and the process of sampling rate increase is called interpolation.
- T. Schilcher. RF applications in digital signal processing//" Digital signal processing". Proceedings, CERN Accelerator School, Sigtuna, Sweden, May 31-June 9, 2007. - Geneva, Switzerland: CERN (2008). - P. 258. - DOI: 10.5170/CERN-2008-003. [](https://cds.cern.ch/record/1100538/files/p249.pdf)
- Sliusar I.I., Slyusar V.I., Voloshko S.V., Smolyar V.G. Next Generation Optical Access based on N-OFDM with decimation.// Third International Scientific-Practical Conference "Problems of Infocommunications. Science and Technology (PIC S&T'2016)". – Kharkiv. - October 3 –6, 2016. [](http://slyusar.kiev.ua/Slyusar_PIC_ST_2016.pdf)
- Saska Lindfors, Aarno Pärssinen, Kari A. I. Halonen. A 3-V 230-MHz CMOS Decimation Subsampler.// IEEE transactions on circuits and systems— Vol. 52, No. 2, February 2005. – P. 110.

 
| vteDigital signal processing |
| --- |
| Theory | Detection theoryDiscrete signalEstimation theoryNyquist–Shannon sampling theorem |
| Sub-fields | Audio signal processingDigital image processingSpeech processingStatistical signal processing |
| Techniques | Z-transformAdvanced z-transformMatched Z-transform methodBilinear transformConstant-Q transformDiscrete cosine transform(DCT)Discrete Fourier transform(DFT)Discrete-time Fourier transform(DTFT)Impulse invarianceIntegral transformLaplace transformPost's inversion formulaStarred transformZak transform |
| Sampling | AliasingAnti-aliasing filterDownsamplingNyquist rate/frequencyOversamplingQuantizationSampling rateUndersamplingUpsampling |