<div class="draftWatermark"></div>

# Exercise 7 - Integrate with SAP Build Work Zone
---


In the following steps, you will add the deployed HTML5 application to a site created in SAP Build Work Zone, standard edition.

## Prerequisites

We have already performed the following steps in the SAP BTP cockpit for you:
- Added an entitlement to SAP Build Work Zone, standard edition.
- Created a subscription to SAP Build Work Zone, standard edition.
- Assigned the `Launchpad_Admin` role collection.

  
## Check the running service and UI after deplyomemnt

Navigate to Instances and Subscriptions and launch SAP Build Work Zone, standard edition:

![](vx_images/325313981703135.png)

From the activity bar, click the **Channel Manager** icon.<br>
For the **HTML5 Apps** channel, click the **Update content** icon.

![](vx_images/80730659011112.png)

The deployed application is updated in the **HTML5 Apps** channel.

From the activity bar, click the **Content Manager** icon.<br>
Click **Content Explorer**, and then click the **HTML5 Apps** tile.

![](vx_images/35854450976522.png)

Click **HTML5 Apps** to browse the applications

![](vx_images/499102567118373.png)

Search for the **incidentmanagementXXX** application where **XXX** corresponds to your project suffix.

Verify that the **ID** column ends with **XXX.Incidents**.<br>
Select the checkbox for your application.<br>
Click **Add**.

The application is added to your **HTML5 Apps** content.

![](vx_images/261654492923856.png)

Go back to the **Content Manager**.<br>
Click **Create > Group**.


![](vx_images/158074159514134.png)

The **New Group** editor opens.

In the **Title** field, enter **Incident Management XXX**, where **XXX** corresponds to your project suffix.<br>
In the **All Apps** list, search for the **incidentmanagementXXX** app.<br>
Use the toggle in the **Assignment Status** column on the right to assign the application to the group.<br>
Click **Save**.

A group is added to your content.

![](vx_images/45431614543339.png)

Go back to **Content Manager**.<br>
Search for the **Everyone** role.<br>
Click on the **Everyone** role. A new editor opens.<br>

![](vx_images/594914367751002.png)

Click **Edit**.<br>
Search for the **incidentmanagementXXX** app, where **XXX** corresponds to your project suffix.<br>
Use the toggle in the **Assignment Status** column on the right to assign the application to **Everyone**.<br>
Click **Save**.

The application can now be viewed by everyone.

![](vx_images/216750681607498.png)

From the activity bar, click the **Site Directory** icon, and click the **+ Create Site** button.<br>

![](vx_images/277314441893079.png)


Name the site (i.e. **Adoption Lab**).

![](vx_images/210914585329309.png)

Click the **Go to site** icon. 

![](vx_images/110473747302976.png)

Click the **Incident Management XXX** tile, where XXX corresponds to your project suffix.
Your application is launched in a site.

![](vx_images/567833970879728.png)





## Summary

You have integrated your deployed application to Work Zone.
