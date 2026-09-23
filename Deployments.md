## Q- How many Deployments exist on the system?
```bash
kubectl get deployments.apps 
```
## Q- What is the image used to create the pods in the new deployment?

```bash
kubectl describe deployment frontend-deployment
```

## Create a new Deployment using the deployment-definition-1.yaml file located at /root/.
There is an issue with the file, so try to fix it.


প্রথমে YAML ফাইলটি দেখুন:
```bash
cat /root/deployment-definition-1.yaml
```
তারপর ভুলটা ঠিক করতে:

```bash
vi /root/deployment-definition-1.yaml
```
Fix করার পর Deployment create করুন:
```bash
kubectl create -f /root/deployment-definition-1.yaml
```
Verify:
```bash
kubectl get deployments
kubectl get pods
```
cat এর output এখানে দিলে আমি কোন line ঠিক করতে হবে exact বলে দেব।


## Create a new Deployment with the below attributes using your own deployment definition file.

Name: httpd-frontend;
Replicas: 3;
Image: httpd:2.4-alpine

Deployment
```bash
vi /root/httpd-frontend.yaml
```
এই YAML দিন:
```bash
apiVersion: apps/v1
kind: Deployment
metadata:
  name: httpd-frontend
spec:
  replicas: 3
  selector:
    matchLabels:
      app: httpd-frontend
  template:
    metadata:
      labels:
        app: httpd-frontend
    spec:
      containers:
      - name: httpd
        image: httpd:2.4-alpine
```
Save করুন:

Esc → :wq → Enter

তারপর:
```bash
kubectl create -f /root/httpd-frontend.yaml
```
Verify:
```bash
kubectl get deployment
kubectl get pods
```

Shortcut commend
```bash
kubectl create deployment httpd-frontend
--image—httpd:2.4-alpine
--replicas=3
```