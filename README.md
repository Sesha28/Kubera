This is example of one deployment that is a mvc app {core-mvc-server}, and another deployment that is also an mvc app {the-contact-app} but has an endpoint http://localhost:31002/FirstContact?txt=Ravathi, such that when your brwose this end point, inside the mvc method of this end point in {the-contact-app} it inturn issues a http request to the ClusterIP {core-web-service-cip} to get data from the first mvc app and display as a response to the browsed url  http://localhost:31002/FirstContact?txt=Ravathi.

The ClusterIP {core-web-service-cip} in the first YML "Deployment_core_app.yml" also bring the second deployment {the-contact-app} in one network.

However there is another ClusterIP {the-contact-app-cip} present in the second YML "Deployment_inter_pod.yml" that adds another network to the deployment {the-contact-app} and further exposes the deployment {the-contact-app} to the outside world via the nodePort configuration present in the second YML "Deployment_core_app.yml"

In a pure linux cluster it will be interesting to see if you need the nodeports at all  as nodeports are only needed to give access to the outside world

//////////////////////////////////////// Docker only deployment//////////////////////////////////////// 
If you are only interested in a docker environment to test pod to pod communication :

1. docker run --name the-core-app-container -d -p 4747:6666 sesha1936/the-core-app
2. 1. docker run --name the-contact-app-container -d -p 4848:5656 sesha1936/the-contact-app
   2. Enter the the-contact-app-container and do the following
     1. run bash
     2. apt-get update
     3. apt install curl vim
     4. Open **appsettings.json** and change  "OtherUrl": "http://localhost:31001/home/GetTime?txt=" to "OtherUrl": "http://localhost:4747/home/GetTime?txt=" save and exit
     5. For docker allone u need to do this. as the "OtherUrl" in the **appsettings.json** is made for a kubernetes deployment
3. Then You Browse
  1. http://localhost:4848/Show
  2. http://localhost:4848/FirstContact?txt=Urvashi
//////////////////////////////////////// Docker only deployment//////////////////////////////////////// 
The git pull url : https://raw.githubusercontent.com/Sesha28/Kubera/main/Deployment_core_app.yml

The git pull url : https://raw.githubusercontent.com/Sesha28/Kubera/main/Deployment_inter_pod.yml
