kubeseal --controller-namespace=flux-system --controller-name=sealed-secrets --fetch-cert >| cert.pem
kubectl -n cert-manager create secret generic cloudflare-lets-encrypt --from-env-file=cloudflare-lets-encrypt --dry-run=client -o yaml > secret.yaml
kubeseal --format=yaml --cert=cert.pem < secret.yaml >| sealed-secret.yaml
