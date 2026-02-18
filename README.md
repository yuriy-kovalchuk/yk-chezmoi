# yk-chezmoi

Personal configuration and environment management using [chezmoi](https://www.chezmoi.io/).

## Deployment Guide
Follow these steps to replicate this environment on a new macOS or Linux machine.

### 1. Install chezmoi
**macOS**:
```bash
brew install chezmoi
```

**Linux**:
```bash
sh -c "$(curl -fsLS get.chezmoi.io)"
```

### 2. Initialize Environment
This command clones the repository and performs initial OS detection:
```bash
# Replace with your actual repository URL if different
chezmoi init https://github.com/yuriy-kovalchuk/yk-chezmoi.git
```

### 3. Review & Apply
Preview the changes to be made to your home directory:
```bash
chezmoi diff
```

If the changes are correct, apply the configuration:
```bash
chezmoi apply
```

## Management & Synchronization

### Applying Updates
To pull the latest changes from the repository and apply them:
```bash
chezmoi update
```

### Modifying Configuration
To edit a managed file (e.g., `.bashrc`):
```bash
chezmoi edit ~/.bashrc
```

### Adding New Files
To add a new configuration file to the repository:
```bash
chezmoi add ~/.new_config_file
```

---
*Maintained by yuriy-kovalchuk*
