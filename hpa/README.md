```bash
helm install nginx-hpa ./nginx-hpa -f values.yaml
helm upgrade nginx-hpa ./nginx-hpa -f values.yaml
helm uninstall nginx-hpa -n default

# 부하 발생
kubectl run -it load-generator --image=busybox --rm --restart=Never -- /bin/sh
while true; do wget -q -O- http://nginx-hpa.default.svc.cluster.local; done
```
