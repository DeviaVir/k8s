# evelyn-mario

## Deploying

evelyn-mario is deployed using the `bitnami/ghost` helm chart. The source can be found here: https://github.com/bitnami/charts/tree/master/bitnami/ghost/#installing-the-chart

### Install

```
helm install ghost bitnami/ghost --namespace evelyn-mario -f values.yaml --version 12.0.0
```

### Upgrade

Update the `values.yaml` and then trigger helm:

```
export GHOST_HOST=$(kubectl get ingress --namespace evelyn-mario ghost --template "{{ range (index .status.loadBalancer.ingress 0) }}{{ . }}{{ end }}")
export GHOST_PASSWORD=$(kubectl get secret --namespace evelyn-mario custom-ghost -o jsonpath="{.data.ghost-password}" | base64 --decode)
export MARIADB_ROOT_PASSWORD=$(kubectl get secret --namespace evelyn-mario ghost-mariadb -o jsonpath="{.data.mariadb-root-password}" | base64 --decode)\n
export MARIADB_PASSWORD=$(kubectl get secret --namespace evelyn-mario ghost-mariadb -o jsonpath="{.data.mariadb-password}" | base64 --decode)\n
export MARIADB_PVC=$(kubectl get pvc --namespace evelyn-mario -l app=mariadb,component=master,release=ghost -o jsonpath="{.items[0].metadata.name}")

helm upgrade -n evelyn-mario ghost bitnami/ghost -f values.yaml --set mariadb.primary.persistence.existingClaim=$MARIADB_PVC --set mariadb.auth.rootPassword=$MARIADB_ROOT_PASSWORD --set mariadb.auth.password=$MARIADB_PASSWORD --set ghostPassword=$GHOST_PASSWORD --set ghostHost=$GHOST_HOST --version 12.0.0
```

## Secrets

```
kubectl -n evelyn-mario create secret generic custom-ghost --from-file=ghost-password=ghost-password.secret
```