# ReShade (splash banner once per launch)

A fork of [ReShade](https://github.com/crosire/reshade) with one change.

Some games, such as DOOM: The Dark Ages, recreate the swap chain on every scene change. Stock ReShade treats each new swap chain as a fresh start, so the splash banner ("Press Home to open the overlay" and so on) pops up again every time. In this fork the banner only appears when the program starts. Once it has gone away it stays gone until the game is restarted.

To use it, install stock ReShade for your game first. Then download `ReShade64.dll` (or `ReShade32.dll` for 32-bit games) from the [releases](https://github.com/evilbananas/reshade-splash-once/releases), rename it to match the ReShade DLL in the game folder (for example `dxgi.dll`), and replace that file.

## RHI

To use this build with [RHI](https://github.com/RankFTW/RHI), put the DLL in `%LOCALAPPDATA%\RHI\Custom\ReShade\`. Then open the game's overrides, set ReShade Channel to Custom, and pick the DLL in the "Select Custom ReShade" dialog.

The change is in `draw_gui()` in [source/runtime_gui.cpp](source/runtime_gui.cpp). Everything else is upstream ReShade; see the [upstream README](https://github.com/crosire/reshade#readme) for build instructions.
