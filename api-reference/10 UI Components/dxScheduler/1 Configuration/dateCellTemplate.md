---
id: dxScheduler.Options.dateCellTemplate
type: template
default: null
---
---
##### shortDescription
Specifies a custom template for day scale items.

##### param(itemData): Object
The data of the current date scale item.

##### param(itemIndex): Number
The item's index.

##### param(itemElement): dxElement
#include common-ref-elementparam with { element: "item" }

##### return: String | Element | jQuery
A template name or container.

---
#include common-demobutton with {
    url: "https://js.devexpress.com/Demos/WidgetsGallery/Demo/Scheduler/CellTemplates/"
}

[note]There is no **dateCellTemplate** in such views as "day" and "timelineDay".

#####See Also#####
- [Timetable](/concepts/05%20UI%20Components/Scheduler/050%20Timetable.md '/Documentation/Guide/UI_Components/Scheduler/Timetable/')
- [Custom Templates](/concepts/05%20UI%20Components/zz%20Common/30%20Templates/10%20Custom%20Templates.md '/Documentation/Guide/UI_Components/Common/Templates/#Custom_Templates')