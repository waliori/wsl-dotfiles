# WSL Dotfiles - Unified Color Scheme System

A sophisticated dotfiles configuration that creates seamless color scheme synchronization between WSL (Windows Subsystem for Linux) and Windows Terminal environments using Pywal.

## Features

### 🎨 Automatic Color Generation
- **Pywal Integration**: Generates color palettes from wallpapers or screenshots
- **Cross-Platform Sync**: Synchronizes colors between WSL and Windows environments
- **Dynamic Updates**: Real-time color scheme updates across all terminal interfaces

### 🖥️ Windows Integration
- **PowerShell Profile**: Enhanced with Starship prompt and Terminal-Icons
- **Windows Terminal**: Automatic color scheme application and cursor color matching
- **Screenshot-to-Palette**: Capture desktop screenshots and generate color schemes
- **Wallpaper Management**: Set wallpapers and sync colors automatically

### 🐧 WSL Integration
- **Starship Prompt**: Customized with Pywal color integration
- **Bash Scripts**: Automatic color synchronization utilities
- **Cross-Environment**: Seamless color updates between Windows and WSL

## Screenshots

### PowerShell with Synchronized Colors
![PowerShell Terminal](./images/screenshot1.png)

### System Monitoring with Color Theme
![System Monitor](./images/screenshot2.png)

### Development Environment
![Development Setup](./images/screenshot3.png)

## Installation

### Prerequisites
- Windows 10/11 with WSL2 enabled
- PowerShell 7+ (covers installation in video)
- Windows Terminal (for best visual experience)
- **Nerd Font** (required for icons - covered in setup video)
- Python and pip (for Pywal installation)
- Optional: **Wallpaper Engine** (for live wallpaper color extraction)

### Setup Steps

1. **Install Pywal**
   ```bash
   pip install pywal
   ```

2. **Install Required PowerShell Modules**
   ```powershell
   # Terminal Icons for file type icons
   Install-Module -Name Terminal-Icons -Force

   # PSReadLine for enhanced autocompletion (covered in Part 2)
   Install-Module -Name PSReadLine -Force
   ```

3. **Install Starship Prompt**
   ```bash
   # In WSL (Ubuntu/Debian)
   curl -sS https://starship.rs/install.sh | sh
   ```
   ```powershell
   # In PowerShell (Windows)
   winget install --id Starship.Starship
   ```

4. **Clone and Setup**
   ```bash
   git clone https://github.com/yourusername/wsl-dotfiles.git
   cd wsl-dotfiles

   # Copy Windows configs
   cp windows/Microsoft.PowerShell_profile.ps1 $HOME/Documents/PowerShell/
   cp windows/.config/* $HOME/.config/

   # Copy WSL scripts
   cp wsl/*.sh $HOME/
   chmod +x $HOME/*.sh

   # Copy Starship config
   cp windows/.config/starship.toml $HOME/.config/
   ```

## Usage

### PowerShell Commands

The PowerShell profile provides several convenient aliases:

```powershell
# Generate colors from current wallpaper and sync
Pywal-Starship

# Update theme from new wallpaper
Wallpaper-Starship

# Take screenshot and generate theme
Screenshot-Starship
```

### Core Functions (from winwal.psm1 module)

- `pywal_to_starship`: Updates Starship colors from current Pywal theme
- `update_pywal_to_starship`: Generates new Pywal theme from wallpaper and syncs
- `screenshot_to_pywal_to_starship`: Takes desktop screenshot, generates theme, and applies colors

### PSReadLine Autocompletion
The setup includes enhanced PowerShell autocompletion with PSReadLine:
- History-based suggestions
- Predictive text
- Enhanced tab completion
- Configured in the PowerShell profile

### Manual Sync

```bash
# In WSL - sync colors to local Starship
~/waltostarship.sh

# In WSL - sync colors to Windows Starship
~/winwaltostarship.sh
```

## Configuration Files

### Windows (`/windows/`)
- `Microsoft.PowerShell_profile.ps1`: PowerShell profile with Pywal integration
- `.config/starship.toml`: Starship prompt configuration with Pywal colors
- `.config/winwal.psm1`: Windows Pywal integration module
- `.config/screenshot.ps1`: Screenshot and wallpaper management

### WSL (`/wsl/`)
- `waltostarship.sh`: Sync Pywal colors to WSL Starship config
- `winwaltostarship.sh`: Sync Pywal colors to Windows Starship config

## Color Palette

The system uses a 9-color palette (color0-color8) extracted by Pywal:
- **color0**: Background
- **color1-color6**: Accent colors
- **color7**: Foreground
- **color8**: Bright background

These colors are automatically applied to:
- Starship prompt segments
- Windows Terminal color scheme
- Terminal Icons theme
- Command prompt colors

## Advanced Features

### Automatic Terminal Integration
- Windows Terminal settings are automatically updated
- Cursor color matches the color scheme
- Previous settings are backed up before changes

### Multi-Backend Support
- Supports multiple Pywal backends (colorthief, colorz, haishoku, etc.)
- Light/dark theme detection and automatic switching
- Terminal Icons integration with dynamic color themes

### Screenshot Workflow
1. Minimizes all windows
2. Captures desktop screenshot
3. Generates color palette with Pywal
4. Updates all terminal configurations
5. Restores windows

## Troubleshooting

### Common Issues
- **Colors not updating**: Ensure Pywal cache exists at `~/.cache/wal/`
- **Windows Terminal not changing**: Check if Terminal is running with proper permissions
- **Scripts not executable**: Run `chmod +x ~/waltostarship.sh ~/winwaltostarship.sh`

### Dependencies
- Ensure all PowerShell modules are installed
- Verify Pywal installation with `wal --version`
- Check Starship installation with `starship --version`

## Videos

### [Part 1: Complete Setup Guide](https://youtu.be/bsZcSO0RGVQ)
Comprehensive tutorial for setting up PowerShell and WSL (bash) environment in Windows 11 with Pywal integration for dynamic color theming from desktop backgrounds and live wallpapers (Wallpaper Engine support).

### [Part 2: Advanced Features](https://youtu.be/Yw0kYV3bD4c)
Advanced configuration including screenshot-based theming, winwal.psm1 module enhancements, and PSReadLine autocompletion setup.

## License

MIT License - Feel free to modify and adapt for your own setup.

## Contributing

Pull requests welcome! Please ensure any changes maintain compatibility across both WSL and Windows environments.