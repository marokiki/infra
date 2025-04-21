```bash
kubeseal --controller-namespace=sealed-secrets --controller-name=sealed-secrets --fetch-cert >| cert.pem
kubectl -n longhorn-system create secret generic longhorn-basic-auth --from-file=auth --dry-run=client -o yaml > secret.yaml
kubeseal --format=yaml --cert=cert.pem < secret.yaml >| sealed-secret.yaml
```
