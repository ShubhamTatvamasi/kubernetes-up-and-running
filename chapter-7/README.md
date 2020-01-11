# Service Discovery

The Service Object
```bash
kubectl run alpaca-prod \
--image=gcr.io/kuar-demo/kuard-amd64:blue \
--replicas=3 \
--port=8080 \
--labels="ver=1,app=alpaca,env=prod"
```
```bash
kubectl expose deployment alpaca-prod
```
```bash
kubectl run bandicoot-prod \
--image=gcr.io/kuar-demo/kuard-amd64:green \
--replicas=2 \
--port=8080 \
--labels="ver=2,app=bandicoot,env=prod"
```
```bash
kubectl expose deployment bandicoot-prod
```
```bash
kubectl get services -o wide
```
```bash
ALPACA_POD=$(kubectl get pods -l app=alpaca \
-o jsonpath='{.items[0].metadata.name}')
```
```bash
kubectl port-forward $ALPACA_POD 48858:8080
```
---
