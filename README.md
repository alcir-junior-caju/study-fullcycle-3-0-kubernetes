# Curso Full Cycle 3.0 - Módulo Kubernetes

<div>
    <img alt="Criado por Alcir Junior [Caju]" src="https://img.shields.io/badge/criado%20por-Alcir Junior [Caju]-%23f08700">
    <img alt="License" src="https://img.shields.io/badge/license-MIT-%23f08700">
</div>

---

## Descrição

O Curso Full Cycle é uma formação completa para fazer com que pessoas desenvolvedoras sejam capazes de trabalhar em projetos expressivos sendo capazes de desenvolver aplicações de grande porte utilizando de boas práticas de desenvolvimento.

---

## Repositório Pai
https://github.com/alcir-junior-caju/study-full-cycle-3-0

---

## Visualizar o projeto na IDE:

Para quem quiser visualizar o projeto na IDE clique no teclado a tecla `ponto`, esse recurso do GitHub é bem bacana

---

### O que é Kubernetes?

`Kubernetes (K8s)` é um produto Open Source utilizado para automatizar a implantação, o dimensionamento e o gerenciamento de aplicativos em container.
- Veio do Google;
    - Borg;
    - Omega;
    - Kubernetes;

### Pontos importantes
- Kubernetes é disponibilizado através de um conjunto de APIs;
- Normalmente acessamos a API usando a CLI `kubectl`;
- Tudo é baseado em estado. Você configura o estado de cada objeto;
- Kubernetes Master;
    - Kube-apiserver;
    - Kube-controller-manager;
    - Kube-scheduler;
- Outros nodes;
    - Kubelet;
    - Kubeproxy;

### Dinâmica superficial
- Cluster: Conjunto de máquinas (Nodes);
- Cada máquina possui uma quantidade de vCPU e Memória;
- Pods: Unidade que contém os containers provisionados;
- O Pod representa os processos rodando no cluster;
- Deployment;
    - ReplicaSets;
        - B = Backend => 3 réplicas;
        - F = Frontend => 2 réplicas;

### Services
- É uma forma de agregar um conjunto de pods para então implementar políticas de visibilidade;

### Ferramentas
- Kind para criar cluster local;
    - Criar um cluster: `kind create cluster`;
    - Exibir clusters: `kind get clusters`;
    - Deletar clusters: `kind delete clusters kind`;
- Kubectl para se comunicar com o kubernetes;
    - Conectando: `kubectl cluster-info --context kind-kind`;
    - Exibir nodes: `kubectl get nodes`;
    - Exibir pods: `kubectl get pods`;
    - Exibir replicasets: `kubectl get replicasets.apps`;
    - Exibir services: `kubectl get services`;
    - Exibir persistent volume claim: `kubectl get pvc`;
    - Exibir config clusters: `kubectl config get-clusters`;
    - Mudando o contexto: `kubectl config use-context nome-do-cluster`;
    - Aplicando o yaml: `kubectl apply -f caminho-do-yaml`;
    - Aplicando o yaml com watch: `kubectl apply -f caminho-do-yaml && watch -n1 kubectl get pods`;
    - Acessar um POD: `kubectl port-forward pod/nome-do-pod 80:80`;
    - Acessar um Service: `kubectl port-forward svc/nome-do-pod 80:80`;
    - Deletar um POD: `kubectl delete pods nome-do-pod`;
    - Informações do POD: `kubectl describe pod nome-do-pod`;
    - Rollout: `kubectl rollout history deployment nome-do-deployment`;
    - Voltar para ultima versão: `kubectl rollout undo deployment nome-do-deployment`;
    - Voltar para uma revisão: `kubectl rollout undo deployment nome-do-deployment --to-revision=numero-da-revisao`;
    - Proxy Kubernetes: `kubectl proxy --port=numero-da-porta`;
    - Ver consumo do pod: `kubectl top pod nome-do-pod`;
    - Criar um POD executando o FORTIO: `kubectl run -it fortio --rm --image=fortio/fortio -- load -qps 800 -t 120s -c 70 "http://goserver-service/healthz"`;
    - StorageClass: `kubectl get storageclass`;
    - Criar namespace: `kubectl create namespace nome-do-namespace`;
    - Ver configurações: `kubectl config view`;
    - Criando um contexto com namespace: `kubectl config set-context nome-contexto --namespace=nome-namespace --cluster=nome-cluster --user=nome-user`;
    - Usar o contexto: `kubectl config use-context nome-contexto`;
    - Ver o contexto atual: `kubectl config current-context`;
    - Service accounts: `kubectl get serviceaccounts`;

### HPA - Horizontal POD Autoscaler
- Metrics Server;
    - https://github.com/kubernetes-sigs/metrics-server;
    - Para rodar local baixar o arquivo e adicionar `--kubelet-insecure-tls` no args;
    - Aplicar as configurações;
    - Para confirmar se está rodando `kubectl get apiservices`;
- Prometheus;
- Grafana;
- Fortio Ferramenta de Stress (k6 pesquisar depois);
    - https://github.com/fortio/fortio;

### Resources
- requests;
- limits;
- vCPU = 1000m (milicores)

### Ingress
- https://kubernetes.io/docs/concepts/services-networking/ingress/;
