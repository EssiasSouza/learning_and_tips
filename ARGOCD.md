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
echo $ARGOCD_VERSION
```
7. Downlaoding ArgoCD CLI
```
curl -sSL -o argocd \
https://github.com/argoproj/argo-cd/releases/download/${ARGOCD_VERSION}/argocd-linux-amd64
```
8. Giving executable permission
```
chmod +x argocd
sudo mv argocd /usr/local/bin/argocd
```
9. Create Kube Config
```
export KUBECONFIG=$HOME/.kube/config
mkdir $HOME/.kube
touch $KUBECONFIG
```

10. Installing Podman
```
sudo apt update
sudo apt install podman -y
```

11. Starting Podman socket becaus it is deamonless
```
systemctl --user start podman.socket
```
12. Adding the podman to run as sudo
```
sudo vi /etc/sudoers

# Add a last line this content below.
ubuntu ALL=(ALL) NOPASSWD: /usr/bin/podman
esc > : > x! > enter
```
13. Starting minikube
```
minikube start --driver=podman
minikube status
```
14. Starting a cluster
```
minikube addons enable ingress
kubectl get nodes
kubectl get pods -A
```
15. Addinng auto-complete to kubectl
```
vi .bashrc
echo 'source <(kubectl completion bash)' >>~/.bashrc
echo 'source <(alias k=kubectl)' >>~/.bashrc
echo 'source <(complete -F __start_kubectl k)' >>~/.bashrc
source .bashrc
```
16. Checking Cluster
```
kubectl get nodes
kubectl get namespaces
```
17. Creating argocd namespace
```
kubectl create namespace argocd
```

18. Installing manifesto argocd
```
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
kubectl get pods -n argocd
kubectl get pods -n argocd -w
watch -n 1 kubectl get pods -n argocd
```



```
```



```
```


```
kubectl port-forward svc/argocd-server -n argocd 8080:443
```


```
```


```
```


```
```


```
```

# Solving problems

If there is any error to download images you can follow these steps.

1. Enter into node to test inside.
```
minikube ssh
```
2. Run a test
```
curl https://registry.k8s.io
```
3. If the curl can't access the page try changing /etc/resolv.conf
```
sudo vi /etc/resolv.conf
nameserver 8.8.8.8
nameserver 8.8.1.1
```
4. Restart cluster
```
minikube delete
minikube start --driver=podman
```


