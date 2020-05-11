# Oracle’s Cloud Data Platform: Autonomous-Driven & AI-Infused

## Introduction

*Complete AI Portfolio:*
Oracle offers a complete portfolio of products, services, and differentiated capabilities to power your enterprise with artificial intelligence. For business users, Oracle offers ready-to-go AI-powered cloud applications with intelligent features that drive better business outcomes. With Oracle’s ready-to-build AI platform, data scientists and application developers have a full suite of cloud services to build, deploy, and manage AI-powered solutions. With Oracle’s ready-to-work Autonomous Database, machine learning is working behind the scenes to automate security patching, backups, and optimize database query performance, which helps to eliminate human error and repetitive manual tasks so organizations can focus on higher-value activities.

This is the first of several labs that are part of the **Oracle’s Cloud Data Platform
Autonomous-Driven & AI-Infused** workshop. This workshop will walk you through the process of using the Autonomous Data Warehouse for storing analytical datasets and applying Machine Learning models in order to learn the correlation between different attributes and predict the future demand while leveraging Application Express to create a simple application as well as link to a 3rd party web app. These features will also be integrated through the bonus use of a chatbot that you can interact with using natural language.

You will take on 2 Personas during the workshop. The **Data Scientist Persona** will prepare the data for training and validating the machine learning models and apply those models in order to predict the future demand. The **Business Analyst Persona** will also build and apply Machine Learning models using Oracle Analytics Cloud service without writing a single line of code. During the workshop, you will get exposure to Oracle Autonomous Data Warehouse (ADW), Oracle Machine Learning tool (OML), Oracle Analytics Cloud Service (OAC), Oracle Application Express (APEX), Oracle Rest Data Service (ORDS), and the Oracle Digital Assistant (ODA) chatbot.

Here is an example of that Cloud Data Platform Architecture which can be extended with further Oracle services such as federation through Identity Cloud Service (IDCS) and Oracle Integration Cloud (OIC):

![](./LabOverview/images/cloud-data-construction-arch.jpg " ")

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
- A cloud tenancy where you have the resources available to provision an ADW instance with 2 OCPUs, an OAC instance with 2 OCPUs, and an ODA instance.
- Oracle Cloud Infrastructure supports the following browsers and versions: Google Chrome 69 or later, Safari 12.1 or later, Firefox 62 or later.

## Acquire an Oracle Cloud Account and Sign-in

### Option 1: Sign Up for an Oracle Cloud Free Trial Account
- If you do not have an Oracle Cloud account, you can create a Free Trial account. All services needed for this workshop are available to Free Trial accounts. Please note that there is a 30 day period of use for up to $300 in cloud credits. This should not inhibit your ability to complete the workshop. A credit card will be required to activate your account.

- Please click on the URL to create your <a class=“trial-link”  href="https://myservices.us.oraclecloud.com/mycloud/signup?language=en&sourceType=:ex:tb:::RC_NAMK190227P00084:PredictDemandML_ADW_HOL&SC=:ex:tb:::RC_NAMK190227P00084:PredictDemandML_ADW_HOL&pcode=NAMK190227P00084" target="trial">Free Account</a> and complete all the required steps.  

- Soon after requesting your trial, you will receive a follow-up email. You may begin working on this workshop once you receive it. Additionally, you'll have access to a never-expiring Oracle Cloud account allowing you to explore even more capabilities of the Oracle Cloud.

### Option 2: Sign Up for an Oracle SE-Assisted Trial Account
- When signing up for an Oracle SE-Assisted Trial account, similarly to Option 1, you have access to all cloud services needed for this workshop. In addition, an Oracle Cloud Solutions Engineer (SE) will be assigned to help guide you with your journey in the cloud. Please note that for this option, no credit card is required on signup.

- If selecting this option, an Oracle Solution Engineer (SE) must confirm that this is a request for a trial environment on your behalf. The Oracle Solution Engineer can do so through the following link: [SE Trial Setup](https://isrcentral.oracle.com/oalcrm/web/SETrialUI/)

### Option 3 *[Preferred]*: Use an Existing Oracle Cloud Tenancy Account
- If you already have access to an Oracle Cloud tenancy account, please use it for the purposes of this workshop. As a reminder, your tenancy must allow you as a user to have access to cloud services and resources as mentioned above in the "Required Artifacts" section of this lab guide.

## Access the Labs and Navigate to Lab 100

- Access the labs using our user-friendly web interface here: [Cloud Data Platform Workshop](https://austindatamanagement.github.io/oracle-cloud-data-platform-workshop/)
