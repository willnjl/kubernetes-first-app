# Declaritive notes

notes for lecuture on writing yaml files for managing kubernetes clusters

## deployment.yaml

```
kubectl apply -f=deployment.yaml
```
- run deployment on connected cluster
- `-f` is for file
- to update simply reapply same command

`pullImageOption` 

The imagePullPolicy for a container and the tag of the image affect when the kubelet attempts to pull (download) the specified image.

`pullImageOption:always`

every time the kubelet launches a container, the kubelet queries the container image registry to resolve the name to an image digest. If the kubelet has a container image with that exact digest cached locally, the kubelet uses its cached image; otherwise, the kubelet pulls the image with the resolved digest, and uses that image to launch the container


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

you can also use labels

```
kubectl delete deployments,services -l group=example
```

