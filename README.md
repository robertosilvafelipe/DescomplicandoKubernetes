# 🚀 Descomplicando Kubernetes — Cluster local com kind

Este tutorial tem como objetivo ensinar, passo a passo e de forma extremamente didática, como criar um cluster Kubernetes local utilizando o kind (Kubernetes IN Docker), além de apresentar os comandos básicos do kind e do kubectl.

Ao final, há um tópico extra explicando como ativar o autocomplete do kubectl, um recurso essencial para produtividade no dia a dia.

---

## 🧠 O que é o kind?

O kind (Kubernetes IN Docker) é uma ferramenta que permite criar clusters Kubernetes locais utilizando containers Docker como nós do cluster.

Site oficial:  
https://kind.sigs.k8s.io/

---

## 📌 Pré-requisitos

- Docker  
  https://docs.docker.com/get-docker/

- kubectl  
  https://kubernetes.io/docs/tasks/tools/

- kind  
  https://kind.sigs.k8s.io/docs/user/quick-start/

---

## 🔧 Instalando o kind

```bash
curl -Lo ./kind https://kind.sigs.k8s.io/dl/v0.23.0/kind-linux-amd64
```
Baixa o binário oficial do kind.

```bash
chmod +x ./kind
```
Torna o binário executável.

```bash
sudo mv ./kind /usr/local/bin/kind
```
Move o binário para um diretório do PATH.

```bash
kind version
```
Verifica se o kind foi instalado corretamente.

---

## 🏗️ Criando um cluster com kind

```bash
kind create cluster
```
Cria um cluster Kubernetes local com configurações padrão.

```bash
kind create cluster --name meu-cluster
```
Cria um cluster com nome personalizado.

```bash
kind get clusters
```
Lista todos os clusters kind existentes.

```bash
kind delete cluster --name meu-cluster
```
Remove o cluster informado.

---

## 🔍 Verificando o cluster

```bash
kubectl cluster-info
```
Mostra informações básicas do cluster.

```bash
kubectl get nodes
```
Lista os nós do cluster Kubernetes.

---

## 📦 Comandos básicos do kubectl

```bash
kubectl get pods
```
Lista os pods do namespace default.

```bash
kubectl get pods -A
```
Lista pods de todos os namespaces.

```bash
kubectl get svc
```
Lista os serviços existentes.

```bash
kubectl get deployments
```
Lista os deployments existentes no cluster.

```bash
kubectl create deployment nginx --image=nginx
```
Cria um deployment chamado nginx usando a imagem nginx.

```bash
kubectl expose deployment nginx --type=NodePort --port 80
```
Expõe o deployment nginx como um serviço do tipo NodePort.

```bash
kubectl describe pod NOME_DO_POD
```
Mostra detalhes completos de um pod (útil para debug).

```bash
kubectl logs NOME_DO_POD
```
Exibe os logs de um pod.

```bash
kubectl delete deployment nginx
```
Remove o deployment nginx.

```bash
kubectl delete svc nginx
```
Remove o serviço nginx.

---

## 🧪 Gerando manifesto com dry-run (pod-template)

```bash
kubectl run meu-nginx --image nginx --port 80 --dry-run=client -o yaml > pod-template.yaml
```
Gera um arquivo YAML de pod sem criar o recurso no cluster, ideal para estudar e versionar manifests.

---

## ⚡ TÓPICO EXTRA — Autocomplete do kubectl

```bash
sudo apt update
sudo apt install -y bash-completion
```
Instala o pacote de autocomplete do bash.

```bash
kubectl completion bash | sudo tee /etc/bash_completion.d/kubectl > /dev/null
```
Habilita o autocomplete do kubectl no sistema.

```bash
echo 'source <(kubectl completion bash)' >> ~/.bashrc
source ~/.bashrc
```
Ativa o autocomplete para o usuário atual.

```bash
kubectl get po<TAB>
```
Exemplo de uso do autocomplete.

---

## 📚 Referências Oficiais

- Kubernetes Docs  
  https://kubernetes.io/docs/

- kubectl Cheat Sheet  
  https://kubernetes.io/docs/reference/kubectl/cheatsheet/

- kind Docs  
  https://kind.sigs.k8s.io/docs/

- Docker Docs  
  https://docs.docker.com/
