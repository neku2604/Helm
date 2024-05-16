# Helm
Application deployment on EKS

Manual deployment

    # Create po in eks 
    k run nginx --image=nginx 

    # expose pod port 
    k port-forward pod/nginx 8080:80

    # to check if nginx web server working , from laptop browser hit 
    http://localhost:8080/

    # To connect/go inside the pod 
    k exec -it nginx -- /bin/bash


Deployment using deployment file

create deployment.yaml

apiVersion: apps/v1 kind: Deployment metadata: name: nginx-deployment labels: app: nginx spec: replicas: 3 selector: matchLabels: app: nginx template: metadata: labels: app: nginx spec: containers: - name: nginx image: nginx:1.14.2 ports: - containerPort: 80

command to creat kubernetes deployment
kubectl apply -f deployment.yaml

Application deployment using helm
    1.Create a directoty/repo to store helm chart helm create nginx-chart
    2.Helm install - to deploy app helm install nginx-chart .
    3.Helm upgrade - to change and apply any deployment config helm upgrade nginx-chart .
    4.Helm uninstall - to delete all deployment stacks helm uninstall nginx-chart .