# lordofthecode

## Deploying

lordofthecode is deployed using the `bitnami/ghost` helm chart. The source can be found here: https://github.com/bitnami/charts/tree/master/bitnami/ghost/#installing-the-chart

### Upgrade/Install

Update the `values.yaml` and then trigger helm:

```
helm upgrade --install ghost bitnami/ghost --namespace lordofthecode --create-namespace -f values.yaml --version 19.1.67
```

## Secrets

```
kubectl -n lordofthecode create secret generic custom-ghost --from-file=ghost-password=ghost-password.secret
```
