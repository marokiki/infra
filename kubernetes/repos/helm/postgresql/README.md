```bash
kubeseal --controller-namespace=flux-system --controller-name=sealed-secrets --fetch-cert >| cert.pem
kubectl -n flux-system create secret generic postgres-secret --from-file=secrets-values --dry-run=client -o yaml > secret.yaml
kubeseal --format=yaml --cert=cert.pem < secret.yaml >| sealed-secret.yaml
```
