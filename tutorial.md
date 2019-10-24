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
 
 
### Task 1. Setting up your development environment ##
#### Qwiklab
##### Before you click the Start Lab button
Read these instructions. Labs are timed and you cannot pause them. The timer, which starts when you click Start Lab, shows how long Cloud resources will be made available to you.

This Qwiklabs hands-on lab lets you do the lab activities yourself in a real cloud environment, not in a simulation or demo environment. It does so by giving you new, temporary credentials that you use to sign in and access the Google Cloud Platform for the duration of the lab.

#### What you need
To complete this lab, you need:

Access to a standard internet browser (Chrome browser recommended).
Time to complete the lab.
Note: If you already have your own personal GCP account or project, do not use it for this lab.

#### Setting up Google Cloud Platform Console
##### How to start your lab and sign in to the Console

1. Click the Start Lab button. If you need to pay for the lab, a pop-up opens for you to select your payment method. On the left is a panel populated with the temporary credentials that you must use for this lab.  


Note: You can view the menu with a list of GCP Products and Services by clicking the Navigation menu at the top-left, next to “Google Cloud Platform”.
<walkthrough-spotlight-pointer spotlightId="devshell-web-preview-button"
                               text="Open Web Preview">
</walkthrough-spotlight-pointer>
![](https://cdn.qwiklabs.com/a6YnJv8GlGae4rnJIbjA27J8c7YApa%2B6noPFkkKxZjk%3D)

- Verify current account from QwikLab
```bash
gcloud auth list
```

- Check your current project.
```bash
gcloud config list project
```
Your current project name is: {{<project-name>}}  
Your current project id is: {{<project-id>}}  
 Be sure to compare this to the display in your Qwiklab after you start the lab. The display looks like this:  
 ![Login Info](https://cdn.qwiklabs.com/%2FtHp4GI5VSDyTtdqi3qDFtevuY014F88%2BFow%2FadnRgE%3D)  
 
1. Copy the username, and then click Open Google Console. The lab spins up resources, and then opens another tab that shows the Choose an account page.

Tip: Open the tabs in separate windows, side-by-side.

1. On the Choose an account page, click Use Another Account.  
 ![Login Info](https://cdn.qwiklabs.com/eQ6xPnPn13GjiJP3RWlHWwiMjhooHxTNvzfg1AL2WPw%3D) 
 
1.   The Sign in page opens. Paste the username that you copied from the Connection Details panel. Then copy and paste the password.

Important: You must use the credentials from the Connection Details panel. Do not use your Qwiklabs credentials. If you have your own GCP account, do not use it for this lab (avoids incurring charges).

1. Click through the subsequent pages:

Accept the terms and conditions.
Do not add recovery options or two-factor authentication (because this is a temporary account).
Do not sign up for free trials.
After a few moments, the GCP console opens in this tab.
Note: You can view the menu with a list of GCP Products and Services by clicking the Navigation menu at the top-left, next to “Google Cloud Platform”.
![Hamburger](https://cdn.qwiklabs.com/9vT7xPlxoNP%2FPsK0J8j0ZPFB4HnnpaIJVCDByaBrSHg%3D)  
Open the Navigation Menu Icon
<walkthrough-nav-menu-icon>
</walkthrough-nav-menu-icon>
<walkthrough-spotlight-pointer
    spotlightId="nav-menu-icon">
    spotlight on the nav menu icon
</walkthrough-spotlight-pointer>

#### Opening BigQuery console
Although this lab is largely focused on Cloud Dataprep, you need BigQuery as an endpoint for dataset ingestion to the pipeline and as a destination for the output when the pipeline is completed.
![](https://cdn.qwiklabs.com/O2n0exH9RUENSsK99EJIUKFgk%2BX8HlTC95mpNxwqZcM%3D)  

In the Google Cloud Console, select Navigation menu > BigQuery:

The Welcome to BigQuery in the Cloud Console message box opens. This message box provides a link to the quickstart guide and lists UI updates.

Click Done.

Task 2. Creating a BigQuery Dataset
In this task, you will create a new BigQuery dataset to receive the output table of your new pipeline.

In the left pane, select your project name:
![](https://cdn.qwiklabs.com/esw2SaacyT37O73Yl9AXNNnlfgwdd2YzbCs5W1m8yZU%3D)  
Then from the right-hand side of the Console, click CREATE DATASET:

For Dataset ID, type ecommerce.

Leave the other values at their defaults.

Then click Create Dataset. You will now see your dataset under your project in the left-hand menu:

![](https://cdn.qwiklabs.com/%2FWb9tCY5obRnzxLWeG2CKCoALTFsWJEjbHk8iXa6Hjc%3D)  
Now find the Query editor and copy and paste the following SQL query into it:
![]()  
Then click Run. This query copies over a subset of the public raw ecommerce dataset (one day's worth of session data, or about 56 thousands records) into a new table named all_sessions_raw_dataprep, which has been added to your ecommerce dataset for you to explore and clean in Cloud Dataprep.

Confirm that the new table exists in your ecommerce dataset:
![](https://cdn.qwiklabs.com/l4rCFkdBfxvQTSQTABjeUBMZVqzknJPhaFHL9NyTsK4%3D)  

Task 3. Opening Cloud Dataprep
In this task, you will open Cloud Dataprep and go through some initialization steps.

Using a Chrome browser (Reminder: Cloud Dataprep works ONLY in Chrome), open the Navigation menu and select Dataprep.

Accept the terms of service.

In the Share account information with Trifacta dialog, select the checkbox, and then click Agree and Continue. 
![](https://cdn.qwiklabs.com/ANZC4%2Fu1p4kkwTCgTYjvK%2BtmjEd%2Bq%2BhbujlWQm%2FKXHM%3D)  

To allow Trifacta to access your project data, click Allow.
Note: This authorization process might take a few minutes.
In the Sign in with Google window appears, select your Qwiklabs account and then click Allow. Accept the Trifacta Terms of Service if prompted.

If prompted to use the default location for the storage bucket, click Continue.

Soon after you should be on the Cloud Dataprep homepage:
![](https://cdn.qwiklabs.com/GTA3wuNzkntF15ei0Z7iiamjHt%2F7T5ZcdEyB21FK8bY%3D)  

Task 4. Connecting BigQuery data to Cloud Dataprep
In this task, you will connect Cloud Dataprep to your BigQuery data source. On the Cloud Dataprep page:

Click Create Flow in the top-right corner.

In the Create Flow dialog, specify these details:

For Flow Name, type Ecommerce Analytics Pipeline
For Flow Description, type Revenue reporting table
![](https://cdn.qwiklabs.com/M6bE5rIGjhcgBRo%2FQGGSk7q9prlaKdUn%2F9KyMyiJEcI%3D)  

Click Create.

If prompted with a What's a flow? popup, select Don't show me any helpers.

Now Click Import & Add Datasets.
![](https://cdn.qwiklabs.com/cABcT2QfFZpnJzauPTqksypWTNfwpOKpcO24L6F9hNs%3D)  
In the left pane, click BigQuery.

When your ecommerce dataset is loaded, click on it.
![](https://cdn.qwiklabs.com/A1PnS5h0nvcB11tTyzjMNvKuMXNxIUT42EIEYTJi1b0%3D)  

Click on the Create dataset icon (+ sign) on the left of the all_sessions_raw_dataprep table.

Click Import & Add to Flow in the bottom right corner.

The data source automatically updates. In the right pane, Add new Recipe should become an available option. You are ready to go to the next task.
![](https://cdn.qwiklabs.com/vw%2Bak9UPwGhBf%2B5La%2BwLN0G8ILC%2B0g%2FaMc3iurgqeJM%3D)  

Task 5. Exploring ecommerce data fields with a UI
In this task, you will load and explore a sample of the dataset within Cloud Dataprep.

In the right pane, click Add new Recipe.
![](https://cdn.qwiklabs.com/Fcfazc2Vxi2yXFEM5gzmooXcRxIt5Dlly5tM2OlOez4%3D)  

Click Edit Recipe.
Cloud Dataprep loads a sample of your dataset into the Transformer view. This process might take a few seconds. You are now ready to start exploring the data!

Answer the following questions:

How many columns are there in the dataset?
![](https://cdn.qwiklabs.com/rn0tpr5Mp8ST1rzHGaTAw7HfxJdDA4XrsAEOxZYxIIo%3D)  

Answer: 32 columns.

How many rows does the sample contain?
![](https://cdn.qwiklabs.com/6Um%2FiZNdDzEBRsbbMrUQugmtQthKouU8qmsYTgyOFfE%3D)  
Answer: About 12 thousands rows.

What is the most common value in the channelGrouping column?
Hint: Find out by hovering your mouse cursor over the histogram under the channelGrouping column title.
!{}(https://cdn.qwiklabs.com/ZqwIsyvjq2WfBNh1XlLmlht60PfwBnKK%2B8maGuBtOPI%3D)  
Answer: Referral. A referring site is typically any other website that has a link to your content. An example here is a different website reviewed a product on our ecommerce website and linked to it. This is considered a different acquisition channel than if the visitor came from a search engine.

Tip: When looking for a specific column, click the Find column icon ( 33a3808286737935.png ) in the top right corner, then start typing the column's name in the Find column textfield, then click on the column's name. This will automatically scroll the grid to bring the column on the screen.
What are the top three countries from which sessions are originated?
![](https://cdn.qwiklabs.com/AozLCVR6k2yuhGP6RBEmPJmASKtb3zSKh%2BYIzWO6t3U%3D)  






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
