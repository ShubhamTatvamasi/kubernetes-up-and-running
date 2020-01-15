
### Installing Contour

apply Contour
```bash
kubectl apply -f https://raw.githubusercontent.com/projectcontour/contour/master/examples/render/contour.yaml
```

delete Contour
```bash
kubectl delete -f https://raw.githubusercontent.com/projectcontour/contour/master/examples/render/contour.yaml
```

get all 
```bash
kubectl get all -n projectcontour -o wide
```

tunnel makes services of type LoadBalancer accessible on localhost
```bash
minikube tunnel
```
---

### Using ingress

Update your node IP in `/etc/hosts`
```
10.96.254.105 alpaca.example.com
10.96.254.105 bandicoot.example.com
```
> Enter IP of LoadBalancer

```bash
kubectl run be-default \
--image=gcr.io/kuar-demo/kuard-amd64:blue \
--replicas=3 \
--port=8080
kubectl expose deployment be-default

kubectl run alpaca \
--image=gcr.io/kuar-demo/kuard-amd64:green \
--replicas=3 \
--port=8080
kubectl expose deployment alpaca

kubectl run bandicoot \
--image=gcr.io/kuar-demo/kuard-amd64:purple \
--replicas=3 \
--port=8080
kubectl expose deployment bandicoot
```
```bash
kubectl get services -o wide
```
---

### Simplest Usage

```bash
kubectl apply -f simple-ingress.yaml
```
```bash
kubectl apply -f host-ingress.yaml
```
```bash
kubectl apply -f path-ingress.yaml
```

delete everything
```bash
kubectl delete ingress host-ingress path-ingress simple-ingress
kubectl delete service alpaca bandicoot be-default
kubectl delete deployment alpaca bandicoot be-default
```
---
