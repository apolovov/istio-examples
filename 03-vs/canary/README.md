```bash
kubectl apply -k 03-vs/canary/overlays/default/
kubectl apply -k 03-vs/canary/overlays/new-version/
kubectl apply -k 03-vs/canary/overlays/canary/
```
```bash
kubectl -n lab-vs-canary exec -ti deployment/client -- /bin/sh
```
```bash
curl -s front/hello
```
```bash
curl -s front-v1/hello
```
```bash
curl -s front-v2/hello
```
```bash
curl -s -H 'Cookie: A=123;B=abc;user_type=tester' front/hello
```

