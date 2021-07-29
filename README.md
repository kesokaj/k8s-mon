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

````
