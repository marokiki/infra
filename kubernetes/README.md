# Kubernetes
https://qiita.com/segre5458/items/76f0509ee066b2488eab
# 構成
```bash
NAME         STATUS   ROLES           AGE    VERSION   INTERNAL-IP      EXTERNAL-IP   OS-IMAGE             KERNEL-VERSION      CONTAINER-RUNTIME
kinoko-1     Ready    <none>          119m   v1.28.2   192.168.220.25   <none>        Ubuntu 22.04.3 LTS   5.15.0-87-generic   cri-o://1.27.1
kinoko-2     Ready    <none>          119m   v1.28.2   192.168.220.26   <none>        Ubuntu 22.04.3 LTS   5.15.0-87-generic   cri-o://1.27.1
takenoko-1   Ready    control-plane   129m   v1.28.2   192.168.220.21   <none>        Arch Linux           6.5.7-arch1-1       cri-o://1.28.1
takenoko-2   Ready    <none>          129m   v1.28.2   192.168.220.22   <none>        Arch Linux           6.5.7-arch1-1       cri-o://1.28.1
takenoko-3   Ready    <none>          119m   v1.28.2   192.168.220.23   <none>        Arch Linux           6.5.7-arch1-1       cri-o://1.28.1
takenoko-4   Ready    <none>          119m   v1.28.2   192.168.220.24   <none>        Arch Linux           6.5.7-arch1-1       cri-o://1.28.1
```
# Install
`ansible/roles/k8s`