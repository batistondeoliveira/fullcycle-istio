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

4. Configurando add-ons
* Na documentação do istio, vide View the dashboard, clique no link several (https://istio.io/latest/docs/ops/integrations/) é possível ver que temos diversos add-ons que podemos configurar.

Na explicação do video ao clicar no link several foi redirecionado para um link no github (http://github.com/istio/istio) mas especificamente nesse link que caiu (https://github.com/istio/istio/tree/release-1.9/samples/addons) porem, para a versão do istio que estou utilizando, o certo é esse link (https://github.com/istio/istio/tree/release-1.16/samples/addons)

De posse dos yamls do link acima, ele entrou em um arquivo yaml, clicou na opção Raw e copiou o link e executou o comando

kubectl apply -f https://raw.githubusercontent.com/istio/istio/release-1.16/samples/addons/prometheus.yaml
kubectl apply -f https://raw.githubusercontent.com/istio/istio/release-1.16/samples/addons/kiali.yaml
kubectl apply -f https://raw.githubusercontent.com/istio/istio/release-1.16/samples/addons/jaeger.yaml
kubectl apply -f https://raw.githubusercontent.com/istio/istio/release-1.16/samples/addons/grafana.yaml

* Abrindo o dashboard kiali
istioctl dashboard kiali