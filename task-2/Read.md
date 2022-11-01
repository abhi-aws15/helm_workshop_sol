Adding Helm repository mybitnami in local
```
helm repo add mybitnami https://charts.bitnami.com/bitnami
```
Search mysql helm chart. 2nd Column is Chart version. 3rd Column is App version.
```
helm search repo mysql --devel | grep mybitnami
```
