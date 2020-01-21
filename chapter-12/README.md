### One Shot

```bash
kubectl run -i oneshot \
--image=gcr.io/kuar-demo/kuard-amd64:blue \
--restart=OnFailure \
-- ./kuard \
--keygen-enable \
--keygen-exit-on-complete \
--keygen-num-to-gen 10
```
