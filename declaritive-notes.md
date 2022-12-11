# Declaritive notes

notes for lecuture on writing yaml files for managing kubernetes clusters

## deployment.yaml

`kubectl apply -f=deployment.yaml`
- run deployment on connected cluster
- `-f` is for file


## service.yaml

remember that you do not control deployments with a service! 
services control pods.

without services Pods are hard to reach and communicate with.


`kubectl apply -f=service.yaml`
- create service object



