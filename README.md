# iac-flux-keda
Flux Configuration for Keda

## Developer Guide
To test the changes, ensure that you are on your developer machine and that the context is set correctly to your local instance please amend the following script to use the target branch:

```bash
kubectl config use-context docker-desktop
kubectl create namespace keda
flux create source git keda --url="https://github.com/lsc-sde/iac-flux-keda" --branch=main --namespace=keda
flux create kustomization keda-cluster-config --source="GitRepository/keda" --namespace=keda --path="./clusters/local" --interval=1m --prune=true --health-check-timeout=10m --wait=false
flux create kustomization keda-sources --source="GitRepository/keda" --namespace=keda --path="./sources" --interval=1m --prune=true --health-check-timeout=10m --wait=false
```

This should in turn deploy all of the resulting resources on your local cluster.