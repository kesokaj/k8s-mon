````
## Setup repo
helm repo add grafana https://grafana.github.io/helm-charts
helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
helm repo update

## Install
helm install loki grafana/loki -n monitoring -f ./loki/values.yaml
````
