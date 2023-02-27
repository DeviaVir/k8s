# vanleeuwenairconditioning.com

## Secrets

```bash
kubectl -n vanleeuwenairconditioning create secret generic wordpress-secrets \
    --from-file=wordpress-db-password=./database.secret \
    --from-literal=auth_key="XXX" \
    --from-literal=secure_auth_key="XXX" \
    --from-literal=logged_in_key="XXX" \
    --from-literal=nonce_key="XXX" \
    --from-literal=auth_salt="XXX" \
    --from-literal=secure_auth_salt="XXX" \
    --from-literal=logged_in_salt="XXX" \
    --from-literal=nonce_salt="XXX" \
    --from-literal=table_prefix="XXX"
```
