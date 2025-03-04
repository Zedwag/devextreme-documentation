---
id: dxScheduler.Options.onAppointmentFormOpening
type: function(e)
default: null
EventForAction: dxScheduler.appointmentFormOpening
---
---
##### shortDescription
A function that is executed before an appointment details form is opened. Use this function to customize the form.

##### param(e): Object
Information about the event.

##### field(e.appointmentData): Object
The data of the appointment for which a form is opened.

##### field(e.cancel): Boolean
If **true**, prevents the user from opening the appointment details form.

##### field(e.component): {WidgetName}
The UI component's instance.

##### field(e.element): dxElement
#include common-ref-elementparam with { element: "UI component" }

##### field(e.form): dxForm
The form's instance; created only once - when the function is executed for the first time.

##### field(e.model): Object
Model data. Available only if you use Knockout.

##### field(e.popup): dxPopup
The instance of the popup that contains the form.

---

Form items are organized into two groups:

<table class="dx-table">
    <tr>
        <th>Group name</th>
        <th>Description</th>
    </tr>
    <tr>
        <td>mainGroup</td>
        <td>Contains form fields that define main appointment parameters (subject, start and end dates, etc.).</td>
    </tr>
    <tr>
        <td>recurrenceGroup</td>
        <td>Contains form fields that define appointment recurrence parameters.</td>
    </tr> 
</table>

You can add a custom item to any group or create an ungrouped item and display it under the groups, as shown in the following image:

![DevExtreme Scheduler onAppointmentFormOpening](/images/UiWidgets/Scheduler_onAppointmentFormOpening.png)

The code below adds a new form item (`phone`) to the `mainGroup` and creates an ungrouped item (`location`). Note that the array of [form items](/api-reference/10%20UI%20Components/dxForm/1%20Configuration/items.md '/Documentation/ApiReference/UI_Components/dxForm/Configuration/#items') should be checked to ensure that it does not already contain an item with the same data field. The following code also adds a title to the popup:

---
##### jQuery

    <!-- tab: index.js -->
    $(function() {
        $("#schedulerContainer").dxScheduler({
            dataSource: [{
                text: "Attend the conference",
                startDate: new Date(2020, 4, 24, 9, 10),
                endDate: new Date(2020, 4, 24, 11, 20),
            }],
            currentDate: new Date(2020, 4, 24),

            onAppointmentFormOpening: function(e) {
                e.popup.option('showTitle', true);
                e.popup.option('title', e.appointmentData.text ? 
                    e.appointmentData.text : 
                    'Create a new appointment');

                const form = e.form;
                let mainGroupItems = form.itemOption('mainGroup').items; 
                if (!mainGroupItems.find(function(i) { return i.dataField === "phone" })) {
                    mainGroupItems.push({
                        colSpan: 2, 
                        label: { text: "Phone Number" },
                        editorType: "dxTextBox",
                        dataField: "phone"
                    });
                    form.itemOption('mainGroup', 'items', mainGroupItems);
                }
        
                let formItems = form.option("items"); 
                if (!formItems.find(function(i) { return i.dataField === "location" })) {
                    formItems.push({
                        colSpan: 2,
                        label: { text: "Location" },
                        editorType: "dxTextBox",
                        dataField: "location"
                    });
                    form.option("items", formItems);
                }
            }
        });
    });

##### Angular

    <!-- tab: app.component.html -->
    <dx-scheduler
        [dataSource]="schedulerData"
        [currentDate]="currentDate"
        (onAppointmentFormOpening)="onAppointmentFormOpening($event)">
    </dx-scheduler>

    <!-- tab: app.component.ts -->
    import { DxSchedulerModule } from "devextreme-angular";
    // ...
    export class AppComponent {
        schedulerData = [{
            text: "Attend the conference",
            startDate: new Date(2020, 4, 24, 9, 10),
            endDate: new Date(2020, 4, 24, 11, 20),
        }];
        currentDate = new Date(2020, 4, 24);
        
        onAppointmentFormOpening(e) {
            e.popup.option('showTitle', true);
            e.popup.option('title', e.appointmentData.text ? 
                e.appointmentData.text : 
                'Create a new appointment');

            const form = e.form;
            let mainGroupItems = form.itemOption('mainGroup').items; 
            if (!mainGroupItems.find(function(i) { return i.dataField === "phone" })) {
                mainGroupItems.push({
                    colSpan: 2, 
                    label: { text: "Phone Number" },
                    editorType: "dxTextBox",
                    dataField: "phone"
                });
                form.itemOption('mainGroup', 'items', mainGroupItems);
            }
    
            let formItems = form.option("items"); 
            if (!formItems.find(function(i) { return i.dataField === "location" })) {
                formItems.push({
                    colSpan: 2,
                    label: { text: "Location" },
                    editorType: "dxTextBox",
                    dataField: "location"
                });
                form.option("items", formItems);
            }
        }
    }
    @NgModule({
        imports: [
            // ...
            DxSchedulerModule
        ],
        // ...
    })

##### Vue

    <!-- tab: App.vue -->
    <template>
        <DxScheduler
            :data-source="schedulerData"
            :current-date="currentDate"
            @appointment-form-opening="onAppointmentFormOpening"
        />
    </template>

    <script>
    import 'devextreme/dist/css/dx.common.css';
    import 'devextreme/dist/css/dx.light.css';

    import DxScheduler from 'devextreme-vue/scheduler';

    export default {
        components: {
            DxScheduler
        },
        data() {
            return {
                schedulerData: [{
                    text: "Attend the conference",
                    startDate: new Date(2020, 4, 24, 9, 10),
                    endDate: new Date(2020, 4, 24, 11, 20),
                }],
                currentDate: new Date(2020, 4, 24)
            }
        },
        methods: {
            onAppointmentFormOpening(e) {
                e.popup.option('showTitle', true);
                e.popup.option('title', e.appointmentData.text ? 
                    e.appointmentData.text : 
                    'Create a new appointment');

                const form = e.form;
                let mainGroupItems = form.itemOption('mainGroup').items; 
                if (!mainGroupItems.find(function(i) { return i.dataField === "phone" })) {
                    mainGroupItems.push({
                        colSpan: 2, 
                        label: { text: "Phone Number" },
                        editorType: "dxTextBox",
                        dataField: "phone"
                    });
                    form.itemOption('mainGroup', 'items', mainGroupItems);
                }
        
                let formItems = form.option("items"); 
                if (!formItems.find(function(i) { return i.dataField === "location" })) {
                    formItems.push({
                        colSpan: 2,
                        label: { text: "Location" },
                        editorType: "dxTextBox",
                        dataField: "location"
                    });
                    form.option("items", formItems);
                }
            }
        }
    }
    </script>

##### React

    <!-- tab: App.js -->
    import React from 'react';

    import 'devextreme/dist/css/dx.common.css';
    import 'devextreme/dist/css/dx.light.css';
    import Scheduler from 'devextreme-react/scheduler';

    const dataSource = [{
        text: "Attend the conference",
        startDate: new Date(2020, 4, 24, 9, 10),
        endDate: new Date(2020, 4, 24, 11, 20),
    }];

    class App extends React.Component {
        currentDate = new Date(2020, 4, 24);
        
        onAppointmentFormOpening(e) {
            e.popup.option('showTitle', true);
            e.popup.option('title', e.appointmentData.text ? 
                e.appointmentData.text : 
                'Create a new appointment');
            
            const form = e.form;
            let mainGroupItems = form.itemOption('mainGroup').items;
            if (!mainGroupItems.find(function(i) { return i.dataField === "phone" })) {
                mainGroupItems.push({
                    colSpan: 2, 
                    label: { text: "Phone Number" },
                    editorType: "dxTextBox",
                    dataField: "phone"
                });
                form.itemOption('mainGroup', 'items', mainGroupItems);
            }
    
            let formItems = form.option("items"); 
            if (!formItems.find(function(i) { return i.dataField === "location" })) {
                formItems.push({
                    colSpan: 2,
                    label: { text: "Location" },
                    editorType: "dxTextBox",
                    dataField: "location"
                });
                form.option("items", formItems);
            }
        }

        render() {
            return (
                <Scheduler 
                    dataSource={dataSource}
                    defaultCurrentDate={this.currentDate}
                    onAppointmentFormOpening={this.onAppointmentFormOpening}
                />
            );
        }
    }
    export default App;

---

The `mainGroup` consists of two columns. To make a custom item span both columns, set its [colSpan](/api-reference/10%20UI%20Components/dxForm/5%20Item%20Types/SimpleItem/colSpan.md '/Documentation/ApiReference/UI_Components/dxForm/Item_Types/SimpleItem/#colSpan') to 2 - as shown in the code above. Apply the same setting to an ungrouped item if it should span the `mainGroup` and `recurrenceGroup`.

#include common-demobutton with {
    url: "https://js.devexpress.com/Demos/WidgetsGallery/Demo/Scheduler/TimeZonesSupport/"
}

#####See Also#####
- [Form - Change Properties at Runtime](/concepts/05%20UI%20Components/Form/20%20Change%20Properties%20at%20Runtime/05%20Form%20Properties.md '/Documentation/Guide/UI_Components/Form/Change_Properties_at_Runtime/Form_Properties/')
