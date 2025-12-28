# Kubernetes Aliases Cheatsheet

This cheatsheet documents all commands, aliases, and functions defined in `k8s-alias.sh`.

## Table of Contents
- [Basic Aliases](#basic-aliases)
- [Context & Namespace Management](#context--namespace-management)
- [Resource Inspection](#resource-inspection)
- [Events](#events)
- [Interactive Functions](#interactive-functions)
- [Debugging & Troubleshooting](#debugging--troubleshooting)
- [Resource Management](#resource-management)
- [YAML Operations](#yaml-operations)
- [Filtering & Searching](#filtering--searching)
- [Logging](#logging)

---

## Basic Aliases

| Command | Description | Example |
|---------|-------------|---------|
| `k` | Short alias for `kubectl` | `k get pods` |
| `kn` | Alias for `kubens` (namespace switcher) | `kn default` |
| `kubectl` | Wrapper function that uses `kubecolor` and prints commands (unless `-A` or `-o` flags are used) | `kubectl get pods` |

---

## Context & Namespace Management

| Command | Description | Example |
|---------|-------------|---------|
| `x` | Interactive context switcher using fzf | `x` |
| `kc [context]` | Switch Kubernetes context. If no context provided, shows interactive fzf menu | `kc my-context` or `kc` |
| `kn <namespace>` | Set default namespace for current context | `kn production` |

**Note:** Line 11 and 33 both define `kn` - the second definition (line 33) will override the first.

---

## Resource Inspection

| Command | Description | Example |
|---------|-------------|---------|
| `kgworld` | Get all resources across all namespaces (comprehensive view) | `kgworld` |
| `kgnr` | Display all nodes with their resource requests and limits | `kgnr` |
| `kgpc <pod>` | Get list of containers in a pod | `kgpc my-pod` |

---

## Events

| Command | Description | Example |
|---------|-------------|---------|
| `kgel` | Get events sorted by last timestamp | `kgel` |
| `kgec` | Get events sorted by creation timestamp | `kgec` |
| `kger <pod_name>` | Get events for a specific pod, sorted by last timestamp | `kger my-pod` |

---

## Interactive Functions

### Pod Operations

| Command | Description | Usage |
|---------|-------------|-------|
| `kei` | Interactive exec into a pod. Shows running pods via fzf, then execs into selected pod. Tries bash, then ash, then sh | `kei` |

### Secret Operations

| Command | Description | Usage |
|---------|-------------|-------|
| `ksd` | Interactive secret decoder. Shows all secrets via fzf (multi-select), decodes base64 values using jq | `ksd` |
| `ksdf <pattern>` | Filter secrets by pattern (case-insensitive) | `ksdf database` |

### Deployment Operations

| Command | Description | Usage |
|---------|-------------|-------|
| `kdr` | Interactive deployment restart. Shows all deployments via fzf (multi-select), restarts selected deployments | `kdr` |
| `kdy` | Interactive deployment YAML download. Shows all deployments via fzf (multi-select), saves YAML as `<deployment>_<namespace>.yaml` | `kdy` |

### Generic Resource Operations

| Command | Description | Usage |
|---------|-------------|-------|
| `ky <resource_type> [omit_details]` | Interactive YAML download for any resource type. Shows resources via fzf (multi-select), saves YAML files | `ky deployment`<br>`ky pod yes`<br>`ky connector true` |

**Filename format:**
- With `omit_details` = `true/yes/y`: `<name>.yaml`
- Without `omit_details`: `<namespace><resource_type><name>.yaml`

---

## Debugging & Troubleshooting

| Command | Description | Example |
|---------|-------------|---------|
| `kdebug` | Start a debug pod with troubleshooting tools (swiss-army-knife image) in default namespace | `kdebug` |
| `kping <service:port>` | Ping a service using httping tool | `kping whoami:8080` |

---

## Resource Management

| Command | Description | Example |
|---------|-------------|---------|
| `krmfailed` | Delete all failed pods in current namespace | `krmfailed` |

---

## YAML Operations

| Command | Description | Example |
|---------|-------------|---------|
| `kyaml <resource_type> <name>` | Get resource YAML without forbidden fields (uses kubectl-neat) | `kyaml pod whoami` |

---

## Filtering & Searching

### Quick Resource Views (with grep support)

| Command | Description | Usage |
|---------|-------------|-------|
| `xp [pattern]` | Get all pods across namespaces (optionally filtered by pattern) | `xp`<br>`xp error` |
| `xpc [pattern]` | Get pods filtered by error/fail/exception/crash patterns | `xpc` |
| `xd [pattern]` | Get all deployments across namespaces (optionally filtered) | `xd`<br>`xd api` |
| `xs [pattern]` | Get all statefulsets across namespaces (optionally filtered) | `xs`<br>`xs database` |
| `xsv [pattern]` | Get all services across namespaces (optionally filtered) | `xsv`<br>`xsv web` |
| `xi [pattern]` | Get all ingresses across namespaces (optionally filtered) | `xi`<br>`xi prod` |
| `xc [pattern]` | Get all configmaps across namespaces (optionally filtered) | `xc`<br>`xc config` |

### Multi-Resource Search

| Command | Description | Usage |
|---------|-------------|-------|
| `ff <pattern>` | Find deployments, statefulsets, and pods matching pattern (case-insensitive) | `ff api`<br>`ff database` |

### Helper Function

| Command | Description |
|---------|-------------|
| `kgrep <base_cmd> [pattern]` | Generic grep wrapper. Executes base command and optionally filters by pattern | Internal helper function |

---

## Logging

| Command | Description | Example |
|---------|-------------|---------|
| `l` | Alias for `stern` (log tailing tool). **Note:** Defined twice - second definition excludes istio-proxy and istio-init logs | `l <pod>` |
| `ln` | Stern with istio exclusions and namespace flag | `ln <namespace> <pod>` |

**Note:** Line 190 and 191 both define `l` - the second definition (line 191) will override the first, so `l` will exclude istio-proxy and istio-init logs.

---

## External Dependencies

This script relies on several external tools:

- **kubectl-aliases**: From https://github.com/ahmetb/kubectl-aliases (auto-downloaded to `~/.kube/aliases.sh`)
- **kubech**: From https://github.com/DevOpsHiveHQ/kubech (auto-downloaded to `~/.kube/kubech`)
- **kubecolor**: Used as kubectl wrapper for colored output
- **fzf**: Fuzzy finder for interactive selections
- **yq**: YAML processor for parsing kubeconfig
- **jq**: JSON processor for secret decoding
- **kubectl-neat**: For cleaning YAML output
- **stern**: Multi-pod log tailing tool

---

## Usage Tips

1. **Interactive Commands**: Many commands use `fzf` for interactive selection. Make sure `fzf` is installed.
2. **Multi-select**: Commands like `ksd`, `kdr`, `kdy`, and `ky` support multi-select in fzf (use `Tab` to select multiple items).
3. **Color Output**: The `kubectl` wrapper uses `kubecolor` for better readability.
4. **Command Echoing**: The kubectl wrapper prints commands to stderr (unless `-A` or `-o` flags are used) for transparency.
5. **Namespace Context**: Use `kn <namespace>` to set default namespace, or specify `-n <namespace>` in commands.

---

## Quick Reference Card

```
# Basic
k                   # kubectl shortcut
kn <ns>             # Set namespace

# Context
x                    # Switch context (interactive)
kc [ctx]             # Switch context

# Get Resources
xp [pattern]         # Get pods
xd [pattern]         # Get deployments
xs [pattern]         # Get statefulsets
xsv [pattern]        # Get services
xi [pattern]         # Get ingresses
xc [pattern]         # Get configmaps
ff <pattern>         # Find across deployments/statefulsets/pods

# Events
kgel                 # Events by last timestamp
kgec                 # Events by creation time
kger <pod>           # Events for pod

# Interactive
kei                  # Exec into pod
ksd                  # Decode secrets
ksdf <pattern>       # Filter secrets
kdr                  # Restart deployments
kdy                  # Download deployment YAML
ky <resource> [yes]  # Download any resource YAML

# Debug
kdebug               # Debug pod
kping <svc:port>     # Ping service

# Logs
l <pod>              # Tail logs (excludes istio)
ln <ns> <pod>        # Tail logs with namespace
```

---

*Generated from k8s-alias.sh analysis*

