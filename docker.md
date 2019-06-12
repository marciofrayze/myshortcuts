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
kubectl run --generator=run-pod/v1 nginx-pod --image=nginx:alpine  
kubectl expose pod redis --port=6379 --name redis-service  

## Pod Definition yaml example
```
apiVersion: v1
kind: Pod
metadata:
  name: myapp-pod
  namespace: dev
  labels:
    app: myapp
    type: front-end
spec:
  containers:
    - name: nginx-container
      image: nginx
```
**kubectl create -f pod-definition.yaml --namespace=dev**  

## ReplicaSet yaml example
```
apiVersion: apps/v1
kind: ReplicaSet
metadata:
  name: myapp-replicaset
  namespace: dev
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
  selector: 
    matchLabels:  
      type: front-end
```
kubectl create -f replicaset-definition.yaml   
kubectl get replicaset  
kubectl replace -f replicaset-definition.yaml  
kubectl scale --replicas=6 -f replicaset-definition.yaml   
kubectl delete replicaset <replicasetname>    
kubecrl describe replicaset <replicaset>  
kubectl get all  

## Deployment yaml example
```
apiVersion: apps/v1
kind: Deployment
metadata:
  name: myapp-deployment
  namespace: dev  
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
  selector: 
    matchLabels:  
      type: front-end
```
kubectl create -f deployment-definition.yaml  
kubectl get deployment  
kubectl get all  

## Service exposing nodePort yaml example
```
apiVersion: v1
kind: Service
metadata: 
  namespace: dev
  labels:
    app: webapp
  name: webapp-service
spec: 
  ports: 
    - port: 8080
      protocol: TCP
      targetPort: 8080
      nodePort: 30082
  selector:
    app: webapp
  type: NodePort
status: 
  loadBalancer: {}
```

## Creating namespace yaml example
```
apiVersion: v1
kind: Namespace
metadata: 
  namespace: dev
```
**Or: kubectl create namespace dev** 

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
