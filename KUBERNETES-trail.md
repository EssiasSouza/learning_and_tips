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

O Kubernetes é dividido em `node master` e `node worker` (node cluster)

 - **node master** define e mantem o estado desejado do worker e é formado por:
  - kube-apiserver: front-end do plano de controle que processa as solicitações internas e externas
  - kube-schedule: essa é a camada que gerencia a integridade do ambiente derrubando e subindo conatiners.
  - kube-control-manager: esse é um gerenciador que usa vários tipos de controladores para manter o ambiente como você define, fazendo uma avaliação em loop constante buscando diferenças entre o ambiente atual e o que foi definido. Se um pod cair ele logo sobe outro.
  - etcd: é um banco de dados distribuído que armazena configurações de estado do cluster no padrão chave-valor.
 - **node worker** é onde a aplicação será executada e é formado por:
  - pod: representa a menor unidade dos objetos do Kubernetes.
  - Kubelet: é o agente responsável por garantir a execução dos containers dentro de um pod e ele é executado um em cada node.
  - Kube-proxy: é o agente que trabalha na camada de rede decidindo para qual pod ele envia os pacotes de acordo com o destino justamente porque os containers trocam os ips então ele conhece a estrutura.
  - container runtime: é o mecanismo de execução dos nossos containers. Exemplo Conteinerd, Docker ou o Podman.

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
