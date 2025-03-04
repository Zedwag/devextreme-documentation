---
id: dxDropDownList.Options.onValueChanged
type: function(e)
default: null
EventForAction: dxDropDownList.valueChanged
---
---
##### shortDescription
A function that is executed after the UI component's [value](/api-reference/10%20UI%20Components/dxDropDownList/1%20Configuration/value.md '{basewidgetpath}/Configuration/#value') is changed.

##### param(e): Object
Information about the event.

##### field(e.component): {WidgetName}
The UI component's instance.

##### field(e.element): dxElement
#include common-ref-elementparam with { element: "UI component" }

##### field(e.event): event
#include common-ref-eventparam This field is **undefined** if the value is changed programmatically.

##### field(e.model): Object
Model data. Available only if Knockout is used.

##### field(e.previousValue): Object
The UI component's previous value.

##### field(e.value): Object
The UI component's new value.

---
#####See Also#####
- [valueChangeEvent]({basewidgetpath}/Configuration/#valueChangeEvent)