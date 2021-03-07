## Helm Charts for kubeapp
https://github.com/kubeapps/kubeapps/blob/master/chart/kubeapps/README.md

```
kubectl create namespace kubeapps
helm install kubeapps --namespace kubeapps bitnami/kubeapps -f ./kubeapp.yaml
kubectl create --namespace default serviceaccount kubeapps-operator
kubectl create clusterrolebinding kubeapps-operator --clusterrole=cluster-admin --serviceaccount=default:kubeapps-operator
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

## reference
[Your Application Dashboard for Kubernetes](https://kubeapps.com/)
[getting-started](https://github.com/kubeapps/kubeapps/blob/master/docs/user/getting-started.md)
