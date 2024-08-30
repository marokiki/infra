kubeseal --controller-namespace=sealed-secrets --controller-name=sealed-secrets --fetch-cert >| cert.postgres.pem
kubectl -n docker-registory create secret generic harbor-postgres-secret --from-env-file=postgres-secret --dry-run=client -o yaml > secret.postgres.yaml
kubeseal --format=yaml --cert=cert.postgres.pem < secret.postgres.yaml >| sealed-secrets.postgres.yaml

kubeseal --controller-namespace=sealed-secrets --controller-name=sealed-secrets --fetch-cert >| cert.redis.pem
kubectl -n docker-registory create secret generic harbor-redis-secret --from-env-file=redis-secret --dry-run=client -o yaml > secret.redis.yaml
kubeseal --format=yaml --cert=cert.redis.pem < secret.redis.yaml >| sealed-secrets.redis.yaml
