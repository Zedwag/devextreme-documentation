---
id: dxDataGrid.Options.export
type: Object
---
---
##### shortDescription
Configures client-side exporting.

---
A user can click the **Export** button to save an Excel file with the exported data. Data types, sort, filter, and group settings are maintained.

![DevExtreme HTML5 JavaScript DataGrid Export Button](/images/DataGrid/exported_data.png)

The following instructions show how to enable and configure client-side export:

1. **Install or reference the required libraries**  
    This feature requires <a href="https://github.com/exceljs/exceljs" target="_blank">ExcelJS</a> v4+ and <a href="https://github.com/eligrey/FileSaver.js/" target="_blank">FileSaver</a> v2.0.2+. 

    ---
    ##### jQuery
        <!--HTML-->
        <head>
            <!-- ... -->
            <script src="https://cdnjs.cloudflare.com/ajax/libs/babel-polyfill/7.4.0/polyfill.min.js"></script>
            <script src="https://cdnjs.cloudflare.com/ajax/libs/exceljs/4.1.1/exceljs.min.js"></script>
            <script src="https://cdnjs.cloudflare.com/ajax/libs/FileSaver.js/2.0.2/FileSaver.min.js"></script>
            <!-- reference the DevExtreme sources here -->
        </head>

    ##### Angular   

        <!-- tab: Installation command -->
        npm install --save exceljs file-saver

        <!-- tab: tsconfig.app.json -->
        {
            "compilerOptions": {
                // ...
                "paths": {
                    // ...
                    "exceljs": [
                        "node_modules/exceljs/dist/exceljs.min.js"
                    ]
                }
            }
        }

    ##### Vue

        npm install --save exceljs file-saver

        
    ##### React

        npm install --save exceljs file-saver
        
    ---     

2. **Enable the export UI**   
    Set the **export**.[enabled](/api-reference/10%20UI%20Components/dxDataGrid/1%20Configuration/export/enabled.md '/Documentation/ApiReference/UI_Components/dxDataGrid/Configuration/export/#enabled') property to **true**. This property enables export for all columns. Set a column's [allowExporting](/api-reference/_hidden/dxDataGridColumn/allowExporting.md '/Documentation/ApiReference/UI_Components/dxDataGrid/Configuration/columns/#allowExporting') property to **false** to prevent it from being exported:

    ---
    ##### jQuery

        <!--JavaScript-->
        $(function () {
            $("#dataGridContainer").dxDataGrid({
                export: {
                    enabled: true
                },
                columns: [{ ...
                    allowExporting: false
                }, 
                    // ...
                ]
            });
        });

    ##### Angular   

        <!-- tab: app.component.html -->
        <dx-data-grid ... >
            <dxo-export [enabled]="true"></dxo-export>
            <dxi-column ...
                [allowExporting]="false">
            </dxi-column>
        </dx-data-grid>

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

        import { DxDataGridModule } from 'devextreme-angular';

        @NgModule({
            declarations: [
                AppComponent
            ],
            imports: [
                BrowserModule,
                DxDataGridModule
            ],
            providers: [ ],
            bootstrap: [AppComponent]
        })
        export class AppModule { }


    ##### Vue

        <!-- tab: App.vue -->
        <template>
            <DxDataGrid ... >
                <DxExport
                    :enabled="true"
                />
                <DxColumn ... 
                    :allow-exporting="false"
                />
            </DxDataGrid>
        </template>

        <script>
        import 'devextreme/dist/css/dx.common.css';
        import 'devextreme/dist/css/dx.light.css';

        import { DxDataGrid, 
            DxExport,
            DxColumn
        } from 'devextreme-vue/data-grid';

        export default {
            components: {
                DxDataGrid,
                DxExport,
                DxColumn
            }
        }
        </script>

    ##### React

        <!-- tab: App.js -->
        import React from 'react';
        import 'devextreme/dist/css/dx.common.css';
        import 'devextreme/dist/css/dx.light.css';

        import DataGrid, {
            Export,
            Column
        } from 'devextreme-react/data-grid';

        class App extends React.Component {
            render() {
                return (
                    <DataGrid ... >
                        <Export enabled={true} />
                        <Column ...
                            allowExporting={false}
                        />
                    </DataGrid>
                );
            }
        }
        export default App;

    ---

3. **Export the DataGrid**   
    Implement the [onExporting](/api-reference/10%20UI%20Components/dxDataGrid/1%20Configuration/onExporting.md '/Documentation/ApiReference/UI_Components/dxDataGrid/Configuration/#onExporting') handler and call the [exportDataGrid(options)](/api-reference/50%20Common/utils/excelExporter/exportDataGrid(options).md '/Documentation/ApiReference/Common/Utils/excelExporter/#exportDataGridoptions') method in it. In the code below, this method exports the DataGrid as is, but you can use [ExcelExportDataGridProps](/api-reference/50%20Common/Object%20Structures/ExcelExportDataGridProps '/Documentation/ApiReference/Common/Object_Structures/ExcelExportDataGridProps/') to configure export settings, including [cell customization](/api-reference/50%20Common/Object%20Structures/ExcelExportDataGridProps/customizeCell.md '/Documentation/ApiReference/Common/Object_Structures/ExcelExportDataGridProps/#customizeCell'). The DataGrid is exported to an Excel worksheet that is created using the ExcelJS API. To save the Excel document, call the FileSaver's **saveAs** method. The `e.cancel` parameter disables the deprecated built-in export implementation with fewer capabilities.

    ---
    ##### jQuery

        <!--JavaScript-->
        $('#gridContainer').dxDataGrid({
            export: {
                enabled: true
            },
            onExporting: function(e) { 
                var workbook = new ExcelJS.Workbook(); 
                var worksheet = workbook.addWorksheet('Main sheet'); 
                DevExpress.excelExporter.exportDataGrid({ 
                    worksheet: worksheet, 
                    component: e.component,
                    customizeCell: function(options) {
                        var excelCell = options;
                        excelCell.font = { name: 'Arial', size: 12 };
                        excelCell.alignment = { horizontal: 'left' };
                    } 
                }).then(function() {
                    workbook.xlsx.writeBuffer().then(function(buffer) { 
                        saveAs(new Blob([buffer], { type: 'application/octet-stream' }), 'DataGrid.xlsx'); 
                    }); 
                }); 
                e.cancel = true; 
            }
        });

    ##### Angular   

        <!-- tab: app.component.html -->
        <dx-data-grid ...
            (onExporting)="onExporting($event)">
            <dxo-export [enabled]="true"></dxo-export>
        </dx-data-grid>

        <!-- tab: app.component.ts -->
        import { Component } from '@angular/core';
        import { exportDataGrid } from 'devextreme/excel_exporter';
        import { Workbook } from 'exceljs';
        import saveAs from 'file-saver';
        
        @Component({
            selector: 'app-root',
            templateUrl: './app.component.html',
            styleUrls: ['./app.component.css']
        })
        export class AppComponent {
            onExporting(e) {
                const workbook = new Workbook();    
                const worksheet = workbook.addWorksheet('Main sheet');
                exportDataGrid({
                    component: e.component,
                    worksheet: worksheet,
                    customizeCell: function(options) {
                        const excelCell = options;
                        excelCell.font = { name: 'Arial', size: 12 };
                        excelCell.alignment = { horizontal: 'left' };
                    } 
                }).then(function() {
                    workbook.xlsx.writeBuffer()
                        .then(function(buffer: BlobPart) {
                            saveAs(new Blob([buffer], { type: 'application/octet-stream' }), 'DataGrid.xlsx');
                        });
                });
                e.cancel = true; 
            }
        }

        <!-- tab: app.module.ts -->
        import { BrowserModule } from '@angular/platform-browser';
        import { NgModule } from '@angular/core';
        import { AppComponent } from './app.component';
        import { DxDataGridModule } from 'devextreme-angular';

        @NgModule({
            declarations: [
                AppComponent
            ],
            imports: [
                BrowserModule,
                DxDataGridModule
            ],
            providers: [ ],
            bootstrap: [AppComponent]
        })
        export class AppModule { }


    ##### Vue

        <!-- tab: App.vue -->
        <template>
            <DxDataGrid ...
                @exporting="onExporting">
                <DxExport
                    :enabled="true"
                />
            </DxDataGrid>
        </template>

        <script>
        import 'devextreme/dist/css/dx.common.css';
        import 'devextreme/dist/css/dx.light.css';

        import { DxDataGrid, DxExport } from 'devextreme-vue/data-grid';
        import { exportDataGrid } from 'devextreme/excel_exporter';
        import { Workbook } from 'exceljs';
        import saveAs from 'file-saver';

        export default {
            components: {
                DxDataGrid,
                DxExport
            },
            methods: {
                onExporting(e) {
                    const workbook = new Workbook();
                    const worksheet = workbook.addWorksheet('Main sheet');
                    exportDataGrid({
                        component: e.component,
                        worksheet: worksheet,
                        customizeCell: function(options) {
                            const excelCell = options;
                            excelCell.font = { name: 'Arial', size: 12 };
                            excelCell.alignment = { horizontal: 'left' };
                        } 
                    }).then(function() {
                        workbook.xlsx.writeBuffer()
                            .then(function(buffer) {
                                saveAs(new Blob([buffer], { type: 'application/octet-stream' }), 'DataGrid.xlsx');
                            });
                    });
                    e.cancel = true;
                }
            }
        }
        </script>

    ##### React

        <!-- tab: App.js -->
        import React from 'react';
        import 'devextreme/dist/css/dx.common.css';
        import 'devextreme/dist/css/dx.light.css';

        import { Workbook } from 'exceljs';
        import saveAs from 'file-saver';
        import DataGrid, { Export } from 'devextreme-react/data-grid';
        import { exportDataGrid } from 'devextreme/excel_exporter';

        class App extends React.Component {
            render() {
                return (
                    <DataGrid ...
                        onExporting={this.onExporting}>
                        <Export enabled={true} />
                    </DataGrid>
                );
            }
            onExporting(e) {
                const workbook = new Workbook();
                const worksheet = workbook.addWorksheet('Main sheet');
                exportDataGrid({
                    component: e.component,
                    worksheet: worksheet,
                    customizeCell: function(options) {
                        const excelCell = options;
                        excelCell.font = { name: 'Arial', size: 12 };
                        excelCell.alignment = { horizontal: 'left' };
                    } 
                }).then(function() {
                    workbook.xlsx.writeBuffer()
                        .then(function(buffer) {
                            saveAs(new Blob([buffer], { type: 'application/octet-stream' }), 'DataGrid.xlsx');
                        });
                });
                e.cancel = true;
            }
        }
        export default App;

    --- 

The following restrictions apply when users export DataGrid:   

- Only XLSX files are supported out of the box. To export DataGrid to CSV, implement the **exportDataGrid(options)** method as shown in the following ticket: <a href="https://supportcenter.devexpress.com/ticket/details/t920593/pivotgrid-exceljs-export-to-export-pivotgrid-into-csv-file" target="_blank">Export PivotGrid into CSV file</a>.

- Excel limits the number of grouping levels to 7, while in the DataGrid it is unlimited.

- Only visible columns are exported. See the [onExporting](/api-reference/10%20UI%20Components/dxDataGrid/1%20Configuration/onExporting.md '/Documentation/ApiReference/UI_Components/dxDataGrid/Configuration/#onExporting') property description for a workaround.

- [Detail rows](/api-reference/10%20UI%20Components/dxDataGrid/1%20Configuration/masterDetail '/Documentation/ApiReference/UI_Components/dxDataGrid/Configuration/masterDetail/') are not exported.

- [Group rows](/api-reference/10%20UI%20Components/dxDataGrid/6%20Row/rowType.md '/Documentation/ApiReference/UI_Components/dxDataGrid/Row/#rowType') are always exported in an expanded state and the [isExpanded](/api-reference/10%20UI%20Components/dxDataGrid/6%20Row/isExpanded.md '/Documentation/ApiReference/UI_Components/dxDataGrid/Row/#isExpanded') property is ignored.

- Customizations made in the [cellTemplate](/api-reference/_hidden/dxDataGridColumn/cellTemplate.md '/Documentation/ApiReference/UI_Components/dxDataGrid/Configuration/columns/#cellTemplate'), [groupCellTemplate](/api-reference/_hidden/dxDataGridColumn/groupCellTemplate.md '/Documentation/ApiReference/UI_Components/dxDataGrid/Configuration/columns/#groupCellTemplate'), [headerCellTemplate](/api-reference/_hidden/dxDataGridColumn/headerCellTemplate.md '/Documentation/ApiReference/UI_Components/dxDataGrid/Configuration/columns/#headerCellTemplate'), and [rowTemplate](/api-reference/10%20UI%20Components/dxDataGrid/1%20Configuration/rowTemplate.md '/Documentation/ApiReference/UI_Components/dxDataGrid/Configuration/#rowTemplate') are omitted, but you can recreate them in the exported file using the ExcelJS API. Use the [customizeCell](/api-reference/50%20Common/Object%20Structures/ExcelExportDataGridProps/customizeCell.md '/Documentation/ApiReference/Common/Object_Structures/ExcelExportDataGridProps/#customizeCell') function to do this. [View Demo](https://js.devexpress.com/Demos/WidgetsGallery/Demo/DataGrid/ExcelJSCellCustomization/)

- [Data mapping](/concepts/70%20Data%20Binding/5%20Data%20Layer/2%20Reading%20Data/3%20Data%20Transformation/1%20Item%20Mapping.md '/Documentation/Guide/Data_Binding/Data_Layer/#Reading_Data/Data_Transformation/Item_Mapping') is ignored. Use [calculated columns](/api-reference/_hidden/GridBaseColumn/calculateCellValue.md '/Documentation/ApiReference/UI_Components/dxDataGrid/Configuration/columns/#calculateCellValue') instead.

#include common-demobutton-named with {
    name: "Overview",
    url: "https://js.devexpress.com/Demos/WidgetsGallery/Demo/DataGrid/ExcelJSOverview/"
}
#include common-demobutton-named with {
    name: "Export Images",
    url: "https://js.devexpress.com/Demos/WidgetsGallery/Demo/DataGrid/ExcelJSExportImages/"
}
#include common-demobutton-named with {
    name: "Export Multiple Grids",
    url: "https://js.devexpress.com/Demos/WidgetsGallery/Demo/DataGrid/ExcelJSExportMultipleGrids/"
}

[tags] xlsx, csv