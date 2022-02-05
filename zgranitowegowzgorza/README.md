# zgranitowegowzgorza

## Deploying

zgranitowegowzgorza is deployed using the `bitnami/ghost` helm chart. The source can be found here: https://github.com/bitnami/charts/tree/master/bitnami/ghost/#installing-the-chart

### Install

```
helm install ghost bitnami/ghost --namespace zgranitowegowzgorza -f values.yaml --version 10.1.19
```

### Upgrade

Update the `values.yaml` and then trigger helm:

```
export MARIADB_ROOT_PASSWORD=$(kubectl get secret --namespace zgranitowegowzgorza ghost-mariadb -o jsonpath="{.data.mariadb-root-password}" | base64 --decode)
export MARIADB_PASSWORD=$(kubectl get secret --namespace zgranitowegowzgorza ghost-mariadb -o jsonpath="{.data.mariadb-password}" | base64 --decode)
helm upgrade ghost bitnami/ghost --namespace zgranitowegowzgorza -f values.yaml --set mariadb.rootUser.password=$MARIADB_ROOT_PASSWORD --set mariadb.db.password=$MARIADB_PASSWORD --version 10.1.19 
```

## Secrets

```
kubectl -n zgranitowegowzgorza create secret generic custom-ghost --from-file=ghost-password=ghost-password.secret
```
