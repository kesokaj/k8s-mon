# Prerequisite
````
* A real terminal, MAC or Linux. It works on Windows aswell.
* Helm
* Kubectl and a valid kubeconfig file
````

## If you don't have helm installed.
````
curl https://baltocdn.com/helm/signing.asc | sudo apt-key add -
sudo apt-get install apt-transport-https --yes
echo "deb https://baltocdn.com/helm/stable/debian/ all main" | sudo tee /etc/apt/sources.list.d/helm-stable-debian.list
sudo apt-get update
sudo apt-get install helm
````

````
## Setup repo
helm repo add grafana https://grafana.github.io/helm-charts
helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
helm repo update

## Create namespace
kubectl create ns monitoring

## Install
helm install loki grafana/loki -n monitoring -f ./loki/values.yaml
helm install promtail grafana/promtail -n monitoring -f ./promtail/values.yaml
helm install prometheus prometheus-community/prometheus -n monitoring -f ./prometheus/values.yaml
helm install grafana grafana/grafana -n monitoring -f ./grafana/values.yaml

## Setup ingress (edit host in file to match your own)
kubectl apply -f ingress.yaml (or ingressroute.yaml for traefik)

````
