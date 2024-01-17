This is example of one deployment that is a mvc app {core-mvc-server}, and another deployment that is also an mvc app {the-contact-app} but has an endpoint http://localhost:31002/FirstContact?txt=Ravathi, such that when your brose this end point inside the mvc method {the-contact-app} inturn issues a http request to the ClusterIP {core-web-service-cip} to get data from the first mvc app and display as a response to the browsed url  http://localhost:31002/FirstContact?txt=Ravathi.

The ClusterIP {core-web-service-cip} in the first YML "Deployment_core_app.yml" also bring the second deployment {the-contact-app} in one network.

However there is another ClusterIP {the-contact-app-cip} present in the second YML "Deployment_inter_pod.yml" that adds another network to the deployment {the-contact-app} and further exposes the deployment {the-contact-app} to the outside world via the nodePort configuration present in the second YML "Deployment_core_app.yml"

In a pure linux cluster it will be interesting to see if you need the nodeports at all  as nodeports are only needed to give access to the outside world
