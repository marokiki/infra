kubeseal --controller-namespace=sealed-secrets --controller-name=sealed-secrets --fetch-cert >| cert.pem
kubectl -n database create secret generic postgres-secret --from-env-file=secret-values --dry-run=client -o yaml > secret.yaml
kubeseal --format=yaml --cert=cert.pem < secret.yaml >| sealed-secret.yaml
