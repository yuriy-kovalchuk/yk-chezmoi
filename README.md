# yk-chezmoi

Personal dotfiles managed via [chezmoi](https://www.chezmoi.io/).

## What is this?
`chezmoi` is a tool that manages your dotfiles (like `.zshrc`, `.gitconfig`, etc.) across multiple machines. 
- **Source of Truth**: This directory (`~/Developer/yk-chezmoi`) is where your actual configuration lives.
- **Home Directory**: `chezmoi` "applies" these files to your actual home directory (`~`).
- **Templates**: It supports templates, allowing you to use different configurations (like email addresses or paths) on different machines.

## Initial Setup
### 1. Install chezmoi
**macOS:**
```bash
brew install chezmoi
```

**Linux (via curl):**
```bash
sh -c "$(curl -fsLS get.chezmoi.io)"
```

### 2. Initialize chezmoi
Pointing to this directory:
   ```bash
   chezmoi init --source ~/Developer/yk-chezmoi
   ```

2. **Add a file**:
   ```bash
   chezmoi add ~/.yourconfigfile
   ```

3. **Apply changes**:
   ```bash
   chezmoi apply
   ```

## Workflow: Safe Changes
Before applying changes that might overwrite your files, you should always preview them:

1. **Check what will change**:
   ```bash
   chezmoi -S . diff
   ```
   This shows a "git diff" style output of what `chezmoi` *wants* to do to your home directory.

2. **Run a dry-run**:
   ```bash
   chezmoi -S . apply --dry-run --verbose
   ```
   This tells you exactly what files would be modified without actually touching them.

3. **Apply with confidence**:
   ```bash
   chezmoi -S . apply
   ```

## Using on a new PC
To replicate your setup on a new machine:
1. Install `chezmoi`.
2. Run:
   ```bash
   chezmoi init https://github.com/YOUR_USERNAME/yk-chezmoi.git
   ```
3. Apply the changes:
   ```bash
   chezmoi apply
   ```

## Managed Files
- `~/.hello-chezmoi.txt`: A simple hello world example.

## Cross-Platform Support (macOS & Linux)
We use `chezmoi` templates to handle differences between operating systems.

### OS detection
The file `.chezmoi.toml.tmpl` automatically detects your OS and makes an `osid` variable available in all templates.

### Using OS-specific logic
In any managed file, you can use logic like this:
```bash
{{ if eq .osid "darwin" -}}
# macOS specific settings
alias ls='ls -G'
{{ else if eq .osid "linux" -}}
# Linux specific settings
alias ls='ls --color=auto'
{{ end -}}
```
# yk-chezmoi
