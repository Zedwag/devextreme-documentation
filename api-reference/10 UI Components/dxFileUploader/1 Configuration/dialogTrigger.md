---
id: dxFileUploader.Options.dialogTrigger
type: String | Element | jQuery
default: undefined
---
---
##### shortDescription
Specifies the HTML element which invokes the file upload dialog.

---

#include common-demobutton with {
    url: "https://js.devexpress.com/Demos/WidgetsGallery/Demo/FileUploader/CustomDropzone/"
}

You can use a selector string, jQuery object or DOM element to specify the **dialogTrigger** property:

- String

    ---

        <!-- tab: JavaScript -->
        dialogTrigger: '.open-button'

    ---

- jQuery object
	 
    ---

        <!-- tab: JavaScript -->
        dialogTrigger: $('.open-button')

    ---

- DOM element

    ---

        <!-- tab: JavaScript -->
        dialogTrigger: $('.open-button')[0]

    ---
