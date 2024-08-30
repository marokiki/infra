htpasswd -c auth <user name>

kubeseal --controller-namespace=sealed-secrets --controller-name=sealed-secrets --fetch-cert >| cert.pem
kubectl -n netbox create secret generic netbox-basic-auth --from-file=auth --dry-run=client -o yaml > secret.yaml
kubeseal --format=yaml --cert=cert.pem < secret.yaml >| sealed-secret.yaml

kubeseal --controller-namespace=sealed-secrets --controller-name=sealed-secrets --fetch-cert >| cert.netbox.pem
kubectl -n netbox create secret generic netbox-secret --from-env-file=netbox-secret --dry-run=client -o yaml > secret.netbox.yaml
kubeseal --format=yaml --cert=cert.netbox.pem < secret.netbox.yaml >| sealed-secret.netbox.yaml

kubeseal --controller-namespace=sealed-secrets --controller-name=sealed-secrets --fetch-cert >| cert.redis.pem
kubectl -n netbox create secret generic redis-secret --from-env-file=redis-secret --dry-run=client -o yaml > secret.redis.yaml
kubeseal --format=yaml --cert=cert.redis.pem < secret.redis.yaml >| sealed-secret.redis.yaml
