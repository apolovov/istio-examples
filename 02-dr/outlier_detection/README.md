```
watch -n 0.2 'istioctl -i d8-istio -n lab-lb-outlier-detection proxy-config endpoints frontend-86d78d5df8-x764h | grep backend'
```

```
while true; do curl -w " %{http_code}" backend; echo; sleep 0.2; done
```
