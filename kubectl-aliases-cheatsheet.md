# kubectl-aliases Cheatsheet

Complete reference for [ahmetb/kubectl-aliases](https://github.com/ahmetb/kubectl-aliases) - a comprehensive collection of kubectl aliases.

**Source:** https://raw.githubusercontent.com/ahmetb/kubectl-aliases/master/.kubectl_aliases

## Table of Contents
- [Naming Conventions](#naming-conventions)
- [Basic Aliases](#basic-aliases)
- [Action Aliases](#action-aliases)
- [Resource-Specific Aliases](#resource-specific-aliases)
- [Output Format Aliases](#output-format-aliases)
- [Namespace Variants](#namespace-variants)
- [All-Namespaces Variants](#all-namespaces-variants)
- [Watch & Label Combinations](#watch--label-combinations)
- [Quick Reference](#quick-reference)

---

## Naming Conventions

Understanding the alias patterns will help you use them effectively:

| Pattern | Meaning | Example |
|---------|---------|---------|
| `k` | kubectl | `k get pods` |
| `ksys` | kubectl with `--namespace=kube-system` | `ksys get pods` |
| `kg` | kubectl get | `kg pods` |
| `kd` | kubectl describe | `kd pod my-pod` |
| `krm` | kubectl delete | `krm pod my-pod` |
| `ka` | kubectl apply | `ka -f file.yaml` |
| `kex` | kubectl exec | `kex pod my-pod -- bash` |
| `klo` | kubectl logs | `klo pod my-pod` |
| `kp` | kubectl proxy | `kp` |
| `kpf` | kubectl port-forward | `kpf svc/my-svc 8080:80` |
| `krun` | kubectl run (interactive) | `krun my-pod --image=nginx` |
| `po` | pods | `kgpo` = get pods |
| `dep` | deployment | `kgdep` = get deployment |
| `sts` | statefulset | `kgsts` = get statefulset |
| `svc` | service | `kgsvc` = get service |
| `ing` | ingress | `kging` = get ingress |
| `cm` | configmap | `kgcm` = get configmap |
| `sec` | secret | `kgsec` = get secret |
| `no` | nodes | `kgno` = get nodes |
| `ns` | namespaces | `kgns` = get namespaces |
| `oyaml` | output yaml | `kgpooyaml` = get pods -o=yaml |
| `owide` | output wide | `kgpoowide` = get pods -o=wide |
| `ojson` | output json | `kgpoojson` = get pods -o=json |
| `sl` | show-labels | `kgposl` = get pods --show-labels |
| `w` | watch | `kgpow` = get pods --watch |
| `all` | all-namespaces | `kgpoall` = get pods --all-namespaces |
| `n` | with namespace flag | `kgpon` = get pods --namespace |
| `l` | with label selector | `kgpol` = get pods -l |

---

## Basic Aliases

| Alias | Command | Description |
|-------|---------|-------------|
| `k` | `kubectl` | Main kubectl shortcut |
| `ksys` | `kubectl --namespace=kube-system` | kubectl for kube-system namespace |

---

## Action Aliases

### Apply
| Alias | Command | Description |
|-------|---------|-------------|
| `ka` | `kubectl apply --recursive -f` | Apply resources from files/directories |
| `ksysa` | `kubectl --namespace=kube-system apply --recursive -f` | Apply in kube-system |
| `kak` | `kubectl apply -k` | Apply kustomization |

### Kustomize
| Alias | Command | Description |
|-------|---------|-------------|
| `kk` | `kubectl kustomize` | Build kustomization |

### Exec
| Alias | Command | Description |
|-------|---------|-------------|
| `kex` | `kubectl exec -i -t` | Exec into pod (interactive, TTY) |
| `ksysex` | `kubectl --namespace=kube-system exec -i -t` | Exec in kube-system |

### Logs
| Alias | Command | Description |
|-------|---------|-------------|
| `klo` | `kubectl logs -f` | Follow logs |
| `ksyslo` | `kubectl --namespace=kube-system logs -f` | Follow logs in kube-system |
| `klop` | `kubectl logs -f -p` | Follow logs (previous instance) |
| `ksyslop` | `kubectl --namespace=kube-system logs -f -p` | Follow previous logs in kube-system |

### Proxy & Port-Forward
| Alias | Command | Description |
|-------|---------|-------------|
| `kp` | `kubectl proxy` | Start proxy server |
| `kpf` | `kubectl port-forward` | Port forward to resource |

### Run
| Alias | Command | Description |
|-------|---------|-------------|
| `krun` | `kubectl run --rm --restart=Never --image-pull-policy=IfNotPresent -i -t` | Run interactive pod |
| `ksysrun` | `kubectl --namespace=kube-system run --rm --restart=Never --image-pull-policy=IfNotPresent -i -t` | Run in kube-system |

### Generic Actions
| Alias | Command | Description |
|-------|---------|-------------|
| `kg` | `kubectl get` | Get resources |
| `ksysg` | `kubectl --namespace=kube-system get` | Get in kube-system |
| `kd` | `kubectl describe` | Describe resources |
| `ksysd` | `kubectl --namespace=kube-system describe` | Describe in kube-system |
| `krm` | `kubectl delete` | Delete resources |
| `ksysrm` | `kubectl --namespace=kube-system delete` | Delete in kube-system |

---

## Resource-Specific Aliases

### Pods
| Alias | Command | Description |
|-------|---------|-------------|
| `kgpo` | `kubectl get pods` | Get pods |
| `ksysgpo` | `kubectl --namespace=kube-system get pods` | Get pods in kube-system |
| `kdpo` | `kubectl describe pods` | Describe pods |
| `ksysdpo` | `kubectl --namespace=kube-system describe pods` | Describe pods in kube-system |
| `krmpo` | `kubectl delete pods` | Delete pods |
| `ksysrmpo` | `kubectl --namespace=kube-system delete pods` | Delete pods in kube-system |

### Deployments
| Alias | Command | Description |
|-------|---------|-------------|
| `kgdep` | `kubectl get deployment` | Get deployments |
| `ksysgdep` | `kubectl --namespace=kube-system get deployment` | Get deployments in kube-system |
| `kddep` | `kubectl describe deployment` | Describe deployments |
| `ksysddep` | `kubectl --namespace=kube-system describe deployment` | Describe deployments in kube-system |
| `krmdep` | `kubectl delete deployment` | Delete deployments |
| `ksysrmdep` | `kubectl --namespace=kube-system delete deployment` | Delete deployments in kube-system |

### StatefulSets
| Alias | Command | Description |
|-------|---------|-------------|
| `kgsts` | `kubectl get statefulset` | Get statefulsets |
| `ksysgsts` | `kubectl --namespace=kube-system get statefulset` | Get statefulsets in kube-system |
| `kdsts` | `kubectl describe statefulset` | Describe statefulsets |
| `ksysdsts` | `kubectl --namespace=kube-system describe statefulset` | Describe statefulsets in kube-system |
| `krmsts` | `kubectl delete statefulset` | Delete statefulsets |
| `ksysrmsts` | `kubectl --namespace=kube-system delete statefulset` | Delete statefulsets in kube-system |

### Services
| Alias | Command | Description |
|-------|---------|-------------|
| `kgsvc` | `kubectl get service` | Get services |
| `ksysgsvc` | `kubectl --namespace=kube-system get service` | Get services in kube-system |
| `kdsvc` | `kubectl describe service` | Describe services |
| `ksysdsvc` | `kubectl --namespace=kube-system describe service` | Describe services in kube-system |
| `krmsvc` | `kubectl delete service` | Delete services |
| `ksysrmsvc` | `kubectl --namespace=kube-system delete service` | Delete services in kube-system |

### Ingresses
| Alias | Command | Description |
|-------|---------|-------------|
| `kging` | `kubectl get ingress` | Get ingresses |
| `ksysging` | `kubectl --namespace=kube-system get ingress` | Get ingresses in kube-system |
| `kding` | `kubectl describe ingress` | Describe ingresses |
| `ksysding` | `kubectl --namespace=kube-system describe ingress` | Describe ingresses in kube-system |
| `krming` | `kubectl delete ingress` | Delete ingresses |
| `ksysrming` | `kubectl --namespace=kube-system delete ingress` | Delete ingresses in kube-system |

### ConfigMaps
| Alias | Command | Description |
|-------|---------|-------------|
| `kgcm` | `kubectl get configmap` | Get configmaps |
| `ksysgcm` | `kubectl --namespace=kube-system get configmap` | Get configmaps in kube-system |
| `kdcm` | `kubectl describe configmap` | Describe configmaps |
| `ksysdcm` | `kubectl --namespace=kube-system describe configmap` | Describe configmaps in kube-system |
| `krmcm` | `kubectl delete configmap` | Delete configmaps |
| `ksysrmcm` | `kubectl --namespace=kube-system delete configmap` | Delete configmaps in kube-system |

### Secrets
| Alias | Command | Description |
|-------|---------|-------------|
| `kgsec` | `kubectl get secret` | Get secrets |
| `ksysgsec` | `kubectl --namespace=kube-system get secret` | Get secrets in kube-system |
| `kdsec` | `kubectl describe secret` | Describe secrets |
| `ksysdsec` | `kubectl --namespace=kube-system describe secret` | Describe secrets in kube-system |
| `krmsec` | `kubectl delete secret` | Delete secrets |
| `ksysrmsec` | `kubectl --namespace=kube-system delete secret` | Delete secrets in kube-system |

### Nodes
| Alias | Command | Description |
|-------|---------|-------------|
| `kgno` | `kubectl get nodes` | Get nodes |
| `kdno` | `kubectl describe nodes` | Describe nodes |

### Namespaces
| Alias | Command | Description |
|-------|---------|-------------|
| `kgns` | `kubectl get namespaces` | Get namespaces |
| `kdns` | `kubectl describe namespaces` | Describe namespaces |
| `krmns` | `kubectl delete namespaces` | Delete namespaces |

---

## Output Format Aliases

### YAML Output
| Alias | Command | Description |
|-------|---------|-------------|
| `kgoyaml` | `kubectl get -o=yaml` | Get any resource as YAML |
| `ksysgoyaml` | `kubectl --namespace=kube-system get -o=yaml` | Get as YAML in kube-system |
| `kgpooyaml` | `kubectl get pods -o=yaml` | Get pods as YAML |
| `ksysgpooyaml` | `kubectl --namespace=kube-system get pods -o=yaml` | Get pods as YAML in kube-system |
| `kgdepoyaml` | `kubectl get deployment -o=yaml` | Get deployments as YAML |
| `kgstsoyaml` | `kubectl get statefulset -o=yaml` | Get statefulsets as YAML |
| `kgsvcoyaml` | `kubectl get service -o=yaml` | Get services as YAML |
| `kgingoyaml` | `kubectl get ingress -o=yaml` | Get ingresses as YAML |
| `kgcmoyaml` | `kubectl get configmap -o=yaml` | Get configmaps as YAML |
| `kgsecoyaml` | `kubectl get secret -o=yaml` | Get secrets as YAML |
| `kgnooyaml` | `kubectl get nodes -o=yaml` | Get nodes as YAML |
| `kgnsoyaml` | `kubectl get namespaces -o=yaml` | Get namespaces as YAML |

### Wide Output
| Alias | Command | Description |
|-------|---------|-------------|
| `kgowide` | `kubectl get -o=wide` | Get any resource in wide format |
| `ksysgowide` | `kubectl --namespace=kube-system get -o=wide` | Get wide in kube-system |
| `kgpoowide` | `kubectl get pods -o=wide` | Get pods in wide format |
| `kgdepowide` | `kubectl get deployment -o=wide` | Get deployments in wide format |
| `kgstsowide` | `kubectl get statefulset -o=wide` | Get statefulsets in wide format |
| `kgsvcowide` | `kubectl get service -o=wide` | Get services in wide format |
| `kgingowide` | `kubectl get ingress -o=wide` | Get ingresses in wide format |
| `kgcmowide` | `kubectl get configmap -o=wide` | Get configmaps in wide format |
| `kgsecowide` | `kubectl get secret -o=wide` | Get secrets in wide format |
| `kgnoowide` | `kubectl get nodes -o=wide` | Get nodes in wide format |
| `kgnsowide` | `kubectl get namespaces -o=wide` | Get namespaces in wide format |

### JSON Output
| Alias | Command | Description |
|-------|---------|-------------|
| `kgojson` | `kubectl get -o=json` | Get any resource as JSON |
| `ksysgojson` | `kubectl --namespace=kube-system get -o=json` | Get as JSON in kube-system |
| `kgpoojson` | `kubectl get pods -o=json` | Get pods as JSON |
| `kgdepojson` | `kubectl get deployment -o=json` | Get deployments as JSON |
| `kgstsojson` | `kubectl get statefulset -o=json` | Get statefulsets as JSON |
| `kgsvcojson` | `kubectl get service -o=json` | Get services as JSON |
| `kgingojson` | `kubectl get ingress -o=json` | Get ingresses as JSON |
| `kgcmojson` | `kubectl get configmap -o=json` | Get configmaps as JSON |
| `kgsecojson` | `kubectl get secret -o=json` | Get secrets as JSON |
| `kgnoojson` | `kubectl get nodes -o=json` | Get nodes as JSON |
| `kgnsojson` | `kubectl get namespaces -o=json` | Get namespaces as JSON |

---

## All-Namespaces Variants

All these aliases include `--all-namespaces` flag:

| Alias | Command | Description |
|-------|---------|-------------|
| `kgall` | `kubectl get --all-namespaces` | Get all resources across namespaces |
| `kdall` | `kubectl describe --all-namespaces` | Describe all resources |
| `kgpoall` | `kubectl get pods --all-namespaces` | Get all pods |
| `kdpoall` | `kubectl describe pods --all-namespaces` | Describe all pods |
| `kgdepall` | `kubectl get deployment --all-namespaces` | Get all deployments |
| `kddepall` | `kubectl describe deployment --all-namespaces` | Describe all deployments |
| `kgstsall` | `kubectl get statefulset --all-namespaces` | Get all statefulsets |
| `kdstsall` | `kubectl describe statefulset --all-namespaces` | Describe all statefulsets |
| `kgsvcall` | `kubectl get service --all-namespaces` | Get all services |
| `kdsvcall` | `kubectl describe service --all-namespaces` | Describe all services |
| `kgingall` | `kubectl get ingress --all-namespaces` | Get all ingresses |
| `kdingall` | `kubectl describe ingress --all-namespaces` | Describe all ingresses |
| `kgcmall` | `kubectl get configmap --all-namespaces` | Get all configmaps |
| `kdcmall` | `kubectl describe configmap --all-namespaces` | Describe all configmaps |
| `kgsecall` | `kubectl get secret --all-namespaces` | Get all secrets |
| `kdsecall` | `kubectl describe secret --all-namespaces` | Describe all secrets |

---

## Namespace Variants

These aliases use `--namespace` flag (you provide namespace as argument):

### Generic
| Alias | Command | Description |
|-------|---------|-------------|
| `kexn` | `kubectl exec -i -t --namespace` | Exec with namespace |
| `klon` | `kubectl logs -f --namespace` | Logs with namespace |
| `kpfn` | `kubectl port-forward --namespace` | Port-forward with namespace |
| `kgn` | `kubectl get --namespace` | Get with namespace |
| `kdn` | `kubectl describe --namespace` | Describe with namespace |
| `krmn` | `kubectl delete --namespace` | Delete with namespace |

### Resource-Specific with Namespace
| Alias | Command | Description |
|-------|---------|-------------|
| `kgpon` | `kubectl get pods --namespace` | Get pods with namespace |
| `kdpon` | `kubectl describe pods --namespace` | Describe pods with namespace |
| `krmpon` | `kubectl delete pods --namespace` | Delete pods with namespace |
| `kgdepn` | `kubectl get deployment --namespace` | Get deployments with namespace |
| `kddepn` | `kubectl describe deployment --namespace` | Describe deployments with namespace |
| `krmdepn` | `kubectl delete deployment --namespace` | Delete deployments with namespace |
| `kgstsn` | `kubectl get statefulset --namespace` | Get statefulsets with namespace |
| `kdstsn` | `kubectl describe statefulset --namespace` | Describe statefulsets with namespace |
| `krmstsn` | `kubectl delete statefulset --namespace` | Delete statefulsets with namespace |
| `kgsvcn` | `kubectl get service --namespace` | Get services with namespace |
| `kdsvcn` | `kubectl describe service --namespace` | Describe services with namespace |
| `krmsvcn` | `kubectl delete service --namespace` | Delete services with namespace |
| `kgingn` | `kubectl get ingress --namespace` | Get ingresses with namespace |
| `kdingn` | `kubectl describe ingress --namespace` | Describe ingresses with namespace |
| `krmingn` | `kubectl delete ingress --namespace` | Delete ingresses with namespace |
| `kgcmn` | `kubectl get configmap --namespace` | Get configmaps with namespace |
| `kdcmn` | `kubectl describe configmap --namespace` | Describe configmaps with namespace |
| `krmcmn` | `kubectl delete configmap --namespace` | Delete configmaps with namespace |
| `kgsecn` | `kubectl get secret --namespace` | Get secrets with namespace |
| `kdsecn` | `kubectl describe secret --namespace` | Describe secrets with namespace |
| `krmsecn` | `kubectl delete secret --namespace` | Delete secrets with namespace |

### Output Formats with Namespace
| Alias | Command | Description |
|-------|---------|-------------|
| `kgoyamln` | `kubectl get -o=yaml --namespace` | Get YAML with namespace |
| `kgpooyamln` | `kubectl get pods -o=yaml --namespace` | Get pods YAML with namespace |
| `kgdepoyamln` | `kubectl get deployment -o=yaml --namespace` | Get deployment YAML with namespace |
| `kgstsoyamln` | `kubectl get statefulset -o=yaml --namespace` | Get statefulset YAML with namespace |
| `kgsvcoyamln` | `kubectl get service -o=yaml --namespace` | Get service YAML with namespace |
| `kgingoyamln` | `kubectl get ingress -o=yaml --namespace` | Get ingress YAML with namespace |
| `kgcmoyamln` | `kubectl get configmap -o=yaml --namespace` | Get configmap YAML with namespace |
| `kgsecoyamln` | `kubectl get secret -o=yaml --namespace` | Get secret YAML with namespace |
| `kgowiden` | `kubectl get -o=wide --namespace` | Get wide with namespace |
| `kgpoowiden` | `kubectl get pods -o=wide --namespace` | Get pods wide with namespace |
| `kgdepowiden` | `kubectl get deployment -o=wide --namespace` | Get deployment wide with namespace |
| `kgstsowiden` | `kubectl get statefulset -o=wide --namespace` | Get statefulset wide with namespace |
| `kgsvcowiden` | `kubectl get service -o=wide --namespace` | Get service wide with namespace |
| `kgingowiden` | `kubectl get ingress -o=wide --namespace` | Get ingress wide with namespace |
| `kgcmowiden` | `kubectl get configmap -o=wide --namespace` | Get configmap wide with namespace |
| `kgsecowiden` | `kubectl get secret -o=wide --namespace` | Get secret wide with namespace |
| `kgojsonn` | `kubectl get -o=json --namespace` | Get JSON with namespace |
| `kgpoojsonn` | `kubectl get pods -o=json --namespace` | Get pods JSON with namespace |
| `kgdepojsonn` | `kubectl get deployment -o=json --namespace` | Get deployment JSON with namespace |
| `kgstsojsonn` | `kubectl get statefulset -o=json --namespace` | Get statefulset JSON with namespace |
| `kgsvcojsonn` | `kubectl get service -o=json --namespace` | Get service JSON with namespace |
| `kgingojsonn` | `kubectl get ingress -o=json --namespace` | Get ingress JSON with namespace |
| `kgcmojsonn` | `kubectl get configmap -o=json --namespace` | Get configmap JSON with namespace |
| `kgsecojsonn` | `kubectl get secret -o=json --namespace` | Get secret JSON with namespace |

---

## Watch & Label Combinations

### Show Labels
| Alias | Command | Description |
|-------|---------|-------------|
| `kgsln` | `kubectl get --show-labels --namespace` | Get with labels and namespace |
| `kgposln` | `kubectl get pods --show-labels --namespace` | Get pods with labels and namespace |
| `kgdepsln` | `kubectl get deployment --show-labels --namespace` | Get deployments with labels and namespace |
| `kgstssln` | `kubectl get statefulset --show-labels --namespace` | Get statefulsets with labels and namespace |
| `kgsvcsln` | `kubectl get service --show-labels --namespace` | Get services with labels and namespace |
| `kgingsln` | `kubectl get ingress --show-labels --namespace` | Get ingresses with labels and namespace |
| `kgcmsln` | `kubectl get configmap --show-labels --namespace` | Get configmaps with labels and namespace |
| `kgsecsln` | `kubectl get secret --show-labels --namespace` | Get secrets with labels and namespace |

### Watch
| Alias | Command | Description |
|-------|---------|-------------|
| `kgwn` | `kubectl get --watch --namespace` | Watch with namespace |
| `kgpown` | `kubectl get pods --watch --namespace` | Watch pods with namespace |
| `kgdepwn` | `kubectl get deployment --watch --namespace` | Watch deployments with namespace |
| `kgstswn` | `kubectl get statefulset --watch --namespace` | Watch statefulsets with namespace |
| `kgsvcwn` | `kubectl get service --watch --namespace` | Watch services with namespace |
| `kgingwn` | `kubectl get ingress --watch --namespace` | Watch ingresses with namespace |
| `kgcmwn` | `kubectl get configmap --watch --namespace` | Watch configmaps with namespace |
| `kgsecwn` | `kubectl get secret --watch --namespace` | Watch secrets with namespace |

### Wide + Show Labels
| Alias | Command | Description |
|-------|---------|-------------|
| `kgowidesln` | `kubectl get -o=wide --show-labels --namespace` | Wide + labels + namespace |
| `kgpoowidesln` | `kubectl get pods -o=wide --show-labels --namespace` | Pods wide + labels + namespace |
| `kgdepowidesln` | `kubectl get deployment -o=wide --show-labels --namespace` | Deployment wide + labels + namespace |
| `kgstsowidesln` | `kubectl get statefulset -o=wide --show-labels --namespace` | Statefulset wide + labels + namespace |
| `kgsvcowidesln` | `kubectl get service -o=wide --show-labels --namespace` | Service wide + labels + namespace |
| `kgingowidesln` | `kubectl get ingress -o=wide --show-labels --namespace` | Ingress wide + labels + namespace |
| `kgcmowidesln` | `kubectl get configmap -o=wide --show-labels --namespace` | Configmap wide + labels + namespace |
| `kgsecowidesln` | `kubectl get secret -o=wide --show-labels --namespace` | Secret wide + labels + namespace |

### Show Labels + Wide (alternative order)
| Alias | Command | Description |
|-------|---------|-------------|
| `kgslowiden` | `kubectl get --show-labels -o=wide --namespace` | Labels + wide + namespace |
| `kgposlowiden` | `kubectl get pods --show-labels -o=wide --namespace` | Pods labels + wide + namespace |
| `kgdepslowiden` | `kubectl get deployment --show-labels -o=wide --namespace` | Deployment labels + wide + namespace |
| `kgstsslowiden` | `kubectl get statefulset --show-labels -o=wide --namespace` | Statefulset labels + wide + namespace |
| `kgsvcslowiden` | `kubectl get service --show-labels -o=wide --namespace` | Service labels + wide + namespace |
| `kgingslowiden` | `kubectl get ingress --show-labels -o=wide --namespace` | Ingress labels + wide + namespace |
| `kgcmslowiden` | `kubectl get configmap --show-labels -o=wide --namespace` | Configmap labels + wide + namespace |
| `kgsecslowiden` | `kubectl get secret --show-labels -o=wide --namespace` | Secret labels + wide + namespace |

### Show Labels + Watch
| Alias | Command | Description |
|-------|---------|-------------|
| `kgslwn` | `kubectl get --show-labels --watch --namespace` | Labels + watch + namespace |
| `kgposlwn` | `kubectl get pods --show-labels --watch --namespace` | Pods labels + watch + namespace |
| `kgdepslwn` | `kubectl get deployment --show-labels --watch --namespace` | Deployment labels + watch + namespace |
| `kgstsslwn` | `kubectl get statefulset --show-labels --watch --namespace` | Statefulset labels + watch + namespace |
| `kgsvcslwn` | `kubectl get service --show-labels --watch --namespace` | Service labels + watch + namespace |
| `kgingslwn` | `kubectl get ingress --show-labels --watch --namespace` | Ingress labels + watch + namespace |
| `kgcmslwn` | `kubectl get configmap --show-labels --watch --namespace` | Configmap labels + watch + namespace |
| `kgsecslwn` | `kubectl get secret --show-labels --watch --namespace` | Secret labels + watch + namespace |

### Watch + Show Labels
| Alias | Command | Description |
|-------|---------|-------------|
| `kgwsln` | `kubectl get --watch --show-labels --namespace` | Watch + labels + namespace |
| `kgpowsln` | `kubectl get pods --watch --show-labels --namespace` | Pods watch + labels + namespace |
| `kgdepwsln` | `kubectl get deployment --watch --show-labels --namespace` | Deployment watch + labels + namespace |
| `kgstswsln` | `kubectl get statefulset --watch --show-labels --namespace` | Statefulset watch + labels + namespace |
| `kgsvcwsln` | `kubectl get service --watch --show-labels --namespace` | Service watch + labels + namespace |
| `kgingwsln` | `kubectl get ingress --watch --show-labels --namespace` | Ingress watch + labels + namespace |
| `kgcmwsln` | `kubectl get configmap --watch --show-labels --namespace` | Configmap watch + labels + namespace |
| `kgsecwsln` | `kubectl get secret --watch --show-labels --namespace` | Secret watch + labels + namespace |

### Label Selectors
| Alias | Command | Description |
|-------|---------|-------------|
| `kgpol` | `kubectl get pods -l` | Get pods with label selector |
| `ksysgpol` | `kubectl --namespace=kube-system get pods -l` | Get pods with label in kube-system |
| `kgdepl` | `kubectl get deployment -l` | Get deployments with label selector |
| `kgstsl` | `kubectl get statefulset -l` | Get statefulsets with label selector |
| `kgsvcl` | `kubectl get service -l` | Get services with label selector |
| `kgingl` | `kubectl get ingress -l` | Get ingresses with label selector |
| `kgcml` | `kubectl get configmap -l` | Get configmaps with label selector |
| `kgsecl` | `kubectl get secret -l` | Get secrets with label selector |
| `kgnol` | `kubectl get nodes -l` | Get nodes with label selector |
| `kgnsl` | `kubectl get namespaces -l` | Get namespaces with label selector |

### Watch + Show Labels + Label Selector
| Alias | Command | Description |
|-------|---------|-------------|
| `kgpowsll` | `kubectl get pods --watch --show-labels -l` | Watch pods with labels and label selector |
| `ksysgpowsll` | `kubectl --namespace=kube-system get pods --watch --show-labels -l` | Watch pods in kube-system |
| `kgdepwsll` | `kubectl get deployment --watch --show-labels -l` | Watch deployments with labels and selector |
| `kgstswsll` | `kubectl get statefulset --watch --show-labels -l` | Watch statefulsets with labels and selector |
| `kgsvcwsll` | `kubectl get service --watch --show-labels -l` | Watch services with labels and selector |
| `kgingwsll` | `kubectl get ingress --watch --show-labels -l` | Watch ingresses with labels and selector |
| `kgcmwsll` | `kubectl get configmap --watch --show-labels -l` | Watch configmaps with labels and selector |
| `kgsecwsll` | `kubectl get secret --watch --show-labels -l` | Watch secrets with labels and selector |
| `kgnowsll` | `kubectl get nodes --watch --show-labels -l` | Watch nodes with labels and selector |
| `kgnswsll` | `kubectl get namespaces --watch --show-labels -l` | Watch namespaces with labels and selector |

---

## Quick Reference

### Most Common Commands

```
# Basic
k                    # kubectl
ksys                 # kubectl --namespace=kube-system

# Get Resources
kgpo                 # get pods
kgdep                # get deployments
kgsts                # get statefulsets
kgsvc                # get services
kging                # get ingresses
kgcm                 # get configmaps
kgsec                # get secrets
kgno                 # get nodes
kgns                 # get namespaces

# Describe
kdpo                 # describe pods
kddep                # describe deployments
kdsts                # describe statefulsets

# Delete
krmpo                # delete pods
krmdep               # delete deployments
krmsts               # delete statefulsets

# Output Formats
kgpooyaml            # pods as yaml
kgpoowide            # pods in wide format
kgpoojson            # pods as json

# All Namespaces
kgpoall              # get all pods
kgdepall             # get all deployments

# With Namespace
kgpon <ns>           # get pods --namespace <ns>
kexn <ns> <pod>      # exec --namespace <ns> <pod>
klon <ns> <pod>      # logs --namespace <ns> <pod>

# Interactive
kex <pod>            # exec into pod
klo <pod>            # follow logs
krun <name> --image= # run interactive pod

# Proxy & Port-Forward
kp                   # start proxy
kpf svc/my-svc 8080:80  # port-forward

# Apply
ka -f file.yaml      # apply file
kak .                # apply kustomization
```

### Usage Examples

```bash
# Get all pods in current namespace
kgpo

# Get all pods across all namespaces
kgpoall

# Get pods in specific namespace
kgpon production

# Get pods in kube-system
ksysgpo

# Describe a pod
kdpo my-pod

# Get pods as YAML
kgpooyaml my-pod

# Get pods in wide format
kgpoowide

# Watch pods
kgpown production

# Get pods with labels shown
kgposln production

# Get pods with label selector
kgpol app=nginx

# Watch pods with labels
kgpowsln production

# Exec into pod
kex my-pod -- bash

# Follow logs
klo my-pod

# Port forward
kpf svc/my-service 8080:80

# Apply manifest
ka -f deployment.yaml

# Delete pod
krmpo my-pod

# Run interactive pod
krun test --image=nginx -- bash
```

---

## Installation

To use these aliases, add to your shell configuration:

```bash
# Download and source the aliases
curl -fsSL "https://raw.githubusercontent.com/ahmetb/kubectl-aliases/master/.kubectl_aliases" > ~/.kube/aliases.sh
source ~/.kube/aliases.sh

# Or add to your ~/.bashrc or ~/.zshrc
echo 'source ~/.kube/aliases.sh' >> ~/.bashrc
```

---

## Notes

- All aliases are designed to work with standard kubectl syntax
- Namespace variants (with `n` suffix) require you to provide the namespace as an argument
- `ksys` variants automatically use `kube-system` namespace
- Label selectors (with `l` suffix) require you to provide the label selector as an argument
- Watch commands will run continuously until interrupted (Ctrl+C)
- The aliases maintain compatibility with kubectl's standard flags and arguments

---

*Reference: [ahmetb/kubectl-aliases](https://github.com/ahmetb/kubectl-aliases)*

