# databases

## MySQL

```bash
kubectl -n databases create secret generic my-mysql-secret \
  --from-literal=mysql-root-password="$(openssl rand -base64 32)" \
  --from-literal=mysql-password="$(openssl rand -base64 32)" \
  --from-literal=mysql-replication-password="$(openssl rand -base64 32)"
```

```bash
helm -n databases upgrade --install mysql oci://registry-1.docker.io/bitnamicharts/mysql \
    -f mysql.yaml \
    --version 12.3.4
```
