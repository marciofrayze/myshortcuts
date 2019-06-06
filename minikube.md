# Minikube/Kubernetes/Docker

## Generating local docker image
eval $(minikube docker-env)  
docker build -t app .  
docker run app  

## Kubernetes
kubectl get nodes  
kubectl cluster-info  
kubectl run app --image=app:latest --port=8080 --image-pull-policy=Never  
kubectl get pods  
kubectl expose deployment/app --type="NodePort" --port 8080  
kubectl describe services/app  
kubectl get apiservices  
kubectl create namespace mem-example  

## Minikube
minikube ip  
minikube addons enable metrics-server  
minikube dashboard  
minikube start --memory 4096  
minikube delete  
minikube config set memory 8192  
minikube config set cpus 2  
