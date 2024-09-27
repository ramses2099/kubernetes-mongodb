# kubernetes-mongodb
Project kubernetes mongodb and mongo express


## Complete Application Setup with Kubernetes Components

- mongoDB
- mongo-express

## K8s Components

- 2 Deployment / Pod
- 2 Service
- 1 ConfigMap
- 1 Secret

## Internal Service
- 1 MongoDB pod

- 1 Mongo Express pod

## generate secret
- echo -n 'root' | base64
cm9vdA==
- echo -n 'pwd01' | base64
cHdkMDE=

## execute created secret
kubectl apply -f mongo-secret.yml
- secret/mongodb-secret created

## view the result
kubectl get secret

## deploy the pod
kubectl apply -f .\mongo-deployment.yml
- deployment.apps/mongodb-deployment created

## show all resource
kubectl get all
kubectl get pod

## show the status of the pod
kubectl get pod --watch

## create the services
kubectl apply -f .\mongo-deployment.yml
- deployment.apps/mongodb-deployment unchanged
- service/mongodb-service created

## check the services
kubctl get service

## see if the service is attach to the container
kubectl describe service mongodb-service

## see aditional details of the pod
kubectl get pod -o wide

## create config map
kubectl apply -f .\mongo-configmap.yml
- configmap/mongodb-configmap created

## deploy mongo-express
kubectl apply -f .\mongo-express-deployment.yml
- deployment.apps/mongo-express created

## see the logs
kubctl logs mongo-express

## create the external services for mongo-express
kubectl apply -f .\mongo-express-deployment.yml
deployment.apps/mongo-express unchanged
service/mongo-express-service created

## http access url
http://10.101.13.76:30001 

## asign public api adress
minikube service name-service

## open dashboard minikube
minikube dashboard