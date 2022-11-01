adding proper annotation
```
  annotations:
    "helm.sh/hook": test
    "helm.sh/hook-delete-policy":  hook-succeeded

```
writing manifest in templates/tests/test-connection.yaml 
```
      args: ['{{ .Release.Name }}-helm-module:{{ .Values.service.port }}']

```
Go inside Chart. First install and then test
```
helm install hello ./nginx-app/
cd nginx-app/
helm test hello
```
