---
title: "Update our Pipeline"
chapter: false
weight: 52
pre: "<b>5.2 </b>"
---

We need to make an update to our CI/CD pipeline in order to pull code from your GitHub repository and to use your personal JFrog Artifactory instance. The CI/CD pipeline is defined in [pipelines.yml](https://github.com/jfrogtraining/azure-aks-workshop/pipelines.yml). This pipeline file is parameterized with a values.yml file. We need to update this file.

1. In your Azure Cloud Shell, use the editor and view the pipelines.yml file. View and understand the steps. Note the parameterized values.

![Azure Cloud Shell Editor Pipeline](/images/azure-cloud-shell-editor-pipeline.png)

2. In the editor, select the values.yml file and updated the parameterized values to point to your GitHub repository and JFrog Artifactory instance. Use CTRL+S or CMD+S to save the file.

![Azure Cloud Shell Editor Values](/images/azure-cloud-shell-editor-values.png)

3. In your Azure Cloud Shell, change directory to _azure-aks-workshop_. Commit these changes.

```
cd ~/azure-aks-workshop
git add .
git commit -m 'Updated values.yml.'
```

4. Next, push these updates. When prompted for a username and password, use your GitHub username and personal access token.

``
git push origin master
``

We are now ready to add your CI/CD pipeline and execute!
