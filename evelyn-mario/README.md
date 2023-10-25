# evelyn-mario

## Deploying

evelyn-mario is deployed using the `bitnami/ghost` helm chart. The source can be found here: <https://github.com/bitnami/charts/tree/master/bitnami/ghost/#installing-the-chart>

### Install

```bash
helm install ghost bitnami/ghost --namespace evelyn-mario -f values.yaml --version 12.0.0
```

### Upgrade

Update the `values.yaml` and then trigger helm:

```bash
export GHOST_HOST=$(kubectl get ingress --namespace evelyn-mario ghost --template "{{ range (index .status.loadBalancer.ingress 0) }}{{ . }}{{ end }}")
export GHOST_PASSWORD=$(kubectl get secret --namespace evelyn-mario custom-ghost -o jsonpath="{.data.ghost-password}" | base64 --decode)

helm upgrade -n evelyn-mario ghost bitnami/ghost -f values.yaml --set ghostPassword=$GHOST_PASSWORD --set ghostHost=$GHOST_HOST --version 19.1.67
```

## Secrets

```bash
kubectl -n evelyn-mario create secret generic custom-ghost --from-file=ghost-password=ghost-password.secret
```
