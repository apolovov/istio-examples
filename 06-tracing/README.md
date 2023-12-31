```bash
kubectl apply -k 07-observability/overlays/good_header
kubectl apply -k 07-observability/overlays/bad_header
kubectl apply -k 07-observability/overlays/tracing
```
```bash
kubectl -n lab-bookinfo-good exec -ti deployment/client -- /bin/sh
kubectl -n lab-bookinfo-bad exec -ti deployment/client -- /bin/sh
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
```bash
kubectl edit mc istio
```
```yaml
apiVersion: deckhouse.io/v1alpha1
kind: ModuleConfig
metadata:
  name: istio
spec:
  version: 2
  enabled: true
  settings:
    tracing:
      collector:
        zipkin:
          address: zipkin.istio-jaeger.svc.cluster.local:9411
      enabled: true
      kiali:
        jaegerURLForUsers: http://$INGRESS_HOST_IP:80/jaeger
        jaegerGRPCEndpoint: http://tracing.istio-jaeger.svc.cluster.local:16685/
      sampling: 100.0

```
```bash
kubectl -n lab-bookinfo-good delete pod --all
kubectl -n lab-bookinfo-bad delete pod --all
```
