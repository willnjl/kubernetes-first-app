# Declaritive notes

notes for lecuture on writing yaml files for managing kubernetes clusters

## deployment.yaml

```
kubectl apply -f=deployment.yaml
```
- run deployment on connected cluster
- `-f` is for file
- to update simply reapply same command


## service.yaml

remember that you do not control deployments with a service! 
services control pods.

without services Pods are hard to reach and communicate with.


```
kubectl apply -f=service.yaml
```
- create service object

 ## Cleanup

you can delete imperatively using the service or deployment name. eg.
```
kubectl delete deployment first-app-deployment
```
or you can you can use the .yaml files to specify which objects you want to remove
```
kubectl delete -f=deployment.yaml,service.yaml
```

