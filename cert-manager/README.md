# cert-manager

## install

```bash
helm upgrade --install \
  cert-manager jetstack/cert-manager \
  --namespace cert-manager \
  --create-namespace \
  --version v1.17.1 \
  -f values.yaml
kubectl apply -f clusterissuer.yaml
```
