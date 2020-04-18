# Set up kubernetes monitoring

## `kubectl create namespace monitoring`
## `kubectl config set-context --current --namespace=monitoring`
## `helm repo add stable https://kubernetes-charts.storage.googleapis.com/`
## `helm install prometheus stable/prometheus-operator`

## Create a ingress file

`apiVersion: extensions/v1beta1
kind: Ingress
metadata:
  name: grafana
spec:
  rules:
  - host: <website>
    http:
      paths:
      - backend:
          serviceName: prometheus-grafana
          servicePort: 80`

## `kubectl create -f ingress.yaml`
