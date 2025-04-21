kubeseal --controller-namespace=sealed-secrets --controller-name=sealed-secrets --fetch-cert >| cert.pem
kubectl -n monitoring create secret generic grafana-secret --from-env-file=grafana-secret --dry-run=client -o yaml > secret.yaml
kubeseal --format=yaml --cert=cert.pem < secret.yaml >| sealed-secret.yaml

