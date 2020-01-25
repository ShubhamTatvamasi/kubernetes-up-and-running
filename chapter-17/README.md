# Deploying Real-World Applications

### Jupyter

```bash
kubectl create namespace jupyter
```
```bash
kubectl create -f jupyter.yaml
```
```bash
pod_name=$(kubectl get pods --namespace jupyter --no-headers | awk '{print $1}')
kubectl logs --namespace jupyter ${pod_name}
```
```bash
kubectl port-forward -n jupyter ${pod_name} 8888:8888
```
```bash
kubectl expose deployment jupyter -n jupyter --type='NodePort' --port=8888
```
---

### Ghost

```bash
kubectl create cm --from-file ghost-config.js ghost-config
```
```bash
kubectl expose deployments ghost --port=2368
```
```bash
kubectl create configmap ghost-config-mysql --from-file ghost-config-mysql.js
```
---

### Redis

```bash
kubectl create configmap \
--from-file=slave.conf=./slave.conf \
--from-file=master.conf=./master.conf \
--from-file=sentinel.conf=./sentinel.conf \
--from-file=init.sh=./init.sh \
--from-file=sentinel.sh=./sentinel.sh \
redis-config
```
