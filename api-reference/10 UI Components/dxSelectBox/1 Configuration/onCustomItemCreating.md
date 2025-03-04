---
id: dxSelectBox.Options.onCustomItemCreating
type: function(e)
default: function(e) { if(!e.customItem) { e.customItem = e.text; } }
EventForAction: dxSelectBox.customItemCreating
---
---
##### shortDescription
A function that is executed when a user adds a custom item. Requires [acceptCustomValue](/api-reference/10%20UI%20Components/dxSelectBox/1%20Configuration/acceptCustomValue.md '{basewidgetpath}/Configuration/#acceptCustomValue') to be set to **true**.

##### param(e): Object
Information about the event.

##### field(e.component): {WidgetName}
The UI component's instance.

##### field(e.customItem): String | Object | Promise<any>
The field where to place a custom item.

##### field(e.element): dxElement
#include common-ref-elementparam with { element: "UI component" }

##### field(e.model): Object
Model data. Available only if you use Knockout.

##### field(e.text): String
The input field's text.

---
#include common-demobutton with {
    url: "https://js.devexpress.com/Demos/WidgetsGallery/Demo/SelectBox/SearchAndEditing/"
}

#####See Also#####
- [Create a User-Defined Item](/concepts/05%20UI%20Components/SelectBox/15%20Create%20a%20User-Defined%20Item.md '/Documentation/Guide/UI_Components/{WidgetName}/Create_a_User-Defined_Item/')