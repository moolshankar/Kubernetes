# Handy commands

## Create pod with command
kubectl run nginx --image=nginx

## List pods with wide option
kubectl get pods -o wide

## Generate yml file kubernetes dry run command
kubectl run redis --image=redis --dry-run=client -o yaml
