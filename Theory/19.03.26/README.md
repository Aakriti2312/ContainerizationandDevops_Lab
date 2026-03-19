# Kubernetes Hands-on with k3d and kubectl  
Date: 19-03-2026  

---


##  Step 1: Create Kubernetes Cluster

```bash
k3d cluster create mycluster1
```
![](./images/image1.jpeg)

### List Available Clusters
```bash
k3d cluster list
```
![](./images/image2.jpeg)

### Check Cluster Nodes
```bash
kubectl get nodes
```
![](./images/image4.jpeg)

### Check Pods (Initial State)
```bash
kubectl get pods
```
![](./images/image3.jpeg)

## Step 2: Create a Pod
```bash
kubectl run nginx --image=nginx
```
![](./images/image5.jpeg)

### Describe Pod
```bash
kubectl describe pod nginx
```
![](./images/image6.jpeg)

## Step 3: Create Deployment
```bash
kubectl create deployment web --image=nginx
```
![](./images/image7.jpeg)
### Scale Deployment
Scale to 3 replicas:
```bash
kubectl scale deployment web --replicas=3
```
![](./images/image8.jpeg)

### Check pods:
```bash
kubectl get pods
```
![](./images/image9.jpeg)
### Scale down to 2 replicas:
```bash
kubectl scale deployment web --replicas=2
```
![](./images/image10.jpeg)

## Step 4: Expose Deployment
```bash
kubectl expose deployment web --port=80 --type=NodePort
```
![](./images/image11.jpeg)

### Check Services
```bash
kubectl get services
```
![](./images/image12.jpeg)

### Access Application
```bash
kubectl port-forward services/web 8080:80
```
![](./images/image13.jpeg)

### Open in browser:
```bash
http://localhost:8080
```
## Cleanup Resources
Delete Pod:
```bash
kubectl delete pod nginx
```
Delete Deployment:
```bash
kubectl delete deployment web
```
![](./images/image14.jpeg)

## How kubectl Connects to Cluster

kubectl is a client tool

It connects to clusters using a configuration file

Default file:
~/.kube/config
Stores:

Cluster details

Authentication info

Contexts
