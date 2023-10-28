```bash
kubeseal --controller-namespace=flux-system --controller-name=sealed-secrets --fetch-cert >| cert.pem
kubectl -n flux-system create secret generic netbox-basic-auth --from-file=auth --dry-run=client -o yaml > secret.yaml
kubeseal --format=yaml --cert=cert.pem < secret.yaml >| sealed-secret.yaml

kubeseal --controller-namespace=flux-system --controller-name=sealed-secrets --fetch-cert >| cert-postgres.pem
kubectl -n flux-system create secret generic netbox-postgres-secret-netbox --from-env-file=secret-values-postgres --dry-run=client -o yaml > secret-postgres.yaml
kubeseal --format=yaml --cert=cert-postgres.pem < secret-postgres.yaml >| sealed-secret-postgres.yaml
```
