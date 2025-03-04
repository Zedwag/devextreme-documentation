To display a chart in the RangeSelector background, provide data for it using the [dataSource](/api-reference/10%20UI%20Components/dxRangeSelector/1%20Configuration/dataSource.md '/Documentation/ApiReference/UI_Components/dxRangeSelector/Configuration/#dataSource') property. Next, specify the fields to be used as the argument and value fields. To do this, use the **argumentField** and **valueField** properties within the [series](/api-reference/10%20UI%20Components/dxRangeSelector/1%20Configuration/chart/series '/Documentation/ApiReference/UI_Components/dxRangeSelector/Configuration/chart/#series') object. In case you have several chart series, their common settings can be specified within the [commonSeriesSettings](/api-reference/10%20UI%20Components/dxRangeSelector/1%20Configuration/chart/commonSeriesSettings.md '/Documentation/ApiReference/UI_Components/dxRangeSelector/Configuration/chart/#commonSeriesSettings') object.

	<!--JavaScript-->
	var rangeSelectorOptions = {
		dataSource: [
			{ x: 10, y1: 0, y2: 10 },
			{ x: 15, y1: 6, y2: 12 },
			{ x: 20, y1: 8, y2: 15 },
			{ x: 30, y1: 10, y2: 10 },
			{ x: 50, y1: 16, y2: 5 }
		],
		chart: {
			commonSeriesSettings: {
				argumentField: 'x'
			},
			series: [
				{ valueField: 'y1' },
				{ valueField: 'y2' }
			]
		}
	};

Additionally, you can [set up a color](/concepts/05%20UI%20Components/RangeSelector/10%20Visual%20Elements/40%20Background/50%20Setting%20Up%20a%20Color.md '/Documentation/Guide/UI_Components/RangeSelector/Visual_Elements/#Background/Setting_Up_a_Color') for the range selector's background using the **background**.**color** property. In this case, a chart will be displayed on the background that will be painted in the specified color.

Besides displaying a chart in the background, the RangeSelector UI component can be bound to the [Chart](/api-reference/10%20UI%20Components/dxChart '/Documentation/ApiReference/UI_Components/dxChart/') UI component in order to perform zooming and scrolling on the chart. Refer to the following help topic to learn more about these features: [Zooming and Panning Using the RangeSelector Component](/Documentation/Guide/UI_Components/Chart/Zooming_and_Panning/#Using_the_RangeSelector_Component).

#include common-demobutton-named with {
    url: "https://js.devexpress.com/Demos/WidgetsGallery/Demo/RangeSelector/ChartOnBackground/",
    name: "Chart on Background"
}
#include common-demobutton-named with {
    url: "https://js.devexpress.com/Demos/WidgetsGallery/Demo/Range_Selector/CustomizedChartOnBackground/",
    name: "Customized Chart on Background"
}