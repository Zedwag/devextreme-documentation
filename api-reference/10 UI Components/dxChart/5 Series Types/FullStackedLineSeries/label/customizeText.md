---
id: dxChartSeriesTypes.FullStackedLineSeries.label.customizeText
type: function(pointInfo)
notUsedInTheme: 
---
---
##### shortDescription
Customizes the text displayed by point labels.

##### param(pointInfo): Object
Information on the series point.

##### return: String
The text for the label to display.

---
This property accepts a function whose parameter exposes the following fields.

<table class="dx-table">
    <tr>
        <th>Field</th>
        <th>Description</th>
    </tr>
    <tr>
        <td>originalValue</td>
        <td>The raw value of the point.</td>
    </tr>
    <tr>
        <td>value</td>
        <td>The <i>originalValue</i> after <a href="/Documentation/ApiReference/UI_Components/dxChart/Configuration/valueAxis/#valueType">type cast</a>.</td>
    </tr>
    <tr>
        <td>valueText</td>
        <td>The <i>value</i> with an applied <a href="/Documentation/ApiReference/UI_Components/dxChart/Series_Types/FullStackedLineSeries/label/#format">format</a> and converted to string.</td>
    </tr>
    <tr>
        <td>originalArgument</td>
        <td>The raw argument of the point.</td>
    </tr>
    <tr>
        <td>argument</td>
        <td>The <i>originalArgument</i> after <a href="/Documentation/ApiReference/UI_Components/dxChart/Configuration/argumentAxis/#argumentType">type cast</a>.</td>
    </tr>
    <tr>
        <td>argumentText</td>
        <td>The <i>argument</i> with an applied <a href="/Documentation/ApiReference/UI_Components/dxChart/Series_Types/FullStackedLineSeries/label/#argumentFormat">format</a> and converted to string.</td>
    </tr>
    <tr>
        <td>percent</td>
        <td>The percentage value of the point.</td>
    </tr>
    <tr>
        <td>percentText</td>
        <td>The <i>percent</i> with an applied <a href="/Documentation/ApiReference/UI_Components/dxChart/Series_Types/FullStackedLineSeries/label/#format">format</a> and converted to string.</td>
    </tr>
    <tr>
        <td>total</td>
        <td>The sum of all values in the stack.</td>
    </tr>
    <tr>
        <td>totalText</td>
        <td>The <i>total</i> with an applied <a href="/Documentation/ApiReference/UI_Components/dxChart/Series_Types/FullStackedLineSeries/label/#format">format</a> and converted to string.</td>
    </tr>
    <tr>
        <td>point</td>
        <td>The <a href="/Documentation/ApiReference/UI_Components/dxChart/Chart_Elements/Point/">Point</a> object.</td>
    </tr>
    <tr>
        <td>seriesName</td>
        <td>The name of the series to which the point belongs.</td>
    </tr>
</table>

#include dataviz-ref-functioncontext

#####See Also#####
- [Value Formatting](/Documentation/Guide/Common/Value_Formatting/)