---
title: "1 - Architecture Overview"
date: 2020-04-18T00:39:21+07:00
---

#### Architecture Overview

The architecture for this module is very straightforward. All of your static web content including HTML, CSS, JavaScript, images and other files will be managed by AWS Amplify Console and served via Amazon CloudFront. Your end users will then access your site using the public website URL exposed by AWS Amplify Console. You don't need to run any web servers or use other services in order to make your site available.

![Static website architecture](/images/1.staticwebsite/1.1-architect-web.png?width=90pc)    

#### Implementation Instructions

Ensure you've completed the setup guide before beginning the workshop.

Each of the following sections provides an implementation overview and detailed, step-by-step instructions. The overview should provide enough context for you to complete the implementation if you're already familiar with the AWS Management Console or you want to explore the services yourself without following a walkthrough.

#### Region Selection

This workshop step can be deployed in any AWS region that supports the following services:

- AWS Amplify Console
- AWS CodeCommit

You can refer to the **AWS region table** in the AWS documentation to see which regions have the supported services. Among the supported regions you can choose are:
* North America: N. Virginia, Ohio, Oregon
* Europe: Ireland, London, Frankfurt
* Asia Pacific: Tokyo, Seoul, Singapore, Sydney, Mumbai

Once you've chosen a region, you should deploy all of the resources for this workshop there. Make sure you select your region from the dropdown in the upper right corner of the AWS Console before getting started.


