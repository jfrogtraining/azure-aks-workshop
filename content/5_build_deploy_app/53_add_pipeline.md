﻿---
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

5. Click **Create Source**. JFrog Pipelines will process the CI/CD pipeline. The status should show **Not Synced** then **Syncing** and then **Success**.

![Success Pipeline Source](/images/success-pipeline-source.png)

6. Go to **Application** > **Pipelines** > **My Pipelines**. Notice that your pipeline has a status of **Not Built**.

![My Pipelines](/images/my-pipelines.png)

7. Click on your pipeline, **workshop_app_build**.

![Workshop Pipeline](/images/workshop-pipeline.png)

8. Click on the _docker_build_ step and trigger the step to execute the pipeline. JFrog Pipelines will allocate build nodes and execute your pipeline.

![Trigger Pipeline](/images/trigger-pipeline.png)

9. It will take a few minutes to execute. Click on the _Run_ to monitor the status of each step.

![Pipeline Wait](/images/pipeline-wait.png)

10. Use the pulldown to select each step and view the logs.

![Pipeline Step Logs](/images/pipeline-step-logs.png)

11. When the pipeline execution completes (approximately 5-10 minutes), view the log for the _aks_deploy_ step.

12. Scroll down to get the **$url** value. Click on the link to view the application!

![AKS Deploy URL](/images/aks-deploy-url.png)
