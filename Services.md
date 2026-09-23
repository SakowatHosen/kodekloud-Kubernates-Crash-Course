## Q- How many Services exist on the system?

```bash
kubectl get service
```

## Q- What is the targetPort configured on the kubernetes service?
```bash
kubectl describe service
```

## Q- What is the image used to create the pods in the deployment?

```bash
kubectl describe deployments.apps 
```
### Q- Create a new service to access the web application using the service-definition-1.yaml file.

Name: webapp-service
Type: NodePort
targetPort: 8080
port: 8080
nodePort: 30080
selector:
  name: simple-webapp

/root/-এ service-definition-1.yaml তৈরি/এডিট করে এই configuration দিন:
```bash
  vi /root/service-definition-1.yaml
  ```
```bash
apiVersion: v1
kind: Service
metadata:
  name: webapp-service
spec:
  type: NodePort
  selector:
    name: simple-webapp
  ports:
  - targetPort: 8080
    port: 8080
    nodePort: 30080
```
তারপর:
```bash
kubectl create -f /root/service-definition-1.yaml
```
Verify:
```bash
kubectl get svc
```
Expected:
```bash
webapp-service   NodePort   ...   8080:30080/TCP
```
যদি file আগে থেকেই দেওয়া থাকে, আগে দেখে নিন:
```bsah
cat /root/service-definition-1.yaml
```