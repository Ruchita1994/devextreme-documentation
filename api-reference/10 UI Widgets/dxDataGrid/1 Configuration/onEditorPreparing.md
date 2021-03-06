---
id: dxDataGrid.Options.onEditorPreparing
type: function(e)
default: null
EventForAction: dxDataGrid.editorPreparing
---
---
##### shortDescription
A function used to customize or replace [default editors](/api-reference/_hidden/GridBaseColumn/editorOptions.md '/Documentation/ApiReference/UI_Widgets/dxDataGrid/Configuration/columns/#editorOptions'). Not executed for cells with an [editCellTemplate](/api-reference/_hidden/dxDataGridColumn/editCellTemplate.md '/Documentation/ApiReference/UI_Widgets/dxDataGrid/Configuration/columns/#editCellTemplate').

##### param(e): Object
Information about the event that caused the function's execution.

##### field(e.cancel): Boolean
Allows you to cancel creating the editor.        
Set it to **true** and implement a custom editor.

##### field(e.component): {WidgetName}
The widget's instance.

##### field(e.dataField): String
The name of the field that provides data for the column's editor.

##### field(e.disabled): Boolean
Indicates whether the editor is disabled.

##### field(e.editorElement): dxElement
#include common-ref-elementparam with { element: "editor" }

##### field(e.editorName): String
Allows you to change the editor. Accepts names of DevExtreme widgets only, for example, *"dxTextBox"*.      
Import a new editor's module when [DevExtreme modules](/concepts/Common/30%20Modularity '/Documentation/Guide/Common/Modularity/') are used.

##### field(e.editorOptions): Object
Gets and sets the editor configuration.

##### field(e.element): dxElement
#include common-ref-elementparam with { element: "widget" }

##### field(e.model): Object
Model data. Available only if you use Knockout.

##### field(e.parentType): String
The editor's location. One of *"dataRow"*, *"filterRow"*, *"headerRow"* or *"searchPanel"*.      
Options passed to the function depend on this value.

##### field(e.readOnly): Boolean
Indicates whether the editor is read-only.

##### field(e.row): dxDataGridRowObject
The [properties](/api-reference/10%20UI%20Widgets/dxDataGrid/6%20Row '/Documentation/ApiReference/UI_Widgets/dxDataGrid/Row/') of the row's editor.

##### field(e.rtlEnabled): Boolean
Indicates whether the editor uses right-to-left representation.

##### field(e.setValue(newValue, newText)): any
A method you should call to change the cell value and, optionally, the displayed value after the editor's value is changed.

##### field(e.updateValueTimeout): Number
Gets and sets the delay between when a user stops typing a filter value and the change is applied. Available if the **parentType** is *"filterRow"* or *"searchPanel"*.

##### field(e.value): any
The editor's value.

##### field(e.width): Number
The editor's width; equals **null** for all editors except for those whose **parentType** equals *"searchPanel"*.

---
Use this function to:

- Override the default editor's **onValueChanged** handler. For other default editor customizations, use [editorOptions](/api-reference/_hidden/GridBaseColumn/editorOptions.md '/Documentation/ApiReference/UI_Widgets/dxDataGrid/Configuration/columns/#editorOptions').

    ---
    ##### jQuery

        <!-- tab: index.js -->
        $(function() {
            $("#dataGridContainer").dxDataGrid({
                // ...
                onEditorPreparing: function(e) {
                    if (e.dataField === "requiredDataField" && e.parentType === "dataRow") {
                        var standardHandler = e.editorOptions.onValueChanged;
                        e.editorOptions.onValueChanged = function(e) { // Overrides the standard handler
                            // ...
                            // Custom commands go here
                            // ...
                            standardHandler(e); // Calls the standard handler to save the edited value
                        }
                    }
                }
            });
        });

    ##### Angular

        <!-- tab: app.component.html -->
        <dx-data-grid ...
            (onEditorPreparing)="overrideOnValueChanged($event)">
        </dx-data-grid>

        <!-- tab: app.component.ts -->
        import { Component } from '@angular/core';

        @Component({
            selector: 'app-root',
            templateUrl: './app.component.html',
            styleUrls: ['./app.component.css']
        })
        export class AppComponent {
            overrideOnValueChanged(e) {
                if (e.dataField === 'requiredDataField' && e.parentType === 'dataRow') {
                    let standardHandler = e.editorOptions.onValueChanged;
                    e.editorOptions.onValueChanged = function (e) { // Overrides the standard handler
                        // ...
                        // Custom commands go here
                        // ...
                        standardHandler(e); // Calls the standard handler to save the edited value
                    }
                }
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
            providers: [],
            bootstrap: [AppComponent]
        })
        export class AppModule { }

    ##### Vue

        <!-- tab: App.vue -->
        <template>
            <DxDataGrid ...
                @editor-preparing="overrideOnValueChanged">
            </DxDataGrid>
        </template>

        <script>
        import 'devextreme/dist/css/dx.common.css';
        import 'devextreme/dist/css/dx.light.css';

        import DxDataGrid from 'devextreme-vue/data-grid';

        export default {
            components: {
                DxDataGrid
            },
            // ...
            methods: {
                overrideOnValueChanged(e) {
                    if (e.dataField === 'requiredDataField' && e.parentType === 'dataRow') {
                        let standardHandler = e.editorOptions.onValueChanged;
                        e.editorOptions.onValueChanged = function (e) { // Overrides the standard handler
                            // ...
                            // Custom commands go here
                            // ...
                            standardHandler(e); // Calls the standard handler to save the edited value
                        }
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

        import DataGrid from 'devextreme-react/data-grid';

        class App extends React.Component {
            overrideOnValueChanged(e) {
                if (e.dataField === 'requiredDataField' && e.parentType === 'dataRow') {
                    let standardHandler = e.editorOptions.onValueChanged;
                    e.editorOptions.onValueChanged = function (e) { // Overrides the standard handler
                        // ...
                        // Custom commands go here
                        // ...
                        standardHandler(e); // Calls the standard handler to save the edited value
                    }
                }
            }
            render() {
                return (
                    <DataGrid ...
                        onEditorPreparing={this.overrideOnValueChanged}>
                    </DataGrid>
                );
            }
        }
        export default App;

    ##### ASP.NET MVC Controls

        <!-- tab: Razor C# -->
        @(Html.DevExtreme().DataGrid()
            // ...
            .OnEditorPreparing("overrideOnValueChanged")
        )

        <script type="text/javascript">
            function overrideOnValueChanged(e) {
                if (e.dataField === "requiredDataField" && e.parentType === "dataRow") {
                    var standardHandler = e.editorOptions.onValueChanged;
                    e.editorOptions.onValueChanged = function(e) { // Overrides the standard handler
                        // ...
                        // Custom commands go here
                        // ...
                        standardHandler(e); // Calls the standard handler to save the edited value
                    }
                }
            }
        </script>

    ---

- Replace the default editor. The old editor's configuration applies to the replacement editor. To define the configuration from scratch, use an [editCellTemplate](/api-reference/_hidden/dxDataGridColumn/editCellTemplate.md '/Documentation/ApiReference/UI_Widgets/dxDataGrid/Configuration/columns/#editCellTemplate').
    
    In the following code, the DevExtreme [TextArea](https://js.devexpress.com/Demos/WidgetsGallery/Demo/TextArea/Overview) widget is the replacement editor:

    ---
    ##### jQuery

        <!-- tab: index.js -->
        $(function() {
            $("#dataGridContainer").dxDataGrid({
                // ...
                onEditorPreparing: function(e) {
                    if (e.dataField === "description" && e.parentType === "dataRow") {
                        e.editorName = "dxTextArea";
                    }
                }
            });
        });

    ##### Angular

        <!-- tab: app.component.html -->
        <dx-data-grid ...
            (onEditorPreparing)="replaceEditor($event)">
        </dx-data-grid>

        <!-- tab: app.component.ts -->
        import { Component } from '@angular/core';
        import 'devextreme/ui/text_area';

        @Component({
            selector: 'app-root',
            templateUrl: './app.component.html',
            styleUrls: ['./app.component.css']
        })
        export class AppComponent {
            replaceEditor(e) { 
                if (e.dataField === 'description' && e.parentType === 'dataRow') {
                    e.editorName = 'dxTextArea';
                }
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
            providers: [],
            bootstrap: [AppComponent]
        })
        export class AppModule { }

    ##### Vue

        <!-- tab: App.vue -->
        <template>
            <DxDataGrid ...
                @editor-preparing="replaceEditor">
            </DxDataGrid>
        </template>

        <script>
        import 'devextreme/dist/css/dx.common.css';
        import 'devextreme/dist/css/dx.light.css';

        import DxDataGrid from 'devextreme-vue/data-grid';
        import 'devextreme/ui/text_area';

        export default {
            components: {
                DxDataGrid
            },
            // ...
            methods: {
                replaceEditor(e) { 
                    if (e.dataField === 'description' && e.parentType === 'dataRow') {
                        e.editorName = 'dxTextArea';
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

        import DataGrid from 'devextreme-react/data-grid';
        import 'devextreme/ui/text_area';

        class App extends React.Component {
            replaceEditor(e) { 
                if (e.dataField === 'description' && e.parentType === 'dataRow') {
                    e.editorName = 'dxTextArea';
                }
            }
            render() {
                return (
                    <DataGrid ...
                        onEditorPreparing={this.replaceEditor}>
                    </DataGrid>
                );
            }
        }
        export default App;

    ##### ASP.NET MVC Controls

        <!-- tab: Razor C# -->
        @(Html.DevExtreme().DataGrid()
            // ...
            .OnEditorPreparing("replaceEditor")
        )

        <script type="text/javascript">
            function replaceEditor(e) {
                if (e.dataField === "description" && e.parentType === "dataRow") {
                    e.editorName = "dxTextArea";
                }
            }
        </script>

    ---

- Customize editors used in the [search panel](/api-reference/10%20UI%20Widgets/GridBase/1%20Configuration/searchPanel '/Documentation/ApiReference/UI_Widgets/dxDataGrid/Configuration/searchPanel/'), [filter row](/api-reference/10%20UI%20Widgets/GridBase/1%20Configuration/filterRow '/Documentation/ApiReference/UI_Widgets/dxDataGrid/Configuration/filterRow/'), and [selection column](/concepts/05%20Widgets/DataGrid/15%20Columns/10%20Column%20Types/4%20Command%20Columns/00%20Command%20Columns.md '/Documentation/Guide/Widgets/DataGrid/Columns/Column_Types/Command_Columns/').        
Use the **parentType** function parameter to check if the editor being customized belongs to one of these UI elements.

- [Dynamically change editor options in the editing state](/concepts/05%20Widgets/DataGrid/99%20How%20To/Dynamically%20Change%20Editor%20Options%20in%20the%20Editing%20State.md '/Documentation/Guide/Widgets/DataGrid/How_To/Dynamically_Change_Editor_Options_in_the_Editing_State/').

- Implement other customization cases.

#include common-demobutton with {
    url: "https://js.devexpress.com/Demos/WidgetsGallery/Demo/DataGrid/CommandColumnCustomization/"
}

#####See Also#####
- **columns[]**.[showEditorAlways](/api-reference/_hidden/GridBaseColumn/showEditorAlways.md '/Documentation/ApiReference/UI_Widgets/dxDataGrid/Configuration/columns/#showEditorAlways')
