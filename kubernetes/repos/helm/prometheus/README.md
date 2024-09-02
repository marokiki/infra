kubeseal --controller-namespace=sealed-secrets --controller-name=sealed-secrets --fetch-cert >| cert.pem
kubectl -n monitoring create secret generic alertmanager-secrets --from-env-file=alertmanager-secrets --dry-run=client -o yaml > secret.yaml
kubeseal --format=yaml --cert=cert.pem < secret.yaml >| sealed-secret.yaml

kubeseal --controller-namespace=sealed-secrets --controller-name=sealed-secrets --fetch-cert >| cert.basic.pem
kubectl -n monitoring create secret generic prometheus-basic-auth --from-file=auth --dry-run=client -o yaml > secret.basic.yaml
kubeseal --format=yaml --cert=cert.basic.pem < secret.basic.yaml >| sealed-secret.basic.yaml
