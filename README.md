# 🚀 Descomplicando Kubernetes — Cluster local com kind

Este tutorial tem como objetivo **ensinar, passo a passo**, como **criar um cluster Kubernetes local usando o kind (Kubernetes IN Docker)** e apresentar os **comandos básicos do kind e do kubectl**.

No final, há um **tópico extra** ensinando como ativar o **autocompletion do kubectl**, algo essencial para produtividade no dia a dia.

Este material é ideal para:
- Iniciantes em Kubernetes
- Estudantes
- Profissionais de DevOps
- Ambientes de laboratório e estudo

---

## 🧠 O que é o kind?

O **kind** (*Kubernetes IN Docker*) é uma ferramenta que permite criar **clusters Kubernetes locais**, usando **containers Docker como nós**.

Ele é muito utilizado para:
- Estudos
- Testes
- Laboratórios locais
- Simulações de ambientes Kubernetes

🔗 Site oficial:  
https://kind.sigs.k8s.io/

---

## 📌 Pré-requisitos

Antes de começar, você precisa ter instalado:

- **Docker**
  - https://docs.docker.com/get-docker/
- **kubectl**
  - https://kubernetes.io/docs/tasks/tools/
- **kind**
  - https://kind.sigs.k8s.io/docs/user/quick-start/

> 💡 Este tutorial foi pensado para Linux/WSL, mas funciona também em macOS.

---

## 🔧 Instalando o kind

### Download do binário

```bash
curl -Lo ./kind https://kind.sigs.k8s.io/dl/v0.23.0/kind-linux-amd64
Tornando o binário executável
chmod +x ./kind
Movendo para um diretório do PATH
sudo mv ./kind /usr/local/bin/kind
Validando a instalação
kind version
🏗️ Criando um cluster Kubernetes com kind
Criando um cluster simples
kind create cluster

Esse comando:

Cria um cluster Kubernetes local

Usa Docker como backend

Cria automaticamente o contexto no kubectl

Criando um cluster com nome personalizado
kind create cluster --name meu-cluster

Isso é útil quando você quer trabalhar com mais de um cluster local.

Listando clusters criados
kind get clusters
Deletando um cluster
kind delete cluster --name meu-cluster
🔍 Verificando o cluster com kubectl
Verificando se o cluster está acessível
kubectl cluster-info
Listando os nós do cluster
kubectl get nodes

Saída esperada (exemplo):

NAME                 STATUS   ROLES           AGE   VERSION
kind-control-plane   Ready    control-plane   2m    v1.xx.x
📦 Comandos básicos do kubectl
Listar pods
kubectl get pods

Por padrão, lista os pods do namespace default.

Listar pods de todos os namespaces
kubectl get pods -A
Listar services
kubectl get svc
Criar um deployment de exemplo
kubectl create deployment nginx --image=nginx
Verificar o deployment criado
kubectl get deployments
Expor o deployment como serviço
kubectl expose deployment nginx --type=NodePort --port=80
Descrever um recurso (debug)
kubectl describe pod NOME_DO_POD
Ver logs de um pod
kubectl logs NOME_DO_POD
Remover recursos
kubectl delete deployment nginx
kubectl delete svc nginx
🧭 Trabalhando com contextos
Ver contexto atual
kubectl config current-context
Listar todos os contextos
kubectl config get-contexts
Trocar de contexto
kubectl config use-context kind-meu-cluster
⚡ TÓPICO EXTRA — Ativando o autocomplete do kubectl

O autocomplete ajuda muito no dia a dia, evitando erros de digitação e acelerando comandos.

Instalando o bash-completion
sudo apt update
sudo apt install -y bash-completion
Ativando o autocomplete do kubectl
kubectl completion bash | sudo tee /etc/bash_completion.d/kubectl > /dev/null
Ativando para o usuário atual
echo 'source <(kubectl completion bash)' >> ~/.bashrc

Recarregue o shell:

source ~/.bashrc
Testando o autocomplete

Digite:

kubectl get po<TAB>

O shell completará automaticamente para:

kubectl get pods
📚 Links de Referência Oficiais

Kubernetes Docs
https://kubernetes.io/docs/

kubectl Cheat Sheet
https://kubernetes.io/docs/reference/kubectl/cheatsheet/

kind Documentation
https://kind.sigs.k8s.io/docs/

Docker Documentation
https://docs.docker.com/
