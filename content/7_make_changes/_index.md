---
title: "Make Changes"
chapter: false
weight: 7
pre: "<b>7 </b>"
---

In the previous steps, we manually built and deployed our application from our code. Any code change can automatically trigger a build.

1. In your Azure Cloud Shell, use the editor and select workshop-app/src/app/app.component.html.

![Azure Cloud Shell Editor App](/images/azure-cloud-shell-editor-app.png)
   
2. Updated the value of the _a-text_ tag. Make it "Azure Workshop App: Build Num".

3. Copy the animation attribute from the animation attribute from the _a-image_ tag and add it to the _a-text_ tag, too.

4. Commit these changes.

```
cd ~/azure-aks-workshop
git add .
git commit -m 'Updated the application content.'
```

5. Next, push these updates. When prompted for a username and password, use your GitHub username and personal access token.

``
git push origin master
``

6. This should automatically trigger a new build. Go to **Application** > **Pipelines** > **My Pipelines** and click on your **workshop_app_build**.

7. View the progress of the new run. When complete, go the **$url** in the browser again to view the updated application.

Congratulations! You have set up a CI/CD pipeline that will automatically build and deploy new code!
