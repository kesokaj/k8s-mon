````
## Add helm repo
helm repo add prometheus-community https://prometheus-community.github.io/helm-charts

## Install
helm install prom prometheus-community/prometheus -n monitoring -f values

## Upgrade
helm repo update
helm upgrade --install prom prometheus-community/prometheus -n monitoring -f values
````
