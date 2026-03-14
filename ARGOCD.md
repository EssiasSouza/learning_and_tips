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
6. Installing ArgoCD CLI
```
ARGOCD_VERION=$(curl --silent "https://github.com/argoproj/argo-cd/releases/latest/" | grep '"tag_name"' | sed -E 's/.*"([^"]+)".*/\1/')
echo $ARGOCD.VERSION
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


###


```

```

---

###


```

```

---
