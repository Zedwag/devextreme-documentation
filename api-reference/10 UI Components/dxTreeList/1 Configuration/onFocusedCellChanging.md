---
id: dxTreeList.Options.onFocusedCellChanging
type: function(e)
default: null
EventForAction: dxTreeList.focusedCellChanging
---
---
##### shortDescription
A function that is executed before the focused cell changes. Applies only to cells in data rows.

##### param(e): Object
Information about the event that caused the function's execution.

##### field(e.cancel): Boolean
Allows you to cancel focusing a new cell.

##### field(e.cellElement): dxElement
#include common-ref-elementparam with { element: "to-be-focused cell" }

##### field(e.columns): Array<dxTreeListColumn>
The visible columns' properties.

##### field(e.component): {WidgetName}
The UI component's instance.

##### field(e.element): dxElement
#include common-ref-elementparam with { element: "UI component" }

##### field(e.event): event
#include common-ref-eventparam

##### field(e.isHighlighted): Boolean
**true** if the cell is highlighted; otherwise **false**, even if the cell's row is highlighted.

##### field(e.model): Object
Model data. Available only if you use Knockout.

##### field(e.newColumnIndex): Number
The index of the column the cell that should be focused belongs to.

##### field(e.newRowIndex): Number
The index of the row the cell that should be focused belongs to.

##### field(e.prevColumnIndex): Number
The index of the previously focused cell's column.

##### field(e.prevRowIndex): Number
The index of the previously focused cell's row.

##### field(e.rows): Array<dxTreeListRowObject>
The visible rows' properties.

---

<!-- %fullDescription% -->

<!-- import * from 'api-reference\10 UI Components\dxDataGrid\1 Configuration\onFocusedCellChanging.md' -->
