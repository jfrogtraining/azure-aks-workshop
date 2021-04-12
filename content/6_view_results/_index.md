---
title: "View Results in JFrog"
chapter: false
weight: 6
pre: "<b>6 </b>"
---

We have built and published our Docker image. Let's view these results in JFrog Artifactory.

1. Go to your JFrog Platform instance and switch to the **Packages** view in Artifactory. Go to **Artifactory** ► **Packages**.
2. Type ```workshop-app``` and search. This will show the Docker image that was just build.
3. Click on it to view the details.
![Docker Workshop App](/images/docker-workshop-app.png)
4. This will show a list of the versions. Click on the latest version that was built.
![Docker Workshop App Versions](/images/docker-workshop-app-versions.png)
5. In the **Xray Data** tab, view the security violations. License violations are available in the JFrog Platform Pro and Enterprise tiers.
![Xray Data](/images/docker-workshop-app-xray-data.png)
6. Click on any violation to see the details and impact in the **Issue Details** tab.
![Xray Detail](/images/docker-workshop-app-xray-detail.png)
7. Scroll down to the **References** section to access links to documentation that can help you remediate the issue.
![Xray Detail References](/images/docker-workshop-app-xray-detail-references.png)

{{% notice info %}}
Xray supports all major package types, understands how to unpack them, and uses recursive scanning to see into all of the underlying layers and dependencies of components, even those packaged in Docker images, and zip files.
The comprehensive vulnerability intelligence databases are constantly updated giving the most up-to-date understanding of the security and compliance of your binaries.
{{% /notice %}}

8. Close the **Issue Details** tab.
9. View the Docker configuration for the image in the **Docker Layers** tab.
10. On the **Builds** tab, click on _workshop\_app\_build_ in the list.
![Build List](/images/docker-workshop-app-build-list.png)
11. Then click on your most recent build.
12. View your build data across the various tabs.
![Build Data](/images/docker-workshop-app-build-data.png)

Our JFrog CI/CD pipeline provided an overview of a typical build, docker build and push, security scan, promotion and deploy process using JFrog Artifactory, Xray, Pipelines and Azure AKS.
