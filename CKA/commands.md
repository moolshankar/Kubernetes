# Handy commands

## Create pod with command
```bash
kubectl run nginx --image=nginx
```

## List pods with wide option
```bash
kubectl get pods -o wide
```

## Generate yaml file kubernetes dry run command
```bash
kubectl run redis --image=redis --dry-run=client -o yaml > redis.yaml
```

## Generate yaml file for exiting pod
```bash
kubectl get pod <pod-name> -o yaml > pod-definition.yaml
```

## Edit existing pod properties
```bash
kubectl edit pod pod-name
```

## Count pods in current namespace
```bash
kubectl get pods --no-headers | wc -l
```

## Display the details of the pod with name <pod-name>.
```bash
kubectl describe pods/<pod-name>
```

## Delete a pod using the type and name specified in the pod.yaml file.
```bash
kubectl delete -f pod.yaml
```

## Delete all the pods and services that have the label '<label-key>=<label-value>'.
```bash
kubectl delete pods,services -l <label-key>=<label-value>
```

## Delete all pods, including uninitialized ones.
```bash
kubectl delete pods --all
```

## Set namespace in context
```bash
kubectl config set-context --current --namespace=<namespace-name>
```

## List of all the supported resource types and their abbreviated aliases
```bash
kubectl api-resources
```

## List all pods running on node server01
```bash
kubectl get pods --field-selector=spec.nodeName=server01
```

## Learn more about a resource type
```bash
kubectl explain replicaset
```

# Create commands shortcuts for frequent long commnds

## Core shortcut
```bash
alias k='kubectl'
```

## Fast resource viewing
```bash
alias kgp='kubectl get pods'
alias kgd='kubectl get deployments'
alias kgs='kubectl get services'
alias kgn='kubectl get nodes'
```

## Detailed resource viewing
```bash
alias kgpw='kubectl get pods -o wide'
alias kgy='kubectl get -o yaml'
```

## Formatting & Management
```bash
alias kd='kubectl describe'
alias krm='kubectl delete'
```

## Reference (Bookmark this page for exam. It will be very handy):

https://kubernetes.io/docs/reference/kubectl/conventions/

### Create an NGINX Pod

kubectl run nginx --image=nginx

### Generate POD Manifest YAML file (-o yaml). Don't create it(--dry-run)
```bash
kubectl run nginx --image=nginx --dry-run=client -o yaml
```

### Create a deployment
```bash
kubectl create deployment --image=nginx nginx
```

### Generate Deployment YAML file (-o yaml). Don't create it(--dry-run)
```bash
kubectl create deployment --image=nginx nginx --dry-run=client -o yaml
```

### Generate Deployment YAML file (-o yaml). Don’t create it(–dry-run) and save it to a file.
```bash
kubectl create deployment --image=nginx nginx --dry-run=client -o yaml > nginx-deployment.yaml
```

### Make necessary changes to the file (for example, adding more replicas) and then create the deployment.
```bash
kubectl create -f nginx-deployment.yaml
```


OR

In k8s version 1.19+, we can specify the --replicas option to create a deployment with 4 replicas.
```bash
kubectl create deployment --image=nginx nginx --replicas=4 --dry-run=client -o yaml > nginx-deployment.yaml
```
## Reference
https://kubernetes.io/docs/reference/kubectl/

# K8S Service

## Create a Service named redis-service of type ClusterIP to expose pod redis on port 6379
```bash
kubectl expose pod redis --port=6379 --name redis-service --dry-run=client -o yaml
```
Or

```bash
kubectl create service clusterip redis --tcp=6379:6379 --dry-run=client -o yaml
```
(This will not use the pods labels as selectors, instead it will assume selectors as app=redis. You cannot pass in selectors as an option. So it does not work very well if your pod has a different label set. So generate the file and modify the selectors before creating the service)

## Create a Service named nginx of type NodePort to expose pod nginx's port 80 on port 30080 on the nodes:
```bash
kubectl expose pod nginx --type=NodePort --port=80 --name=nginx-service --dry-run=client -o yaml
```
(This will automatically use the pod's labels as selectors, but you cannot specify the node port. You have to generate a definition file and then add the node port in manually before creating the service with the pod.)

Or

```bash
kubectl create service nodeport nginx --tcp=80:80 --node-port=30080 --dry-run=client -o yaml
```

## Reference:
https://kubernetes.io/docs/reference/generated/kubectl/kubectl-commands

https://kubernetes.io/docs/reference/kubectl/conventions/
