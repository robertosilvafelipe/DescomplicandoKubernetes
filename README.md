# 🚀 Descomplicando Kubernetes — Cluster local com kind

Este tutorial tem como objetivo ensinar, passo a passo e de forma extremamente didática, como criar um cluster Kubernetes local utilizando o kind (Kubernetes IN Docker), além de apresentar os comandos básicos do kind e do kubectl.

Ao final, há um tópico extra explicando como ativar o autocomplete do kubectl, um recurso essencial para produtividade no dia a dia.

Este material é ideal para:
- Iniciantes em Kubernetes
- Estudantes
- Profissionais de DevOps
- Ambientes de laboratório e estudo

---

## 🧠 O que é o kind?

O kind (Kubernetes IN Docker) é uma ferramenta que permite criar clusters Kubernetes locais utilizando containers Docker como nós do cluster.

Ele é amplamente utilizado para:
- Estudos
- Testes
- Laboratórios locais
- Simulações de ambientes Kubernetes

Site oficial do kind:  
https://kind.sigs.k8s.io/

---

## 📌 Pré-requisitos

Antes de iniciar este tutorial, você precisa ter os seguintes componentes instalados em sua máquina:

- Docker  
  https://docs.docker.com/get-docker/

- kubectl  
  https://kubernetes.io/docs/tasks/tools/

- kind  
  https://kind.sigs.k8s.io/docs/user/quick-start/

Este tutorial foi pensado para Linux e WSL, mas também funciona em macOS.

---

## 🔧 Instalando o kind no Linux

### Baixando o binário do kind

```bash
curl -Lo ./kind https://kind.sigs.k8s.io/dl/v0.23.0/kind-linux-amd64
```

### Tornando o binário executável

```bash
chmod +x ./kind
```

### Movendo o binário para um diretório do PATH

```bash
sudo mv ./kind /usr/local/bin/kind
```

### Validando a instalação

```bash
kind version
```

---

## 🏗️ Criando um cluster Kubernetes com kind

```bash
kind create cluster
```

```bash
kind create cluster --name meu-cluster
```

```bash
kind get clusters
```

```bash
kind delete cluster --name meu-cluster
```

---

## 🔍 Verificando o cluster com kubectl

```bash
kubectl cluster-info
```

```bash
kubectl get nodes
```

---

## 📦 Comandos básicos do kubectl

```bash
kubectl get pods
```

```bash
kubectl get pods -A
```

```bash
kubectl get svc
```

```bash
kubectl create deployment nginx --image=nginx
```

```bash
kubectl get deployments
```

```bash
kubectl expose deployment nginx --type=NodePort --port=80
```

```bash
kubectl describe pod NOME_DO_POD
```

```bash
kubectl logs NOME_DO_POD
```

```bash
kubectl delete deployment nginx
kubectl delete svc nginx
```

---

## ⚡ TÓPICO EXTRA — Ativando o autocomplete do kubectl

```bash
sudo apt update
sudo apt install -y bash-completion
```

```bash
kubectl completion bash | sudo tee /etc/bash_completion.d/kubectl > /dev/null
```

```bash
echo 'source <(kubectl completion bash)' >> ~/.bashrc
source ~/.bashrc
```

Teste:

```bash
kubectl get po<TAB>
```

---

## 📚 Links de Referência Oficiais

- Kubernetes Docs  
  https://kubernetes.io/docs/

- kubectl Cheat Sheet  
  https://kubernetes.io/docs/reference/kubectl/cheatsheet/

- kind Docs  
  https://kind.sigs.k8s.io/docs/

- Docker Docs  
  https://docs.docker.com/
