# Exercise 4 - Enhance Fiori Elements with  Custom Action and Fragment


## 0, Change the fiori to flexible layout
![](vx_images/image-38.png)

## 1, Add a field for entity **Conversations**
![](vx_images/image.png)
![](vx_images/image-1.png)
![](vx_images/image-2.png)

Name: image
Type: LargeBinary
![](vx_images/image-3.png)
Add Annotation as the following:
Annotation Target: Core.MediaType
Annotation Value: application/pdf

## 2, Add Object Page for entity Conversations
![](vx_images/image-4.png)
![](vx_images/image-5.png)
![](vx_images/image-6.png)
![](vx_images/image-7.png)
![](vx_images/image-8.png)
![](vx_images/image-9.png)
![](vx_images/image-10.png)
![](vx_images/image-11.png)

## 3, Test to upload PDF document to Conversations entity.
![](vx_images/image-13.png)
![](vx_images/image-14.png)
![](vx_images/image-12.png)
![](vx_images/image-15.png)
![](vx_images/image-16.png)
![](vx_images/image-17.png)
![](vx_images/image-18.png)
![](vx_images/image-19.png)

## 4, Add a custom controller in the objectpage of Conversations entity.

![](vx_images/image-20.png)
Controller Name: ConversationsController
![](vx_images/image-21.png)

![](vx_images/image-22.png)

Adjust the Controller code as the following:


```
sap.ui.define(['sap/ui/core/mvc/ControllerExtension','sap/base/security/URLWhitelist' ,'sap/ui/model/json/JSONModel'], function (ControllerExtension,URLWhitelist,JSONModel) {
	'use strict';

	return ControllerExtension.extend('incidentmanagement004.Incidents.ext.controller.ConversationsController', {
		// this section allows to extend lifecycle hooks or hooks provided by Fiori elements
		
		showPDF:async function(oEvent){

			var sImageUrl = oEvent.getModel().getBindings().filter( bn=>{ return bn.sPath=='image' }).at(0).vValue;
			let oPdfmodel = new JSONModel({
				Source: sImageUrl,
				Title: 'pdf',
				Height: "1000px"
			});
			URLWhitelist.add("blob");
			this.base.getExtensionAPI()._view.setModel(oPdfmodel,"pdf");
			this.base.getExtensionAPI()._view.getModel('pdfview').setData({"Viewshow":true});

			alert('hello hero');

		},
		
		
		
		override: {
			/**
             * Called when a controller is instantiated and its View controls (if available) are already created.
             * Can be used to modify the View before it is displayed, to bind event handlers and do other one-time initialization.
             * @memberOf incidentmanagement004.Incidents.ext.controller.ConversationsController
             */



			onInit: function () {
				// you can access the Fiori elements extensionAPI via this.base.getExtensionAPI
				// var oModel = this.base.getExtensionAPI().getModel();
				let oPdfview = new JSONModel({
					Viewshow: false
				});
				this.base.getView().setModel(oPdfview,"pdfview");
			}
		}
	});
});

```
## 5, Add a custom action and fragment in the objectpage of Conversations entity.
![](vx_images/image-23.png)
![](vx_images/image-24.png)
![](vx_images/image-27.png)
Action ID: DisplayPDF
Button Text: Display PDF Document
Handler File: ConversationsController.controller (incidentmanagement004.Incidents.ext.controller.ConversationsController.controller, JS)
Handler Button: showPDF

![](vx_images/image-25.png)

Title: PdfViewer
Fragment Name: PdfViewerFrag
![](vx_images/image-26.png)

![](vx_images/image-28.png)

```

<core:FragmentDefinition xmlns:core="sap.ui.core" xmlns="sap.m" xmlns:macros="sap.fe.macros">
<ScrollContainer id="_IDGenScrollContainer1"
		height="100%"
		width="100%"
		horizontal="true"
		vertical="true" visible="{pdfview>/Viewshow}">
		<FlexBox id="_IDGenFlexBox1" direction="Column" renderType="Div" class="sapUiSmallMargin">
			<PDFViewer id="_IDGenPDFViewer1" source="{pdf>/Source}"  title="{pdf>/Title}" height="{pdf>/Height}" >
				<layoutData>
					<FlexItemData id="_IDGenFlexItemData1" growFactor="1" />
				</layoutData>
			</PDFViewer>
		</FlexBox>
	</ScrollContainer>
</core:FragmentDefinition>

```

## 6, Test to view PDF document in custom Fragment

![](vx_images/image-30.png)
![](vx_images/image-29.png)
![](vx_images/image-31.png)
![](vx_images/image-33.png)
![](vx_images/image-34.png)
![](vx_images/image-35.png)
![](vx_images/image-36.png)
![](vx_images/image-37.png)












