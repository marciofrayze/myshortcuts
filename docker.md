# Docker/Kubernetes/Minikube/Minishift

## Generating local docker image
eval $(minikube docker-env)  
docker build -t <app> .  
docker run <app>  
docker rmi <image>
  
# Dockerfile example
```
# This is a comment
FROM rhel7.3
MAINTAINER  Marcio Frayze David <mfdavid@gmail.com>
LABEL description="Custom httpd container image" \
      version="1.0"
RUN yum update -y && \
    yum install -y httpd && \
    yum clean all
EXPOSE 80
ENV LogLevel "info" \
    HELLO "World"
ADD http://someserver.com/file/filename.pdf /var/www/html
USER apache
ENTRYPOINT ["/usr/sbin/httpd"]
CMD ["-d","FOREGROUND"]
```
  
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
