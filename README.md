Here we do deploy 4 instances of a ASP.NET 7 mvc app. 
For Docker Desktop we just need NodePort. Cluster IP is provided as a sample. 
Looking at the NodePort snippet at the bottom, we have to browse this url  http://localhost:31001 in Chrome.
The pull url for this yml is https://raw.githubusercontent.com/Sesha28/Kubera/main/Deployment_core_app.yml

commands to execute this 
pull yml from github by simply borwsing and copy pasting the content into a ne file called Deployment_core_app.yml
kubectl apply -f Deployment_core_app.yml
browse from your windows machine http://localhost:31001
kubectl display pods -o wide
kubectl get all

kubectl delete deployment core-mvc-server
kubectl delete svc core-web-service
