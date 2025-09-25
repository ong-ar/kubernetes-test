```bash
helm install hpa-test . -f values.yaml
helm upgrade hpa-test . -f values.yaml
helm uninstall hpa-test -n default

# 부하 발생
kubectl run -it load-generator --image=busybox --rm --restart=Never -- /bin/sh
while true; do wget -q -O- http://hpa-test.default.svc.cluster.local; done

# 확인
kubectl get pods -w
kubectl get hpa -w
```
