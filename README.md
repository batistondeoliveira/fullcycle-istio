# fullcycle-istio

Minha Documentação = https://docs.google.com/document/d/1kvX-T4wZ61krd7m-GE5XgALNGhL2VK7kp33DuP-pylI/edit

Código Fonte Wesley = https://github.com/devfullcycle/fc-istio

k3d => substitui o kind que vimos no módulo kubernetes

Opções para trabalhar com kubernetes local:

* minikube
* kind
* k3d
* micro k8s

1. Instalação do k3d
https://k3d.io

a) Criar Cluster
k3d cluster create -p "8000:30000@loadbalancer" --agents 2 onde 2 é a quantidade de nodes.

OBSERVAÇÃO: A partir da porta 30000 até a 32000 e alguma coisa, nós temos a região do node ports.

2. Instalação do Istio
https://istio.io

a) Baixe com curl -L https://istio.io/downloadIstio | sh -
b) Mova a pasta gerada para onde quiser no seu computador (pasta opt por exemplo)

istioctl install (instala o core default vide https://istio.io/latest/docs/setup/additional-setup/config-profiles/)

3. Configurando o Sidecar proxy
kubectl label namespace default istio-injection=enabled