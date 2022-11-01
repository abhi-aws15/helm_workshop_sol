Add a bitnami mysql helm chart as the subchart 
```
dependencies: # A list of the chart requirements (optional)
  - name: mysql
    version: 9.4.1
    repository: https://charts.bitnami.com/bitnami
    condition: mysql.enabled

```
```
helm dependency build
```

Adding this parameters in values.yaml
```
mysql:
  enabled: true
  auth:
    rootPassword: abcd1234
```

