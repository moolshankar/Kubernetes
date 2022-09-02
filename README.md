# Kubernetes

https://minikube.sigs.k8s.io/docs/start/

## start minikube cluster with
minikube start

## Start new deployment using command
kubectl create deployment hello-minikube --image=k8s.gcr.io/echoserver:1.4

## Or from file using command
kubectl create -f pod-definiton.yml

## Expose new application using command
kubectl expose deployment hello-minikube --type=NodePort --port=8080

## Use port forward to access application in browser
kubectl port-forward service/hello-minikube 7080:8080
