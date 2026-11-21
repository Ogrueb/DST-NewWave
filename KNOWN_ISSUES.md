# Known issues

## Tested on one PC only

DST NewWave has been played on one computer: Windows 11 with AMD integrated graphics. Everything
else was checked by reading the code, not by running it:

- **Nvidia and Intel graphics.** Expected to work through DXVK. Untested: exclusive full screen and
  Alt+Tab (use the default borderless mode if it misbehaves), and the terrain path used when
  `graphics.terrain_hw` is switched off.
- **Windows 10.** No Windows 11-only calls were found, but it has not been run.
- **Linux on a real desktop.** The AppImage has only run on a cloud machine with software Vulkan.
  Reports from real hardware are very welcome.

## Graphics cards that cannot run the 64-bit build

DXVK 3.1.1 needs Vulkan 1.3 and a few newer extensions. Nvidia GeForce 600 and 700 series and Intel
6th to 10th generation graphics never get a driver with them. The game says so at start-up; use the
32-bit build, which gets basic testing only (start, play, save and load).

## Windows

- The installer is not code-signed, so SmartScreen warns about it.
- On Windows "N" editions, the music conversion needs the Media Feature Pack. Without it the game runs
  without music; the installed `README.txt` says how to convert the track by hand.
- Crashes that Windows ends without running any handler (mostly heap corruption) leave no report.

## Linux

- No crash handler yet.
- The shader warm-up at start-up is Windows-only for now, so the first minutes may stutter more.
- Small text is a little softer than on Windows (no hinting).
- Needs glibc 2.35 or newer.
- Needs a Vulkan driver new enough for DXVK 3.1. The Mesa that Ubuntu 22.04 and Debian 12 ship is
  too old (Ubuntu 24.04 with its updates is fine); on those systems you need a newer Mesa or your
  GPU vendor's driver. With a driver that is too old the game says so when it starts.

## Game

- Frame rates on the largest maps (254 tiles) are limited by the GPU and DXVK, not the game: expect
  around 40 fps there on integrated graphics. The preset map sizes run much faster.
- The mod menus (Custom missions, the Mods tab and the Mod buildings page) work but are rough;
  improving them is planned after release.
- Special requests never worked in the original (the data has none) and are not supported.
- The intro video is absent (no copy of it is known).
- The settings for slope shading, caustics and rock and silt are new and may need tuning.
