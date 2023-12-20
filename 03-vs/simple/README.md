```bash
kubectl -n lab-vs-simple exec -ti deployment/client -- /bin/bash
```

```bash
curl -s front/hello
```
```bash
curl -s admin/hello
```
```bash
curl -s front/admin
```
