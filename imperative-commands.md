
# Kubernenetes First App Commands

commands for managing deployments imperatively using command line.

Tested using minikube VM box.

## starting development
```
minicube start
```
- start kubernetes  in VM development server
- used for practice

```
minikube dashboard
```
- Open cluster dashboard
- attached

```
kubectl
```
- kubectl controls the Kubernetes cluster manager.
- always ran localy.
- send commands to Master node aka cluster

## deployment


```
kubectl create deployment first-app --image=willnjl/kub-first-app
```
- sends command to master node (control plane) to build the image.
- the Master node will then analyze the currently running pods and find the best node for the new pods
- aguments deployment-name && --image=image 
- will restart crashed pods automatically

```
kubectl get deployments
```
- view deployment status.
- will show 0/1 ready until start up is complete.

```
kubectl expose deployment first-app --type=LoadBalancer --port 8080
```
- using the Loadbalancer type creates a stable IP for pods and balances incoming traffic.
- It is only availible if your hosting e.g AWS.
- creates a service
- exposes port for external access


```
kubectl get services
```
- show availible services
- will show externally accessible IP on hosted env
- external IP will shown as pending on minikube ( not accessible )

```
minikube service first-app
```
- used to view our application hosted on minukube
- minukube specific (not availible on hosted deployment)

```
kubectl scale deployment/first-app --replicas=3
```
- create 3 pods
- traffic will be evenly distobuted by the loadbalancer
- if one pod crashes - traffic will be directed to working pod while the other restarts


### updating a deployment


1. update code
2. rebuild image with version tag incremented
3. push image version to remote repo
4. run 
```
kubectl set image deployments/first-app kub-first-app=willnjl/kub-first-app:2
```
   - `kub-first-app` is the image name that we are changing
   - `deployments/first-app` is the name of the deployment
   - `willnjl/kub-first-app:2` is the version we want to replace it with

5. 
```
kubectl rollout status deployments/first-app
``` 
   - check status of rollout

### Rollout Rollback / Undo Deployment

```
kubectl rollout undo deployments/first-app
```

## Cleanup

- 
  ```
  kubectl delete service first-app
  ```
- 
  ```
  kubectl delete deployment first-app`
   ```