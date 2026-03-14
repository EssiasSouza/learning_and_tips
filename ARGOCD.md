##Installation and runnig ArgoCD

### Downloading and installing minikube

1. Geting the latest binary `minikube`
```
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
```
2. Installing minikube no path
```
sudo install minikube-linux-amd64 /usr/local/bin/minikube
```
3. Downloading `kubectl`
```
curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
```
4. Giving permissions as executable
```
chmod +x kubectl
```
5. Install kubectl as path
```
sudo mv kubectl /usr/local/bin
```
6. Looking for ArgoCD CLI version
```
ARGOCD_VERSION=$(curl --silent "https://api.github.com/repos/argoproj/argo-cd/releases/latest" | grep '"tag_name"' | sed -E 's/.*"([^"]+)".*/\1/')
echo $ARGOCD.VERSION
```
7. Downlaoding ArgoCD CLI
```
curl -sSL -o /tmp/argocd-${ARGOCD_VERSION} https://github.com/argoproj/argo-d/releases/download/${ARGOCD_VERSION}/argocd-linux-amd64
```
8. Giving executable permission
```
chmod +x /tmp/argocd-${ARGOCD_VERSION}
sudo mv /tmp/argocd-${ARGOCD_VERSION} /usr/local/bin/argocd
```

---


###


```

```

---

###


```

```

---
