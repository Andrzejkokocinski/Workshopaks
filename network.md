
```console
kubectl cluster-info
```

That can be like below
<pre>
Kubernetes master is running at https://ingressdem-ingressdemoaksrg-95975e-809b9e85.hcp.westeurope.azmk8s.io:443
healthmodel-replicaset-service is running at https://ingressdem-ingressdemoaksrg-95975e-809b9e85.hcp.westeurope.azmk8s.io:443/api/v1/namespaces/kube-system/services/healthmodel-replicaset-service/proxy
CoreDNS is running at https://ingressdem-ingressdemoaksrg-95975e-809b9e85.hcp.westeurope.azmk8s.io:443/api/v1/namespaces/kube-system/services/kube-dns:dns/proxy
kubernetes-dashboard is running at https://ingressdem-ingressdemoaksrg-95975e-809b9e85.hcp.westeurope.azmk8s.io:443/api/v1/namespaces/kube-system/services/kubernetes-dashboard/proxy
Metrics-server is running at https://ingressdem-ingressdemoaksrg-95975e-809b9e85.hcp.westeurope.azmk8s.io:443/api/v1/namespaces/kube-system/services/https:metrics-server:/proxy
</pre>

```console
kubectl get pods --all-namespaces
```

That can be like below

<pre>
NAMESPACE     NAME                                   READY   STATUS    RESTARTS   AGE
kube-system   coredns-7fc597cc45-99z5r               1/1     Running   0          20m
kube-system   coredns-7fc597cc45-m2xk2               1/1     Running   0          16m
kube-system   coredns-autoscaler-7ccc76bfbd-hqjhz    1/1     Running   0          20m
kube-system   kube-proxy-k5xgs                       1/1     Running   0          17m
kube-system   kubernetes-dashboard-cc4cc9f58-mdpm6   1/1     Running   0          20m
kube-system   metrics-server-58b6fcfd54-ghhwx        1/1     Running   0          20m
kube-system   omsagent-bpr8v                         1/1     Running   0          17m
kube-system   omsagent-rs-779b64789b-7tqkt           1/1     Running   0          20m
kube-system   tunnelfront-85fc855c56-52rhs           1/1     Running   0          20m
</pre>

```console
kubectl get deployments -n kube-system
```

<pre>
NAME                   READY   UP-TO-DATE   AVAILABLE   AGE
coredns                2/2     2            2           22m
coredns-autoscaler     1/1     1            1           22m
kubernetes-dashboard   1/1     1            1           22m
metrics-server         1/1     1            1           22m
omsagent-rs            1/1     1            1           22m
tunnelfront            1/1     1            1           22m
</pre>
```console
kubectl run --generator=run-pod/v1 busybox --image=busybox:1.28 --command -- sleep 3600
```
```console
kubectl exec -it busybox -- cat /etc/resolv.conf 
```
```console
kubectl exec -it busybox -- nslookup kubernetes
```

```console
kubectl describe pods/busybox
```
```console
kubectl logs coredns-7fc597cc45-99z5r -n kube-system
```
<pre>
[WARNING] No files matching import glob pattern: custom/*.override
[WARNING] No files matching import glob pattern: custom/*.server
.:53
2020-01-10T17:37:53.174Z [INFO] CoreDNS-1.3.1
2020-01-10T17:37:53.174Z [INFO] linux/amd64, go1.11.4, 6b56a9c
CoreDNS-1.3.1
linux/amd64, go1.11.4, 6b56a9c
2020-01-10T17:37:53.174Z [INFO] plugin/reload: Running configuration MD5 = d8c69602fc5a3428908dc8f34f9aae58
97cc45-99z5r -n kube-system
</pre>