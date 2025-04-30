# BoxBuilder for Android/Termux
"We have box64 at home"

A streamlined tool to build and package box64 for [MiceWine](https://github.com/KreitinnSoftware/MiceWine-Application).

## Features
- Automated box64 compilation for ARM64
- Automated dependency installation
- sys/sem.h patching
- .rat package creation
- Commit management
- Automated tuning for current device 

## Prerequisites
- Android device with Termux
- Basic understanding of Termux

## Installation
1. Copy the script to Termux:
   ```sh
   curl https://github.com/Happ1ness-dev/BoxBuilder/boxbuilder -o $PREFIX/bin/boxbuilder && chmod +x $PREFIX/bin/boxbuilder
   ```
2. Run initial setup:
   ```sh
   boxbuilder
   ```

## First Run Setup
You'll be prompted for:
1. Dependency installation + sem.h patching (recommended)
2. Box64 repository (cloning) path (default: `~/git-projects/box64`)
3. Output directory for .rat packages (default: `/sdcard/Download`)

Configuration is saved to `~/.config/BoxBuilder/settings.conf`

## Usage
```sh
boxbuilder [command]

Commands:
  build           - Build box64
  build update    - Update repo & rebuild
  pull            - Update repository
  checkout [hash] - Switch to specific commit
  repatch         - Reapply sys/sem.h patch
  config          - Show current configuration
```

## Package Creation
Successful builds create a .rat package containing:
- box64 binary
- box64.box64rc config
- Package metadata

Output path: Your specified directory (default: `/sdcard/Download`)

## Important Notes
- Android 10+ (API 29+) is required
- Repository operations use `git reset --hard`
- The script patches `sys/sem.h` to prevent build errors
- Builds have ARM Dynarec and Android-specific optimizations enabled by default 