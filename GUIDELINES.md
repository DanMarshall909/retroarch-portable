# Repository Guidelines

Unified instructions for all contributors (human or AI). Keep changes small, reproducible, and free of copyrighted ROM or BIOS content.

## Project Structure & Assets
- `retroarch.exe`, `retroarch.cfg`: Main binary and primary config; keep config diffs readable.
- `cores/`: Libretro cores under version control; names must match launch commands and playlists.
- `roms/` and `system/`: User-provided ROMs/BIOS (ignored); never commit.
- `saves/`, `states/`, `screenshots/`, `logs/`: Runtime output; clean before committing unless diagnosing issues.
- `autoconfig/`, `overlays/`, `shaders/`, `assets/`, `database/`, `playlists/`: Input profiles, visuals, UI assets, and metadata that should stay in sync with the config.

## Build, Test, and Development Commands
- `retroarch.exe --menu`: Open the UI to confirm playlists, overlays, and controller profiles.
- `retroarch.exe -L cores/<core>.dll "roms/<System>/game.zip"`: Launch a core with a ROM to validate configs.
- `retroarch.exe --appendconfig retroarch.cfg --verbose`: Smoke-test config changes; review `logs/retroarch.log` for warnings.

## Coding Style & Naming Conventions
- Configs use `key = value`; keep spacing consistent and ASCII only. Mirror existing option casing from `retroarch.cfg`.
- Place ROMs in system-named folders (e.g., `roms/SNES/`) and align filenames with playlists and launch commands.
- Use descriptive names for overlays/shaders (e.g., `crt-easymode.slangp`) and keep directory casing consistent.

## Testing Guidelines
- For each changed subsystem, launch one ROM with the relevant core; confirm video, audio, input, and shader behavior.
- Check `logs/retroarch.log` for missing BIOS, shader errors, controller mapping issues, or deprecated options.
- Keep logs out of commits unless explicitly needed for review; trim noisy diffs in configs when possible.

## Commit & Pull Request Guidelines
- Use concise, imperative commits (e.g., "Update shader defaults", "Add SNES controller profile").
- In PRs, note the user-facing effect, tested launch commands, and any BIOS/ROM expectations.
- Do not include ROMs, BIOS, personal saves, or machine-specific paths; redact sensitive details in shared logs.
