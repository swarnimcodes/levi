# NixOS System Configuration

A declarative NixOS system configuration for a Linux workstation running NixOS 25.05.

## Features

- **Desktop Environment**: KDE Plasma 6 with SDDM display manager
- **Audio**: PipeWire audio server
- **Networking**: NetworkManager
- **Kernel**: Latest Linux kernel
- **Development Tools**: neovim, ripgrep, fd, claude-code
- **Flakes-based**: Reproducible builds with dependency pinning

## Prerequisites

- NixOS 25.05 or compatible version
- Nix Flakes enabled

## Usage

### Applying Configuration Changes

```bash
# Apply configuration and make it the default
sudo nixos-rebuild switch --flake .#nixos

# Test configuration without making it default
sudo nixos-rebuild test --flake .#nixos

# Build configuration without switching
sudo nixos-rebuild build --flake .#nixos
```

### Updating Dependencies

```bash
# Update all flake inputs
sudo nix flake update

# Apply updated configuration
sudo nixos-rebuild switch --flake .#nixos
```

### Rolling Back

```bash
# Rollback to previous generation
sudo nixos-rebuild switch --rollback
```

## Configuration Files

- `flake.nix` - Flake definition declaring inputs and outputs
- `flake.lock` - Locked dependency versions (auto-generated)
- `configuration.nix` - Main system configuration
- `hardware-configuration.nix` - Hardware-specific settings (auto-generated)

## Package Management

```bash
# Search for packages
nix search nixpkgs <package-name>

# Temporarily install a package
nix-shell -p <package-name>

# List installed packages
nix-env -q
```

## Customization

1. Modify `configuration.nix` to add packages, services, or system settings
2. Run `sudo nixos-rebuild switch --flake .#nixos` to apply changes
3. If changes fail, rollback using `sudo nixos-rebuild switch --rollback`

## Notes

- Never manually edit `hardware-configuration.nix` or `flake.lock`
- All commands should be run from the repository root directory
- Unfree packages are enabled by default

## License

MIT License - see [LICENSE](LICENSE) file for details
