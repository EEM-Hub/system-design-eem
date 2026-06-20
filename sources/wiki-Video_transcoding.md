---
source: https://en.wikipedia.org/wiki/Video_transcoding
fetched: 2026-06-19
---

Direct digital-to-digital conversion of one encoding to another For other uses, see [Transcode (disambiguation)](./Transcode_(disambiguation)) and [H.264/MPEG-4 AVC products and implementations § Transcoding](./H.264/MPEG-4_AVC_products_and_implementations#Transcoding). 
|  | This articleneeds additional citations forverification.Please helpimprove this articlebyadding citations to reliable sources. Unsourced material may be challenged and removed.Find sources:"Transcoding"–news·newspapers·books·scholar·JSTOR(October 2015)(Learn how and when to remove this message) |
| --- | --- |

 

**Transcoding** is the direct digital-to-digital conversion of one encoding to another,[[1]](./Transcoding#cite_note-1) such as for [video](./Video) data files, audio files (e.g., [MP3](./MP3), [WAV](./WAV)), or [character encoding](./Character_encoding) (e.g., [UTF-8](./UTF-8), [ISO/IEC 8859](./ISO/IEC_8859)). This is usually done in cases where a target device (or [workflow](./Workflow)) does not support the format or has limited storage capacity that mandates a reduced file size,[[2]](./Transcoding#cite_note-SMP-2) or to convert incompatible or obsolete data to a better-supported or modern format.

 

In the analog video world, transcoding can be performed just while files are being searched, as well as for presentation. For example, [Cineon](./Cineon) and [DPX](./DPX) files have been widely used as a common format for [digital cinema](./Digital_cinema), but the data size of a two-hour movie is about 8 [terabytes](./Terabyte) (TB).[[2]](./Transcoding#cite_note-SMP-2) That large size can increase the cost and difficulty of handling movie files. However, transcoding into a [JPEG2000](./JPEG2000) lossless format has better [data compression](./Data_compression) performance than other lossless coding technologies; in many cases, JPEG2000 can compress images to half their original size.[[2]](./Transcoding#cite_note-SMP-2)

 

Transcoding is commonly a [lossy process](./Lossy_compression), introducing [generation loss](./Generation_loss); however, transcoding can be lossless if the output is either losslessly compressed or uncompressed.[[2]](./Transcoding#cite_note-SMP-2) The process of transcoding into a lossy format introduces varying degrees of generation loss, while the transcoding from lossy to lossless or uncompressed is technically a lossless conversion because no information is lost; however, when the conversion is irreversible, it is then more correctly known as *destructive*.

 

## Process

 

Transcoding is a two-step process in which the original data is decoded to an intermediate uncompressed format (e.g., [PCM](./PCM) for audio; [YUV](./YUV) for video), which is then encoded into the target format.

 

## Re-encoding/recoding

 

One may also **re-encode** data in the same format, for a number of reasons:

 Editing If one wishes to edit data in a compressed format (for instance, perform image editing on a [JPEG](./JPEG) image), one will generally decode it, edit it, then re-encode it. This re-encoding causes [digital generation loss](./Digital_generation_loss); thus, if one wishes to edit a file repeatedly, one should only decode it *once*, and make all edits on that copy, rather than repeatedly re-encoding it. Similarly, if encoding to a lossy format is required, it should be deferred until the data is finalised, e.g., after mastering. Lower bitrate **[Transrating](./Transrating)** is a process similar to transcoding in which files are coded to a lower bitrate without changing video formats;[[3]](./Transcoding#cite_note-Ryan-3) this can include [sample rate conversion](./Sample_rate_conversion), but may use an identical sampling rate with higher compression. This allows one to fit given media into smaller storage space (for instance, fitting a [DVD](./DVD) onto a [Video CD](./Video_CD)), or over a lower bandwidth channel. [Image scaling](./Image_scaling) Changing the picture size of video is known as **transsizing**, and is used if the output resolution differs from the resolution of the media. On a powerful enough device, image scaling can be done on playback, but it can also be done by re-encoding, particularly as part of transrating (such as a [downsampled](./Downsampled) image requiring a lower bitrate). 

One can also use formats with [bitrate peeling](./Bitrate_peeling), which allow one to easily lower the bitrate without re-encoding, but quality is often lower than a re-encode. For example, in [Vorbis](./Vorbis), bitrate peeling as of 2008, the quality is inferior to re-encoding.

 

## Drawbacks

 

The key drawback of transcoding in lossy formats is decreased quality. [Compression artifacts](./Compression_artifact) are cumulative, so transcoding causes a progressive loss of quality with each successive generation, known as [digital generation loss](./Digital_generation_loss). For this reason, transcoding (in lossy formats) is generally discouraged unless unavoidable.

 

For users wanting to be able to re-encode audio into any format, and for [digital audio editing](./Digital_audio_editing), it is best to retain a master copy in a [lossless format](./Data_compression#Audio) (such as [FLAC](./FLAC), [ALAC](./Apple_Lossless), TTA, [WavPack](./WavPack), and others) that take around half the storage space needed when compared to original uncompressed [PCM](./PCM) formats (such as [WAV](./WAV), and [AIFF](./Audio_Interchange_File_Format)), as lossless formats usually have the added benefit of having [meta data](./Meta_data) options, which are either completely missing or very limited in PCM formats. These lossless formats can be transcoded to PCM formats or transcoded directly from one lossless format to another lossless format, without any loss in quality. They can be transcoded into a lossy format, but these copies will then not be able to be transcoded into another format of any kind (PCM, lossless, or lossy) without a subsequent loss of quality.

 

For [image editing](./Image_editing) users are advised to capture or save images in a [raw](./Raw_image_format) or uncompressed format, and then edit a copy of that master version, only converting to lossy formats if smaller file sized images are needed for final distribution. As with audio, transcoding from lossy format to another format of any type will result in a loss of quality.

 

For [video editing](./Video_editing), (for video converting), images are normally compressed directly during the recording process due to the huge [file sizes](./File_size) that would be created if they were not, and because the huge storage demands being too cumbersome for the user otherwise. However, the amount of compression used at the recording stage can be highly variable, and is dependent on a number of factors, including the quality of images being recorded (e.g. analog or digital, standard def. or high def., etc.), and type of equipment available to the user, which is often related to budget constraints – as highest quality digital video equipment, and storage space, may be expensive. Effectively this means that any transcoding will involve some cumulative image loss, and hence the most practical solution insofar as minimizing loss of quality is for the original recording to be deemed the master copy, and for desired subsequent transcoded versions, which will often be in a different format and smaller file size, to be transcoded only from that master copy.

non expert here, this needs expanding/explaining better. (after edit) still non expert, but perhaps clearer now? 

## Usage

 

Although transcoding can be found in many areas of content adaptation, it is commonly used in the area of [mobile phone](./Mobile_phone) content adaptation. In this case, transcoding is a must, due to the diversity of [mobile devices](./Mobile_device) and their capabilities. This diversity requires an intermediate state of content adaptation in order to make sure that the source content will adequately function on the target device to which it is sent.

 

Transcoding video from most consumer [digital cameras](./Digital_cameras) can reduce the file size significantly while keeping the quality about the same. This is possible because most consumer cameras are [real-time](./Real-time_computing), power-constrained devices having neither the processing power nor the robust power supplies of desktop CPUs.

 

One of the most popular technologies in which transcoding is used is the [Multimedia Messaging Service](./Multimedia_Messaging_Service) (MMS), which is the technology used to send or receive messages with media (image, sound, text and video) between mobile phones. For example, when a camera phone is used to take a digital picture, a high-quality image of at least 640 × 480 [pixels](./Pixels) is created. When sending the image to another phone, this high-resolution image might be transcoded to a lower-resolution image with fewer colors in order to better fit the target device's screen size and color limitations. This size and color reduction improves the user experience on the target device, and is sometimes the only way for content to be sent between different mobile devices.

 

Transcoding is extensively used by [home theatre PC](./Home_theatre_PC) software to reduce the usage of [disk space](./Disk_space) by video files.  The most common operation in this application is the transcoding of [MPEG-2](./MPEG-2) files to the [MPEG-4](./MPEG-4) or [H.264](./H.264) format.

 

Real-time transcoding in a many-to-many way (any input format to any output format) is becoming a necessity to provide true search capability for any multimedia content on any mobile device, with over 500 million videos on the web and a plethora of mobile devices.

 

## History

 

Before the advent of semiconductors and integrated circuits, real-time resolution and frame rate transcoding between different [analog video](./Composite_video) standards was achieved by a [CRT](./Cathode-ray_tube)/[camera tube](./Camera_tube) combination. The CRT part does not write onto a [phosphor](./Phosphor), but onto a thin, dielectric target; the camera part reads the deposited charge pattern at a different scan rate from the back side of this target.[[4]](./Transcoding#cite_note-4) The setup could also be used as a [genlock](./Genlock).

 

## See also

 Concepts 
- [Data conversion](./Data_conversion)
- [Data transformation](./Data_transformation)
- [Lossy data conversion](./Lossy_data_conversion)
- [Video coding](./Video_coding)
- [Adaptive bitrate streaming](./Adaptive_bitrate_streaming)

 Comparison 
- [Comparison of DVD ripper software](./Comparison_of_DVD_ripper_software)
- [Comparison of video converters](./Comparison_of_video_converters)

 

## Citations

  
1. [↑](./Transcoding#cite_ref-1) Margaret Rouse. ["transcoding"](https://web.archive.org/web/20180114183759/http://searchmicroservices.techtarget.com/definition/transcoding). Archived from [the original](http://searchmicroservices.techtarget.com/definition/transcoding) on 2018-01-14. Retrieved 2018-01-14.
2. [1](./Transcoding#cite_ref-SMP_2-0) [2](./Transcoding#cite_ref-SMP_2-1) [3](./Transcoding#cite_ref-SMP_2-2) [4](./Transcoding#cite_ref-SMP_2-3) 
   "Advancements in Compression and Transcoding: 2008 and Beyond",
   [Society of Motion Picture and Television Engineers](./Society_of_Motion_Picture_and_Television_Engineers) (SMPTE),
   2008, webpage: [SMPTE-spm](https://archive.today/20110719180141/https://www.smpte.org/events/smpte_annual_tech/schedule/06wedspm1/).

3. [↑](./Transcoding#cite_ref-Ryan_3-0) Branson, Ryan (6 July 2015). ["Why is Bit Rate Important When Converting Videos to MP3?"](http://converta2z.blogspot.in/2015/07/why-is-bit-rate-important-when.html). *Online Video Converter*. [Archived](https://web.archive.org/web/20150809101034/http://converta2z.blogspot.in/2015/07/why-is-bit-rate-important-when.html) from the original on 9 August 2015. Retrieved 10 August 2015.
4. [↑](./Transcoding#cite_ref-4) ["*GEC 7828 Scan conversion tube* data sheet"](http://www.mif.pg.gda.pl/homepages/frank/sheets/201/7/7828.pdf) (PDF). General Electric Corporation. 10 April 1961. [Archived](https://web.archive.org/web/20170426062159/http://www.mif.pg.gda.pl/homepages/frank/sheets/201/7/7828.pdf) (PDF) from the original on 26 April 2017. Retrieved 21 April 2017.

 

## General and cited references

 
- [Federal Standard 1037C](./Federal_Standard_1037C)
- [MIL-STD-188](./MIL-STD-188)
- [List of Portable Multimedia Software](./List_of_Portable_Multimedia_Software)
- P. A. A. Assuncao and M. Ghanbari, "[A frequency-domain video transcoder for dynamic bit-rate reduction of MPEG-2 bit streams](https://ieeexplore.ieee.org/document/736724)", in *IEEE Transactions on Circuits and Systems for Video Technology*, vol. 8, no. 8, pp. 953-967, Dec. 1998.
- Huifang Sun, Xuemin Chen, and Tihao Chiang, *[Digital Video Transcoding for Transmission and Storage](https://www.routledge.com/Digital-Video-Transcoding-for-Transmission-and-Storage/Sun-Chiang-Chen/p/book/9780849316944)*, New York, CRC Press, 2005.

 

## External links

 
- [IDC Report on Video Transcoding](https://web.archive.org/web/20070929052138/http://www.ed-china.com/ARTICLES/2006NOV/2/2006NOV10_HA_AVC_HN_12.PDF)
- [Five Steps for Building Transcoding into Your Workflow whitepaper](http://www.telestream.net/telestream-support/articles/article-5-steps-transcoding.htm)
- [Transcoding White Papers](http://www.ateme.com/-White-papers-)

 
| Authority control databases | GND |
| --- | --- |