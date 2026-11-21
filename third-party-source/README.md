# Source of the LGPL libraries shipped with the port

The exact upstream source of the two LGPL libraries in the releases, unmodified.

| File | Library | Ships in | From |
|---|---|---|---|
| `openal-soft-1.24.3.tar.bz2` | OpenAL Soft 1.24.3 (GNU LGPL 2) | Windows (`OpenAL32.dll`, upstream binary) and Linux (`libopenal.so.1`) | the upstream release tarball, https://github.com/kcat/openal-soft/releases/tag/1.24.3 |
| `ffmpeg-n7.1.2.tar.xz` | FFmpeg 7.1.2 (GNU LGPL 2.1 or later) | Linux only (`libavformat.so.61`, `libavcodec.so.61`, `libavutil.so.59`) | `git archive` of tag `n7.1.2` (commit f893221c8d89cb798b829bebe71d55e1a3f242fd) of https://github.com/FFmpeg/FFmpeg, the tag the build clones |

`SHA256SUMS` has their hashes. The FFmpeg configure line and build steps are in
[THIRD_PARTY_NOTICES.md](../THIRD_PARTY_NOTICES.md).
