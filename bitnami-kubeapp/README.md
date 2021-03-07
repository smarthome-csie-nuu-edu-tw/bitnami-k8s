## Helm Charts for kubeapp
https://github.com/kubeapps/kubeapps/blob/master/chart/kubeapps/README.md

```
helm repo add bitnami https://charts.bitnami.com/bitnami
kubectl create namespace kubeapps
helm install kubeapps --namespace kubeapps bitnami/kubeapps
```

## Ans範例
```
helm install kubeapps --namespace kubeapps \
    --set ingress.enabled=true
    --set ingress.hostname=""
    --set ingress.extraHosts[0].name="console.example.com"
    --set ingress.extraHosts[0].path="/catalog"
    bitnami/kubeapps
```
