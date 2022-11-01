Set Root Passwd while installing mysql
```
helm install mysql --set auth.rootPassword=abhishek@infracloud mybitnami/mysql 
```
To Verify
```
#Output shows the passwd
kubectl get secret --namespace default mysql -o jsonpath="{.data.mysql-root-password}" | base64 -d

#Set env variable
echo Username: root
MYSQL_ROOT_PASSWORD=$(kubectl get secret --namespace default mysql -o jsonpath="{.data.mysql-root-password}" | base64 -d)

#Verify connection to your database
kubectl run mysql-client --rm --tty -i --restart='Never' --image  docker.io/bitnami/mysql:8.0.31-debian-11-r0 --namespace default --env MYSQL_ROOT_PASSWORD=$MYSQL_ROOT_PASSWORD --command -- bash

mysql -h mysql.default.svc.cluster.local -uroot -p"$MYSQL_ROOT_PASSWORD"
```
Post Installtion check- A statefulset mysql with 1 replica is created. A PV and PVC is created of 8Gi.
