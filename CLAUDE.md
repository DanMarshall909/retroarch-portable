# RetroArch Portable Configuration

This is a portable RetroArch setup designed for easy cloning and deployment across multiple computers.

## Project Goals

- **Portable**: Self-contained installation that can be copied to any Windows machine
- **Version Controlled**: Track configuration changes via Git for easy sync and rollback
- **User Friendly**: Simple setup process with documented configuration choices
- **Incremental**: Make small, tested changes rather than large sweeping modifications

## Directory Structure

```
RetroArch-Win64/
├── retroarch.exe           # Main executable (download separately)
├── retroarch.cfg           # User configuration
├── CLAUDE.md               # This file - project documentation
├── .gitignore              # Git ignore rules
│
├── cores/                  # Emulator cores (tracked in git)
├── roms/                   # Game ROMs (ignored - add your own)
│   ├── NES/
│   ├── SNES/
│   ├── Genesis/
│   ├── GB/
│   ├── GBA/
│   ├── N64/
│   ├── PS1/
│   ├── Atari2600/
│   └── Arcade/
├── system/                 # BIOS files (ignored - add your own)
├── saves/                  # Game saves
├── states/                 # Save states
└── screenshots/            # Captured screenshots
```

## Quick Start

### Cloning to a New Computer
```bash
git clone https://github.com/DanMarshall909/retroarch-portable.git
```
Then:
1. Download RetroArch portable from https://www.retroarch.com/
2. Extract to this folder (merge with existing files)
3. Add your ROMs to appropriate `roms/` subfolders
4. Add BIOS files to `system/` if needed (PS1, Neo Geo)

### Launching Games
```bash
# SNES
retroarch.exe -L cores/snes9x_libretro.dll "roms/SNES/game.zip"

# NES
retroarch.exe -L cores/mesen_libretro.dll "roms/NES/game.zip"

# Genesis
retroarch.exe -L cores/genesis_plus_gx_libretro.dll "roms/Genesis/game.zip"

# Arcade (MAME 2003 Plus - works with older ROM dumps)
retroarch.exe -L cores/mame2003_plus_libretro.dll "roms/Arcade/game.zip"
```

## Installed Cores

| System | Core File | Notes |
|--------|-----------|-------|
| NES | mesen_libretro.dll | Highly accurate |
| SNES | snes9x_libretro.dll | Good balance of speed/accuracy |
| Genesis/Mega Drive | genesis_plus_gx_libretro.dll | Excellent compatibility |
| Atari 2600 | stella_libretro.dll | Full featured |
| Game Boy/GBC | gambatte_libretro.dll | Accurate |
| GBA | mgba_libretro.dll | Modern, accurate |
| PS1 | swanstation_libretro.dll | Requires BIOS in system/ |
| N64 | mupen64plus_next_libretro.dll | Good compatibility |
| Arcade | mame2003_plus_libretro.dll | Best for older ROM dumps |
| Arcade | fbneo_libretro.dll | Needs exact modern romsets |

## Key Configuration Settings

| Setting | Value | Reason |
|---------|-------|--------|
| video_driver | d3d11 | Best Windows compatibility |
| video_shader | crt-easymode.slangp | Authentic CRT scanlines |
| video_shader_enable | true | Shaders on by default |
| menu_driver | xmb | PlayStation-style menu |
| input_joypad_driver | dinput | Better generic controller support |
| log_verbosity | true | Helps debug ROM issues |

## BIOS Requirements

| System | BIOS File | Location |
|--------|-----------|----------|
| PS1 | scph1001.bin (or similar) | system/ |
| Neo Geo | neogeo.zip | system/ |

## Arcade ROM Notes

**MAME 2003 Plus** works better with older ROM dumps (from early 2000s).
**FinalBurn Neo** requires exact modern MAME romset versions.

If arcade ROMs fail to load, check `logs/retroarch.log` for missing files.

## Controls

| Action | Key |
|--------|-----|
| Open Menu | F1 |
| Toggle Fullscreen | F |
| Quit | Esc |
| Save State | F2 |
| Load State | F4 |
| Toggle Shader | M |

## Troubleshooting

### ROM won't load
- Check `logs/retroarch.log` for specific errors
- Arcade ROMs often need exact file names/CRCs
- Some systems need BIOS files in `system/`

### Controller not detected
- Connect controller before starting RetroArch
- Try Settings > Drivers > Input > dinput
- Press F1 > Settings > Input to remap

### No CRT shader effect
- Shader must match video driver (Slang for D3D11, GLSL for OpenGL)
- Press F1 > Shaders to manually load

## Git Workflow

```bash
# After making settings changes
git add retroarch.cfg .gitignore CLAUDE.md
git commit -m "Update settings"
git push
```

## Repository

https://github.com/DanMarshall909/retroarch-portable
