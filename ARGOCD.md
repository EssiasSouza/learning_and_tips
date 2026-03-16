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
19. Creating a portforward
```
kubectl port-forward svc/argocd-server -n argocd 8080:443
kubectl port-forward svc/argocd-server -n argocd 8080:443 &
kubectl port-forward svc/argocd-server -n argocd 8080:443 --address 0.0.0.0
```
20. Getting secret to discover the ArgoCD password
```
kubectl get -n argocd
kubectl get -n argocd secrets argocd-initial-admin-secret
kubectl get -n argocd secrets argocd-initial-admin-secret -o json
```
21. Copy value of "password":
22. Run echo to see the password
```
echo <copied_password_value> | base64 -d
```
Simplfiying steps 20, 21 and 22
```
kubectl get -n argocd secrets argocd-initial-admin-secret -o json \
| jq -r '.data.password' \
| base64 -d
```
or...
```
kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d
```
23. Logging on the CLI
```
argocd login localhost:8080 \
--username admin \
--password <ARGOCD PASSWORD> \
--insecure
```
24. Checking if login is ok.
```
argocd version
```
25. Listing configured clusters on ArgoCD
```
argocd cluster list
```
---
### CREATING A SSH PAIR OF KEYS
```
ssh-keygen -t rsa -b 4096 -f ~/.ssh/argocd_rsa
```
1. Edit .bashrc adding content below.

```
eval "$(ssh-agent -s)"
source .bashrc
```

2. Adding this key to the agent
```
ssh-add ~/.ssh/argocd_rsa
```
3. Copy your Public Key to past on your GitHub
   - Enter your GitHub Account
   - User Settings
   - SSH and GPG keys
   - New SSH Keys
```
cat .ssh/argocd_rsa.pub ssh-rsa Public Key
```
4. Test your connection on GitHub
```
ssh -T git@github.com
```
5. Create locally a new branch 
```
git checkout -b argocd
```
6. Creating needed files
```
mkdir -p k8s-manifests && touch k8s-manifests/{backend-deployment.yaml,backend-service.yaml,frontend-deployment.yaml,frontend-service.yaml,ingress.yaml}
```
- backend-deployment.yaml
```
apiVersion: apps/v1
kind: Deployment
metadata:
  name: backend
  namespace: default
spec:
  replicas: 1
  selector:
    matchLabels:
      app: backend
  template:
    metadata:
      labels:
        app: backend
    spec:
      containers:
      - name: backend
        image: rafaelvzago/fortune-backend-rust:1.0
        ports:
        - containerPort: 8080
        env:
        - name: API_URL
          value: "https://api.adviceslip.com/advice"
```
- backend-service.yaml
```
apiVersion: v1
kind: Service
metadata:
  name: backend
  namespace: default
spec:
  selector:
    app: backend
  ports:
    - protocol: TCP
      port: 8080
      targetPort: 8080
  type: ClusterIP
```
- frontend-deployment.yaml
```
apiVersion: apps/v1
kind: Deployment
metadata:
  name: frontend
  namespace: default
spec:
  replicas: 1
  selector:
    matchLabels:
      app: frontend
  template:
    metadata:
      labels:
        app: frontend
    spec:
      containers:
      - name: frontend
        image: rafaelvzago/fortune-frontend:1.0
        ports:
        - containerPort: 80
```
- frontend-service.yaml
```
apiVersion: v1
kind: Service
metadata:
  name: frontend
  namespace: default
spec:
  selector:
    app: frontend
  ports:
    - protocol: TCP
      port: 80
      targetPort: 80
  type: ClusterIP
```
- ingress.yaml
```
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  name: fortune-cookie-ingress
  namespace: default
  annotations:
    nginx.ingress.kubernetes.io/rewrite-target: /
spec:
  rules:
  - host: fortune-cookie.local
    http:
      paths:
      - path: /
        pathType: Prefix
        backend:
          service:
            name: frontend
            port:
              number: 80
```

```
```



```
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


