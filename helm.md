# Some Useful Helm Commands #
```
helm create <chartname>
```
### How to Install a helm release ###


```
helm install <NAME> <CHART> <flags>
```
#### There are some useful flags like -f <values.yaml> where you can apply your values.yaml, you can use --set to change a particular value in values.yaml, In the below example: optima is the release name and ./optima is the path to the chart or can call as chartname ####
```
helm install -f myvalues.yaml --set env=prod optima ./optima
```
### If one wants to do a testrun so as to check the installation without actually installing the charts, them can use --dryrun flag ###
```
helm install <NAME> <CHART> --dry-run --debug
```
### If you want to delete any release you can use this commad ###
```
helm uninstall <release name>
```
### If you want to check if there are any syntax errors, use helm template command it will render the charts locally ###
```
helm template <NAME> <CHART> <--flags>
```
### This command gives you the list of releases that are there in the namespace, one can use --filter flag to filter out the names that you want to check ###
```
helm list --filter 'ara[a-z]+'
```
