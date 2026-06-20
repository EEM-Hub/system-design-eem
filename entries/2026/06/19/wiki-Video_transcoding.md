---
source: sources/wiki-Video_transcoding.md
source_url: https://en.wikipedia.org/wiki/Video_transcoding
---

## Transcoding: Digital-to-Digital Format Conversion

Transcoding is the direct digital-to-digital conversion of one encoding to another, applicable to video, audio, and character encoding data. It is performed when a target device or workflow does not support the source format, when storage capacity requires reduced file sizes, or when converting obsolete formats to modern ones. Transcoding is a two-step process: decode the source to an intermediate uncompressed format, then encode into the target format.

## Key Concepts

- **Transcoding** — converting data from one digital encoding to another (e.g., MPEG-2 to H.264, MP3 to WAV, UTF-8 to ISO-8859)
- **Two-step process** — decode to intermediate uncompressed format (PCM for audio, YUV for video), then encode to target format
- **Lossy vs. lossless transcoding** — transcoding is commonly lossy (introduces generation loss), but can be lossless if output is losslessly compressed or uncompressed
- **Generation loss** — compression artifacts are cumulative; each successive transcode in lossy formats progressively degrades quality
- **Transrating** — reducing bitrate without changing the video format; may include sample rate conversion or higher compression at the same sample rate
- **Transsizing** — changing the picture resolution of video (image scaling as part of transcoding)
- **Bitrate peeling** — technique to lower bitrate without full re-encoding, though quality is typically inferior to a proper re-encode (e.g., Vorbis)
- **Master copy principle** — always retain a lossless or uncompressed master; transcode only from the master to avoid cumulative quality loss
- **Re-encoding/recoding** — encoding data back into the same format, typically after editing; defer lossy encoding until data is finalized

## Commands and Syntax

No specific CLI commands or configuration syntax are defined in this source. However, the general procedural workflow is:

1. **Decode** source file to intermediate uncompressed format (PCM, YUV, raw)
2. **Edit** (if needed) in the uncompressed domain — make all edits before re-encoding
3. **Encode** to target format
4. **Avoid chained lossy transcodes** — always transcode from the master, not from a previously transcoded copy

Common format pipelines referenced:
- **Video**: Cineon/DPX → JPEG2000 (lossless, ~50% compression); MPEG-2 → MPEG-4/H.264
- **Audio**: WAV/AIFF (PCM) → FLAC/ALAC/WavPack (lossless, ~50% size) → MP3/lossy (final distribution only)
- **Image**: Raw → lossless working copy → JPEG (final distribution only)

## Relationships

- **Data compression** — transcoding relies on encode/decode cycles; compression ratio and algorithm choice determine quality/size tradeoffs
- **Adaptive bitrate streaming** — transcoding produces multiple bitrate versions of content for streaming delivery
- **Digital generation loss** — the core quality risk in lossy transcoding; directly related to compression artifact accumulation
- **Video coding standards** — MPEG-2, MPEG-4, H.264 are common transcoding targets
- **Lossless codecs** (FLAC, ALAC, WavPack) — serve as archival intermediates that enable future lossless transcoding to any format
- **Mobile content adaptation** — transcoding is essential for MMS and diverse mobile device support (resolution, color depth, codec compatibility)
- **Digital cinema** — Cineon/DPX to JPEG2000 transcoding addresses the ~8 TB storage challenge of uncompressed feature films
- **Analog-to-digital history** — early transcoding used CRT/camera tube combinations for real-time scan rate conversion between analog video standards

## Exam-Relevant Points

- Transcoding is a **two-step process**: decode to intermediate uncompressed → encode to target
- Lossy-to-lossy transcoding **always** introduces generation loss; artifacts are cumulative
- Lossy-to-lossless transcoding is technically **lossless** (no additional information lost), but the original quality lost in the first lossy encode is not recovered
- **Transrating** = same format, lower bitrate; **transsizing** = different resolution
- Lossless formats (FLAC, ALAC) compress to roughly **half** the size of uncompressed PCM while preserving full quality
- JPEG2000 lossless can compress digital cinema frames to approximately **half** their original size
- Best practice: keep a **lossless master** and only transcode to lossy formats for final distribution
- For editing workflows: decode **once**, make all edits, then encode — never repeatedly decode/re-encode
- Consumer camera footage can often be significantly reduced in size with minimal quality loss because real-time, power-constrained capture devices use suboptimal compression
- Historical transcoding between analog standards used physical CRT/camera tube scan converters before semiconductor solutions existed
