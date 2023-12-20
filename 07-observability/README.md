```bash
kubectl apply -k 07-observability/overlays/default
kubectl apply -k 07-observability/overlays/ingress
kubectl apply -k 07-observability/overlays/loop_curl
```
```bash
kubectl -n istio-bookinfo exec -ti deployment/client -- /bin/sh
```
```bash
curl -sS productpage:9080/productpage | grep -o "<title>.*</title>"
while :; do curl -s productpage:9080/productpage | grep -o "<title>.*</title>"; sleep 1; done
watch -n 1 curl -o /dev/null -s -w %{http_code} productpage:9080/productpage
```
```bash
http://$INGRESS_HOST_IP/productpage
while :; do curl -s http://$INGRESS_HOST_IP/productpage | grep -o "<title>.*</title>"; sleep 1; done
watch -n 1 curl -o /dev/null -s -w %{http_code} http://$INGRESS_HOST_IP/productpage
```
