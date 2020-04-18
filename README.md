# Set up kubernetes monitoring #


### Create a namespace
`kubectl create namespace monitoring`


### Jump to the monitoring namespace
`kubectl config set-context --current --namespace=monitoring`

### Add the prometheus-grafana repository

## NOTE:- Grafana pod will be created by the prometheus Operator

`helm repo add stable https://kubernetes-charts.storage.googleapis.com/`
`helm install prometheus stable/prometheus-operator`

## sample ingress file

```apiVersion: extensions/v1beta1
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
          servicePort: 80

## Create the ingress 
`kubectl create -f ingress.yaml`
