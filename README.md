# Kind

__O kind é uma ferramenta para executar localmente um cluster kubernetes usando o docker. Os comando do kind ficam dentro do arquivo kind, por isso é necessário primeiro o path depois os comandos que deseja.__

- Instalando o docker e dando a permisão de sudo para o usuário.
        
        sudo apt install docker-ce
        sudo curl -L https://get.docker.com/ | bash
        sudo usermod -aG docker $USER

- Baixando o kind e instalando.

        curl -Lo ./kind https://kind.sigs.k8s.io/dl/v0.8.1/kind-linux-amd64
        sudo chmod +x ./kind && sudo mv ./kind /usr/local/bin/

- Criando um cluster

        ./kind create cluster --nome clustername
        ./run/kind get clusters


# Helm

__É bem parecido com um instalador de pacotes, porém ele foca na instalação de softwares de maneira rápida e facil.__

- Como instalar

        curl https://baltocdn.com/helm/signing.asc | sudo apt-key add -
        sudo apt-get install apt-transport-https --yes
        echo "deb https://baltocdn.com/helm/stable/debian/ all main" | sudo tee /etc/apt/sources.list.d/helm-stable-debian.list
        sudo apt-get update
        sudo apt-get install helm
        

# Kubernetes

__Um orquestrador de containers. É uma uma plataforma de código aberto usada para orquestrar e gerenciar clusters de contêineres, eliminando a maior parte dos processos manuais necessários para implantar e escalar os aplicativos em contêineres.__

# Kubectl

__Linha de comando para interação com o kubernetes.__

- Instalando o kubectl

        curl -LO https://storage.googleapis.com/kubernetes-release/release/` curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt`/bin/linux/amd64/kubectl
        chmod +x kubectl && sudo mv kubectl /usr/local/bin/
        kubectl version --client
        kubectl get nodes


## Recusos
__Pod__
- É onde você pode guardar containers.


__Statefulset__
- Manter o estado de aplicativos além do ciclo de vida um pod individual, como o armazenamento

__Deployment__
- Representa uma serie de pods identicos com identidades unicas, um deployment roda multiplas replicas de uma aplicação e automaticamente replica uma instancia caso uma dessas replicas caia.

__Service__
- Um serviço permite que você acesse um grupo de replicas pods dinamicamente.

__namespace__
- Kubernetes suporta clusters virtuais multiplos apoiado pelo mesmo cluster fisico. Esses clusters virtuais são chamados de namespaces.

## Comands

__apply__
- Aplica ou da update em recursos de um arquivo ou stdin.

__get__
- Utilizado para listar um ou mais recursos.

__delete__
- Excluir recursos de um arquivo, stdin ou especificando seletores de rótulo, nomes, seletores de recursos ou recursos.


# Port-forward

__Foi aplicado, e o nifi rodou normalmente no localhost. Serve para rodar no localhost qualquer serviço que esteja rodando já em um cluster. Literalmente joga o nifi do cluster para o localhost.__

Exemplo do comando para rodar o nifi na porta 8080 direto no localhost. 
- pods: my-release-nifi-0
- namespace: mundodocker

        kubectl port-forward my-release-nifi-0 8080:8080 -n mundodocker


## Bibliografia helm

- https://medium.com/@maths.nunes/o-que-%C3%A9-o-helm-e-porque-voc%C3%AA-deve-us%C3%A1-lo-508b7350dcd
- https://github.com/cetic/helm-nifi


## Bibliografia kubectl & kubernetes

- [O que é o kubernetes e a sua importância](https://www.profissionaisti.com.br/o-que-e-o-kubernetes-e-sua-importancia/)
- https://medium.com/pixelpoint/kubernetes-port-forwarding-simple-like-never-before-20a8ab16370f
- https://kubernetes.io/docs/concepts/workloads/controllers/statefulset/
- https://docs.microsoft.com/pt-br/azure/aks/concepts-clusters-workloads
- https://kubernetes.io/docs/reference/kubectl/overview/
- https://kubernetes.io/docs/tasks/tools/install-kubectl/

## Bibliografia port-forward

- https://medium.com/pixelpoint/kubernetes-port-forwarding-simple-like-never-before-20a8ab16370f
- https://github.com/AlexsJones/kubernetes-nifi-cluster

