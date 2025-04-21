# ingress-nginx

## install via minikube

```bash
minikube start --ports=80:30080,443:30443
```

## install via helm

```bash
helm upgrade --install ingress-nginx ingress-nginx \
  --repo https://kubernetes.github.io/ingress-nginx \
  --namespace ingress-nginx --create-namespace \
  -f values.yaml
```
