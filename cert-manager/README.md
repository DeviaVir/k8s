# cert-manager

## install

```
helm install \
  cert-manager jetstack/cert-manager \
  --namespace cert-manager \
  --create-namespace \
  --version v1.7.1 \
  -f values.yaml
kubectl apply -f clusterissuer.yaml
```