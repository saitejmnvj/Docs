# Helm-charts
We use Helm charts to easily deploy and manage the deployments of our backend services on to GKE clusters. 
General Helm directory structure is as follows:
```
Optima-charts
 ┣ templates
 ┃ ┣ tests
 ┃ ┃ ┗ test-connection.yaml
 ┃ ┣ deployment.yaml
 ┃ ┣ ingress.yaml
 ┃ ┣ NOTES.txt
 ┃ ┣ service.yaml
 ┃ ┗ _helpers.tpl
 ┣ .helmignore
 ┣ Chart.yaml
 ┗ values.yaml
```
All the K8s resources are placed inside the templates directory like deployment yamls, ingress and the service, Chart.yaml contains definitions required for the charts, the helpers.tpl has all the template definitions for charts. 

The repository contains deployments for both **node micro-services** as well as **spingboot micro-services**

<hr>

# Command We are using to operate the charts #

## Helm Commands

How to install the charts
```
helm install optima ./optima-charts
```
If the installation got failed, you need to delete the release inorder to install it again, here optima is the release name
```
helm uninstall optima
```
#### 
<hr>

## Debugging the deployed resources(Kubernetes Commands) ##

Inorder to check the what resources got deployed, we use two commands: the get command and the describe command 

We use kubectl to check the status of the resources that got deployed
```
kubectl get all
kubectl get deployments
kubectl get ingress
kubectl describe account-deployment<this is the deployment name>
```
Suppose that we want to know each and every detail about the resource, we use describe command:
` kubectl describe service servicename
`
One can use logs command to check the logs of the container running 
```
kubectl logs <podname> 
```
<hr>

# Some useful Helm Commands #
```
helm create <chartname>
```
How to Install a helm release 
```
helm install <NAME> <CHART> <flags>
```
There are some useful flags like -f <values.yaml> where you can apply your values.yaml, you can use --set to change a particular value in values.yaml, In the below example: optima is the release name and ./optima is the path to the chart or can call as chartname 
```
helm install -f myvalues.yaml --set env=prod optima ./optima
```
If one wants to do a testrun so as to check the installation without actually installing the charts, them can use --dryrun flag
```
helm install <NAME> <CHART> --dry-run --debug
```
If you want to delete any release you can use this commad 
```
helm uninstall <release name>
```
If you want to check if there are any syntax errors, use helm template command it will render the charts locally
```
helm template <NAME> <CHART> <--flags>
```
This command gives you the list of releases that are there in the namespace, one can use --filter flag to filter out the names that you want to check 
```
helm list --filter 'ara[a-z]+'
```
