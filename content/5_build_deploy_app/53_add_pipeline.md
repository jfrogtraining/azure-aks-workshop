---
title: "Add our CI/CD Pipeline"
chapter: false
weight: 53
pre: "<b>5.3 </b>"
---

1. In your JFrog Platform instance, go to **Application** > **Pipelines** > **Pipeline Sources**.

![Pipeline Sources](/images/pipeline-sources.png)

2. Click **Add a pipeline source**.

3. Click **Add Pipeline Source** at the top right and select **From YAML**.

![Pipeline From YAML](/images/pipeline-from-yaml.png)

3. For **SCM Provider Integration**, select the **github_integration** that you created previously.

4. For **Repository Full Name**, select your forked **<username>/azure-aks-workshop**.

4. For **Branch**, select **master**.

4. Leave **Pipeline Config File Filter** as _pipelines.yml_.

![Create Pipeline Source](/images/create-pipeline-source.png)

5. Click **Create Source**.
