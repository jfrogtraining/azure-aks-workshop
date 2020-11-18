---
title: "Build and Push the Docker Image"
chapter: false
weight: 52
pre: "<b>5.2 </b>"
---

We will now build a Docker image with our NPM package and publish the image to our JFrog Artifactory repository.

![JFrog CLI Docker](/images/jfrog-cli-docker.svg)

1. In your Azure Cloud Shell. Let's create a Docker image for our NPM application. Let's create an environment variable for our image name. Substitute your _server name_ in the following command.

``
export IMAGE_NAME=<server name>.jfrog.io/docker-demo/npm-app:latest
``

2. Now let's build a docker image with the following command.

``
sudo docker build -t $IMAGE_NAME .
``

This command should result in a successful Docker image build.
![Docker Build](/images/docker-build.png)

{{%expand "Docker rate limit policies! Artifactory can help!" %}}
Docker Hub has set a new limit on data transfer beginning November 1st for free accounts: 100 pulls for anonymous users and 200 pulls for authenticated/free users for every 6 hours per IP address or a unique user.

Artifactory can protect you from this by proxying and caching images! This reduces the number of pulls from Docker Hub.

Docker also has a 6 month retention policy for free accounts. You can avoid that as well by using Artifactory as your private registry.

![Docker Remote](/images/docker-remote.png)
.{{% /expand%}}

3. Now use the JFrog CLI to push the docker image.

``
sudo jfrog rt docker-push $IMAGE_NAME docker-demo --build-name=npm_build --build-number=1
``

4. Now trigger a Xray scan of the build.

``
jfrog rt build-scan npm_build 1
``

This command should result in successful scanning.
![Xray Scan](/images/xray-scan.png)

5. If our build passes the Xray scan, we can promote it with the following command. This promotes from the _dev_ repository to the _prod_ repository. Substitute your _server name_ in the following command.

``
jfrog rt docker-promote npm-app docker-demo-dev-local docker-demo-prod-local --copy
``

{{%expand "Review what we have done." %}}
![Docker Review](/images/docker-review.png)
.{{% /expand%}}

6. In your JFrog Platform instance, go to **Artifactory** ► **Artifacts** to see this in the docker repositories.

![Promote](/images/promote.png)
