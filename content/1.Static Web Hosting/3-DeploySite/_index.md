---
title: "3 - Deploy the site"
date: 2020-04-18T00:39:21+07:00
---

#### Deploy the site with the AWS Amplify Console
Next you'll use the **AWS Amplify Console** to deploy the website you've just commited to git. The Amplify Console takes care of the work of setting up a place to store your static web application code and provides a number of helpful capabilities to simplify both the lifecycle of that application as well as enable best practices.


1. Launch the [Amplify Console console page](https://console.aws.amazon.com/amplify/home)
2. Click **Get Started** under Deploy with Amplify Console
3. Select the *Repository service provider* used today and select **Continue** ( If you used GitHub, you'll need to authorize AWS Amplify to your GitHub account )
   ![Amplify](/images/1.staticwebsite/1.6-amplify.png?width=90pc) 
4. From the dropdown select the *Repository* and *Branch* created today
     ![Amplify](/images/1.staticwebsite/1.7-amplify.png?width=90pc)   
5. On the "Configure build settings" page leave all the defaults and select **Next**
6. On the "Review" page select **Save and deploy**
    
The process takes a couple of minutes for Amplify Console to create the neccesary resources and to deploy your code.
    
   ![Amplify](/images/1.staticwebsite/1.8-amplify.png?width=90pc)   

Once completed, click on the site image to launch your Wild Rydes site.
![Amplify](/images/1.staticwebsite/1.9-amplify.png?width=50pc)   
If you click on the link for *Master* you'll see various pieces of information about your website deployment, including sample renderings on various platforms:
![Amplify](/images/1.staticwebsite/1.81-amplify.png?width=90pc)   
![Amplify](/images/1.staticwebsite/1.10-amplify.png?width=90pc)   