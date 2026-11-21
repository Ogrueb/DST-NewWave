# Third-party software in DST NewWave

DST NewWave includes the software below. Each part keeps its own licence; the full licence texts are
installed with the game (Windows: the `licences` folder; Linux: beside the program and in the
AppImage's `usr/share/doc`).

| Component | Version | Licence | Used for | Where |
|---|---|---|---|---|
| [SDL](https://libsdl.org) | 3.4.2 (Windows), 3.4.8 (Linux) | zlib | window, input, timer, folder dialog | `SDL3.dll`, `lib/libSDL3.so.0` |
| [DXVK](https://github.com/doitsujin/dxvk) | 3.1.1, with two patches (below) | zlib | Direct3D 8/9 on Vulkan (64-bit Windows and Linux) | `d3d8.dll`, `d3d9.dll`, `lib/libdxvk_d3d8.so.0`, `lib/libdxvk_d3d9.so.0` |
| [OpenAL Soft](https://github.com/kcat/openal-soft) | 1.24.3, unmodified | GNU LGPL 2 | sound output | `OpenAL32.dll` (upstream binary), `lib/libopenal.so.1` |
| [FFmpeg](https://ffmpeg.org) | 7.1.2, unmodified, Linux only | GNU LGPL 2.1 or later | decoding the original WMA music | `lib/libavformat.so.61`, `lib/libavcodec.so.61`, `lib/libavutil.so.59` |
| [libogg](https://xiph.org/ogg/) / [libvorbis](https://xiph.org/vorbis/) | 1.3.5 / 1.3.7 | BSD 3-clause | the Windows installer's music converter (`dst_musicconv.exe`) | inside the converter |
| [stb_vorbis](https://github.com/nothings/stb) | | MIT or public domain | playing Ogg music and sounds | inside the game program |
| [stb_truetype](https://github.com/nothings/stb) | | MIT or public domain | text at any size (Linux) | inside the game program |
| [Liberation Sans](https://github.com/liberationfonts/liberation-fonts) | 2.1.5, unmodified | SIL Open Font Licence 1.1 | the options window's and the game's text | inside the program; `fonts/LiberationSans-Regular.ttf` on Linux |

## Backdrop pictures

The backdrop pictures included with the game come from wallpapers whose authors could not be traced;
they were cropped and tinted for the game. No licence is claimed for them. If you are the author of
one and want it credited or removed, please [open an issue](../../issues).

## Source of the LGPL libraries

OpenAL Soft and FFmpeg are separate shared libraries that the game loads at run time. You may replace
them with your own builds of the same libraries (same file names and interfaces), for example a
modified version. Their corresponding source, unmodified upstream in both cases, is in this
repository's [`third-party-source/`](third-party-source/) folder, with SHA-256 hashes:

- **OpenAL Soft 1.24.3**: `openal-soft-1.24.3.tar.bz2`; upstream https://github.com/kcat/openal-soft, tag `1.24.3`
- **FFmpeg 7.1.2**: `ffmpeg-n7.1.2.tar.xz`; upstream https://github.com/FFmpeg/FFmpeg, tag `n7.1.2` (also https://ffmpeg.org/releases/),
  configured with
  `--disable-everything --enable-decoder=wmav2 --enable-demuxer=asf --enable-protocol=file
  --enable-shared --disable-static --disable-programs --disable-doc --disable-x86asm
  --disable-autodetect --disable-network --disable-swscale --disable-swresample --disable-postproc
  --disable-avfilter --disable-avdevice`

This software uses code of FFmpeg (https://ffmpeg.org) licensed under the LGPLv2.1.

## DXVK patches

DXVK is built from its `v3.1.1` tag with two small patches, published in this repository under
[`dxvk-patches/`](dxvk-patches/):

- `0002-d3d9-ff-tweening-without-blendweight.patch`: vertex tweening in the fixed-function pipeline
  when the vertex declaration has no blend weight (animated models).
- `0003-d3d9-swvp-typed-output-buffer.patch`: the `ProcessVertices` output buffer on drivers that
  use a typed buffer view (Nvidia, Intel, lavapipe).

The numbers continue the project's own series; patch 0001 was only for a 32-bit Linux build and is
not used in any release.
