# Exercise 2 - Refer to an SAP S/4HANA Cloud Service in Your Data Model
---

In this exercise, we will add an SAP S/4HANA Cloud service, the Business Partner, to our project and associate it with our incident management model.

![](vx_images/325096176622878.png)

![](vx_images/180396878915669.png)

##### Discover an SAP S/4HANA Cloud Service and Add it to Your Data Model

From the **Storyboard**, click "+" on the **External Resources** tile. This opens the **Service Center** on the left-hand side.

![](vx_images/509205977768349.png)

There, you can see the **SAP System** node. Technically, it contains destinations to OData services in your backend system that an administrator has set up for you. These can be services from an SAP S/4HANA system or from other SAP backend systems.

Expand **SAP System > lcapteched**, and select **ADOPTION_LAB_API_BUSINESS_PARTNER**.

You can now see the details of the chosen service, its entities, the properties for each entity, and general data about the service.<br>
Click **Add External Data Model** in the upper-right corner of the screen.<br>
This adds the chosen service to you project.

![](vx_images/598492050897106.png)

Return to the **Storyboard**. After a couple of seconds, the new service is displayed in the **External Resources** tile.

![](vx_images/234222255270663.png)

##### Associate a Business Partner Entity with the Incidents Entity

From the **Storyboard**, under **Data Models**, select an entity and click **Open in Graphical Modeler** to get back to the graphical modeler.

![](vx_images/367782484117154.png)

From the **Incidents** entity, click  the **Add Relationship** icon.<br>
Drag the end of line of the relationship to an empty space on the canvas and click the mouse button.

![](vx_images/134533916964505.png)

This creates a new association to a Business Partner entity. However, we don't see the Business Partner on the canvas. This is because it is in a different namespace than our own Incidents entity.

A new dialog appears.<br>
1. From the **Target Entity** dropdown list, select **API_BUSINESS_PARTNER-A_BusinessPartner**. <br>
2. Change the suggested **Property Name** to **customer**. <br>
3. Leave all the other suggestions (**Association** and **To-One**) as they are, and click **Create**.

![](vx_images/43290972958856.png)

You can now see the final data model:

![](vx_images/447214291160287.png)


## Summary

You have added an external reference to the SAP S/4HANA Cloud backend system and connected it to your **Incidents** data model.

---

### Add Sample Data



We will now populate our data model with some sample data so that we can test our service. Note that even though it says sample data, the data can be of two types:
- Fixed values that are part of your application and should be deployed along with the application. An example could be the data for **Urgency** if there is only a fixed set of urgencies that cannot be changed
- Sample data that is only used to test the services and applications that you create and that should not be part of a productive deployment.

Go to the **Storyboard** and from the **Data Models** tile, click the **Urgency** entity, and select **Add Sample Data**.<br>
The Sample Data Editor opens.

![](vx_images/233732661754306.png)

Change the **Mock Data** switch to **Off** and enter 3 as the number of rows.<br>
Click **Add**.<br>
Leave the **name** field empty.<br>
In the **descr** field, enter Low, Medium and High for each row respectively.

![](vx_images/268773366674401.png)

Now we will import data from a file to the **A_BusinessPartner** entity.

Open the [Customers](https://robin-qiu.github.io/BTP-CAP-Development-with-SAP-Build-Code---Bring-Your-Own-Tenant/vx_attachments/477573873607615/customers.csv ':include') :floppy_disk::floppy_disk::floppy_disk: file, and click the **Download** icon.

Alternatively, using a local text editor, create a local file named `customers.csv`.<br>
Add the following content to the file and save it locally:
```
BusinessPartner,FirstName,LastName
1001036,Daniel,Watts
1001038,Stormy,Weathers
1001039,Sunny,Sunshine
```

From the editor, select **A_BusinessPartner** and click **Import**.<br>
From the file selection dialog box that opens, select the 'customers.csv' file that you created.<br>
The data is added.

![](vx_images/175262150656873.png)

Now we will import data from a file to **Incidents** entity.

Open the [Incidents](https://robin-qiu.github.io/BTP-CAP-Development-with-SAP-Build-Code---Bring-Your-Own-Tenant/vx_attachments/477573873607615/incidents.csv ':include') :floppy_disk::floppy_disk::floppy_disk: file, and click the **Download** icon.

Alternatively, using a local text editor, create a local file named `incidents.csv`.
Add the following content to the file and save it locally:

```
ID,title,urgency_code,customer_BusinessPartner
3b23bb4b-4ac7-4a24-ac02-aa10cabd842c,Inverter not functional,H,1001036
3a4ede72-244a-4f5f-8efa-b17e032d01ee,No current on a sunny day,H,1001038
3ccf474c-3881-44b7-99fb-59a2a4668418,Strange noise when switching off Inverter,M,1001039
3583f982-d7df-4aad-ab26-301d4a157cd7,Solar panel broken,H,1001039
```

From the editor, select **Incidents** and click **Import**.<br>
From the file selection dialog box that opens, select the 'incidents.csv' file that you created.<br>
The data is added.

![](vx_images/573743529808339.png)

For the last step, we will import data from a file to the **Conversations** entity.<br>

Open the [Conversations](https://robin-qiu.github.io/BTP-CAP-Development-with-SAP-Build-Code---Bring-Your-Own-Tenant/vx_attachments/477573873607615/conversations.csv ':include') :floppy_disk::floppy_disk::floppy_disk: file, and click the **Download** icon.<br>

Alternatively, using a local text editor, create a local file named `conversations.csv`.<br>
Add the following content to the file and save it locally:

```
ID,incidents_ID,timestamp,author,message
2b23bb4b-4ac7-4a24-ac02-aa10cabd842c,3b23bb4b-4ac7-4a24-ac02-aa10cabd842c,1995-12-17T03:24:00Z,Harry John,Can you please check if battery connections are fine?
2b23bb4b-4ac7-4a24-ac02-aa10cabd843c,3a4ede72-244a-4f5f-8efa-b17e032d01ee,1995-12-18T04:24:00Z,Emily Elizabeth,Can you please check if there are any loose connections?
9583f982-d7df-4aad-ab26-301d4a157cd7,3583f982-d7df-4aad-ab26-301d4a157cd7,2022-09-04T12:00:00Z,Sunny Sunshine, please check why the solar panel is broken
9583f982-d7df-4aad-ab26-301d4a158cd7,3ccf474c-3881-44b7-99fb-59a2a4668418,2022-09-04T13:00:00Z,Bradley Flowers,What exactly is wrong?
```

From the editor, select **Conversations** and click **Import**.<br>
From the file selection dialog box that opens, select the 'conversations.csv' file that you created.<br>
The data is added.

![](vx_images/256062509682978.png)

## Summary

We have now added some sample data to two data models that we can use later to test the service that we will create.


---


### Create a Service (API)


After the creation of the data model (persistence layer), we will now select what to expose to the outside world as an API. This API can then be consumed by UI apps, workflows, etc. For this purpose, we will add several entities to a service. CAP will expose this service automatically as an OData service.

##### Create New Service Entities

We will add 4 entities to the service: Customers, Incidents, Conversations, and Urgency.

Go back to the **Storyboard** tab in SAP Business Application Studio.

In the **Storyboard**, from the **Services** tile, click **+** button, and input service name as **Processor**.
The CDS Graphical Modeler opens.

![](vx_images/184032481646313.png)

From the toolbar, click **Add Entity** and click **Entity1**.
![](vx_images/242923124964620.png)

The **New Projection** dialog box opens.


From the toolbar, click **Add Entity**, and click **Entity1**.

The **New Projection** dialog box opens.

Select the **teched.Incidents** entity, make sure that the **Enable draft editing** checkbox is selected, and click **OK**.<br>

![](vx_images/259833168419462.png)

The **Incidents** entity appears in the CDS Graphical Modeler.

![](vx_images/566714115289893.png)

Click **"Open Property Sheet"** icon and import the S/4HANA Cloud OData service

![](vx_images/402074199160402.png)

Browse the OData CDS file
![](vx_images/127424188057467.png)

Select the **A_BusinessPartner** entity

![](vx_images/312584391425553.png)


Select the **API_Busniess_Partner.A_BusinessPartner** entity, clear the **Enable draft editing** checkbox if not already cleared, and click **OK**.
The **A_BusinessPartner** entity appears in the CDS Graphical Modeler.


1. Click the **Show Details** icon, and select the **Projection** tab.
3. Clear the **all properties** checkbox, and select the following properties:
   
   a. BusinessPartner
    
   b. FirstName
   
   c. LastName

![](vx_images/318353620309231.png)

3. **IMPORTANT**: Change the name of the **A_BusinessPartner** entity to **Customers**.

![](vx_images/438594928098788.png)





From the toolbar, click **Add Entity** and click **Entity1**.

The **New Projection** dialog box opens.

Select the **teched.Conversations** entity, clear the **Enable draft editing** checkbox, and click **OK**.<br>
The **Conversations** entity appears in the CDS Graphical Modeler.

![](vx_images/582693940493533.png)

From the toolbar, click **Add Entity** and click **Entity1**.

The **New Projection** dialog box opens.

Select the **teched.Urgency** entity, clear the **Enable draft editing** checkbox, and click **OK**.<br>
The **Urgency** entity appears in the CDS Graphical Modeler.

![](vx_images/167643060220681.png)
 
Make sure that the **ProcessorService** contains the 4 entities that you just added.

![](vx_images/317314111543434.png)

##### Summary
You have now added a **Processor** service to your project. Essentially, this service will expose your data model as an OData V4, RESTful API to your application.

---


### Preview Your Service




Now that we have a service, we can preview it with sample data and with live data without having to deploy to the cloud. 

##### Preview with Sample Data

From the activity bar on the left, click the **Run Configurations** icon.
The **Run Configurations** view opens.

Click the default run configuration: **Run incident_managementXXX-1**.

In the **OData** section that opens, **Mock Data** is selected.

From the **Run Configurations** view, click the **Run Module** icon.

![](vx_images/137415347510788.png)

Wait until see the console output like below:
![](vx_images/30136006762873.png)

If the pop-ups are blocked by your browser, please unblock lik this:
![](vx_images/299246633708383.png)

After a couple of seconds, a new browser tab opens and a screen like the one below is displayed.

> Note: If you don't get a new tab, please check whether there is a blocker running in your browser. If so, please allow the SAP Business Application Studio domain to open a new tab.

![](vx_images/172454412187919.png)


You can see a preview of the service including the **ProcessorService** in the list of services on the right-hand side.<br>
From the **Customers** row, click the **View as code** icon to preview the list of customers with the sample data.<br>

The **Customers** sample data is displayed.<br>
The data is queried and exposed using OData V4. Please note that this service is run from an in-memory database that is automatically opened for you during the preview, so any modification to the data will not persist.

![](vx_images/342893437295058.png)


##### Preview with Live Data

Switch back to the tab that has SAP Business Application Studio with your project.<br>
We will now look at the second version of the preview, which uses live data. This time, the data for the business partner is actually fetched from the SAP S/4HANA Cloud system instead of from sample data.

To get there, first click the **Stop Preview** button.

![](vx_images/577664340642085.png)

From the activity bar, open the **Run Configurations** view.

Click the **API_BUSINESS_PARTNER** run configuration.<br>
In the **OData** section of the editor that opens, **Live Data** is selected.

From the **Run Configurations** view, click the **Run Module** icon.

![](vx_images/141003102046420.png)

After a couple of seconds, a new browser tab opens and a screen like this is displayed:

![](vx_images/353903386155788.png)

> Note: If you don't get a new tab, please check whether there is a blocker running in your browser. If so, please allow the SAP Business Application Studio domain to open a new tab.

A preview of the service opens and the **ProcessorService** appears in the list of services on the right-hand side.<br>
From the **Customers** row, click the **View as code** icon to preview the list of customers.<br>
This time you will get a lot more data than before. Also, the names are different. This is the real business partner data from the SAP S/4HANA backend.<br>

![](vx_images/573263798888774.png)

Go to SAP Business Application Studio, and click the **Stop Preview** button.

![](vx_images/103804727062761.png)


##### Summary
We have now previewed our service without any deployment.


