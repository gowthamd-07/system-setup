# DevOps System Setup

This directory contains scripts, configurations, and documentation for setting up a comprehensive DevOps development environment with Kubernetes tooling, shell enhancements, and productivity utilities.

## 📁 Contents

### Scripts

- **`k8s-alias.sh`** - Comprehensive Kubernetes aliases and interactive functions
  - Auto-downloads `kubectl-aliases` and `kubech`
  - Provides colored kubectl output via `kubecolor`
  - Interactive functions for pod exec, secret decoding, deployment management, and more
  - See [k8s-alias-cheatsheet.md](./k8s-alias-cheatsheet.md) for full documentation

- **`mac-setup.sh`** - macOS keyboard settings optimization
  - Faster key repeat rate for improved typing experience
  - Run once to apply system-wide settings

### Configuration Files

- **`starship.toml`** - Starship prompt configuration
  - Beautiful, cross-shell prompt with Kubernetes context display
  - Shows AWS profile, GCP project, Azure subscription, Docker context
  - Displays Git status, Terraform workspace, and language versions
  - Uses Catppuccin Mocha color palette

### Documentation

- **`setup.txt`** - Complete installation guide for all DevOps tools
  - Installation instructions for Kubernetes tools (kubectl, kubecolor, kubectx, etc.)
  - Cloud provider CLIs (AWS, Azure, GCP)
  - Container tools (Docker, Helm, Kind)
  - Service mesh tools (Istio, ArgoCD)
  - Development tools (Go, Python, Java, Node.js, Terraform)
  - Recommended installation order and verification checklist

- **`k8s-alias-cheatsheet.md`** - Quick reference for custom aliases and functions
  - Documents all commands defined in `k8s-alias.sh`
  - Interactive functions, filtering commands, debugging tools
  - See this file for detailed usage examples

- **`kubectl-aliases-cheatsheet.md`** - Reference for kubectl-aliases library
  - Complete documentation of the [ahmetb/kubectl-aliases](https://github.com/ahmetb/kubectl-aliases) library
  - Naming conventions, resource-specific aliases, output formats
  - Hundreds of pre-defined shortcuts

## 🚀 Quick Start

### 1. Install Prerequisites

Install core tools using Homebrew (macOS) or your package manager:

```bash
# Core Kubernetes tools
brew install kubectl kubecolor kubectx fzf jq yq stern

# Optional but recommended
brew install kubectl-neat  # or: kubectl krew install neat
```

### 2. Setup Kubernetes Aliases

Add the aliases script to your shell configuration:

**For Zsh:**
```bash
echo 'source ~/Documents/Personal/DevOps/system-setup/k8s-alias.sh' >> ~/.zshrc
source ~/.zshrc
```

**For Bash:**
```bash
echo 'source ~/Documents/Personal/DevOps/system-setup/k8s-alias.sh' >> ~/.bashrc
source ~/.bashrc
```

### 3. Configure Starship Prompt

Install Starship and copy the configuration:

```bash
# Install Starship
brew install starship

# Copy configuration
mkdir -p ~/.config
cp ~/Documents/Personal/DevOps/system-setup/starship.toml ~/.config/starship.toml

# Add to shell config
echo 'eval "$(starship init zsh)"' >> ~/.zshrc  # or .bashrc
source ~/.zshrc
```

### 4. Apply macOS Settings (macOS only)

```bash
bash ~/Documents/Personal/DevOps/system-setup/mac-setup.sh
```

## 📚 Key Features

### Interactive Kubernetes Operations

- **`kei`** - Interactive pod exec (select pod via fzf, auto-detects shell)
- **`ksd`** - Interactive secret decoder (multi-select, decodes base64)
- **`kdr`** - Interactive deployment restart (multi-select)
- **`kdy`** - Download deployment YAML interactively
- **`ky <resource>`** - Download any resource YAML interactively
- **`kc`** - Interactive context switcher
- **`x`** - Quick context switcher using kubech

### Quick Resource Views

- **`xp [pattern]`** - Get all pods (optionally filtered)
- **`xd [pattern]`** - Get all deployments
- **`xs [pattern]`** - Get all statefulsets
- **`xsv [pattern]`** - Get all services
- **`xi [pattern]`** - Get all ingresses
- **`xc [pattern]`** - Get all configmaps
- **`ff <pattern>`** - Find across deployments/statefulsets/pods

### Enhanced Logging

- **`l <pod>`** - Tail logs with stern (excludes istio-proxy/istio-init)
- **`ln <namespace> <pod>`** - Tail logs with namespace

### Debugging Tools

- **`kdebug`** - Start debug pod with troubleshooting tools
- **`kping <service:port>`** - Ping a service
- **`kger <pod>`** - Get events for a pod

## 🔧 Dependencies

The scripts require the following tools (see `setup.txt` for installation):

### Required
- `kubectl` - Kubernetes CLI
- `kubecolor` - Colored kubectl output
- `fzf` - Fuzzy finder for interactive selection
- `jq` - JSON processor
- `yq` - YAML processor
- `kubectx` / `kubens` - Context and namespace switching

### Optional but Recommended
- `kubectl-neat` - Clean YAML output
- `stern` - Multi-pod log tailing
- `kubectl-aliases` - Auto-downloaded by script
- `kubech` - Auto-downloaded by script

## 📖 Documentation

- **[k8s-alias-cheatsheet.md](./k8s-alias-cheatsheet.md)** - Complete reference for custom aliases
- **[kubectl-aliases-cheatsheet.md](./kubectl-aliases-cheatsheet.md)** - Reference for kubectl-aliases library
- **[setup.txt](./setup.txt)** - Comprehensive installation guide

## 🎨 Starship Prompt Features

The Starship configuration displays:

- **Directory** - Current working directory (truncated to repo root)
- **Git** - Branch name and status indicators
- **Cloud Providers** - AWS profile, GCP project, Azure subscription
- **Kubernetes** - Current context and namespace
- **Docker** - Active Docker context
- **Languages** - Go, Python, Java, Node.js versions
- **Terraform** - Terraform version
- **Time** - Current time (HH:MM format)
- **Status** - Command exit status (on error)

## 💡 Usage Tips

1. **Multi-select in fzf**: Use `Tab` to select multiple items in interactive commands
2. **Pattern filtering**: Most `x*` commands support optional grep patterns
3. **Command echoing**: kubectl wrapper prints commands to stderr for transparency
4. **Color output**: All kubectl commands use `kubecolor` for better readability
5. **Namespace context**: Set default namespace with `kn <namespace>` or use `-n` flag

## 🔗 External Resources

- [kubectl-aliases](https://github.com/ahmetb/kubectl-aliases) - Comprehensive kubectl aliases
- [kubectx](https://github.com/ahmetb/kubectx) - Fast context/namespace switching
- [kubech](https://github.com/DevOpsHiveHQ/kubech) - Per-shell context management
- [kubecolor](https://github.com/hidetatz/kubecolor) - Colored kubectl output
- [stern](https://github.com/stern/stern) - Multi-pod log tailing
- [Starship](https://starship.rs) - Cross-shell prompt

## 🐛 Troubleshooting

### kubectl-ctx/kubens not found
```bash
brew install kubectx
```

### fzf not working
```bash
$(brew --prefix)/opt/fzf/install
```

### kubectl-neat not found
```bash
brew install kubectl-neat
# or
kubectl krew install neat
```

### Shell functions not available
```bash
source ~/Documents/Personal/DevOps/system-setup/k8s-alias.sh
# Then add to your ~/.zshrc or ~/.bashrc
```

## 📝 Notes

- The `k8s-alias.sh` script automatically downloads `kubectl-aliases` and `kubech` if they don't exist
- All kubectl commands are wrapped to use `kubecolor` for colored output
- The script is designed for bash/zsh compatibility
- macOS keyboard settings require admin privileges (run `mac-setup.sh` once)

---

**Last Updated**: 2024

