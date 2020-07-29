# Lab 10000: Getting Started with Data Safe

## Introduction
Data Safe is a unified control center for your Oracle Databases which helps you understand the sensitivity of your data, evaluate risks to data, mask sensitive data, implement and monitor security controls, assess user security, monitor user activity, and address data security compliance requirements. Whether you’re using Oracle Autonomous Database or Oracle Database Cloud Service (Exadata, Virtual Machine, or Bare Metal), Data Safe delivers essential data security capabilities as a service on Oracle Cloud Infrastructure.

This lab walks you through the steps to get started using Oracle Data Safe on Oracle Cloud Infrastructure.

**_To log issues_**, click here to go to the [github oracle](https://github.com/oracle/learning-library/issues/new) repository issue submission form.

### Objectives
-   Learn how to register a target database
-   Learn how to assess database configurations with Oracle Data Safe 
-   Learn how to access userrs with Oracle Data Safe
-   Learn how to discover sensitive data model with Oracle Data Safe
-   Learn how to verify a sensitive data model with Oracle Data Safe
-   Learn how to update a sensitive data model with Oracle Data Safe
-   Learn how to create a sensitive type and category with Oracle Data Safe
![](./images/1.png " ")

### Required Artifacts
-   The following lab requires an Oracle Public Cloud account. You may use your own cloud account, a cloud account that you obtained through a trial, or a training account whose details were given to you by an Oracle instructor.
-	An Oracle Database Service enabled in a region in your tenancy
-	A registered target database in Oracle Data Safe with sample audit data and the password for the SYS user account.

### Extra Resources
- Click this link learn more about Enabling Data Safe in a region: [Enable Data Safe](https://docs.oracle.com/en/cloud/paas/data-safe/udscs/enable-oracle-data-safe.html#GUID-409260CE-2D7B-4029-B7CA-2EDD6E961CEB)
-   To learn more about Oracle Autonomous Data Warehouse (ADW), feel free to watch the following video by clicking on this link: [ADW - How it Works](https://www.youtube.com/watch?v=f4BurlkdEQM)
-   To learn more about Oracle Application Express (APEX), feel free to explore the capabilities by clicking on this link: [APEX Overview](https://apex.oracle.com/en/)
-   Additionally, to see an example of what kind of sites and apps are possible to quickly create with APEX, check out a showcase by clicking on this link: [Built with APEX](https://www.builtwithapex.com/)

~~## Part 1. Registering a Target Database
- You can register Autonomous Databases and DB systems in the Oracle cloud with Oracle Data Safe. The following table lists the supported cloud databases, their versions, and whether public or private IP addresses for the databases are supported.
https://docs.oracle.com/en/cloud/paas/data-safe/udscs/target-database-registration-overview.html#GUID-10B10D3D-8807-4778-8C91-80AEE4F7F4F0 use this table
~~- For this lab we will be registering an Autonomous Database
### **Step 1:** 
1. To register an Autonomous Database with Oracle Data Safe, you require permissions in Oracle Cloud Infrastructure Identity and Access Management (IAM), on the database, and in Oracle Data Safe.
~~2. Permission in IAM to access to the database. The user group to which you belong requires at least the **inspect** permission on the **autonomous-database** resource type. For example, to grant the **Data-Safe-Admins** group the **inspect** permission on all Autonomous Databases in the **Finance** compartment, a tenancy administrator could write the following policy statement:
allow group Data-Safe-Admins to inspect autonomous-database in compartment Finance <!-- See how to add code snippet copy on md-->

~~3. Permission to log in to the database as an administrator. You need to be able to log in as a PDB administrator (ADMIN) or as a user that has execute permission on the DS_TARGET_UTIL package in order to grant additional roles to the DS$ADMIN service account for Oracle Data Safe.
4. Permission to manage at least one feature in Oracle Data Safe. The user group to which you belong needs to be granted the manage privilege on at least one feature in Oracle Data Safe (Assessment, Activity Auditing, or Discovery and Masking) so that you can register, update, and delete target databases for that feature. ~~

### **Step ~~2~~ 1:** 
- By default, your Autonomous Database comes with a database account specifically created for Oracle Data Safe named DS$ADMIN. - The roles that you grant to this account determine the Oracle Data Safe features that you can use with your Autonomous Database. By default, the DS$ASSESSMENT_ROLE and DS$AUDIT_COLLECTION_ROLE roles are already granted. These particular roles allow you to assess users and security configurations on your Autonomous Database and start audit trail collection immediately after you register the database.

- The following table describes the available roles for Autonomous Databases.
Use the table here https://docs.oracle.com/en/cloud/paas/data-safe/udscs/register-autonomous-databases-that-have-public-ip-addresses.html#GUID-1026A408-2D57-420C-927B-588948C2A89C

- To grant or revoke roles from the Oracle Data Safe service account on an Autonomous Database database, you can run the DS_TARGET_UTIL PL/SQL package on the Autonomous Database. You need to run this package as the PDB Admin user (ADMIN) or as a user that has execute permission on the DS_TARGET_UTIL PL/SQL package.

- You can grant or revoke roles as often as needed.
- Using a tool like SQL*Plus or SQL Developer, log in to your Autonomous Database as the PDB Admin user (ADMIN) or as a user that has execute permission on the DS_TARGET_UTIL PL/SQL package.
- Grant or revoke a role from the Oracle Data Safe service account by running one of the following commands:
EXECUTE DS_TARGET_UTIL.GRANT_ROLE('role_name');
or
EXECUTE DS_TARGET_UTIL.REVOKE_ROLE('role_name');
- where role_name is the name of an Oracle Data Safe role. role_name must be in quotation marks.

### **Step ~~3~~2:** 
- You can register an Autonomous Database from its Console in Oracle Cloud Infrastructure Console. From this Console, you can also access the Oracle Data Safe Console.

1. Sign in to Oracle Cloud Infrastructure.<!-- Add login console images if skipping lab 0-->
2. In the upper right corner, select the region in which your Autonomous Database resides.
3. From the navigation menu, select **Autonomous Data Warehouse** or **Autonomous Transaction Processing**.
4. From the **COMPARTMENT** drop-down list, select the compartment that contains your Autonomous Database.
5. Click the name of your Autonomous Database. The **Autonomous Database Information** tab on the **Autonomous Database Details** page is displayed.
6. Under **Data Safe**, click **Register**.
7. A Confirm dialog box asks if you are sure you want to register the database with Oracle Data Safe.
8. Click **Confirm**. Wait for registration to finish.
9. When registration is completed, the **Status** reads **Registered**. A resource group is created in Oracle Data Safe with the same name as the compartment that contains the database in Oracle Cloud Infrastructure. The user registering the database is automatically authorized to manage the User Assessment, Security Assessment, and Activity Auditing features for that resource group.
10. (Optional) Click **View Console** to navigate to the Oracle Data Safe Console for the database.

## Part 2. Assess Database Configurations with Oracle Data Safe
-	Using Oracle Data Safe you can assess the security of a database by using the Security Assessment feature and fix issues.
### **Step 1:** 
-	In the Oracle Data Safe Console, generate a Comprehensive Assessment report
-	Navigate to the Oracle Data Safe Console
-	Click the **Home** tab and then **Security Assessment**.
<!-- Image 1-->
-	On the **Security Assessment** page, select the check box for your target database, and click **Assess**.
<!-- Image 2-->
- 	Wait a moment for the report to generate.
-	When the report is generated, review the high risk, medium risk, and low risk values.
-	In the **Last Generated Report** column, click **View Report**.
<!-- Image 3-->
-	The **Comprehensive Assessment** report is displayed on the **Reports** tab.
-	In the upper right corner, view the target name, when the database was assessed, and the database version.
<!-- Image 4-->
-	View the values for the different risk levels. These values give you an idea of how secure your database is.
<!-- Image 5-->
-	View the values for security controls, user security, and security configurations. These totals show you the number of findings for each high-level category.
-	Browse the report by scrolling down and expanding and collapsing categories. Each category lists related findings about your database and how you can make changes to improve its security.
-	View the **Summary** table. This table compares the number of findings for each category and counts the number of findings per risk level. It helps you to identify the areas that need attention on your database.
<!-- Image 6-->
### **Step 2:** 
-	At the top of the report, click **Medium Risk** to filter the report to show only the medium risk findings.
-	Deselect all other risk levels.
-	Scroll through the report to view the medium risk findings.
-	At the top of the report, click **Low Risk** to filter the report to show only the low risk findings.
-	Deselect all other risk levels.
-	Review the low risk findings.
-	At the top of the report, click **Advisory** to filter the report to show only the advisory findings.
-	Deselect all other risk levels.
-	Review the advisory findings.
### **Step 3:** 
-	At the top of the report, click **Evaluate** to filter the report to show only the Evaluate findings.
<!-- Image 7-->
-	Deselect all other risk levels.
-	Scroll through the report to view the findings.
-	Focus on **System Privilege Grants** under Privileges and Roles:
-	System privileges (ALTER USER, CREATE USER, DROP USER) can be used to create and modify other user accounts, including the ability to change passwords. This ability can be abused to gain access to another user's account, which may have greater privileges. The Privilege Analysis feature may be helpful to determine whether or not a user or role has used account management privileges.
-	Security Assessment found 59 grants of system privilege grants on your target database.
<!-- Image 8-->
<!-- Maybe add in the Evil Rich part-->

### **Step 4:** 
- At the top of the report, click **Advisory** to filter the report to show only the Advisory findings.
<!-- Image -->
-	Deselect all other risk levels.
-	Scroll through the report to review the findings. For example, the following findings have a Pass status.
<!-- Image -->
-	User Accounts in SYSTEM or SYSAUX Tablespace Case-Sensitive Passwords
<!-- Image -->
Users with Default Passwords
<!-- Image -->
-	Password Verifiers
-	User Parameters
-	Users with Unlimited Password Lifetime
-	System Privileges Granted to PUBLIC
<!-- Image -->
-	Roles Granted to Public
<!-- Image -->
-	Column Privileges Granted to PUBLIC DBA Role
<!-- Image -->
-	....and more

### **Step 5:** 
-	In the Oracle Data Safe Console, click the **Home** tab, and then click **Security Assessment**.
-	On the **Security Assessment** page, select the check box for your target database, and then click **Assess**.
-	In the **Last Generated Report** column, click the View Report link. The Comprehensive Assessment report is displayed.
-	View the totals for the risk levels. If you fixed any of the previous risks, then the totals will be lower than in the first assessment.
-	Check the A**ccount Management Privileges** entry in the Evaluate category. Notice that EVIL_RICH is no longer listed.
-	To compare the results with the first assessment, do the following:
-	Click the **Reports** tab.
-	Click **Security Assessment**.
-	Click **Comprehensive Assessments**.
-	Click the previous assessment report to open it.
-	**Note:** Currently, there's no compare functionality in the product so to compare assessment results, you need to view both reports and manually compare.

## Part 3. Assess Users with Oracle Data Safe
-	Using Oracle Data Safe, assess user security in your target database by using the User Assessment feature and fix issues.

### **Step 1:** 
-	Navigate to the Oracle Data Safe Service Console
-	In the Oracle Data Safe Console, click the **Home** tab, and then click **User Assessment**. The User Assessment page is displayed.
<!-- Image 3.1-->
- Select the check box for your target database, and click Assess.
<!-- Image 3.2-->
-	Wait for the report to generate.
-	When the report is generated, view the totals in the Critical Risk, High Risk, Medium Risk, and Low Risk columns.
-	In the Last Generated Report column, click View Report. The User Assessment report is displayed.
<!-- Image 3.3-->

### **Step 2:** 
-	View the **User Risk** chart. This chart compares the number of critical, high, medium, and low risk users.
-	View the **User Roles** chart. This chart compares the number of users with the DBA, DV Admin, and Audit Admin roles.
<!-- Image 3.4-->
-	Click the second small circle below the charts to view the third and fourth charts.
-	View the **Last Password Change** chart. This chart shows you the number of users who have changed their passwords in the last 30 days, the last 30-90 days, and 90 days ago or more.
-	View the **Last Login** chart. This chart shows you the number of users that logged in in the last 24 hours, in the last week, within the current month, within the current year, and a year ago or more.
<!-- Image 3.5-->

### **Step 3:** 
-	Click the + sign to view the list of columns that you can display in the table. Add and remove columns as you wish, and then close the list.
<!-- Image 3.6-->
-	In the **Audit Records** column, click **View Activity** for the following users to view the audit records that they generated. Filters are automatically applied to **Operation Time** and **User Name**. Click Back to **User Assessment** report to return to the **User Assessment** report.
<!-- Image 3.7-->
-	SECURE_STEVE: Notice that SECURE_STEVE has not generated any audit records. This use may be a rogue user.
<!-- Image 3.8-->
-	DBA_DEBRA: Notice that DBA_DEBRA has several login failures. Some other user may be trying to log in with this account.
-	DBA_DEBRA: Notice that DBA_DEBRA has the Audit Admin role, but has not generated any audit records.
-	View more detail about DBA_DEBRA:
-	In the table, click DBA_DEBRA. The **User Details** dialog box is displayed.
-	On the right, expand the roles to view the privileges.
-	On the left, click the question mark next to **Risk**. Here you can review the factors that designate a user as Critical, High, Medium, or Low risk.
-	Click outside the dialog box to close it.
-	Close the User Details dialog box.

### **Step 4:** 
<!-- Figure out if SQL developer parts should be kept -->
-	In SQL Developer, run the following code to drop SECURE_STEVE:
<!-- Image 3.9-->
-	Run the following code to revoke the AUDIT_ADMIN role from DBA_DEBRA:
<!-- Image 3.10-->

### **Step 5:** 
-	Return to Oracle Data Safe.
-	Click the **Home** tab, and then click **User Assessment**.
-	Select the check box for your target database, and then click **Assess**.
-	Click **View Report**.
-	Look for changes in the **User Assessment** report. Notice that DBA_DEBRA no longer has the AUDIT_ADMIN role.

## Part 4. Discover Sensitive Data with Oracle Data Safe
### **Step 1:** 
-	Navigate to the Oracle Data Safe Service Console
-	To access the **Data Discovery** wizard, click the **Home** tab, and then click **Data Discovery**.
<!-- Image 4.1-->
-	On the Select Target for Sensitive Data Discovery page, your target database is listed.
-	Often, you want to perform data discovery against a production database where you can get an accurate and up-to-date picture of your sensitive data. You can discover sensitive data in the source database (a production or copy) and mask the cloned copies of this source database. Or, you can simply run a data discovery job on the actual database that you want to mask.
-	Select your target database, and then click **Continue**.
<!-- Image 4.2-->
-	Next, the **Select Sensitive Data Model** page is displayed. On this page, you can create a new sensitive data model, select an existing one from the Library, or import a file-based sensitive data model.
<!-- Image 4.3-->
-	Leave **Create** selected.
-	Name the sensitive data model as **SDM1**.
-	Enable **Show and save sample data** so that Data Discovery retrieves sample data for each sensitive column, if it's available.
-	Select your resource group.
-	Click **Continue**.
-	On the **Select Schemas for Sensitive Data Discovery** page, select the schema that you want Data Discovery to search. In this case, select the **HCM1** schema, and click **Continue**.
<!-- Image 4.4-->
-	On the **Select Sensitive Types for Sensitive Data Discovery** page, you select the sensitive types that you want to discover. Data Discovery categorizes its sensitive types as Identification Information, Biographic Information, IT Information, Financial Information, Healthcare Information, Employment Information, and Academic Information. Do the following:
-	**Expand all** the categories by moving the Expand All slider to the right to view each sensitive type. Notice that you can select individual sensitive types, sensitive categories, and all sensitive types.
-	Scroll down the list and review the sensitive types available.
<!-- Image 4.5-->
-	Return to the top of the list and select the **Select All** check box.
-	At the bottom of the page, select the **Non-Dictionary Relationship Discovery** check box.
-	Oracle Data Safe automatically discovers referential relationships defined in the data dictionary. The **Non-Dictionary Relationship Discovery** feature helps to identify application-level parent-child relationships that are not defined in the data dictionary. It helps discover application-level relationships so that data integrity is maintained during data masking.
-	When you are ready to start the data discovery job, click **Continue**.
-	Wait for the job to finish.
<!-- Image 4.6-->
-	If the job is successful, the **Detail** column states Data discovery job finished successfully, and you can click **Continue**. Otherwise, you need to click **Back** or **Exit** and investigate the issue.

### **Step 2:** 
-	On the **Non-Dictionary Referential Relationships** page, you are presented with a list of potential non-dictionary (application level) referential relationships that Data Discovery found by using column name patterns and column data patterns. Do the following:
-	To view all of the columns, move the **Expand All** slider to the right. Data Discovery found some potentially sensitive columns (non-dictionary referential relationships) in the PU_PETE schema.
<!-- Image 4.7-->
-	Click **Save** and **Continue**.
-	The **Sensitive Data Discovery Result** page is displayed. On this page, you can view and manage the sensitive columns in your sensitive data model. Your sensitive data model is saved to the Library.
<!-- Image 4.8-->
-	Notice that Data Discovery found sensitive columns in all three sensitive categories that you selected. To view the sensitive columns, move the **Expand All** slider to the right. The list includes the following:
-	Sensitive columns discovered based on the sensitive types that you selected
-	Dictionary-based referential relationships
-	Non-dictionary referential relationships
-	Take a look at how the sensitive columns are organized. Initially, they are grouped by sensitive categories and sensitive types.
-	To list the sensitive columns by schema and table, select **Schema View** from the drop-down list next to the **Expand All Slider**. **Schema View** is useful for quickly finding a sensitive column in a table and for viewing the list of sensitive columns in a table. For example, in the EMPLOYEES table there are several sensitive columns listed.
-	If needed, you can add and remove sensitive columns from your sensitive data model. Sensitive columns that have a check box are removable. To remove a sensitive column from your sensitive data model, you deselect its check box. You can use the **Add** button to add more sensitive columns.
-	Notice that some of the sensitive columns do not have a check box. These are dependent columns. They have a relationship with their parent column. For example, in the EMPLOYEES table, JOB_ID is listed. It has a relationship defined in the Oracle data dictionary to the JOBS.JOB_ID sensitive column. If you remove a sensitive column that has a referential relationship, both the sensitive column and referential relationship are removed from the sensitive data model. Therefore, if you deselect JOBS.JOB_ID, then EMPLOYEES.JOB_ID is removed too.
-	View the sample data for the HCM1.SUPPLEMENTAL_DATA.LAST_INS_CLAIM column.
-	The sensitive type is **Healthcare Provider** and the discovered sensitive column is LAST_INS_CLAIM, which has values such as Cavity and Hair Loss. Your value may be different. This column isn't a Healthcare Provider type of column and thus it is a false positive. You can deselect this column. Being able to remove a sensitive column is important when your sensitive data model includes false positives. To be able to recognize false positives, it helps to know your data well.

-	**Tip:** To quickly locate a sensitive column, enter the name or part of the name in the search box.

### **Step 3:** 
-	Suppose that you're missing some sensitive columns in your sensitive data model. While working in the Data Discovery wizard, you can backtrack to reconfigure and rerun the data discovery job. You can repeat the process as many times as you need until you feel that your sensitive data model is accurate. Try the following:

-	Click **Back** 
-	Now you are on the **Select Sensitive Types for Sensitive Data Discovery** page. Here you can change your sensitive type selections and choose whether to include non-dictionary referential relationships in the search.
-	Select all of the sensitive categories.
<!-- Image 4.9-->
-	Deselect **Non-Dictionary Relationship Discovery**.
<!-- Image 4.10-->
-	To rerun the data discovery job, click **Continue**.
-	When the job is finished, click **Continue**. Because you chose to not discover non-dictionary referential relationships, the wizard takes you directly to the **Sensitive Data Discovery Result** page.
-	Expand all of the sensitive columns and review the results.
<!-- Image 4.11-->
-	To view the newly discovered sensitive columns, click **View newly discovered sensitive columns only**. Notice that Data Discovery found additional sensitive columns.

### **Step 4:** 
-	Scroll down and click Report at the bottom right corner of the screen.
The report shows you a chart that compares sensitive categories. You can also view totals of sensitive values, sensitive types, sensitive tables, and sensitive columns. The table at the bottom of the report displays individual sensitive column names, sample data for the sensitive columns, column counts based on sensitive categories, and estimated data counts.
<!-- Image 4.12-->
-	Analyze the data:
-	To drill-down into a sensitive category in the chart, position your mouse over the chart, and then click the **Expand** button.
<!-- Image 4.13-->
-	To drill-up, position your mouse over an expanded sensitive category, and then click the **Collapse** button.
-	To enlarge the chart, click the **Expand** button (double-arrows) in the bottom right corner. View the chart and click **Close**.
-	Expand the list of sensitive columns and review the information.
<!-- Image 4.14-->
-	Click **Exit**.
<!-- Image 4.15-->
-	To access the report from the Reports tab, do the following:
-	Click the **Reports** tab.
<!-- Image 4.16-->
-	Scroll down, and under **Discovery Reports**, click **Data Discovery**.
-	Click your sensitive data model to open the report.

### **Step 5:** 
-	Click the **Library**  tab.
-	Click **Sensitive Data**  Models.
-	The Sensitive Data Models page is displayed, listing the sensitive data models to which you have access. For each sensitive data model, you can view information about when your sensitive data model was created, when it was last updated, and who owns it.
<!-- Image 4.17-->
-	Click the name of your sensitive data model to open it.

<!-- Image 4.18-->
-	To return to the **Sensitive Data Models** page, click the **Library** tab, and then click **Sensitive Data Models**.
-	If you need to remove your sensitive data model from the Library, you can select the check box for it, and click **Delete**.


### **Step 6:** 
- Select the check box for your sensitive data model.
- Click **Download**. Your sensitive data model is downloaded to your browser.
- Open the file, and review the XML code.
- Save the file to your desktop as **SDM1.xml**, and then close the file.

## Part 5. Verify Sensitive Data Model with Oracle Data Safe
- Using Oracle Data Safe, verify a sensitive data model by using the verification option in the Library and by using the Data Discovery wizard.

### **Step 1:** 
- Please visit Lab 4: Configuring a development system for use with your EXACS database for instructions to securely configure ExaCS to connect using Oracle SQL Developer, SQLXL and SQL*Plus. <!-- Need to update this to SQL Dev Connection-->

### **Step 2:** 
- On the SQL Worksheet, run the following command to add an AGE column to the EMPLOYEES table.
ALTER TABLE HCM1.EMPLOYEES ADD AGE NUMBER;  <!-- Need to update this as a code snippet-->
- Click the **Refresh** button to view the newly added column.

### **Step 3:** 
-	Navigate to the Oracle Data Safe Service Console
- In the Oracle Data Safe Console, click the **Library** tab, and then click **Sensitive Data Models**.
- Select the check box for your sensitive data model that you created in Discovery Lab 1 - Discover Sensitive Data with Oracle Data Safe (**SDM1**).
- Click **Verify Against Target**.
<!-- Image-->
- On the **Select Target for Data Model Verification** page, select your target database, and click **Continue**.
The verification job is started.
<!-- Image-->
- When the job is finished, notice that the **Detail** column reads Data model verification job finished successfully.
- Click **Continue**.
- On the **Data Model Verification Result** page, notice that there are no differences to report. The verification job did not find the new sensitive column, AGE.
- The verification feature checks whether the sensitive columns in the sensitive data model are present in the target database. If there are some present in the sensitive data model, but missing in the target database, it reports them. In addition, it reports new referential relationships for the columns already present in the sensitive data model. It does not, however, discover ALL the relationships.
<!-- Image-->
- Click **Continue**

### **Step 4:** 
- On the **Sensitive Data Model: SDM1** page, click **Add**. The **Add Sensitive Columns** dialog box is displayed.
<!-- Image-->
- Expand the **HCM1** schema, and then the **EMPLOYEES** table.
- Select the **AGE** column.
<!-- Image-->
- At the top of the dialog box in the **Sensitive Type** field, enter **age**. AGE is automatically retrieved as a sensitive type and you can select it.
<!-- Image-->
- Scroll to the bottom and click **Add to Result**. Your sensitive data model is updated to include the AGE column.
- To verify, enter age in the search box. HCM1.EMPLOYEES.AGE should be listed under **Biographic Information**.
<!-- Image-->
- Click **Save and Continue**.
- Click **Exit**.

### **Step 5:** 
- Return to SQL Developer.
- On the SQL Worksheet, run the following commands to drop the HCM1.EMPLOYEES.AGE column.
ALTER TABLE HCM1.EMPLOYEES DROP COLUMN AGE; <!-- Need to update this as a code snippet-->
- To verify that the EMPLOYEES table no longer has an AGE column, run the following script:
SELECT AGE FROM HCM1.EMPLOYEES; <!-- Need to update this as a code snippet-->
- Notice that the AGE column is gone and you receive an "Invalid Identifier" message when you run the command.
- If the AGE column is still there, click the **Refresh** button to refresh the table.

### **Step 6:** 
- Return to Oracle Data Safe.
- Click the **Home** tab, and then click **Data Discovery**.
<!-- Image-->
- On the **Select Target for Sensitive Data Discovery** page, select your target database, and then click **Continue**.
<!-- Image-->
- The **Select Sensitive Data Model** page is displayed.
- For **Sensitive Data Model**, select **Pick from Library**, and then click **Continue**. The **Select Sensitive Data Model** page is displayed.
<!-- Image-->
- Select your sensitive data model, **SDM1**.
- Scroll down to the bottom of the page and select **Verify if SDM** is compatible with the target.
<!-- Image-->
- To start the verification job, click Continue.
- If the job finishes successfully, click **Continue**. The **Data Model Verification Result** page is displayed.
- Expand **Missing sensitive columns**, and then HCM1. The Data Discovery wizard identifies the AGE column as missing from the database.
<!-- Image-->

### **Step 7:** 
- You can manually update your sensitive data model while continuing to work in the Data Discovery wizard. In which case, you simply deselect your sensitive column and save your sensitive data model. This part, however, shows you another way to do it from the Library.

- Click **Exit** to exit the Data Discovery wizard.
- Click the **Library** tab, and then click **Sensitive Data Models**.
- Click your sensitive data model to open it.
- Search for **AGE**.
<!-- Image-->
- In the list of sensitive columns, deselect HCM1.EMPLOYEES.AGE.
- Your sensitive data model is now updated and accurate.
- Click **Save** then **Exit**.

## Part 6. Update a Sensitive Data Model with Oracle Data Safe
- Using Oracle Data Safe, perform an incremental update to a sensitive data model by using the Data Discovery wizard.
### **Step 1:** 
- Please visit Lab 4: Configuring a development system for use with your EXACS database for instructions to securely configure ExaCS to connect using Oracle SQL Developer, SQLXL and SQL*Plus. <!-- Need to update this to SQL Dev Connection-->

### **Step 2:** 
- On the SQL Worksheet, run the following commands to add an AGE column to the EMPLOYEES table.
ALTER TABLE HCM1.EMPLOYEES ADD AGE NUMBER;
<!-- Need to update this as a code snippet-->
- On the Navigator tab, click the **Refresh** button.
- AGE is added to the bottom of the list in the EMPLOYEES table.

### **Step 3:** 
-	Navigate to the Oracle Data Safe Service Console
- In the Oracle Data Safe Console, click **Data Discovery**. The Select Target for Data Discovery page is displayed.
<!-- Image-->
- Select your target database, and then click **Continue**. The **Select Sensitive Data Model** page is displayed.
<!-- Image-->
- For **Sensitive Data Model**, click **Pick from Library**.
<!-- Image-->
- Click **Continue**. The **Select Sensitive Data Model** page is displayed.
- Select your sensitive data model (**SDM1**).
<!-- Image-->
- Leave **Update the SDM with the target** selected.
- Click **Continue**. The wizard launches a data discovery job.
- When the job is finished, notice that the **Detail** column reads **Data discovery job finished successfully**.
- Click **Continue**. The **Sensitive Data Model: SDM1 page** is displayed.
- Notice that you have the newly discovered sensitive column, AGE. Only newly discovered columns are displayed at the moment.
- **Expand all** of the nodes.
- To view all of the sensitive columns in the sensitive data model, click **View all sensitive columns**.
- You can toggle the view back and forth between displaying all of the sensitive columns or just the newly discovered ones.
- Click **Exit**.

## Part 6. Create a Sensitive Type and Sensitive Category with Oracle Data Safe

### **Step 1:** 
-	Navigate to the Oracle Data Safe Service Console
- In the Oracle Data Safe Console, click the **Library** tab, and then click **Sensitive Types**. The Sensitive Types page is displayed. On this page you can view predefined sensitive types and manage your own sensitive types.
<!-- Image-->
- Scroll through the list and become familiar with the different sensitive types available. The list contains predefined sensitive types only.
<!-- Image-->
- Move the **Hide Oracle Predefined** slider to the right. The list removes the Oracle defined sensitive types, showing only the ones that you have defined.
<!-- Image-->
- Move the slider back to the left.
- To find out how many sensitive types exist in the Library, scroll to the bottom of the page. The list contains 128 items.
- To sort the list by sensitive category, position your cursor over the **Sensitive Type Category** header, and then click the arrow.
- To sort the list by sensitive types, position your cursor over the **Sensitive Type Name** header, and then click the arrow.
- To view the definition for a sensitive type, click directly on any one of the sensitive types. The **Sensitive Type Details** dialog box is displayed.
<!-- Image-->
- View the sensitive type's short name, description, column name pattern (regular expression), column comment pattern (regular expression), column data pattern (regular expression), the search pattern semantic (And or Or), the default masking format associated with the sensitive type, and the sensitive category and resource group to which the sensitive type belongs.
- Click **Close** to close the dialog box.
- To check if there is a sensitive type that discovers department IDs, in the search field, enter **Department**. The search finds **Department Name**, but nothing for department IDs.
<!-- Image-->
- Clear the search field, and then press **Enter** to restore the list.
- Keep this page open because you return to it later in the lab.

### **Step 2:** 
- Please visit Lab 4: Configuring a development system for use with your EXACS database for instructions to securely configure ExaCS to connect using Oracle SQL Developer, SQLXL and SQL*Plus. <!-- Need to update this to SQL Dev Connection-->
- Run the following script:
SELECT * FROM HCM1.DEPARTMENTS; <!-- Need to update this to code snippet md-->
- Notice that the department ID values are 10, 20, 30, up to 270.

### **Step 3:** 
- Return to the **Sensitive Types** page in the Oracle Data Safe Console.
- Click **Add**.
- The **Create Sensitive Type** dialog box is displayed.
<!-- Image-->
- From the **Create Like** drop-down list, select **Employee ID Number**.
- In the **Sensitive Type Name** field, enter **Custom Department ID Number**.
- In the **Sensitive Type Short Name** field, enter **Custom Dept ID**.
- It is helpful to use a word like "Custom" when naming your own sensitive types to make them easier to search for and identify.
- In the **Sensitive Type Description** field, enter Identification number assigned to departments. Examples: 10, 20, 30…1000.
- In the **Column Name Pattern** field, enter:
(^|[_-])(DEPT?|DEPARTMENT).?(ID|NO$|NUM|NBR)<!-- Need to update this to code snippet md-->
- In the **Column Comment Pattern** field, enter:
(DEPT?|DEPARTMENT).?(ID|NO |NUM|NBR)<!-- Need to update this to code snippet md-->
- In the **Column Data Pattern** field, enter:
^[0-9]{2,4}$<!-- Need to update this to code snippet md-->

- For **Search Pattern Semantic**, select **And**.
- In the **Default Masking Format** field, enter **Identification Number**.
- In the **Sensitive Category** field, enter **Sensitive Category**. If you do not specify a sensitive category, the category is automatically named "Uncategorized."
- Select your resource group.
- Click **Save**.
- Your sensitive type is included in the list and is available in the Data Discovery wizard.
<!-- Image-->
- Move the **Hide Oracle Predefined** slider to the right to view your custom sensitive type in the list.
**All Done!**
