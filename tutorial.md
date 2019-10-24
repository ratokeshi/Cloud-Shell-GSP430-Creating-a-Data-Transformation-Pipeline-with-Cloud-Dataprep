# GSP430 -- Tutorial: Creating a Data Transformation Pipeline with Cloud Dataprep #

## Overview
Cloud Dataprep by Trifacta is an intelligent data service for visually exploring, cleaning, and preparing structured and unstructured data for analysis. In this lab you explore the Cloud Dataprep UI to build a data transformation pipeline that runs at a scheduled interval and outputs results into BigQuery.

The dataset you'll use is an ecommerce dataset that has millions of Google Analytics session records for the Google Merchandise Store loaded into BigQuery. You have a copy of that dataset for this lab and will explore the available fields and row for insights.

### Objectives ###
In this lab, you learn how to perform these tasks:  

Connect BigQuery datasets to Cloud Dataprep.  
Explore dataset quality with Cloud Dataprep.  
Create a data transformation pipeline with Cloud Dataprep.  
Schedule transformation jobs outputs to BigQuery.  

## Prerequisites ##

 -  You have a Google Cloud Platform account and a Google Project (note the Google Project Id) provided by Quiklab. You can find this on the left side of the QwikLab page.
 -  The [Google Chrome browser](https://www.google.com/chrome/browser/desktop/). Other browsers are currently not supported by Cloud Dataprep.
 
 
## Task 1. Setting up your development environment ##
### Qwiklab
#### Before you click the Start Lab button
Read these instructions. Labs are timed and you cannot pause them. The timer, which starts when you click Start Lab, shows how long Cloud resources will be made available to you.

This Qwiklabs hands-on lab lets you do the lab activities yourself in a real cloud environment, not in a simulation or demo environment. It does so by giving you new, temporary credentials that you use to sign in and access the Google Cloud Platform for the duration of the lab.

#### What you need
To complete this lab, you need:

Access to a standard internet browser (Chrome browser recommended).
Time to complete the lab.
Note: If you already have your own personal GCP account or project, do not use it for this lab.


Note: You can view the menu with a list of GCP Products and Services by clicking the Navigation menu at the top-left, next to “Google Cloud Platform”.

</walkthrough-spotlight-pointer>
![](https://cdn.qwiklabs.com/a6YnJv8GlGae4rnJIbjA27J8c7YApa%2B6noPFkkKxZjk%3D)

1. Verify current account from QwikLab
```bash
gcloud auth list
```

2. Check your current project.
```bash
gcloud config list project
```







## -replaceme-Task-or-section
-replaceme-text text text
```bash
-replaceme-script-script-script
```
Test Completed Task
Click Check my progress to verify your performed task.
Go back to the qwiklabs page and look for the **Check My Progress**



Congratulations!
You've successfully explored your ecommerce dataset and created a recurring data transformation pipeline with Cloud Dataprep.

Go back to the Qwicklabs page to verify the lab shows as complete.

<walkthrough-conclusion-trophy></walkthrough-conclusion-trophy>
