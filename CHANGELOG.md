# Changelog

<!-- DRAFT. Player-facing. The first public release is described against the original 2003 game,
     since no earlier version was public. Versions before 1.0 were private play-test builds. -->

## 1.0

First public release. Compared with the original game:

### Runs on today's PCs

- 64-bit Windows build drawing through DXVK 3.1.1 (Direct3D 8 on Vulkan), with a start-up check
  that names the problem when no graphics card can run it, and points to the 32-bit build.
- 32-bit Windows build on Windows' own Direct3D 8, as the fallback for PCs without Vulkan.
- Native Linux build as an AppImage: reads the game from any folder (Windows install, Wine, a copy),
  file names in any letter case, plays the original WMA music, text at any size, and says so
  when the Vulkan driver is too old for DXVK.
- New window and input layer (SDL 3) and sound on OpenAL Soft in place of DirectSound.
- Shader warm-up at start-up, so the first minutes of a game do not stutter.
- Several per-frame slowdowns of the original removed (files looked for on disk every frame,
  textures reloaded every frame, light state work under DXVK).
- A Windows installer that copies the game's data from your own copy, converts the music, installs
  just for you or for everyone, and uninstalls cleanly. Your original installation is not changed.
- Saves, settings and logs in your user folder (Saved Games on Windows), with a portable mode.
  Saves in the original game's folder are still found. Works with non-ASCII Windows user names.
- Crash reports with a minidump on Windows.

### Display and controls

- Any resolution, borderless window, window or true full screen; monitor choice; vsync; frame cap
  up to the display's refresh rate; anti-aliasing and anisotropic filtering.
- Widescreen with an adjustable field of view; objects at the screen's edges no longer vanish early.
- Text size from 50 to 150 %, optionally following the resolution; sharper menu lettering.
- An options window inside the game for every setting, with key rebinding, camera and zoom speed,
  edge scrolling on or off, mute in the background, and autosave (every N minutes, N slots kept).
- The window no longer shows "(Not responding)" during long loads.

### Fixes to the original game

- Crashes: a start-up crash on PCs with many display modes; a profile name over 127 characters; a
  profile or `options.inf` with no end marker that hung the loader.
- Saves: values on scenery objects that never loaded, empty treasure names that shifted the rest of
  the save, values that could not be read back, scenery rotation re-randomised on every load.
- The production screen: a click on the last import no longer also sells the next export.
- Building attraction and environment modifiers are applied instead of being discarded.
- Spelling in mission and building texts corrected (65 entries, listed in
  [SPELLING_FIXES.md](SPELLING_FIXES.md)), stray characters in texts replaced,
  long advisor messages wrapped, and buildings that had no click sound now have one. Done when the
  data is read: your game files are not edited.
- **Game rules** option: *Original* (default) keeps the original balance; *Bug-fixed* applies the
  confirmed balance bugs' fixes, among them the loan charged only once and the wave timing in
  missions 53 to 56, 85 to 88 and 91.

### Sandbox and world

- Maps up to 254 tiles; terrain styles including a rift valley; a map seed you can type or step;
  a terrain preview and gallery; water, light and sea height settings; animal and decor densities;
  deposits that follow the terrain; presets that can be saved, loaded and deleted.
- Backdrop pictures beyond the fog all round the map, one or two for each sandbox sea (included;
  your own or a mod's can replace them), and the land beyond the map's edge with its decor.
- Optional terrain-aware ground (off by default): slope shading, caustics that fade on steep and deep
  ground, and rock on slopes and silt in hollows.
- Air tubes on slopes, ramps, raised tubes over short buildings, and tubes stacked over one another,
  with walkers that follow them; a red placement box where a tube blocks a building.

### Mods

- A `mods` folder whose files replace the game's own when they are read, with a load order and a log
  of every replaced file.
- Mods can add missions (the *Custom missions* screen under New Game) and buildings (the *Mods* tab
  of the build panel), use PNG textures with transparency and Ogg sounds.
- Saves record the mods they used and warn on load when they differ. A *Hide mod menus* setting.
- A modding kit with the guide, templates, a sample mod and the list of the game's files.
