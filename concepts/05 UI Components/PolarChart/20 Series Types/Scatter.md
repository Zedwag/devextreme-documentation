With the *scatter* series type, data is displayed as a collection of points. This series type is often used to display radar points.

![PolarScatterSeriesType ChartJS](/images/ChartJS/PolarScatter.png)

To understand how polar charts are built, imagine how a chart in a rectangular coordinate system is transformed by rounding its argument axis.

![Transformation from Rectangular to Polar Coordinates PolarScatterSeriesType ChartJS](/images/ChartJS/PolarScatter_TransformationFromStandardChart.png)

PolarChart uses the *scatter* series type by default. But in some cases, you may need to specify this series type explicitly. For this purpose, assign *'scatter'* to the **type** property of the **series** configuration object.

    <!--JavaScript-->var polarChartOptions = {
        // ...
        series: {
            type: 'scatter'
        }
    };

To learn how to specify data for a chart series, refer to the [Data Binding](/Documentation/Guide/Data_Binding/Specify_a_Data_Source/Local_Array/) topic.

Note that you can use a spider web for polar charts displaying discrete data. For this purpose, set the UI component's [useSpiderWeb](/api-reference/10%20UI%20Components/dxPolarChart/1%20Configuration/useSpiderWeb.md '/Documentation/ApiReference/UI_Components/dxPolarChart/Configuration/#useSpiderWeb') property to **true**.

![SpiderWeb PolarScatterSeriesType ChartJS](/images/ChartJS/PolarScatter_useSpiderWeb.png)

You can change the default appearance using series properties. For instance, you can change the following.

*   **Point Color**  
    A color from the chart's [palette](/concepts/60%20Themes%20and%20Styles/20%20SVG-Based%20Components%20Customization/10%20Palettes/00%20Palettes.md '/Documentation/Guide/Themes_and_Styles/SVG-Based_Components_Customization/#Palettes') is used by default. Set a custom color using the series' [color](/api-reference/10%20UI%20Components/dxPolarChart/1%20Configuration/commonSeriesSettings '/Documentation/ApiReference/UI_Components/dxPolarChart/Configuration/commonSeriesSettings/') property.
    
*   **Point Properties**  
    Set up the series' [point](/api-reference/10%20UI%20Components/dxPolarChart/5%20Series%20Types/CommonPolarChartSeries/point '/Documentation/ApiReference/UI_Components/dxPolarChart/Configuration/commonSeriesSettings/point/') object (see the [Series Points](/concepts/05%20UI%20Components/PolarChart/10%20Visual%20Elements/020%20Series%20Points/10%20Series%20Points.md '/Documentation/Guide/UI_Components/PolarChart/Visual_Elements/#Series_Points') topic).
    
*   **Point Labels**  
    Make point labels visible by setting the **visible** property of the series' [label](/api-reference/10%20UI%20Components/dxPolarChart/5%20Series%20Types/CommonPolarChartSeries/label '/Documentation/ApiReference/UI_Components/dxPolarChart/Series_Types/ScatterSeries/label/') object. For details on other label properties, refer to the [Series Point Labels](/concepts/05%20UI%20Components/PolarChart/10%20Visual%20Elements/030%20Series%20Point%20Labels.md '/Documentation/Guide/UI_Components/PolarChart/Visual_Elements/#Series_Point_Labels') topic.

These and other properties that can be set for series of the *scatter* type are explained in the [ScatterSeries](/api-reference/10%20UI%20Components/dxPolarChart/5%20Series%20Types/ScatterSeries '/Documentation/ApiReference/UI_Components/dxPolarChart/Series_Types/ScatterSeries/') Reference section. Set the required series properties within the [series](/api-reference/10%20UI%20Components/dxPolarChart/1%20Configuration/series '/Documentation/ApiReference/UI_Components/dxPolarChart/Configuration/series/') object of the chart's configuration object.