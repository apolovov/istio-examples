```bash
kubectl apply -k 02-dr/load_balancing/consistent_hash/overlays/default/
kubectl apply -k 02-dr/load_balancing/consistent_hash/overlays/consistent_hash/
```
```bash
kubectl -n lab-dr-lb-ch exec -ti deployment/client -- /bin/sh
```
```bash
curl -s front/hello
```
```bash
curl -s -H 'X-Forwarded-For: 4.3.2.1' front/hello
```

