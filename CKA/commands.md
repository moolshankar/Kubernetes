# Handy commands

## Create pod with command
kubectl run nginx --image=nginx

## List pods with wide option
kubectl get pods -o wide

## Generate yaml file kubernetes dry run command
kubectl run redis --image=redis --dry-run=client -o yaml > redis.yaml

## Generate yaml file for exiting pod
kubectl get pod <pod-name> -o yaml > pod-definition.yaml

## Edit existing pod properties
kubectl edit pod pod-name

## Count pods in current namespace
kubectl get pods --no-headers | wc -l

## Display the details of the pod with name <pod-name>.
kubectl describe pods/<pod-name>

## Delete a pod using the type and name specified in the pod.yaml file.
kubectl delete -f pod.yaml

## Delete all the pods and services that have the label '<label-key>=<label-value>'.
kubectl delete pods,services -l <label-key>=<label-value>

## Delete all pods, including uninitialized ones.
kubectl delete pods --all

## Set namespace in context
kubectl config set-context --current --namespace=<namespace-name>

## List of all the supported resource types and their abbreviated aliases
kubectl api-resources

## List all pods running on node server01
kubectl get pods --field-selector=spec.nodeName=server01

# Create commands shortcuts for frequent long commnds

## Core shortcut
alias k='kubectl'

## Fast resource viewing
alias kgp='kubectl get pods'
alias kgd='kubectl get deployments'
alias kgs='kubectl get services'
alias kgn='kubectl get nodes'

## Detailed resource viewing
alias kgpw='kubectl get pods -o wide'
alias kgy='kubectl get -o yaml'

## Formatting & Management
alias kd='kubectl describe'
alias krm='kubectl delete'

## Reference
https://kubernetes.io/docs/reference/kubectl/



