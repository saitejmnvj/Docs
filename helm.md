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
### If you want to delete any release you can use this commad ###
```
helm uninstall <release name>
```
### If you want to check if there are any syntax errors, use helm template command it will render the charts locally ###
```
helm template <NAME> <CHART> <--flags>
```