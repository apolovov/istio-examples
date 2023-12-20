```bash
kubectl apply -k 02-dr/connectionPool/overlays/default/
kubectl apply -k 02-dr/connectionPool/overlays/connection_pool/
```
```bash
kubectl -n lab-dr-lb-ch exec -ti deployment/client -- /bin/sh
```
```bash
curl -s front/hello
```
