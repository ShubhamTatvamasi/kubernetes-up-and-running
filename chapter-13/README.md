### ConfigMap

```bash
kubectl create configmap my-config \
--from-file=my-config.txt \
--from-literal=extra-param=extra-value \
--from-literal=another-param=another-value
```

```bash
curl -o kuard.crt https://storage.googleapis.com/kuar-demo/kuard.crt
curl -o kuard.key https://storage.googleapis.com/kuar-demo/kuard.key
```

```bash
kubectl create secret generic kuard-tls \
--from-file=kuard.crt \
--from-file=kuard.key
```

```bash
kubectl create secret docker-registry my-image-pull-secret \
--docker-username=username \
--docker-password=password \
--docker-email=email@address.com
```
