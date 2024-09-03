## 볼륨 공유

- emptydir

```bash
kubectl apply -f emptydir-pod.yaml
kubectl exec pod-volume-1 -c container1 -- touch /mount1/file1
kubectl exec pod-volume-1 -c container2 -- ls /mount2
kubectl exec pod-volume-1 -c container3 -- ls /mount1
```

- hostpath

```bash
kubectl apply -f hostpath-pod.yaml
minikube ssh
cat /tmp/kubernetes-demo/test.txt
```

## 퍼시스턴트 볼륨과 퍼시스턴트 볼륨클레임

```bash
kubectl apply -f pv.yaml
kubectl apply -f pvc.yaml
kubectl apply -f pv-pod.yaml
kubectl get pod task-pv-pod
```

## 스토리지 클래스와 동적브로비저닝

```bash
kubectl get storageclass
kubectl apply -f dynamic-pvc.yaml
kubectl get pvc dynamic-pvc
```
