```bash
kubectl apply -k 02-dr/load_balancing/grpc/overlays/default
kubectl apply -k 02-dr/load_balancing/grpc/overlays/enable_istio
```

```bash
kubectl -n lab-lb-grpc delete pod --all
```
