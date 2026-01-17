# RetroArch Portable Configuration

Portable RetroArch setup for cloning and running on any Windows machine.

## Reference
- Canonical contributor guidance (for humans and AI) lives in `GUIDELINES.md`.
- Keep this repo free of ROMs/BIOS; commit only config, cores, and supporting assets.

## Quick Start
1. `git clone https://github.com/DanMarshall909/retroarch-portable.git`
2. Download RetroArch portable from https://www.retroarch.com/ and extract into this folder.
3. Add ROMs to `roms/<System>/` and BIOS files to `system/` where required.
4. Launch test (example): `retroarch.exe -L cores/snes9x_libretro.dll "roms/SNES/game.zip"`.

## Notes
- Core binaries live in `cores/`; ensure launch commands and playlists use the same filenames.
- Runtime output (`saves/`, `states/`, `screenshots/`, `logs/`) should stay out of commits unless intentionally reviewing issues.
