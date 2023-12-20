```bash
kubectl apply -k 05-se/overlays/default
kubectl apply -k 05-se/overlays/serviceentry
```
```bash
kubectl -n lab-se exec -ti deployment/client -- /bin/sh
```
```bash
curl -s https://ip.flant.ru
```

