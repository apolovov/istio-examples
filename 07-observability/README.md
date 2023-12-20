```bash
kubectl apply -k 07-observability/overlays/default
```
```bash
kubectl -n lab-se exec -ti deployment/client -- /bin/sh
```
```bash
curl -sS productpage:9080/productpage | grep -o "<title>.*</title>"
```
```bash
while :; do curl -s $MYHOST/productpage | grep -o "<title>.*</title>"; sleep 1; done
watch -n 1 curl -o /dev/null -s -w %{http_code} $MYHOST/productpage
```
