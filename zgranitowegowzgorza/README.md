# zgranitowegowzgorza

## Deploying

zgranitowegowzgorza is deployed using the `bitnami/ghost` helm chart. The source can be found here: https://github.com/bitnami/charts/tree/master/bitnami/ghost/#installing-the-chart

### Install

```
helm install ghost bitnami/ghost --namespace zgranitowegowzgorza -f values.yaml
```

### Upgrade

Update the `values.yaml` and then trigger helm:

```
helm upgrade ghost bitnami/ghost --namespace zgranitowegowzgorza -f values.yaml
```
