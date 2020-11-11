---
title: "Deploy Your Image with AKS"
chapter: false
weight: 73
pre: "<b>7.3 </b>"
---

With an AKS cluster deployed, we are now ready to deploy our NPM application!  

1. First, let's create a namespace to provide isolation. Execute the following.

``
kubectl create namespace azureworkshop
``

2. Next, we need to set our Artifactory registry credentials in order to pull the NPM application image. We will do this my creating Kubernetes secrets to store these. Execute the following command. Substitute your _server name_ and JFrog Platform credentials (_username_ and _API key_).

``
kubectl create secret docker-registry regcred 
    --namespace azureworkshop
    --docker-server=$jfrog_server_id 
    --docker-username=$jfrog_user
    --docker-password=$jfrog_apikey
``

3. We will use a Kubernetes deployment manifest to deploy the NPM application image. First, we must make a substitution in the file for the image that we want to deploy.

``
sed "s|imageName|$image_name|g" deployment.yaml > my-deployment.yaml
``

4. Now we can deploy with the following command.

``
kubectl apply -f my-deployment.yaml --namespace azureworkshop
``

5. Execute the following to see your deployed pod.

``
kubectl get pods --namespace azureworkshop
``

You should see you npm-app pod.

![Kubectl Get Pods](/images/kubectl-get-pods.png)

6. Now let's get the external IP so that we can view your application. Execute the following.

``
kubectl get services --namespace azureworkshop
``

This will provide the EXTERNAL-IP.

![Kubectl External IP](/images/kubectl-external-ip.png)

7. In your browser, go to https://\<EXTERNAL-IP\> to view your deployed web application. 
8. Click through the self-signed certificate warning. You should see the following web application.

![NPM Application](/images/npm-app.png)


Congratulations! You have used Azure AKS to deploy the image that you built with the JFrog Platform.




