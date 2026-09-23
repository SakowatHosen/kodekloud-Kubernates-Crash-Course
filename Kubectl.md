

## Q-1 How many nodes are part of the cluster?

```bash
kubectl get nodes
```

## Q-2 What is the version of Kubernetes running on the nodes ?

```bash
kubectl version 
```

## Q-3 What is the flavor and version of Operating System on which the Kubernetes nodes are running?

```bash
kubectl get nodes -o wide
```

