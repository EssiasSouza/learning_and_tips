# Main Kubernetes trail for me

- Docker
- Kubernetes básico
- KCNA
- CKAD
- CKA
- CKS
- Helm
- ArgoCD / GitOps
- Service Mesh (Istio)
- Observability (Prometheus/Grafana)

## Installing

KUBECTL

- Create a folder, download kubectl file and put it in the path
```
mkdir c:/softs/kubectl
curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl”
```

MINIKUBE

- Download [https://storage.googleapis.com/minikube/releases/latest/minikube-installer.exe(https://storage.googleapis.com/minikube/releases/latest/minikube-installer.exe)
- Run minikube-installer.exe
- Check if path has `C:\Program Files\Kubernetes\Minikube`

## Resumo das responsabilidades dos componentes que você já estudou

| Componente         | Função                     |
| ------------------ | -------------------------- |
| API Server         | Porta de entrada           |
| Scheduler          | Escolhe o Node             |
| Controller Manager | Mantém estado desejado     |
| kubelet            | Garante containers rodando |
| **kube-proxy**     | Rede e Services            |
| Container Runtime  | Cria containers            |
| Pod                | Agrupa containers          |
| Node               | Máquina                    |
| Cluster            | Conjunto de tudo           |



## Studies notes

Kubernetes uses YAML file to run as manifests. To know more about and how to use see documentation on [https://yaml.org/spec/1.2.2/](https://yaml.org/spec/1.2.2/)

To check if the yaml text is correct or no access [https://www.yamllint.com/](https://www.yamllint.com/)

For know more about certifications see on [https://www.cncf.io/](https://www.cncf.io/)

To see more about the projects that are related with Kubernetes see on [https://landscape.cncf.io/](https://landscape.cncf.io/)

### Kubernetes Foundation Notes

The Kubernetes is divided in `node master` e `node worker` (node cluster)

 - **node master** defines and keep the desired stat from worker and is composed by:
  - kube-apiserver: front-end of the control plane that process the interneal an external requests
  - kube-schedule: Is one layer that manage the environment integrity terminating and runing new containers
  - kube-control-manager: this is a manager that uses several kinds of controller to keep the environment as you define, making a checking-up in a constant loop lookinh for differences betwen the actual environment and what was defined. If a pod is crashed it soon rise other one.
  - etcd: is a distributed database that stores the cluster state configuration in a key-value format.
 - worker node is where the application will run and it is composed of:
  - Pod: represents the smallest unit of Kubernetes objects.
  - Kubelet: is the agent responsible for ensuring that containers are running inside a Pod, and it runs on each node.
  - Kube-proxy: is the agent that operates at the network layer, deciding to which Pod it sends packets according to the destination, mainly because containers change IPs, so it knows the cluster networking structure.
  - Container runtime: is the execution engine for our containers, such as Containerd, Docker, or Podman.

## Kubernetes cluster
```
Kubernetes cluster
│
├── Control plane
│     ├── etcd
│     ├── kube-apiserver
│     ├── kube-scheduler
│     └── kube-controller-manager
│
├── Compute machines
│     ├── kubelet
│     ├── kube-proxy
│     └── Container runtime > Pods > Containers 
```

### Runing tools

 - Deployment: is a creator of replicasets that ensures the pods are created as configured. This is on the strategy level, looking at configuration of your need in your environment
 - Replicaset: is a configuration to run the environment. This is on the quantity level, ensuring the quantity of pods need to be runing.
 - kubelet: is the runner in the last part of structure, in fact running the pods.

### 

### commands

```
minikube start
kubectl cluster info
```

**error hyper-v vs virtual-box**

```
minikube delete
minikube start --driver=hyperv
```
