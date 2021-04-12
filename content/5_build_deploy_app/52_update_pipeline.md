---
title: "Update our Pipeline"
chapter: false
weight: 52
pre: "<b>5.2 </b>"
---

We need to make an update to our CI/CD pipeline in order to pull code from your GitHub repository and to use your personal JFrog Artifactory instance. The CI/CD pipeline is defined in [pipeline.yml](https://github.com/jfrogtraining/azure-aks-workshop/pipeline.yml). This pipeline file is parameterized with a values.yml file. We need to update this file.

1. In your Azure Cloud Shell, use the editor and view the pipeline.yml file. View the steps.
