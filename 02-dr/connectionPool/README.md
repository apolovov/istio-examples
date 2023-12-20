```bash
kubectl apply -k 02-dr/connectionPool/overlays/default/
kubectl apply -k 02-dr/connectionPool/overlays/connection_pool/
```
```bash
kubectl -n lab-dr-cp exec -ti deployment/client -- /bin/sh
```
```bash
curl -s front/hello
```
```bash
nc front 80

GET /hello HTTP/1.1
Host: front
User-Agent: curl/8.4.0
Accept: */*
```
