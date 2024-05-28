# Exercise 3 - Create a List Report UI Application and Deploy to PostgreSQL on SAP BTP, hyperscaler option
---

After creating a service with several entities, we will now create a list report with an object page, based on the SAP Fiori elements technology.

## Create a New UI Application

Go back to the **Storyboard** tab in SAP Business Application Studio.<br>
In the **UI Applications** tab, click + (Add UI).<br>
The UI Application wizard opens.<br>

![](vx_images/465895673133297.png)

In the **Display Name** field, enter **Incidents**.<br>
From the **Data Source** dropdown list, select **Processor**.<br>
Click **Next**.<br>

![](vx_images/466856031254494.png)

You can choose the technology you want to use to create your new UI app. You have a choice between a Template-based, responsive application" representing SAP Fiori elements (FE), and a "Mobile-centric, freestyle application" representing the Mobile Development Kit (MDK).

For the **UI Application Type**, click the **Template-Based, Responsive Application** tile, and then click **Next**.

Here's some background that you can choose to skip:
Both UI application types create responsive apps that can be used on mobile devices and on desktops. However, FE users would rather start with desktops and MDK apps rather than with mobile. Both adhere to the templates, however, in the MDK case, it is a template that can be changed in whichever way the user wants. FE is more restricted with respect to changes to the template.  However, the resulting app always adheres to the newest SAP Fiori guidelines and comes with a lot of functionality out-of-the-box.

![](vx_images/389121490027570.png)

For the **UI Application Template**, click the **List Report Page** tile, and then click **Next**.

![](vx_images/124842263950172.png)

For the **Data Objects** step, fill in the following:

From the **Main entity** dropdown list,	select **Incidents**.<br>
From the **Navigation entity** dropdown list, select **None**.<br>
Click **Finish**.<br>

![](vx_images/351401395341367.png)

And there you go, with just 4 steps you have created a complete UI app on top of your service entity. After a few seconds, the new UI app is displayed in the **UI Applications** tile of the **Storyboard** tab.<br>
After some more seconds, the **Page Map** editor pops up on the side, showing the pages that were generated for the UI app.

![](vx_images/290922597922887.png)

We now have a fully functional list report and an object page. Both pages are automatically populated with all the fields from our Incidents service entity, except for the ones that don't make sense. For example, the ID field that contains a UUID is not included, since showing UUIDs does not make for a good user experience.

While we could now already start testing our UI application and would get a nice application, we will first optimize the UI in a couple of places.

## Adjust the List Page of Your UI Application

From the **Page Map** editor, select the **List Report** tile, and click the **Configure Page** pencil icon.

![](vx_images/242990500434987.png)

You can now see the details of this page.<br>
Expand the **Columns** section under the **Table** section, and see the properties of your service entity. It should look like this:

![](vx_images/20542858667481.png)

Click on **urgency_code**, and make the following updates on the right:

1. Change the **Label** to **Urgency** and click **Enter** to make the label look better. 

2. From the **Text** dropdown list, select **urgency/descr**.

3. From the **Text Arrangement** dropdown list, select **Text Only**. This will configure the list to show the description of the urgency instead of its code.

![](vx_images/257313062886378.png)

Under **Table > Columns**, select **customer_BusinessPartner**.

Change the **Label** to **Customer** and press **Enter** to make the the label look better.

 ![](vx_images/427701815840088.png)

Select **Table**.<br>
From the **Initial Load** dropdown list, select **Enabled**.

This enables an initial load of data so that you do not need to click the **Go** button to load it.

 ![](vx_images/583391758484555.png)

## Adjust the Object Page of Your UI Application and Add Value Helps

Click **Page Map** on the upper part of the editor to go back to the page map.<br>
Select the **ObjectPage** tile and click the **Configure Page** pencil icon.

![](vx_images/202052096065386.png)

Select the **Header** section. <br>
From the **Title** dropdown list, select **title**, so that the incident title appears in the header.

 ![](vx_images/398432552291947.png)
 
Under the **Sections** section, select **General Information** to update the urgency and customer fields with label and value help.

From **General Information > Form > Fields**, select **urgency_code**.<br>

Then, in the panel that opens on the right, in the **Label** field, change the text to **Urgency**, and then press enter.<br>
From the **Text** dropdown list, select **urgency/descr**. <br>
From the **Text Arrangement** dropdown list, select **Text Only**. <br>
From the **Display Type** dropdown list, select **Value Help**.<br>

![](vx_images/340894073703020.png)

The **Define Value Help Protperties** dialog box opens.

In the **Label** field, enter **Urgency**.<br>
From the **Value Description Property** dropdown list, select **descr**.<br>
From the **Text Arrangement** dropdown list, select **Text Only**.<br>


Leave the **Display as Dropdown** option switched on, and click **Apply**.<br>

![](vx_images/199342270431321.png)

Now we will carry out similar steps for the customer column.<br>
Only this time we will create a value help instead of a dropdown list because we expect the list of customers from the backend to be too huge to handle in a dropdown.<br>

From **General Information > Form > Fields**, select **customer_BusinessPartner**.<br>

In the panel that opens on the right, in the **Label** field, change the text to **Customer**, and press Enter.<br>
From the **Text** dropdown list, select **customer_BusinessPartner**. <br>
From the **Text Arrangement** dropdown list, select **Text Only**. <br>
From the **Display Type** dropdown list, select **Value Help**.<br>

![](vx_images/374061000558743.png)

[](/exercises/Ex7/images/customercolumnpage.png)

The **Define Value Help Protperties** dialog box opens.<br>
Switch off the **Display as Dropdown** option.<br>
Click **Add Column**.<br>
From the **Property** dropdown list, select **FirstName**.<br>  
Click **Add Column**.<br>
From the **Property** dropdown list, select **LastName**.<br>
Click **Apply**.<br>

![](vx_images/490884242976407.png)

## Add the Conversations Section to the Object Page

Now we will add the **Conversations** section next to the **General Information**.<br>

Select **Sections**, click + (Add Sections), and select **Add Table Section**.<br>

The **Add Table Section** dialog box opens.<br>

![](vx_images/277671409672042.png)

In the **Label** field, enter **Conversations**, and press **Enter**.<br>
From the **Value Source** dropdown list, select **conversations**.<br>
Click **Add**.<br>

![](vx_images/355352459118258.png)

Select **Conversations > Table > Columns**, click the + icon , and select **Add Basic Columns**.<br>

![](vx_images/207562894832661.png)

The **Add Basic Columns** dialog box opens.<br> 
From the **VColumns** dropdown list, select **author**, **timestamp**, and **message**.<br>
Click **Add**.<br>

![](vx_images/8923262649650.png)




Close the **Page Map** editor and navigate back to the **Storyboard** tab.

## Summary
You have now added a new UI application to your project.

---

<br>

### Add Application Logic to the Application


In this exercise, we will add a logic of automatic urgency determination.
Customers may forget to select the urgency when creating an incident, so whenever an "Urgent" appears in the title, the incident will automatically be marked as urgent.

##### Update Incident from the Incident's Subject

From the **Storyboard**, select the **Processor**, and click **Open in Graphical Modeler**.
The CDS Graphical Modeler opens.

Select the **Incidents** entity and click the **Add Logic** icon.

![](vx_images/498682644587171.png)

The **Add Application Logic** dialog box opens.
From the dialog box:

For the **Service Entity** field, make sure that the **ProcessorService.incidents** value is selected.

For the **Name** field, enter **changeUrgencyDueToSubject** for the value.

Click **Add**.

![](vx_images/544312663937425.png)

The application logic editor opens.
From the **CONFIGURATION** tab of the application logic editor, select the following options:

In the **Phase** section, select **Before**.

In the **Standard Event** section, select **Create** and **Update**.

Click **Open Code Editor > Application Logic**.

![](vx_images/28233307900270.png)

The application logic handler file opens.
In the **'changeUrgencyDueToSubject.js'** file, after the comment "//Your code here", add the following content:

```
const incident = request.data;
if (incident.title?.toLowerCase().includes("urgent")) {
      incident.urgency = {      
        code: "H",        
        descr: "High"        
      };
}
```      

The outcome should look like this:

![](vx_images/348955230501654.png)


We have now finished configuring the application and we can preview it.

##### Preview the Application

From the activity bar on the left of the page, click the **Run Configurations** icon. 

From the **Run Configurations** view, click the **Run Module** icon.

![](vx_images/561275100579870.png)

A preview of the application opens, showing the **Incidents** tile on the left.

Click the **Incidents** tile.
The list of incidents opens in a new tab.

Click the **Strange noise when switching off Inverter incident**, which has **Medium** urgency, and then click **Edit**.

Add the word **Urgent** to the beginning of the **Title** and click **Save**.

Go back to the list of incidents and see that the **Urgency** changed to **High**.

![](vx_images/198364398393646.png)

Go back to SAP Business Application Studio and click **Stop Preview** button.

##### Summary
We added application logic to the application. 

---

<br>

### Deploy Your Application


In this section, we will deploy the project to the Business Technology Platform (BTP), Cloud Foundry environment.

##### Deploy the project to BTP

We already completed the environment set up for you. This is what we did:

* Enabled the Cloud Foundry environment.
   
* Added an entitlement for SAP HANA Cloud.
   
* Added an entitlement for SAP HANA Schemas & HDI Containers.
   
* Added you as a member in a Cloud Foundry space.
   
Since these steps are completed, you can now select a space and deploy an application to the SAP BTP, Cloud Foundry environment.

Deployment is composed of 3 steps that are available from the **Task Explorer**:

1. Build an application.
   
2. Log in to the target space in the Cloud Foundry environment.
   
3. Deploy the application.
   
To start deployment:<br>

From the activity bar, click the **Task Explorer** icon.

Expand the **Deploy** section, select **Deploy incident_managementXXX**, and then click the **Run** icon.

![](vx_images/101135592297646.png)

A build starts and the **Cloud Foundry Sign In and Targets editor** opens.

- Enter the following Cloud Foundry endpoint **https://api.cf.eu10-004.hana.ondemand.com** .<br>
  **Important**: Sometimes, the system recommends the **https://api.cf.eu10.hana.ondemand.com** URL. Make sure you manually enter the **-004** part behind **eu10**.<br>

- Choose **SSO Passcode** as the authentication method.<br>

- Press the **Open a new browser page to generate your SSO passcode** link.<be>

![](vx_images/173655056885563.png)

- Next, provide the value **lcap-platform** and choose **Sign in with Alternative Identity Provider**.
![](vx_images/347285589157171.png)

This opens a new page, with a temporary passcode created for your user.

- Press the button on the right of the password to copy it to the clipboard as indicated here:

![](vx_images/529814230110584.png)

- Paste the copied passcode into the field **Enter your SSO Passcode** on the **Cloud Foundry Sign In and Targets editor** page.
- Click **Sign In**.

After a couple of seconds, the following page opens:

![](vx_images/176835270241710.png)

In this page:

- Choose the the organization.
- Choose the space.
- Click **Apply**.

The deployment starts and progress can be tracked in the Terminal.
It takes **several minutes** for the application to be deployed.

Since the default deployed database is HANA Cloud, it will fail to deploy the application with the message like this:

![](vx_images/557884004970729.png)

#### In our exercise, we will modify the deploy configuration files to switch the database to PostgreSQL on SAP BTP, hyperscaler option.

1. Input the CDS command to add PostgreSQL to the **mta.yaml** and **package.json** files.

`cds add postgres`

![](vx_images/202965572065297.png)

It will add some new configurations with PostgreSQL like below.

![](vx_images/154636051200283.png)


![](vx_images/5535359463020.png)


2. Remove HANA Cloud related configurations.

In **package.json** file, delete **hdb** and **@sap/cds-hana** from the **dependencies** part.
![](vx_images/440794672261215.png)


Change the CDS database configuration.

```
"[production]": {
        "kind": "postgres",
        "imp": "@cap-js/postgres"
      },
```

![](vx_images/501930284917867.png)      

In the mta.yaml file, delete HANA Cloud related configurations

Unser **resources** part, remove "**incident_managementXXX-service-db"** block

![](vx_images/503827120304181.png)

Remove **"incident_managementXXX-db"** block.
![](vx_images/137196439321485.png)


Under **modules** part, remove **"incident_managementXXX-db-deployer"** block.
![](vx_images/513280697830624.png)

In **"incident_managementXXX-srv"** module, remove the obsolete required resources.
![](vx_images/514576699025954.png)


Meanwhile, please check your subscribed PostgreSQL service plan and modify **"incident_managementXXX-postgres"** service-plan part in mta.yaml file.

![](vx_images/125352626006130.png)

![](vx_images/262191796027685.png)

At last, let's re-deploy the application and check the console output.


It may take **5 -10 minutes** to initialize the PostgreSQL database, so please be patient.

![](vx_images/68062669950287.png)



##### Check the running service and UI after deployment

Once Deploy is complete, copy or click on the URL that appears at the end of the Terminal logs under **Project OverviewURL**.<br>
For example, **https://<myaccount>.launchpad.cfapps.<myregion>.hana.ondemand.com/lcapincident_managementXXX.incident_managementLaunchpad-1.0.0**

![](vx_images/94881202341482.png)

Click the **Incidents** tile to open the application with a list of incidents.

It looks very much like the preview page from the last chapter. Indeed, it is almost the same page, but now everything is deployed and runs in the BTP account. <br>

![](vx_images/268432404923002.png)
##### Summary

This concludes this hands-on. In just a few chapters, and without writing code, you have created an OData service based on CAP and a corresponding UI application based on SAP Fiori elements, which you then deployed to the SAP Business Technology Platform. Your application complies to standard designs and comes with a lot of functionality out-of-the-box.

You can continue to next exercises to add unit tests and integrate the application to SAP Build Work Zone.





