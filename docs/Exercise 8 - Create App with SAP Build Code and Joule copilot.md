# Exercise 8 - Create App with SAP Build Code and Joule copilot

---

### Overview
In this unit, we want to create a customer loyalty program application. Customer can get bonus points for their purchases of products and can redeem these points.

Generative AI powered Development using Joule in SAP Build Code.

1. Data Model and Service Creation
1. Sample Data
1. Application Logic

<br>
<br>

**Introduction to SAP Build Code**

SAP Build Code is a turn-key development environment that combines runtime and design time capabilities with built-in solutions for DevOps and Application Lifecycle Management.

![](vx_images/586596853168213.jpg)


**Benefits of SAP Build Code**

* Achieve a clean core by developing side-by-side extensions with SAP Build Code
* Optimize developer efficiency with generative AI, productivity tools, and application lifecycle management
* Enable developers to build and extend powerful end-to-end business applications with programming language of choice
* Leverage interoperability between classic development and low-code development tools

**Key capabilities of SAP Build Code**
* Differentiate cloud solution with stable and future-proof foundation, solution becomes future proof and works with different editions of S/4HANA, and quality assurance options included
* Enable developers to code faster and smarter, code generation based on generative AI, Ease of Application Lifecycle Management
* Application and extension development, Integrate with SAP and non-SAP systems
* Easy access for all types of developers with centralized Lobby, for Fusion Development


### Create Project


The starting point for this tutorial is the lobby of SAP Build, the central entry point for all SAP Build products.

1. Launch the SAP Build Lobby (if you are not already in the Lobby)
2. Click on the Create button

![](vx_images/197476675768242.jpg)




3. Select Build an Application

![](vx_images/294907292022514.jpg)


4. Select SAP Build Code

![](vx_images/377155954262791.jpg)
  

5. Select Full-Stack Application

![](vx_images/203846331177604.jpg)


6. On the next screen, enter the following:

|  Input Field   |                      Input Value                       |
| -------------- | ------------------------------------------------------ |
| Project Name   | Customer_Loyal_AC87395U01                              |
| Description	 | Customer Loyalty Program Model and Services AC87395U01 |


![](vx_images/564323248896999.jpg)


7. Click the Create button.

* The creation of the project can take up to 1 minute.

8. Click on the Customer_Loyal_AC87395U01 project.

![](vx_images/555362819544506.jpg)


9. You might be asked to confirm the cookies settings by clicking OK (or Open Settings to update the settings)


![](vx_images/357583453270556.png)

10. SAP Build Code will be opened, based on SAP Business Application Studio - in the background.

* Please allow some time for SAP Build Code to open!
![](vx_images/243353682117047.jpg)


---

### Create Data Entities with Joule

In this lesson, we will create the data model and the services for the customer loyalty program application.

We could create the data model visually from the Storyboard or by writing the code manually. However, we are going to use the generative AI capabilities of Joule and SAP Build Code to generate the code. Thus, significantly reducing the time and effort required to develop the customer loyalty program application.

1. Launch the Joule digital assistant.

* Please wait for the digital assistant to open. If it fails to open then please refresh your browser.

![](vx_images/553322070958749.png)


2. Click on Open Guide > Data Model and Service Creation.
1. Click Open Joule

![](vx_images/452183659754199.png)


4. Generate the data model and services by copying and pasting the prompt into the box where it says ‘Ask Joule’.

>   
> Design a customer loyalty program application. Define 3 data entities: Customers, Purchases and Redemptions. Each customer must have the following fields: name, email, 7-digit customer number, total purchase value, total reward points, ‘total redeemed reward points’. All fields for each customer should be integer except name and email that will be stored as string. Purchases should include the following fields: purchase value, reward points and selected product. All fields in Purchases must be integer except selected product. Redemptions must have 1 field in integer: redeemed amount. Each purchase and redemption will be associated to a customer. Create 5 rows for each entity.
>   


5. Click Generate.

![](vx_images/41854164674294.png)

6. The code should be generated now below your prompt.

![](vx_images/419192848656766.png)


7. Accept the Code by clicking the Accept icon.

* Once you accept the code, you will see the update on the right side under the Storyboard tab.
* It can take up to 2 minutes for Joule to create the data models and services for you.

![](vx_images/258524327808232.png)


---


# Enhance Sample Data with Joule

In this lesson, we are going to use the generative AI capabilities of Joule and SAP Build Code to generate some sample data. This sample data will be used to test and preview the backend service of our customer loyalty program application.

### Enhance Customer Sample Data
1. Open the the Sample Data Editor in the Storyboard, by selecting Open Editor > Sample Data.

![](vx_images/119833407682871.png)

2. Select Customers data entity then click Enhance.

* This will open again Joule to modify the sample data.

![](vx_images/511363179646206.png)


3. Copy and paste the following Prompt into Joule and click Generate:

> Enhance my sample data with meaningful data. All customer numbers will be 7 digits and one customer must use the customer number 1200547. No field may be empty. Total purchase value must be smaller than 10000. Total reward points and total redeemed reward points both must be unround and different and always sum to one-tenth of total purchase value for each customer.


![](vx_images/351723722964513.png)


* Below your prompt, you can see the customer names, email adresses and purchases are created.

4. Accept the code created by Joule.

![](vx_images/136233566419355.png)


5. You see that the customer Number of one of the customers in the list has been updated to 1200547.

* This is required for demo purposes. Later in the workshop, we will be scanning a customer Loyalty Card that will have a barcode with this number. Thus, we will be able to retrieve exactly this record from the data entity.

![](vx_images/591094413289786.png)


### Enhance Purchases Sample Data

1. Select the Purchases data entity.
1. Enter 5 into the Number of Rows field beside Mock Data
1. Click the Add button to add 5 more rows to the entity.

![](vx_images/207714597160295.png)

4. Click Enhance.

1. Copy the following text for the Prompt in Joule

> Enhance my sample data with meaningful data using electronic office products. Each ‘purchaseValue’ will be between 50 and 1000. Ensure that each ‘rewardPoints’ is always one-tenth of the ‘purchaseValue’. Ensure that the ‘customer’ field is populated.

6. Paste the copied text into the Joule prompt, click Generate.

![](vx_images/524664386057360.png)


* Wait for Joule … Thinking … and the data to be generated. The AI generation may take a little while.

7. Accept the code created by Joule.

![](vx_images/382344589425446.png)


### Enhance Redemptions Sample Data

1. Select Redemptions data entity.

1. Click on Enhance.

![](vx_images/345083618309124.png)


3. Use the following Prompt in Joule:

> Ensure that each redeemed amount is different and between 10 and 100.

4. Click Generate. This may take a little time.

![](vx_images/409814826098681.png)


5. Accept the code created by Joule.

![](vx_images/132414545510681.png)

6. You should see the following after clicking Accept.

![](vx_images/441174904762766.png)




---


# Create Backend Logic with Joule


We have already created the entities, services and sample data with Joule. In this lesson, we will add some logic to our application. We would like to calculate the bonus points for each customer purchase. Additionally, we want to provide the logic for customers to redeem their bonus points.

### Purchases Backend Logic
1. In the Storyboard, click on one of the entities under Services and Open in Graphical Modeler

![](vx_images/387055531708276.png)


2. Select Purchases entity by clicking on the title.

* Note: if you can not see the Purchases entity you may have to zoom out the view.
3. Click on Add Logic.


![](vx_images/270594874622771.png)


4. Leave everything by the default value and click on Add

![](vx_images/592245476915562.png)


5. Select the Standard Event Create.

* That means this logic will be automatically executed if a new purchase is done.
6. Go to Open Code Editor > Application Logic.

* This will open Joule again to create the logic for us.

![](vx_images/23724171133190.png)


7. Use the following Prompt in Joule to create a backend logic:

> Reward points of each purchase will be the one-tenth of the purchase value. Each purchase value will be added to the total purchase value of the related customer. Each reward points will be added to the total reward points of the related customer.


8. Click Generate.

![](vx_images/586354429254387.png)


9. Joule created the following logic:

* Check if the customer exists
* Calculates the rewardPoints from the purchase value
* Updates the total purchase value and the total reward points in the customers entity
10. Accept the code created by Joule.

* Joule might generate different codes for the same prompt. So, you might have a different code for the backend logic which is completely fine if it does the same job. You can ignore this and keep working on the exercise.

![](vx_images/200634697434880.png)


### Redemptions Backend Logic
Now we continue with the Redemptions.

1. Go back to service.cds tab.

1. Select Redemptions entity by clicking on the title.

1. Click on Add Logic.

![](vx_images/21235993065279.png)


4. Click Add.

![](vx_images/372634497558636.png)


5. Select Create.

1. Go to Application Logic under Open Code Editor

![](vx_images/129334806671935.png)


7. Use the following Prompt in Joule to create a backend logic:

> Deduct the redemption amount from ‘totalRewardPoints’ of the related customer. Add the same redemption amount to the ‘totalRedeemedPoints’ of the related customer.


![](vx_images/47375841587064.png)


8. Accept the code created by Joule.

![](vx_images/32025860937318.png)

* Have a closer look at the generated code. It includes some logic to check if a customer has enough points for the redemption.

* Joule might generate different codes for the same prompt. So, you might have a different code for the backend logic which is completely fine if it does the same job. You can ignore this and keep working on the exercise.


9. Go back to Storyboard and open Service Center.

![](vx_images/70866304900163.png)


---


### Add External Data Resource

In this lesson, we will connect to an S4/HANA system to retrieve the product related data.

1. In Service Center go to SAP System and find the BTP destination S4HANA_Joule_Product (S/4 Product).

1. Click Add to CAP

Note: This destination is already configured by your subaccount admin. The destination is connected to a Sandbox API from SAP Business Hub. For more information about the api go to the SAP Business Accelerator Hub: https://api.sap.com/api/API_PRODUCT_SRV/overview


![](vx_images/489115691832554.png)


3. Go to Storyboard and check if the External Resource got updated.

Note: It may take a short time to update!

![](vx_images/289536059649543.png)


4. Go to service.cds tab and Add Entity

* You can drop the new entity anywhere

![](vx_images/197306101970622.png)


5. Select the data entity: S4HANA_Joule_Product.A_ProductBasicText

* Disable the Enable draft editing option.

6. Click Save

![](vx_images/366287269065190.png)

---


### Preparation for the SAP Build Apps Integration
If you want to create a customized UI with SAP Build Apps on top of it, we need to adjust some settings in the service.

To do this, we will use the Graphical Modeler to disable the “Draft Editing” mode for all three entity sets:

* Customers
* Purchases
* Redemptions
1. Select the Redemptions entity and the Redemptions details will appear on the right hand side.

![](vx_images/468667548200176.png)

2. Select Settings => Disable Draft Editing.

* If you do not see Settings may have to move the Show Details content to the left

![](vx_images/188206756462913.png)


3. Select Customers and disable Draft Editing

* You may have to move around to find Customers.


![](vx_images/537965869261108.png)


4. Select Purchases and disable Draft Editing

![](vx_images/352457117304074.png)



---





### UI Application
In this lesson, you will create a UI to display and test the content that we have already created for the customer loyalty program application.

1. Go back to the Storyboard and add a first UI application by clicking on the (+)

![](vx_images/249896536321378.jpg)

2. We will start with the user interface for the data entity Purchases. Enter the following values:
* Display name: Purchases
* Description: Manage Purchases
* Data Source: loyaltyProgramSrv

![](vx_images/45336896025847.jpg)


3. Click Next

![](vx_images/360966080917760.png)


4. Select Template-Based Responsive Application as the UI Application type.

![](vx_images/67770294830517.jpg)



5. Click Next

![](vx_images/365890393027578.png)


6. Select List Report Page

![](vx_images/172301066950180.jpg)

7. Click Next

![](vx_images/433970198341375.png)


8. Select the Purchases entity

1. Click Finish

![](vx_images/234161300922895.jpg)



10. Close the Page Map if needed.
You can repeat the same steps with the Customer and Redemption entity.

Customer:

* Display name: Customers
* Description: Manage Customers
* Data Source: loyaltyProgramSrv
* UI Application type: Template-Based Responsive Application
* UI Application Template: List Report Page
* Main Entity: Customers

>    
> Wait for the UI to create.
>    


Redemptions:

* Display name: Redemptions
* Description: Manage Redemptions
* Data Source: loyaltyProgramSrv
* UI Application type: Template-Based Responsive Application
* UI Application Template: List Report Page
* Main Entity: Redemptions


> Wait for the UI to create. You shoud see a message, that the files have been generated.

![](vx_images/214871422006023.png)



### Modify the UI for the Purchases
Now we are going to modify the UI for the purchases. We will include the products from S/4HANA as value help in the purchases and hide some fields.

1. Go back to the Storyboard.

1. Select the Purchases UI and open it in the Page Map.

* To see which is the Purchases UI, move mouse pointer over the UI to extend the displayed name.

![](vx_images/202981761667489.jpg)

3. We want to modify the Object page. Therefore click on the edit icon

![](vx_images/575531965886386.jpg)


4. In the Sections, expand General Information then expand Form and then expand Fields.
* Afterwards it will look like this:
![](vx_images/350550818840096.jpg)

> The reward points are calculated automatically by the logic Joule has created for us.


5. Delete the Reward Points field by pressing the trash bin icon next to it and Confirm the deletion.

![](vx_images/199200861484563.jpg)



Instead we want to select the products from S/4HANA for the purchases.

6. Click on the field Selected Product and change the Display Type in the properties on the right side to Value Help.
Set the following:

* Label: Product
* Value Source Entity: A_ProductBasicText
* keep the rest as it is.
7. Click Apply

![](vx_images/277332606455750.jpg)


---



### Deployment
The last step in SAP Build Code is to deploy the application to CloudFoundry. This includes also that destinations are created automatically that the ODATA services can be consumed also by other tools like SAP Build Apps.

1. For the deployment go to Task Explorer and click on the Play icon (Run) next to Enable Discovery and Deploy option.

* Please be patient as this may take a few minutes.

![](vx_images/243181755291955.png)


2. Check if the task has launched in the terminal

![](vx_images/30801428116370.png)



3. During the deployment a new page will be opened to to sign into Cloud Foundry.

![](vx_images/383491373431329.png)


4. Please note that this is a shared landscape so we need to minimise the size of your application. Before deploying the application to Cloud Foundry, we need to set the memory footprint of the application.

* Click on the EXPLORER icon and open the mta.yaml file.

![](vx_images/112653176703028.png)


* Search the memory parameter of your application and change the value to 64MB.

![](vx_images/547283245976415.png)


* Right click on the mta.yaml file and click Build MTA Project

![](vx_images/225181462118266.png)



* When the job is complete, you will see the following message in the Terminal.

![](vx_images/510823087923749.png)


5. Return to the Cloud Foundry Sign In and Targets page.

* Endpoint: https://api.cf.eu10-004.hana.ondemand.com

* Click on Open a new browser page to generate your SSO passcode


![](vx_images/329082654514027.png)


6. Enter academy-platform and click Sign in with alternative identity provider.

![](vx_images/45042862750895.png)


7. Copy the Temporary Authentication Code.

![](vx_images/465292736892972.png)


8. Paste the Code and Sign In.

![](vx_images/194792780329202.png)


9. Select the Organization EU10 or US10 and Space.

* Organization: sap-build-code-eu10
* Space: AC_SAPBUILD
* Press Apply

![](vx_images/599101842302869.png)



> After the successful deployment (May take several minutes) you will find the link of the deployed application in the terminal.





10. Use Ctrl+click to try it out!

![](vx_images/462902165879621.jpg)


---


11. Explore the UIs that you have created

![](vx_images/227113433949238.jpg)


12. Click on Go in each of the tiles (Customers, Purchases. Redemptions) in the Customer Loyal UI to see the generated data.

![](vx_images/567672991795813.png)


Congratulations! You have used the generative AI capabilities of Joule in SAP Build Code, to create a CAP service for a customer loyalty program application.