
List clusterroles

```console
kubectl get clusterroles
kubectl get clusterroles system:discovery -o yaml
```

Create roles

```console
kubectl create role pod-reader --verb=get --verb=list --verb=watch --resource=pods
kubectl create role warsztat --verb=get,list,watch --resource=pods,pods/status
```

create clusterrole

```console
kubectl create clusterrole pod-reader --verb=get,list,watch --resource=pods
kubectl create clusterrole "foo" --verb=get --non-resource-url=/logs/*
```

create clusterrolebinding

```console
kubectl create clusterrolebinding root-cluster-admin-binding --clusterrole=cluster-admin --user=root
```

create clusterrole from yaml 

```console
kubectle create namespace monitor
```

```console
kubectl apply -f https://raw.githubusercontent.com/djkormo/k8s-AKS-primer/master/install/addons/kubeview-rbac.yaml
kubectl get clusterrole
```

```console
kubectl apply -f https://raw.githubusercontent.com/Andrzejkokocinski/Workshopaks/master/Role.yaml
kubectl apply -f https://raw.githubusercontent.com/Andrzejkokocinski/Workshopaks/master/Rolebinding.yaml
```

```console
kubectl get clusterroles
```