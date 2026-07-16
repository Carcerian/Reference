# Fedora Linux Gaming & Game Development Setup Guide

Complete command reference for setting up Fedora with gaming platforms, dev tools, and specialized workflows.

---

## Table of Contents
1. [Quick Start](#quick-start)
2. [Gaming Platforms](#gaming-platforms)
3. [Game Development Engines](#game-development-engines)
4. [Retro/Emulation](#retroemulation-retro-gaming)
5. [Graphics & Content Creation](#graphics--content-creation)
6. [Development Tools](#development-tools)
7. [Audio/Music](#audiomusic)
8. [Performance & System](#performance--system)
9. [Scripting & Modding Tools](#scripting--modding-tools)
10. [NWN:EE Tooling & Setup](#nwnee-tooling--setup)
11. [Emulation Setup & Configuration](#emulation-setup--configuration)
12. [Game Development Specifics](#game-development-specifics)

---

## Quick Start

### Install Everything at Once (Core Gaming + Dev)
```bash
sudo dnf install steam lutris retroarch godot blender krita gimp code git -y
```

### Install Everything at Once (Comprehensive)
```bash
sudo dnf install steam lutris retroarch dosbox scummvm mame godot blender unity-hub unreal-engine krita aseprite inkscape gimp imagemagick gcc cmake git python3 rustc code vim neovim wine wine-mono wine-gecko winetricks audacity ffmpeg sox lmms mangohud gpu-monitor-tools htop nvtop gamemode vulkan-tools nodejs perl -y
```

---

## Gaming Platforms

### Core Gaming Launchers
```bash
sudo dnf install steam              # Valve's game platform (essential)
sudo dnf install lutris             # Multi-platform game launcher (GOG, Epic, Steam)
sudo dnf install heroic             # GOG/Epic launcher alternative (lighter)
sudo dnf install proton-ge-custom   # Proton experimental versions (newer game compat)
```

### Post-Install Steam Configuration
```bash
# Enable Steam Proton for Windows games
# Launch Steam → Settings → Compatibility → Enable Proton

# Optional: Install additional Proton versions
flatpak install flathub com.github.Matoking.protontricks
```

---

## Game Development Engines

### Primary Engines
```bash
sudo dnf install godot              # Godot Engine (lightweight, open-source, 2D/3D)
sudo dnf install blender            # Blender (3D modeling, animation, rendering)
```

### Alternative Engines
```bash
sudo dnf install unity-hub          # Unity (if you prefer over Godot)
# Note: UE5 requires Flathub
flatpak install flathub com.epicgames.UnrealEngine
```

### Game Dev Tools
```bash
sudo dnf install aseprite           # Pixel art tool (open-source build)
sudo dnf install tiled              # Tile map editor (indie game standard)
sudo dnf install audacity           # Audio editing for game sfx
```

---

## Retro/Emulation (Retro Gaming)

### Multi-System Emulation
```bash
sudo dnf install retroarch          # Multi-emulator (NES, SNES, Genesis, Atari, GB, etc.)
sudo dnf install dosbox             # DOS games (classic PC era)
sudo dnf install dosbox-staging     # Modern DOSBox fork (better compatibility)
sudo dnf install scummvm            # Classic point-and-click adventures (LucasArts, Sierra)
sudo dnf install mame               # Arcade cabinet emulation
```

### Console Emulators
```bash
sudo dnf install pcsx2              # PlayStation 2
sudo dnf install dolphin-emu        # GameCube/Wii
sudo dnf install cemu               # Wii U
sudo dnf install rpcs3              # PlayStation 3
```

### Handheld Emulators
```bash
sudo dnf install mgba-core          # Game Boy Advance
sudo dnf install snes9x-core        # SNES
sudo dnf install nestopia-core      # NES
sudo dnf install mupen64plus        # Nintendo 64
```

### Game Boy & Older Systems
```bash
sudo dnf install gambatte-core      # Game Boy/Game Boy Color
sudo dnf install genesis-plus-gx    # Sega Genesis/Master System
sudo dnf install atari800-core      # Atari 8-bit
```

---

## Graphics & Content Creation

### Digital Art & Pixel Art
```bash
sudo dnf install krita              # Digital painting (professional, game art friendly)
sudo dnf install aseprite           # Pixel art tool (animation-focused)
sudo dnf install piskel             # Web-based pixel art (lightweight alternative)
```

### Vector & General Graphics
```bash
sudo dnf install inkscape           # Vector graphics (logos, UI design)
sudo dnf install gimp               # Raster image editor (Photoshop alternative)
sudo dnf install imagemagick        # Command-line image processing & batch ops
```

### 3D & Modeling
```bash
sudo dnf install blender            # 3D modeling, UV mapping, rendering
sudo dnf install meshlab            # 3D mesh processing
```

---

## Development Tools

### Compilers & Build Systems
```bash
sudo dnf install gcc                # GNU C/C++ compiler (essential)
sudo dnf install clang              # Clang C/C++ compiler (alternative)
sudo dnf install cmake              # Cross-platform build system
sudo dnf install make               # GNU Make
sudo dnf install ninja-build        # Fast build system
```

### Version Control & Git
```bash
sudo dnf install git                # Git version control (essential)
sudo dnf install gitk               # Git GUI
sudo dnf install github-cli         # GitHub command-line tool
```

### Languages & Runtimes
```bash
sudo dnf install python3            # Python 3 (essential for game tools, scripting)
sudo dnf install python3-pip        # Python package manager
sudo dnf install python3-venv       # Python virtual environments
sudo dnf install rustc              # Rust compiler (systems language, game engines)
sudo dnf install cargo              # Rust package manager
sudo dnf install nodejs             # Node.js (web tools, scripting)
```

### Editors & IDEs
```bash
sudo dnf install code               # VS Code (most popular)
sudo dnf install vim                # Vim (lightweight, keyboard-driven)
sudo dnf install neovim             # Modern Vim fork (better performance, plugins)
sudo dnf install emacs              # Emacs (if you're into that)
```

### Documentation & Help
```bash
sudo dnf install texinfo            # GNU documentation format
sudo dnf install doxygen            # Code documentation generator
sudo dnf install man-pages          # Manual pages (offline docs)
```

---

## Audio/Music

### Audio Editing & Production
```bash
sudo dnf install audacity           # Audio editor (waveform editing)
sudo dnf install ffmpeg             # Multimedia framework (convert, compress)
sudo dnf install sox                # Sound eXchange (command-line audio tool)
sudo dnf install lmms               # Linux MultiMedia Studio (music production)
```

### Music Composition
```bash
sudo dnf install musescore          # Notation software
sudo dnf install fluidsynth         # SoundFont synthesizer
```

---

## Performance & System

### Gaming Performance
```bash
sudo dnf install mangohud           # FPS/performance overlay (in-game)
sudo dnf install gamemode           # Automatic OS optimization for gaming
sudo dnf install vulkan-tools       # Vulkan debugging & profiling
```

### System Monitoring
```bash
sudo dnf install gpu-monitor-tools  # AMD GPU monitoring
sudo dnf install htop               # System resource monitor
sudo dnf install nvtop              # GPU resource monitor (NVIDIA/AMD)
sudo dnf install glxinfo            # OpenGL info utility
sudo dnf install vulkan-info        # Vulkan device info
```

### System Optimization
```bash
sudo dnf install tuned              # Dynamic system tuning daemon
sudo dnf install powertop           # Power consumption analyzer
```

---

## Scripting & Modding Tools

### General Scripting
```bash
sudo dnf install bash               # Bash shell (already installed, reference)
sudo dnf install perl               # Perl scripting
sudo dnf install ruby               # Ruby scripting
sudo dnf install lua                # Lua (game scripting language)
```

### Code Documentation
```bash
sudo dnf install doxygen            # Generate docs from source code
sudo dnf install graphviz           # Visualization software (for Doxygen diagrams)
```

---

## NWN:EE Tooling & Setup

### Wine & Compatibility Layer
```bash
sudo dnf install wine               # Wine (Windows compatibility layer, essential for NWN:EE)
sudo dnf install wine-mono          # .NET support (required for many NWN tools)
sudo dnf install wine-gecko         # Web browser support (IE rendering)
sudo dnf install winetricks         # Wine helper script (install workarounds)
```

### NWN:EE Installation via Lutris (Recommended)
```bash
# Install Lutris first
sudo dnf install lutris

# Then add NWN:EE via Lutris web UI or CLI:
# 1. Open Lutris → Search "Neverwinter Nights Enhanced Edition"
# 2. Click install (Lutris handles Wine prefix & dependencies)
# OR use command line:
# lutris -i "neverwinter-nights-ee" (if available in Lutris database)
```

### NWN:EE Standalone Setup (Manual)
```bash
# Create Wine prefix for NWN:EE
WINEPREFIX=~/.wine_nwnee wineboot -u

# Install NWN:EE from Steam via Proton
# OR install manually to prefix:
WINEPREFIX=~/.wine_nwnee wine /path/to/NWN_EE_Setup.exe

# Create desktop shortcut (optional)
cat > ~/.local/share/applications/nwnee.desktop << 'EOF'
[Desktop Entry]
Type=Application
Name=Neverwinter Nights: Enhanced Edition
Exec=WINEPREFIX=~/.wine_nwnee wine ~/.wine_nwnee/drive_c/Program\ Files/Neverwinter\ Nights\ Enhanced\ Edition/nwn.exe
Icon=
Categories=Game;
EOF
```

### NWN:EE Community Tools (via Wine)
```bash
# Create separate Wine prefix for NWN tools
WINEPREFIX=~/.wine_nwn_tools wineboot -u

# Install tools in this prefix:
# - NWScript Compiler
# - Toolset
# - Aurora Toolset
# - LSSGEE (Lilac Soul's Script Generator)

# Run tools:
WINEPREFIX=~/.wine_nwn_tools wine /path/to/toolname.exe
```

### NWN:EE Configuration
```bash
# Nwnplayer.ini location (Linux Wine path):
~/.wine_nwnee/drive_c/users/[username]/My\ Documents/Neverwinter\ Nights/

# Edit nwnplayer.ini for:
# - Graphics settings (resolution, detail level)
# - Keybinds
# - Video card detection (may need manual tweaking)
```

### Troubleshooting NWN:EE on Linux
```bash
# Check Wine configuration
WINEPREFIX=~/.wine_nwnee winecfg

# Enable DXVK (Direct3D 9-11 to Vulkan translation, better perf)
WINEPREFIX=~/.wine_nwnee wineboot -u
# Then copy DXVK files to prefix/lib64/wine/x86_64-windows/

# Run with verbose logging
WINE_CPU_TOPOLOGY=2:1 WINEPREFIX=~/.wine_nwnee wine nwn.exe

# Test DirectX/OpenGL
glxinfo | grep -i opengl
vulkaninfo
```

### NWN:EE Community Resources
```bash
# Clone popular NWN builder scripts/resources
git clone https://github.com/nwn-devkit/nwn-base-classes.git
git clone https://github.com/Philos-Lib/nwn-lib-base.git

# Access Sinfar public builders Discord (requires invite)
# Access NWN Vault (online repository)
# https://neverwintervaults.org
```

---

## Emulation Setup & Configuration

### RetroArch Initial Setup
```bash
sudo dnf install retroarch

# First launch (creates config directory)
retroarch

# Manual config location
~/.config/retroarch/retroarch.cfg

# Common RetroArch commands
retroarch --help                      # View all options
retroarch -c ~/.config/retroarch/retroarch.cfg /path/to/game.rom
```

### RetroArch Core Installation
```bash
# Via RetroArch UI:
# 1. Online Updater → Core Updater
# 2. Select cores: Nestopia (NES), Snes9x (SNES), Genesis Plus GX, etc.

# OR install via command line (if available)
retroarch -L /path/to/core_name_libretro.so /path/to/game.rom
```

### DOSBox Setup
```bash
sudo dnf install dosbox dosbox-staging

# Launch game
dosbox /path/to/game/directory

# Create DOSBox game config
cat > game.conf << 'EOF'
mount c /path/to/game
c:
cd game_folder
game.exe
EOF

# Run with config
dosbox -conf game.conf
```

### MAME Configuration
```bash
sudo dnf install mame

# List available ROMs
mame -listfull

# Launch arcade game
mame -cc roms_directory game_name

# Fullscreen
mame -f game_name
```

### Console Emulator Setup (Example: Dolphin for GameCube/Wii)
```bash
sudo dnf install dolphin-emu

# First run (creates config)
dolphin-emu

# Config location
~/.config/Dolphin/

# Launch game
dolphin-emu /path/to/game.iso
```

### Game ROM Organization Best Practice
```bash
# Organize by system
~/Games/Emulation/NES/
~/Games/Emulation/SNES/
~/Games/Emulation/Genesis/
~/Games/Emulation/GameCube/
~/Games/Emulation/Arcade/

# Use RetroArch playlist scanner
# Or manually create M3U playlists for disc-based games
```

### Emulation Performance Optimization
```bash
# Enable hardware acceleration in RetroArch
# Settings → Video → Fullscreen
# Settings → Video → GPU Hard Sync

# Lower resolution if struggling
# Settings → Video → Aspect Ratio → Custom

# Check FPS overlay
# Settings → Overlay → Display Overlay
```

---

## Game Development Specifics

### Godot Engine Development
```bash
sudo dnf install godot

# Launch Godot
godot

# Create new project
godot --new-window

# Export templates (for building standalone games)
# Download via Godot Editor → Project → Install Export Templates

# Build 2D/3D game
# 1. Open Godot
# 2. New Project → Choose 2D or 3D
# 3. Create scenes with Godot scripting (GDScript)
# 4. Export → Linux, Windows, Web, etc.
```

### Godot GDScript Setup (Python-like scripting)
```bash
# No additional install needed—GDScript is built-in

# Python pip integration (optional, for external tools)
sudo dnf install python3-pip
pip3 install --user scons          # Build tool for Godot from source

# Use Godot's built-in code editor or VS Code with GDScript plugin
code --install-extension geequlim.godot-tools
```

### Blender Game Asset Creation
```bash
sudo dnf install blender

# Launch Blender
blender

# Common game asset workflows:
# 1. Model 3D assets (characters, props, environments)
# 2. UV unwrap for texturing
# 3. Bake normal maps & textures
# 4. Export to FBX/GLTF for game engines

# Export formats for game engines
# - FBX (widely supported)
# - GLTF 2.0 (modern standard)
# - OBJ (basic, no rigging)
```

### Blender Command-Line Rendering
```bash
# Render scene to PNG
blender -b model.blend -o output_%04d.png -f 1

# Export scene to GLTF
blender -b model.blend --python-expr "import bpy; bpy.ops.export_scene.gltf(filepath='output.gltf')"
```

### Unity Development
```bash
sudo dnf install unity-hub

# Launch Unity Hub
unity-hub

# Install Unity Editor via Hub
# Select version (LTS recommended for stability)

# Create/open project
```

### Python for Game Development
```bash
sudo dnf install python3 python3-pip

# Install game dev libraries
pip3 install --user pygame           # 2D game library (simple, educational)
pip3 install --user panda3d          # 3D engine
pip3 install --user arcade           # Modern 2D library

# Create simple Pygame project
cat > game.py << 'EOF'
import pygame
pygame.init()
screen = pygame.display.set_mode((800, 600))
pygame.display.set_caption("My Game")
running = True
while running:
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            running = False
pygame.quit()
EOF

python3 game.py
```

### Rust for Game Development
```bash
sudo dnf install rustc cargo

# Create new Rust game project
cargo new my_game
cd my_game

# Add Bevy game engine to Cargo.toml
cat >> Cargo.toml << 'EOF'
[dependencies]
bevy = "0.12"
EOF

# Build & run
cargo run
```

### Asset Compression & Optimization
```bash
sudo dnf install imagemagick

# Resize textures
convert input.png -resize 1024x1024 output.png

# Convert to WebP (smaller file size)
convert input.png output.webp

# Batch compress all PNGs
for file in *.png; do 
    convert "$file" -quality 85 "compressed_$file"
done
```

### Git Workflow for Game Projects
```bash
# Initialize game project repo
cd my_game_project
git init
git config user.name "Your Name"
git config user.email "your@email.com"

# Create .gitignore for game assets (large files)
cat > .gitignore << 'EOF'
*.exe
*.app
*.dmg
/Build/
/Exports/
*.unitypackage
*.blend1
*.blend2
node_modules/
.env
EOF

# First commit
git add .
git commit -m "Initial game project setup"

# Push to GitHub
git remote add origin https://github.com/yourusername/my_game_project.git
git branch -M main
git push -u origin main
```

### Performance Profiling
```bash
# Monitor resource usage while game runs
htop
# Press Shift+M to sort by memory, Shift+P for CPU

# GPU-specific monitoring (AMD 6600)
gpu-monitor-tools     # AMD GPU stats
nvtop                 # Alternative tool

# Profile with VulkanInfo
vulkaninfo | grep -A 20 "Device Properties"
```

### Build & Deploy
```bash
# Godot export to Linux
# 1. Project → Export → Linux/X11
# 2. Choose executable name & location

# Godot export to Windows (requires cross-compile or Windows machine)
# 1. Project → Export → Windows Desktop

# Export to Web (HTML5)
# 1. Project → Export → Web
# 2. Upload to itch.io or GitHub Pages

# Publish to itch.io (command line)
pip3 install --user butler
butler push ./builds/linux yourusername/game-name:linux
butler push ./builds/windows yourusername/game-name:windows
butler push ./builds/web yourusername/game-name:web
```

---

## Advanced Configuration & Optimization

### Enable GameMode for All Games
```bash
# Install and enable
sudo dnf install gamemode
sudo systemctl enable gamemoded
sudo systemctl start gamemoded

# Launch any game with GameMode
gamemoderun steam
gamemoderun lutris
gamemoderun godot

# Verify it's working
gamemoderun cat /proc/sys/vm/swappiness  # Should be lower with gamemode active
```

### Configure Proton for Specific Games
```bash
# Steam → Game → Properties → Compatibility
# Enable Proton / Select Version

# Force Proton version for game
# In launch options: PROTON_VERSION=proton-ge-custom gamemoderun %command%

# Check Proton logs
PROTON_LOG=1 steam game_name  # Creates proton-x-xxxxx.log in Steam dir
```

### Optimize Wine Prefix for NWN:EE
```bash
# Reduce prefix size
cd ~/.wine_nwnee
rm -rf drive_d drive_e  # Remove unused drives
du -sh .                # Check size

# Backup prefix
cp -r ~/.wine_nwnee ~/.wine_nwnee.backup

# Clean prefix (removes temp files)
WINEPREFIX=~/.wine_nwnee wine wineboot --shutdown
```

### Monitor Thermal/Power During Gaming
```bash
# Check GPU temperature (AMD 6600)
sensors              # If lm-sensors installed
watch -n 1 sensors   # Live monitoring

# Check CPU frequency scaling
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_cur_freq

# Enable CPU performance mode (if supported)
echo performance | sudo tee /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
```

---

## Helpful Resources

### Official Documentation
- **Fedora Docs**: https://docs.fedoraproject.org/
- **Fedora Gaming Guide**: https://fedoraproject.org/wiki/Gaming
- **ProtonDB**: https://protondb.com/ (Check game compatibility)
- **WineHQ Database**: https://appdb.winehq.org/ (Windows app compatibility)

### NWN:EE Community
- **Neverwinter Vault**: https://neverwintervaults.org
- **NWN Subreddit**: https://www.reddit.com/r/neverwinternights/
- **Sinfar Public Builders Discord**: (Invite-only, contact community)
- **GitHub NWN Resources**: https://github.com/search?q=nwn

### Game Development
- **Godot Docs**: https://docs.godotengine.org/
- **Blender Docs**: https://docs.blender.org/
- **itch.io**: https://itch.io/ (Indie game distribution)
- **GitHub**: https://github.com/ (Code hosting)

### Emulation
- **RetroArch Docs**: https://docs.libretro.com/
- **MAME Docs**: https://docs.mamedev.org/
- **Dolphin Wiki**: https://dolphin-emu.org/docs/

---

## Quick Troubleshooting

### NWN:EE Won't Launch
```bash
# Reset Wine prefix
rm -rf ~/.wine_nwnee
WINEPREFIX=~/.wine_nwnee wineboot -u

# Reinstall via Lutris (cleaner)
lutris -i "neverwinter-nights-ee"
```

### Low FPS in Games
```bash
# Check GPU load
nvtop
# or
gpu-monitor-tools

# Disable V-Sync (can cause lag)
# Steam → Game Properties → Set Launch Option: PROTON_NO_FSYNC=1 %command%

# Lower resolution in-game
# Enable frame rate cap to avoid thermal throttling
```

### Audio Not Working in Wine Apps
```bash
# Reinstall ALSA/PulseAudio in Wine prefix
WINEPREFIX=~/.wine_nwnee winetricks sound=pulse

# Test audio
speaker-test -t sine -f 1000 -l 1
```

### Game Controllers Not Recognized
```bash
# Check if controller detected
jstest /dev/input/js0

# Install controller drivers
sudo dnf install gamepad

# Reconfigure in game settings
```

---

## Summary

**All-in-one installation** (copy & paste):
```bash
sudo dnf install steam lutris retroarch dosbox scummvm godot blender krita gimp code git python3 rustc wine wine-mono wine-gecko winetricks gamemode mangohud vulkan-tools -y
```

**NWN:EE Quick Setup**:
```bash
sudo dnf install wine wine-mono wine-gecko winetricks lutris
# Then use Lutris to install NWN:EE
```

**Game Dev Quick Setup**:
```bash
sudo dnf install godot blender aseprite audacity code git python3 rustc -y
```

You're ready to build, play, and mod! 🎮🛠️

