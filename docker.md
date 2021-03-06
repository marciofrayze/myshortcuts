# Docker/Kubernetes/Minikube/OpenShift/Minishift/k3s/Rancher/Virsh

## Docker
docker build -t some/tagname .  
docker run <image>  
docker rmi <image>  
docker inspect <image>  
docker login  
docker push mfdavid/<imagename>  
docker logs -f ecf  
  
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
kubectl get pods --all-namespaces    
kubectl top node  
kubectl top pod  
kubectl create secret generic <scretname> \--from-literal=<key>=<value>  
kubectl exec -it <container> -- /bin/bash  
kubectl create serviceaccount <accountname>  
kubectl get serviceaccount  
kubectl describe serviceaccount <accountname>  
kubectl describe secret <secretname>  
kublctl taint nodes <nodename> key=value:<tainteffect> (NoSchedule | PreferNoSchedule | NoExecute)  
kubectl describe node <nodename> | grep Taint  
kubectl label nodes <nodename> <labelkey>=<labelvalue>  
kubectl label nodes <node> <labelkey>=<labelvalue>   
kubctl logs -f <podname>  
  
## Pod Definition yaml example
```
apiVersion: v1
kind: Pod
metadata:
  name: myapp-pod
  namespace: dev
  labels:
    app: myapp
    type: sleeper
spec:
  containers:
    - name: sleeper
      image: nginx
      command: ["sleep"]
      args: ["5000"]
      ports:
        - containerPort: 8080
      env:
        - name: APP_COLOR
          value: pink
      - envFrom:
        - configMapRef:
          name: <configname>
      envFrom: 
        - secretRef: 
          name: app-config
      securityContext:
        runAsUser: 1000
        capabilities:
          add: ["MAC_ADMIN"]
  tolerations:
  - key: "myapp"
    operator: "Equal"
    value: "blue"
    effect: "NoSchedule"
  nodeSelector: 
    size: Large 
  affinity: 
    nodeAffinity: requiredDuringSchedulingIgnoreDuringExecution
      nodeSelectorTerms: 
      - matchExpressions: 
        - key: size 
          operator: in 
          values: Large   
  livenessProbe: 
    httpGet: 
      path: /api/healthy 
        port: 8080
    initialDelaySeconds: 10 
    periodSeconds: 5 
    failureThreashold: 8
  readinessProbe: 
    httpGet: 
      path: /api/healthy 
        port: 8080  
    initialDelaySeconds: 10 
    periodSeconds: 5 
    failureThreashold: 8        
  serviceAccount: <accountname>
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
**kubectl config set-context ($kubectl config current-context) --namespace=dev**    

## Creating Compute quota
```
apiVersion: v1
kind: ResourceQuota
metadata: 
  name: compute-quota
  namespace: dev
spec:
  hard:
    pods: "10"
    request.cpu: "4"
    request.memory: 5Gi
    limits.cpu: "10"
    limits.memory: 10Gi
```
**kubectl create -f create-quota-definition.yaml**

## Creating Config map
```
apiVersion: v1
kind: ConfigMap
metadata: 
  name: app-config
data:
  APP_COLOR: blue
  APP_MODE: prod
```
**Or: kubectl create configmap app-config --from-literal=APP_COLOR=blue --from-literal=APP_MODE=prod**


## Creating Secret
```
apiVersion: v1
kind: Secret
metadata: 
  name: app-secret
data:
  DB_HOST: bXlzcWw=
  DB_PASSWORD: cm9vda==
```
**Or: kubecrl create secret generic <scretname> --from-literal=<key>=<value>**

## Minikube
eval $(minikube docker-env)  
minikube ip  
minikube addons enable metrics-server  
minikube dashboard  
minikube start --memory 4096  
minikube delete  
minikube config set memory 8192  
minikube config set cpus 2  

## Microk8s
sudo snap install microk8s --classic --channel=latest
microk8s.enable dashboard registry istio

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

## Minikube
minikube start --vm-driver kvm2 --memory 6144 --cpus 2

## k3s
**Install/upgrade:** curl -sfL https://get.k3s.io | sh -  
**Install without load balancer or another service:** curl -sfL https://get.k3s.io | bash -s -- --no-deploy servicelb  
**Stop:** sudo service k3s stop  
**List pods and kubectl in general:** sudo k3s kubecrl get pods  
**Uninstall k3s:** /usr/local/bin/k3s-uninstall.sh  
**Start as non-root:** curl -sfL https://get.k3s.io > k3s ; chmod +x k3s ; ./k3s server --disable-agent  

## Rancher
`docker run --privileged -d --restart=unless-stopped -p 80:80 -p 443:443 --name rancher rancher/rancher`  
`docker run --privileged -d --restart=unless-stopped -p 8080:80 -p 8443:443 --name rancher rancher/rancher`  
  
Open http://localhost:80 or https://localhost:8443

Add a local microk8s or minikube instance: Clusters >> Add cluster >> Import an existing cluster

If you are using microk8s, change the generated command to use `microk8s.kubectl` instead of `kubectl`

## Virsh
virsh net-list --all  
virsh net-start minikube-net  
sudo ifconfig virbr2 down  
sudo brctl delbr virbr2  
virsh net-start minikube-net   
