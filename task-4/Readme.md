Creating Chart
```
helm create mychart
```
To generate the name for this configmap using helm release name with format
```
{{ .Release.Name }}-nginx-configmap
```
To mount this configmap's index.html content to the pods in Deployment at location /usr/share/nginx/html/index.html
```
          volumeMounts:
          - name: myvol
            mountPath: /usr/share/nginx/html/index.html
            subPath: index.html
      volumes:
      - name: myvol
        configMap:
          name: {{ .Release.Name }}-nginx-configmap
```
To install and Verify (Perform this inside task-4 directory)
```
helm install helm-workshop ./mychart
```
