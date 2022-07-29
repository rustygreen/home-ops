# Raspberry Pi

1. Use [k3sup](https://github.com/alexellis/k3sup)
2. Label node (if desired)

```bash
kubectl taint nodes rasp-1 site=basement:NoSchedule
kubectl label nodes rasp-1 site=basement
```
