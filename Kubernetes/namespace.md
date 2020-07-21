### Viewing namespaces:
You can list the current namespaces in a cluster using:

```bash
kubectl get namespace

kubectl get ns
```
```bash
| ==> kubectl get namespace
NAME              STATUS   AGE
kube-system       Active   15h
default           Active   15h
kube-public       Active   15h
kube-node-lease   Active   15h
mongodb           Active   15h
___________________    | 01:51 PM  ~/depl  (centos)
| ==> kubectl get ns
NAME              STATUS   AGE
kube-system       Active   15h
default           Active   15h
kube-public       Active   15h
kube-node-lease   Active   15h
mongodb           Active   15h
```

## Setting the namespace for a request

```bash
kubectl get pods -n <namespace>
kubectl get pods --namespace=<namespace>
```
Example:
```bash
| ==> kubectl get pods -n mongodb
NAME                                           READY   STATUS    RESTARTS   AGE
mongodb-enterprise-operator-5979f8dff9-vspjh   1/1     Running   0          15h
svclb-ops-manager-svc-ext-ht2d6                1/1     Running   0          15h
svclb-ops-manager-svc-ext-s5szp                1/1     Running   0          15h
svclb-ops-manager-svc-ext-xl5gc                1/1     Running   0          15h
svclb-ops-manager-svc-ext-hc4th                1/1     Running   0          15h
```
```bash
| ==> kubectl get pods --namespace=mongodb
NAME                                           READY   STATUS    RESTARTS   AGE
mongodb-enterprise-operator-5979f8dff9-vspjh   1/1     Running   0          15h
svclb-ops-manager-svc-ext-ht2d6                1/1     Running   0          15h
svclb-ops-manager-svc-ext-s5szp                1/1     Running   0          15h
svclb-ops-manager-svc-ext-xl5gc                1/1     Running   0          15h
svclb-ops-manager-svc-ext-hc4th                1/1     Running   0          15h
```
## Setting the namespace preference
You can permanently save the namespace for all subsequent kubectl commands in that context.

```bash
kubectl config set-context --current --namespace=<namespace>
# Validate it
kubectl config view --minify | grep namespace:
```