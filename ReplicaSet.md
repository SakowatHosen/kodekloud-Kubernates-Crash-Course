## Q-1 How many ReplicaSets exist on the system?

```bash
kubectl get replicaset
```
## Q-1 How about now? How many ReplicaSets do you see?

```bash
kubectl get replicaset
```

## Q-3 How many PODs are DESIRED in the new-replica-set?

```bash
kubectl get replicaset
```
```bash
kubectl describe replicasets.apps 
```

## Delete pod directly
```bash
kubectl delete pod new-replica-set-qw652 
```

## Q- Create a ReplicaSet using the replicaset-definition-1.yaml file located at /root/.

```bash

vi /root/replicaset-definition-1.yaml

 kubectl create -f /root/replicaset-definition-1.yaml

 kubectl get pods
 ```

 ## Q- Fix the issue in the replicaset-definition-2.yaml file and create a ReplicaSet using it.

This file is located at /root/.


```bash
vi /root/replicaset-definition-2.yaml 
````
বর্তমানে:

selector:
  matchLabels:
    tier: frontend

কিন্তু:

labels:
  tier: nginx

দুটো একই হতে হবে। frontend অনুযায়ী ঠিক করুন:

vi /root/replicaset-definition-2.yaml

এটা:

labels:
  tier: nginx

পরিবর্তন করে:

labels:
  tier: frontend

তারপর:
```bash
kubectl create -f /root/replicaset-definition-2.yaml
```
Verify:
```bash
kubectl get rs
kubectl get pods
```


### Q- Delete the two newly created ReplicaSets - replicaset-1 and replicaset-2

```bash
kubectl delete rs replicaset-1 replicaset-2

```
### Q- Fix the original replica set new-replica-set to use the correct image with name as busybox.

Either delete and recreate the ReplicaSet or update the existing ReplicaSet and then delete all PODs, so new ones with the correct image will be created.

If you opt to delete the ReplicaSet and recreate it, please refer to the file named new-replica-set.yaml, which is saved in the /root/ directory for your convenience and fix it.

1. YAML ঠিক করুন
```bash
vi /root/new-replica-set.yaml
```
```bash
image হবে:

image: busybox

অর্থাৎ busybox777 থাকলে busybox করুন।

Save:
Esc → :wq → Enter
```
2. পুরোনো ReplicaSet delete করুন
```bash
kubectl delete rs new-replica-set
```
3. নতুন ReplicaSet তৈরি করুন
```bash
kubectl create -f /root/new-replica-set.yaml
```
4. Check করুন
```bash
kubectl get rs
kubectl get pods
```
সবগুলো Pod-এর READY হওয়া উচিত 1/1 এবং STATUS Running।


## Q- Scale the ReplicaSet to 5 PODs.
Use kubectl scale command or edit the replicaset using kubectl edit replicaset.


```bash
kubectl scale replicaset new-replica-set --replicas=5
```

## Q- Now scale the ReplicaSet down to 2 PODs.
Use the kubectl scale command or edit the replicaset using kubectl edit replicaset.
```bash
kubectl scale replicaset new-replica-set --replicas=2
```
Check 
```bash 
kubectl get rs
kubectl get pods
```