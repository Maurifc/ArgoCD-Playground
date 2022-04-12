# Kubernetes
This repo holds applications K8s Manifests or Hem Charts

**This is intended to be used on Continuos Delivery POC**

## Useful commands

### ArgoCD

Install ArgoCD on Kubernetes cluster
```bash
kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
```

Install Argo CD CLI on your machine
```bash
curl -sSL -o /usr/local/bin/argocd https://github.com/argoproj/argo-cd/releases/latest/download/argocd-linux-amd64
chmod +x /usr/local/bin/argocd
```

Forward ArgoCD port
```bash
kubectl port-forward svc/argocd-server -n argocd 8080:443
```

Get the Admin password
```bash
kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d; echo
```

Access the UI via browser using `admin` user and `http://localhost:8080/`

## References:
https://argo-cd.readthedocs.io/en/stable/cli_installation/