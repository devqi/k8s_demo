# K8s Demo
The application consists of two parts: mongoDB and webApp. They are deployed separately via K8s.

### Configuration

##### mongoDB
- mongo-deployment.yaml
- mongo-service.yaml
- mongo-config.yaml 
- mongo-secret.yaml

##### WebApp
webapp.yaml (deployment and service)

### Tips
##### Commonly used commands
encode text to base64 on Mac
`echo -n textToBeEncoded | base64`

apply definition files (config, secret, deployment, service)
`kubectl apply -f <YAML_FILE>`

view logs of container 
`kubectl logs <POD_NAME> [-f]`

list all deployments under all namespaces
`kubectl get deployments --all-namespaces`

get extra information with `-o wiede` option
`kubectl get node/service/pod/... -o wiede`

get cluster ip 
`minikube ip`
`kubectl get node -o wide`

### Issues
1. The site cannot be reached while using the combination of IP (minikube ip) and nodePort (service in webapp.yaml) to access the webapp.
    - Reason:
    - Solution: run the command `minikube service webapp-service` to open browser or run the command `minkube service webapp-service --url` to get the correct url which should be used in browser to access the site.