# Oracle’s Cloud Data Platform: Autonomous-Driven & AI-Infused

<!-- Comment out table of contents
## Table of Contents
[Introduction](#introduction)
-->

## Introduction

*Complete AI Portfolio:*
Oracle offers a complete portfolio of products, services, and differentiated capabilities to power your enterprise with artificial intelligence. For business users, Oracle offers ready-to-go AI-powered cloud applications with intelligent features that drive better business outcomes. With Oracle’s ready-to-build AI platform, data scientists and application developers have a full suite of cloud services to build, deploy, and manage AI-powered solutions. With Oracle’s ready-to-work Autonomous Database, machine learning is working behind the scenes to automate security patching, backups, and optimize database query performance, which helps to eliminate human error and repetitive manual tasks so organizations can focus on higher-value activities.

This is the first of several labs that are part of the **Oracle’s Cloud Data Platform
Autonomous-Driven & AI-Infused** workshop. This workshop will walk you through the process of using the Autonomous Data Warehouse for storing analytical datasets and applying Machine Learning models in order to learn the correlation between different attributes and predict the future demand while leveraging Application Express to create a simple application as well as link to a 3rd party web app. These features will also be integrated through the bonus use of a chatbot that you can interact with using natural language.

You will take on 2 Personas during the workshop. The **Data Scientist Persona** will prepare the data for training and validating the machine learning models and apply those models in order to predict the future demand. The **Business Analyst Persona** will also build and apply Machine Learning models using Oracle Analytics Cloud service without writing a single line of code. During the workshop, you will get exposure to Oracle Autonomous Data Warehouse (ADW), Oracle Machine Learning tool (OML), Oracle Analytics Cloud Service (OAC), Oracle Application Express (APEX), Oracle Rest Data Service (ORDS), and the Oracle Digital Assistant (ODA) chatbot.

To get an idea of how these services correlate to one another, here is an example of that Cloud Data Platform Architecture which can be extended with further Oracle services such as user federation through Identity Cloud Service (IDCS) and Oracle Integration Cloud (OIC):

![](./images/cloud-data-construction-arch.jpg " ")

**Note**: This lab is intended to be a comprehensive full cloud showcase. As such, it is assumed a user going through this workshop will be provisioning resources and creating users from scratch. If you decide to use existing infrastructure or resources, be aware and keep note of your namings so resources don't overlap and conflict. 

**Note**: Additionally, as much as possible, do not stray away from the naming conventions used for resources in this workshop. You may run into errors if you do.

*In addition to the workshop*, feel free to watch the walkthrough companion videos by clicking on the following links below:

1. [Lab 100 Walkthrough Video](https://www.youtube.com/watch?v=N1EoJtf1onE)
2. [Lab 200 Walkthrough Video](https://www.youtube.com/watch?v=uprqKyeuxik)
3. [Lab 300 Walkthrough Video](https://www.youtube.com/watch?v=Zq0qEgF0bMU)
4. [Lab 400 Walkthrough Video](https://www.youtube.com/watch?v=H_SGzbIW3DA)
5. [Lab 500 Walkthrough Video](https://www.youtube.com/watch?v=wlSVlFv1R2A)
6. [Lab 600 Walkthrough Video](https://www.youtube.com/watch?v=I5prg0Ucso4)

**_To log issues_**, click here to go to the [github oracle](https://github.com/oracle/learning-library/issues/new) repository issue submission form.

### Objectives
- Provision an Autonomous Data Warehouse (ADW) Instance
- Build an Oracle Application Express (APEX) App
- Create Machine Learning Models within the Autonomous Data Warehouse (ADW) Instance by using the Oracle Machine Learning Tool (OML)
- Visualize Data and Prediction Models in Oracle Analytics Cloud (OAC)
- Bonus: Integrate a 3rd Party Web App and Oracle Digital Assistant (ODA) Chatbot


### Required Artifacts
- The following lab requires an Oracle Public Cloud account that will either be supplied by your instructor, or can be obtained through the following steps.
- A cloud tenancy where you have the resources available to provision an ADW instance with 2 OCPUs, an OAC instance with 2 OCPUs, and an ODA instance. To see which services are available in your region, please click on the following link: [Region Services List](https://www.oracle.com/cloud/data-regions.html#northamerica)
- Oracle Cloud Infrastructure supports the following browsers and versions: Google Chrome 69 or later, Safari 12.1 or later, Firefox 62 or later.

## Acquire Oracle Cloud Account and Sign-in

### Step 1: Acquire an Oracle Cloud Trial or Workshop Account
- Bookmark this page for future reference.

- Please click on the URL to create your <a class=“trial-link”  href="https://myservices.us.oraclecloud.com/mycloud/signup?language=en&sourceType=:ex:tb:::RC_NAMK190227P00084:PredictDemandML_ADW_HOL&SC=:ex:tb:::RC_NAMK190227P00084:PredictDemandML_ADW_HOL&pcode=NAMK190227P00084" target="trial">Free Account</a> and complete all the required steps. When you complete the registration process you'll receive a $300 credit that will enable you to complete the lab for free. Additionally, you'll have access to a never-expiring Oracle Cloud account allowing you to explore even more capabilities of the Oracle Cloud.

- Soon after requesting your trial you will receive the following email. You may begin working on this lab once you receive this email.

## Navigate to Lab 100

-   You can always see a list of Lab Guides by clicking on the top right hamburger menu. A sidebar on the right of your browser window will come up. 

-   **You're now ready to continue with Lab 100!**

[Back to top](#introduction)
