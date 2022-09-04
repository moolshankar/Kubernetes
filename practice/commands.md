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
