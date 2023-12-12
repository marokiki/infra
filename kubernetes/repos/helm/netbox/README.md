kubeseal --controller-namespace=flux-system --controller-name=sealed-secrets --fetch-cert >| cert.pem
kubectl -n netbox create secret generic netbox-basic-auth --from-file=auth --dry-run=client -o yaml > secret.yaml
kubeseal --format=yaml --cert=cert.pem < secret.yaml >| sealed-secret.yaml

kubeseal --controller-namespace=flux-system --controller-name=sealed-secrets --fetch-cert >| cert.netbox.pem
kubectl -n netbox create secret generic netbox --from-env-file=netbox --dry-run=client -o yaml > secret.netbox.yaml
kubeseal --format=yaml --cert=cert.netbox.pem < secret.netbox.yaml >| sealed-secret.netbox.yaml
