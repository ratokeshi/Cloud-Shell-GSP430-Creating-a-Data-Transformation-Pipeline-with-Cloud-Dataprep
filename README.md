# Cloud-Shell-GSP430-Creating-a-Data-Transformation-Pipeline-with-Cloud-Dataprep
A Tutorial on how to complete the GSP430 Creating a Data Transformation Pipeline with Cloud DataprepLab directly in console. Using the Google Cloud Shell tutorials
Cloud Dataprep by Trifacta is an intelligent data service for visually exploring, cleaning, and preparing structured and unstructured data for analysis. In this lab you explore the Cloud Dataprep UI to build a data transformation pipeline that runs at a scheduled interval and outputs results into BigQuery.  The dataset you'll use is an ecommerce dataset that has millions of Google Analytics session records for the Google Merchandise Store loaded into BigQuery. You have a copy of that dataset for this lab and will explore the available fields and row for insights.

[https://google.qwiklabs.com/focuses/4415?parent=catalog](https://google.qwiklabs.com/focuses/4415?parent=catalog)

This lab is also part of the [Data Engineering](https://google.qwiklabs.com/quests/25) Quest


Overview
Cloud Dataprep by Trifacta is an intelligent data service for visually exploring, cleaning, and preparing structured and unstructured data for analysis. In this lab you explore the Cloud Dataprep UI to build a data transformation pipeline that runs at a scheduled interval and outputs results into BigQuery.

The dataset you'll use is an ecommerce dataset that has millions of Google Analytics session records for the Google Merchandise Store loaded into BigQuery. You have a copy of that dataset for this lab and will explore the available fields and row for insights.

Objectives
In this lab, you learn how to perform these tasks:

1. Connect BigQuery datasets to Cloud Dataprep.
1. Explore dataset quality with Cloud Dataprep.
1. Create a data transformation pipeline with Cloud Dataprep.
1. Schedule transformation jobs outputs to BigQuery.

What you'll need
The Google Chrome browser. Other browsers are currently not supported by Cloud Dataprep.

What you'll learn
How to explore an ecommerce dataset and create a recurring data transformation pipeline with Cloud Dataprep.

Here are some links: 
[Google Cloud Natural Language API](cloud.google.com/natural-language) and how to use to the Sentiment Analysis feature of the API.

Here are videos for your use:  
[https://www.youtube.com/](From Template replace todo)

To begin the tutorial in a Qwiklab open your Google Cloud Consoles as you normally would.
1.  If you have issues with the console try using incognito mode and go to https://console.cloud.google.com/
2.  If you are in the student session of the GCP Console, click the Cloud Shell icn on the top right that looks like this: ![alt text](https://walkthroughs.googleusercontent.com/tutorial/resources/cloud-shell-icon-v1.svg "Cloud Shell Icon on the top right of the GCP Console")
3.  Enter the following commands to clone this repository and launch the turotial.
```bash
git clone https://github.com/ratokeshi/Cloud-Shell-GSP430-Creating-a-Data-Transformation-Pipeline-with-Cloud-Dataprep.git
&& cd Cloud-Shell-GSP430-Creating-a-Data-Transformation-Pipeline-with-Cloud-Dataprep && cloudshell launch-tutorial tutorial.md
```

```bash
gcloud config configurations create qwiklab-$(date +%s)
gcloud config unset project
gcloud auth login <google5150507_student@qwiklabs.net>
gcloud config set project <from Lab>
cloudshell launch-tutorial tutorial.md
```


To begin the tutorial in your currently authenticated Google account, click on the button given below:
[![Open in Cloud Shell](http://gstatic.com/cloudssh/images/open-btn.png)](https://console.cloud.google.com/cloudshell/open?git_repo=https://github.com/ratokeshi/Cloud-Shell-GSP430-Creating-a-Data-Transformation-Pipeline-with-Cloud-Dataprep&tutorial=tutorial.md)
