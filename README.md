# prometheus-guide

Setup Persistent Volume
```bash
mkdir /mnt/pv{1,2}
```
```yaml
kubectl create -f - <<EOF
kind: PersistentVolume
apiVersion: v1
metadata:
  name: pv-volume1
spec:
  storageClassName:
  capacity:
    storage: 10Gi
  accessModes:
    - ReadWriteOnce
  hostPath:
    path: "/mnt/pv1"
---
kind: PersistentVolume
apiVersion: v1
metadata:
  name: pv-volume2
spec:
  storageClassName:
  capacity:
    storage: 10Gi
  accessModes:
    - ReadWriteOnce
  hostPath:
    path: "/mnt/pv2"
EOF
```


Setup prometheus via helm
```bash
helm repo update
helm install --name promtheus stable/prometheus
```
