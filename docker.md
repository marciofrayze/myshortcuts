# Docker/Kubernetes/Minikube/OpenShift/Minishift

## Docker
docker build -t some/tagname .  
docker run <image>  
docker rmi <image>  
docker inspect <image>  
docker login  
docker push mfdavoid/<imagename>  
  
## Dockerfile example
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
kubectl config view -o jsonpath='{"Cluster name\tServer\n"}{range .clusters[*]}{.name}{"\t"}{.cluster.server}{"\n"}{end}'  
kubectl config get-contexts  
kubectl config use-context <contextname>  
kubectl get services  
kubectl describe service load-balancer  
kubecrl edit pod <podname>  
kubecrl get pods -o wide  
kubecrl describe pod <podname>  
kubectl get pod <pod-name> -o yaml > pod-definition.yaml  

## Pod Definition yaml example
```
apiVersion: v1
kind: Pod
metadata:
  name: myapp-pod
  labels:
    app: myapp
    type: front-end
spec:
  containers:
    - name: nginx-container
      image: nginx
```

## Replication Controller yaml example
```
apiVersion: v1
kind: ReplicationController
metadata:
  name: myapp-rc
  labels:
    app: myapp
    type: front-end
spec:
  template:
    metadata:
      name: myapp-pod
      labels:
        app: myapp
        type: front-end
    spec:
      containers:
        - name: nginx-container
          image: nginx
  replicas: 2    
```

## Minikube
eval $(minikube docker-env)  
minikube ip  
minikube addons enable metrics-server  
minikube dashboard  
minikube start --memory 4096  
minikube delete  
minikube config set memory 8192  
minikube config set cpus 2  

## OpenShift
oc login https://masternode.address.com:8443 -u username -p password  
oc whoami  
oc project <projectname>  
oc new-project <projectname>  
oc status  
oc delete project <projectname>  
oc logout  
oc login -u system:admin  
oc get pods  
oc descript pod <podname>   
oc <projectname> <language>:<version>~<gitrepository>  
oc start-build <projectname>  
oc edit route/<name>  
oc get svc 
oc expose svc <servicename>  
