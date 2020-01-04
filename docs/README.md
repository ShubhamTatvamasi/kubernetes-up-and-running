# docs

diagnostic for the cluster
```bash
kubectl get componentstatuses
```

list all the nodes in your cluster
```bash
kubectl get nodes
```

Get more information with `-o wide`
```bash
kubectl get nodes minikube -o wide
```

describe the node details
```bash
kubectl describe nodes node-1
```

Get the IP of a specfic pod
```bash
kubectl get pods nginx-pod -o jsonpath --template={.status.podIP}
```
