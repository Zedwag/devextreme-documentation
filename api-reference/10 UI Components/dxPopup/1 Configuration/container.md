---
id: dxPopup.Options.container
type: String | Element | jQuery
default: undefined
---
---
##### shortDescription
Specifies the container in which to render the UI component.

---
The default container is defined during the UI component's initialization. It is the viewport, the body element if the viewport is not found or the parent element if the previous two are absent.

The specified container affects some features of the {WidgetName}: the area to be shaded, behavior on scrolling, etc.

#include common-demobutton-named with {
    url: "https://js.devexpress.com/Demos/WidgetsGallery/Demo/Popup/Overview/",
    name: "Popup"
}
