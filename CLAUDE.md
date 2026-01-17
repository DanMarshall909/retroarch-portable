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
├── retroarch.exe           # Main executable
├── retroarch.cfg           # User configuration (create from default)
├── retroarch.default.cfg   # Default settings template (reference only)
├── CLAUDE.md               # This file - project documentation
├── .gitignore              # Git ignore rules
│
├── assets/                 # UI themes (glui, ozone, rgui, xmb)
├── autoconfig/             # Controller profiles (dinput, hid, sdl2, xinput)
├── database/               # Game databases (.rdb files)
├── info/                   # Core information files
├── overlays/               # Visual overlays and borders
├── shaders/                # GLSL shader effects
├── filters/                # Video filters
│
├── cores/                  # Emulator cores (download as needed)
├── saves/                  # Game saves (per-core subdirectories)
├── states/                 # Save states
├── screenshots/            # Captured screenshots
├── system/                 # BIOS and system ROM files
└── playlists/              # Game playlists
```

## Configuration Approach

### Files to Track in Git
- `retroarch.cfg` - Main configuration
- `CLAUDE.md` - Documentation
- `.gitignore` - Ignore rules
- Custom controller configs in `autoconfig/`
- Custom playlists in `playlists/`

### Files to Ignore (machine-specific or large)
- `*.dll` - Runtime libraries
- `cores/` - Large binary files, download per-machine
- `saves/` - Personal save data
- `states/` - Save states
- `screenshots/` - Screenshots
- `system/` - BIOS files (legal concerns)
- `assets/`, `database/`, `shaders/`, `overlays/` - Stock RetroArch content

## Setup Instructions

### First Time Setup
1. Clone this repository
2. Download RetroArch portable from https://www.retroarch.com/
3. Extract to this folder (merge with existing files)
4. Download desired cores via RetroArch menu (Online Updater > Core Downloader)
5. Add BIOS files to `system/` folder as needed

### Syncing to Another Computer
1. Clone the repository
2. Download fresh RetroArch portable and extract
3. Your configuration will be applied automatically

## Common Tasks

### Adding a New Core
1. Open RetroArch
2. Go to: Main Menu > Online Updater > Core Downloader
3. Select and download the desired core

### Updating Configuration
1. Make changes in RetroArch
2. Settings are saved to `retroarch.cfg`
3. Commit changes: `git add retroarch.cfg && git commit -m "description"`

### Controller Setup
1. Connect controller
2. Go to: Settings > Input > Port 1 Controls
3. Configure and save
4. Custom profiles saved to `autoconfig/`

## Key Configuration Settings

Settings we've customized from defaults:

| Setting | Value | Reason |
|---------|-------|--------|
| (none yet) | | |

## Recommended Cores

| System | Core | Notes |
|--------|------|-------|
| NES | mesen | Highly accurate |
| SNES | bsnes | Accuracy focused |
| Genesis | genesis_plus_gx | Good compatibility |
| Game Boy | gambatte | Accurate |
| GBA | mgba | Modern, accurate |
| PS1 | duckstation | Best PS1 emulation |
| N64 | mupen64plus_next | Good compatibility |

## Troubleshooting

### RetroArch won't start
- Ensure all DLL files are present
- Try running as administrator
- Check Windows Defender isn't blocking

### Controller not detected
- Check controller is connected before starting RetroArch
- Try different input driver (Settings > Drivers > Input)
- Update controller firmware

### Audio crackling
- Increase audio latency (Settings > Audio > Output > Audio Latency)
- Try different audio driver

## Development Notes

When working with Claude Code on this project:
- Make small, incremental changes
- Test each change before committing
- Document configuration choices in this file
- Use descriptive commit messages
