---
id: dxPolarChart.Options.valueAxis.minVisualRangeLength
inherits: VizTimeInterval
default: undefined
notUsedInTheme: 
---
---
##### shortDescription
Specifies the minimum length of the [visual range](/api-reference/10%20UI%20Components/dxPolarChart/1%20Configuration/valueAxis/visualRange '/Documentation/ApiReference/UI_Components/dxPolarChart/Configuration/valueAxis/visualRange/').

---
Assign a number to this property if the visual range is set on a numeric axis. If the axis displays date-time values, assign one of the accepted string values or an object to this property. The object should contain one or several fields described in this section, for example:

---
##### jQuery

    <!-- tab: index.js -->
    $(function() {
        $("#polarChart").dxPolarChart({
            // ...
            valueAxis: {
                // ...
                minVisualRangeLength: { weeks: 2 }
            }
        });
    });

##### Angular

    <!-- tab: app.component.html -->
    <dx-polar-chart ... >
        <dxi-value-axis ... >
            <dxo-min-visual-range-length [weeks]="2"></dxo-min-visual-range-length>
        </dxi-value-axis>
    </dx-polar-chart>

    <!-- tab: app.component.ts -->
    import { Component } from '@angular/core';

    @Component({
        selector: 'app-root',
        templateUrl: './app.component.html',
        styleUrls: ['./app.component.css']
    })
    export class AppComponent {
        // ...
    }

    <!-- tab: app.module.ts -->
    import { BrowserModule } from '@angular/platform-browser';
    import { NgModule } from '@angular/core';
    import { AppComponent } from './app.component';

    import { DxPolarChartModule } from 'devextreme-angular';

    @NgModule({
        declarations: [
            AppComponent
        ],
        imports: [
            BrowserModule,
            DxPolarChartModule
        ],
        providers: [ ],
        bootstrap: [AppComponent]
    })
    export class AppModule { }


##### Vue

    <!-- tab: App.vue -->
    <template>
        <DxPolarChart ... >
            <DxValueAxis ... >
                <DxMinVisualRangeLength :weeks="2" />
            </DxValueAxis>
        </DxPolarChart>
    </template>

    <script>
    import DxPolarChart, {
        DxValueAxis,
        DxMinVisualRangeLength
    } from 'devextreme-vue/polar-chart';

    export default {
        components: {
            DxPolarChart,
            DxValueAxis,
            DxMinVisualRangeLength
        },
        data() {
            return {
                // ...
            }
        },
    }
    </script>

##### React

    <!-- tab: App.js -->
    import React from 'react';
    import PolarChart, {
        ValueAxis,
        MinVisualRangeLength
    } from 'devextreme-react/polar-chart';

    class App extends React.Component {
        render() {
            return (
                <PolarChart ... >
                    <ValueAxis ... >
                        <MinVisualRangeLength weeks={2} />
                    </ValueAxis>
                </PolarChart>
            );
        }
    }
    export default App;

---


#####See Also#####
- [wholeRange](/api-reference/10%20UI%20Components/dxPolarChart/1%20Configuration/valueAxis/wholeRange '/Documentation/ApiReference/UI_Components/dxPolarChart/Configuration/valueAxis/wholeRange/')
- [visualRangeUpdateMode](/api-reference/10%20UI%20Components/dxPolarChart/1%20Configuration/valueAxis/visualRangeUpdateMode '/Documentation/ApiReference/UI_Components/dxPolarChart/Configuration/valueAxis/#visualRangeUpdateMode')
