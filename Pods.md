## Q-1 How many pods exist on the system?
```bash
kubectl get pods
```
## Q-2  Create a new pod using the nginx image.

```bash
kubectl run nginx --image=nginx
```bash
kubectl get pod
```
## Q-3 How many pods are created now?
```bash
kubectl get pods
```
## Q-4 Which image is specified for the pods whose names begin with the newpods- prefix?
```bash
kubectl describe pods
```
## Q-5 Which nodes are these pods placed on?
```bash
kubectl get pods -o wide
```
## Q-6 We just created a new pod named webapp. How many containers are part of the webapp pod?
```bash
kubectl get pods webapp
```
## Q- Delete the webapp Pod.

```bash
kubectl delete pod webapp 
```
## Create a new pod with the name redis and the image redis123.

Utilize a pod-definition YAML file. Please note that the image name redis123 is intentionally incorrect. Do NOT correct the image at this stage; you will address this in the subsequent task.


1. YAML file তৈরি করো
vi redis-pod.yaml

এর মধ্যে লিখো:
```bash
apiVersion: v1
kind: Pod
metadata:
  name: redis
spec:
  containers:
    - name: redis
      image: redis123
```
Save করে বের হও।

2. Pod তৈরি করো
```bash
kubectl create -f redis-pod.yaml
```
3. Verify
```bash
kubectl get pods
```

সম্ভবত দেখাবে:

redis   0/1   ErrImagePull



## After edit yml file delete and new created pods


```bash
kubectl delete pod redis
```
```bash
 kubectl create -f redis-pod.yaml
 ```