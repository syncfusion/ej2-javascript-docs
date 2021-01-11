---
title: "Data binding"
component: "TreeGrid"
description: "Learn how to bind local and remote data in the Essential JS 2 TreeGrid control."
---

# Data binding

The TreeGrid uses `DataManager`, which supports both RESTful JSON data services binding and local JavaScript object array binding. The [`dataSource`](../api/treegrid#dataSource) property can be assigned either with the instance of `DataManager` or JavaScript object array collection.
It supports two kinds of data binding method:

* Local data
* Remote data

## Local Data

In Local Data binding, data source for rendering the TreeGrid control is retrieved from the same application locally.

Two types of Data binding are possible with the TreeGrid control.

* Hierarchical Datasource binding
* Self-Referential Data binding (Flat Data)

To bind local data to the treegrid, you can assign a JavaScript object array to the [`dataSource`](../api/treegrid#datasource) property. The local data source can also be provided as an instance of the `DataManager`.

> By default, `DataManager` uses `JsonAdaptor` for local data-binding.

### Hierarchy data source binding

The [`childMapping`](../api/treegrid#childMapping) property is used to map the child records in hierarchy data source.

The following code example shows you how to bind the hierarchical local data into the TreeGrid control.

{% tab template="treegrid/data-binding", es5Template="hierarchybind" %}

```typescript
import { TreeGrid, Page } from '@syncfusion/ej2-treegrid';
import { sampleData } from './datasource.ts';
TreeGrid.Inject(Page);

let treeGridObj: TreeGrid = new TreeGrid({
    dataSource: sampleData,
    childMapping: 'subtasks',
    allowPaging: true,
    pageSettings: {pageSize: 7},
    treeColumnIndex: 1,
    columns: [
                { field: 'taskID', headerText: 'Task ID', width: 90, textAlign: 'Right' },
                { field: 'taskName', headerText: 'Task Name', width: 180 },
                {
                    field: 'startDate', headerText: 'Start Date', width: 90, textAlign: 'Right', type: 'date',format: 'yMd'
                },
                { field: 'duration', headerText: 'Duration', width: 80, textAlign: 'Right' }
    ]
});

treeGridObj.appendTo('#TreeGrid');

```

{% endtab %}

### Self-Referential Data binding (Flat Data)

TreeGrid is rendered from Self-Referential data structures by providing two fields, ID field and parent ID field.

* **ID Field**: This field contains unique values used to identify nodes. Its name is assigned to the [`idMapping`](../api/treegrid#idMapping) property.
* **Parent ID Field**: This field contains values that indicate parent nodes. Its name is assigned to the [`parentIdMapping`](../api/treegrid#parentIdMapping) property.

{% tab template="treegrid/data-binding", es5Template="selfreferencebind" %}

```typescript
import { TreeGrid, Page } from '@syncfusion/ej2-treegrid';
import { projectData } from './datasource.ts';
TreeGrid.Inject(Page);

let treeGridObj: TreeGrid = new TreeGrid({
    dataSource: projectData,
    idMapping: 'TaskID',
    parentIdMapping: 'parentID',
    allowPaging: true,
    treeColumnIndex: 1,
    pageSettings: {pageSize: 7},
    columns: [
                { field: 'TaskID', headerText: 'Task ID', width: 90, textAlign: 'Right' },
                { field: 'TaskName', headerText: 'Task Name', width: 180 },
                {
                    field: 'StartDate', headerText: 'Start Date', width: 90, textAlign: 'Right', type: 'date',format: 'yMd'
                },
                { field: 'Duration', headerText: 'Duration', width: 80, textAlign: 'Right' }
    ]
});

treeGridObj.appendTo('#TreeGrid');

```

{% endtab %}

> Herewith we have provided list of reserved properties and the purpose we used internally in TreeGrid. We recommend to avoid these reserved properties in your dataSource(To get rid of conflicts).

Reserved keywords | Purpose
-----|-----
childRecords | Specifies the childRecords of a parentData
hasChildRecords | Specifies whether the record contains child records
hasFilteredChildRecords | Specifies whether the record contains filtered child records
expanded | Specifies whether the child records are expanded
parentItem | Specifies the parentItem of childRecords
index | Specifies the index of current record
level | Specifies the hierarchy level of record
filterLevel | Specifies the hierarchy level of filtered record
parentIdMapping | Specifies the parentID
uniqueID | Specifies the unique ID of a record
parentUniqueID | Specifies the parent Unique ID of a record
checkboxState | Specifies the checkbox state of a record
isSummaryRow | Specifies the summary of a record
taskData | Specifies the main data
primaryParent | Specifies the Primary data

## Remote data

To bind remote data to TreeGrid component, assign service data as an instance of `DataManager` to the [`dataSource`](../api/treegrid#datasource) property. To interact with remote data source,  provide the endpoint `url` and define the [`hasChildMapping`](../api/treegrid#hasChildMapping) property of treegrid.

The [`hasChildMapping`](../api/treegrid/#haschildmapping) property maps the field name in data source, that denotes whether current record holds any child records. This is useful internally to show expand icon while binding child data on demand.

The TreeGrid provides `Load on Demand` support for rendering remote data. The Load on demand is considered in TreeGrid for the following actions.

* Expanding root nodes.
* Navigating pages, with paging enabled in TreeGrid.

When load on demand is enabled, all the root nodes are rendered in collapsed state at initial load.

When load on demand support is enabled in TreeGrid with paging, the current or active page’s root node alone will be rendered in collapsed state. On expanding the root node, the child nodes will be loaded from the remote server.

When a root node is expanded, its child nodes are rendered and are cached locally, such that on consecutive expand/collapse actions on root node, the child nodes are loaded from the cache instead from the remote server.

Similarly, if the user navigates to a new page, the root nodes of that specific page, will be rendered with request to the remote server.

{% tab template="treegrid/data-binding", es5Template="loadondemand" %}

```typescript
import { TreeGrid, Page }from '@syncfusion/ej2-treegrid';
import { DataManager, WebApiAdaptor } from '@syncfusion/ej2-data';

let data: DataManager = new DataManager({
    url: 'https://ej2services.syncfusion.com/production/web-services/api/SelfReferenceData',
    adaptor: new WebApiAdaptor, crossDomain: true
});

TreeGrid.Inject(Page);
let treegrid: TreeGrid = new TreeGrid({
    dataSource: data,
    hasChildMapping : 'isParent',
    idMapping: 'TaskID',
    parentIdMapping: 'ParentItem',
    height: 260,
    allowPaging: true,
    treeColumnIndex: 1,
        columns: [
        { field: 'TaskID', headerText: 'Task ID', textAlign: 'Right', width: 90 },
        { field: 'TaskName', headerText: 'Task Name', width: 180 },
        { field: 'StartDate', headerText: 'Start Date', textAlign: 'Right', width: 90, format: { skeleton: 'yMd', type: 'date' } },
        { field: 'Duration', headerText: 'Duration', width: 80, textAlign: 'Right' }
    ]
});
treegrid.appendTo('#TreeGrid');

```

{% endtab %}

> By default, `DataManager` uses `ODataAdaptor` for remote data-binding.
> Based on the RESTful web services, set the corresponding adaptor to DataManager. Refer [`here`](https://ej2.syncfusion.com/documentation/data/adaptors/?no-cache=1) for more details.
> Filtering and searching server-side data operations are not supported in load on demand

### Offline Mode

On remote data binding, all treegrid actions such as paging, loading child on-demand, will be processed on server-side. To avoid postback, set the treegrid to load all data on initialization and make the actions process in client-side. To enable this behavior, use the `offline` property of `DataManager`.

{% tab template="treegrid/data-binding", es5Template="offline" %}

```typescript
import { TreeGrid, Page }from '@syncfusion/ej2-treegrid';
import { DataManager, WebApiAdaptor } from '@syncfusion/ej2-data';

let data: DataManager = new DataManager({
    url: 'https://ej2services.syncfusion.com/production/web-services/api/SelfReferenceData',
    adaptor: new WebApiAdaptor, crossDomain: true, offline: true
});

TreeGrid.Inject(Page);
let treegrid: TreeGrid = new TreeGrid({
    dataSource: data,
    idMapping: 'TaskID',
    parentIdMapping: 'ParentItem',
    height: 260,
    allowPaging: true,
    treeColumnIndex: 1,
        columns: [
        { field: 'TaskID', headerText: 'Task ID', textAlign: 'Right', width: 90 },
        { field: 'TaskName', headerText: 'Task Name', width: 180 },
        { field: 'StartDate', headerText: 'Start Date', textAlign: 'Right', width: 90, format: { skeleton: 'yMd', type: 'date' } },
        { field: 'Duration', headerText: 'Duration', width: 80, textAlign: 'Right' }
    ]
});
treegrid.appendTo('#TreeGrid');

```

{% endtab %}

### Custom Adaptor

You can create your own adaptor by extending the built-in adaptors. The following demonstrates custom adaptor approach and how to add a serial number for the records by overriding the built-in response processing using the `processResponse` method of the `WebApiAdaptor`.

{% tab template="treegrid/data-binding", es5Template="customadaptor" %}

```typescript
import { TreeGrid } from '@syncfusion/ej2-treegrid';
import { DataManager, WebApiAdaptor } from '@syncfusion/ej2-data';

class SerialNoAdaptor extends WebApiAdaptor {
    public processResponse(): Object[] {
        let i: number = 0;
        // calling base class processResponse function
        let original: Object[] = super.processResponse.apply(this, arguments);
        // adding serial number
        original.forEach((item: Object) => item['Sno'] = ++i);
        return original;
    }
}

let data: DataManager = new DataManager({
    url: 'https://ej2services.syncfusion.com/production/web-services/api/SelfReferenceData',
    adaptor: new SerialNoAdaptor, crossDomain: true, offline: true
});

let treegrid: TreeGrid = new TreeGrid({
    dataSource: data,
    idMapping: 'TaskID',
    parentIdMapping: 'ParentItem',
    height: 260,
    treeColumnIndex: 1,
        columns: [
        { field: 'Sno', width: 120, headerText: 'SNO', textAlign: 'Right' },
        { field: 'TaskName', headerText: 'Task Name', width: 180 },
        { field: 'StartDate', headerText: 'Start Date', textAlign: 'Right', width: 90, format: { skeleton: 'yMd', type: 'date' } },
        { field: 'Duration', headerText: 'Duration', width: 80, textAlign: 'Right' }
    ]
});
treegrid.appendTo('#TreeGrid');

```

{% endtab %}

### Sending additional parameters to the server

To add a custom parameter to the data request, use the `addParams` method of `Query` class. Assign the `Query` object with additional parameters to the treegrid [`query`](../api/treegrid#query) property.

{% tab template="treegrid/data-binding", es5Template="additionalparam" %}

```typescript
import { TreeGrid, Page } from '@syncfusion/ej2-treegrid';
import { DataManager, Query, WebApiAdaptor } from '@syncfusion/ej2-data';

let data: DataManager = new DataManager({
    url: 'https://ej2services.syncfusion.com/production/web-services/api/SelfReferenceData',
    adaptor: new WebApiAdaptor, crossDomain: true
});

TreeGrid.Inject(Page);
let treegrid: TreeGrid = new TreeGrid({
    dataSource: data,
    idMapping: 'TaskID',
    parentIdMapping: 'ParentItem',
    height: 260,
    allowPaging: true,
    query: new Query().addParams('ej2treegrid', 'true'),
    treeColumnIndex: 1,
        columns: [
        { field: 'TaskID', headerText: 'Task ID', textAlign: 'Right', width: 90 },
        { field: 'TaskName', headerText: 'Task Name', width: 180 },
        { field: 'StartDate', headerText: 'Start Date', textAlign: 'Right', width: 90, format: { skeleton: 'yMd', type: 'date' } },
        { field: 'Duration', headerText: 'Duration', width: 80, textAlign: 'Right' }
    ]
});
treegrid.appendTo('#TreeGrid');

```

{% endtab %}

### Handling HTTP error

During server interaction from the treegrid, some server-side exceptions may occur, and you can acquire those error messages or exception details
in client-side using the [`actionFailure`](../api/treegrid#actionfailure) event.

The argument passed to the [`actionFailure`](../api/treegrid#actionfailure) event contains the error details returned from the server.

{% tab template="treegrid/data-binding", es5Template="actionfailure" %}

```typescript
import { TreeGrid } from '@syncfusion/ej2-treegrid';
import { DataManager } from '@syncfusion/ej2-data';

let data: DataManager = new DataManager({
    url: 'http://some.com/invalidUrl'
});

let treegrid: TreeGrid = new TreeGrid({
    dataSource: data,
    idMapping: 'TaskID',
    parentIdMapping: 'ParentItem',
    actionFailure: (e) => {
       let span: HTMLElement = document.createElement('span');
       treegrid.element.parentNode.insertBefore(span, treegrid.element);
       span.style.color = '#FF0000'
       span.innerHTML = 'Server exception: 404 Not found';
    },
    treeColumnIndex: 1,
        columns: [
        { field: 'TaskID', headerText: 'Task ID', textAlign: 'Right', width: 90 },
        { field: 'TaskName', headerText: 'Task Name', width: 180 },
        { field: 'StartDate', headerText: 'Start Date', textAlign: 'Right', width: 90, format: { skeleton: 'yMd', type: 'date' } },
        { field: 'Duration', headerText: 'Duration', width: 80, textAlign: 'Right' }
    ]
});
treegrid.appendTo('#TreeGrid');

```

{% endtab %}

> The [`actionFailure`](../api/treegrid#actionfailure) event will be triggered not only for the server errors, but
also when there is an exception while processing the treegrid actions.

## Binding with Ajax

You can use TreeGrid [`dataSource`](../api/treegrid#datasource) property to bind the data source to TreeGrid from external Ajax request. In the below code we have fetched the data source from the server with the help of Ajax request and provided that to [`dataSource`](../api/treegrid#datasource) property by using `onSuccess` event of the Ajax.

{% tab template="treegrid/data-binding", es5Template="ajaxbind" %}

```typescript
import { TreeGrid, Page }from '@syncfusion/ej2-treegrid';
import { Ajax } from '@syncfusion/ej2-base';

TreeGrid.Inject(Page);
let treegrid: TreeGrid = new TreeGrid({
    idMapping: 'TaskID',
    parentIdMapping: 'ParentItem',
    pageSettings: {pageSize: 7},
    allowPaging: true,
    treeColumnIndex: 1,
    columns: [
        { field: 'TaskID', headerText: 'Task ID', textAlign: 'Right', width: 90 },
        { field: 'TaskName', headerText: 'Task Name', width: 180 },
        { field: 'Duration', headerText: 'Duration', width: 80, textAlign: 'Right' },
        { field: 'Progress', headerText: 'Progress', width: 80, textAlign: 'Right' }
    ]
});
treegrid.appendTo('#TreeGrid');

let button: HTMLElement = document.createElement('button');
button.textContent = 'Bind Data';
treegrid.element.parentNode.insertBefore(button, treegrid.element);
button.addEventListener("click", function(e){
    let ajax = new Ajax("https://ej2services.syncfusion.com/production/web-services/api/SelfReferenceData","GET");
    treegrid.showSpinner();
    ajax.send();
    ajax.onSuccess = function (data: string) {
        treegrid.hideSpinner();
        treegrid.dataSource = JSON.parse(data);
    };
});

```

{% endtab %}

> * If you bind the dataSource from this way, then it acts like a local dataSource. So you cannot perform any server side crud actions.

## Custom Binding

It is possible to handle data processing externally and bind the result to the TreeGrid. This helps you to provide your own custom data logic. TreeGrid expects an object as the result of the custom logic and the emitted value should be an object with properties result and count.

>In this context, we are going to use DataManager with WebApi Adaptor for handling remote interaction, you can choose any HTTP client as per your choice.

```typescript

import { TreeGrid, Page} from '../src';
import { DataManager, WebApiAdaptor, Query } from '@syncfusion/ej2-data';
import { isNullOrUndefined } from '@syncfusion/ej2-base';

TreeGrid.Inject(Page);

let data: DataManager = new DataManager({
    url: 'http://localhost:51473/api/Tasks',    ////   url for fetching the data from server
    adaptor: new WebApiAdaptor,
    crossDomain: true
});

                        /////  filter query for fetching the root level records only  and  take             value should be equal to the pageSize value of pageSettings

data.executeQuery(new Query().where('ParentId', 'equal', null).take(3).skip(0).requiresCount()).then((e: any) => {

    let treegrid: TreeGrid = new TreeGrid({
        dataSource: { result: e.result, count: e.count },
        hasChildMapping: 'IsParent',
        idMapping: 'TaskId',
        parentIdMapping: 'ParentId',
        allowPaging: true,
        pageSettings: { pageSize: 3, pageSizeMode: 'Root' },
        dataStateChange: function (state: any) {
            if (state.action.requestType === 'paging') {
                data.executeQuery(new Query().skip(state.skip).take(state.take).requiresCount()).then(function (e: any) {
                    this.dataSource = { result: e.result, count: e.count };
                });
            }
        },
        treeColumnIndex: 1,
        columns: [
            { field: 'TaskId', headerText: 'Task ID', isPrimaryKey: true, textAlign: 'Right', width: 120 },
            { field: 'TaskName', headerText: 'Task Name', width: 150 },
            { field: 'StartDate', headerText: 'Start Date', textAlign: 'Right', width: 120, format: { skeleton: 'yMd', type: 'date' } },
            { field: 'Duration', headerText: 'Duration', width: 110, textAlign: 'Right' },
            { field: 'Progress', headerText: 'Progress', width: 110 },
        ]
    });
    treegrid.appendTo('#TreeGrid');
});

```

> We have a limitation for Custom Binding feature of TreeGrid. This feature works only for Self Referential data binding with `pageSizeMode` as `Root`.

### Handling Child Data

Using the custom binding feature you can bind the child data for a parent record as per your custom logic. When a parent record is expanded, [`dataStateChange`](../api/treegrid/#datastatechange) event is triggered in which you can assign your custom data to the `childData` property of the [`dataStateChange`](../api/treegrid/#datastatechange) event arguments.
After assigning the child data, `childDataBind` method should be called from the
[`dataStateChange`](../api/treegrid/#datastatechange) event arguments to indicate that the data is bound.

> In this context, initially we have assigned only the parent records to the treegrid dataSource and fetched the required child records in the [`dataStateChange`](../api/treegrid/#datastatechange) event.

````typescript

import { TreeGrid, Page, Toolbar, Sort } from '../src';
import { DataManager, WebApiAdaptor, Query } from '@syncfusion/ej2-data';
import { isNullOrUndefined } from '@syncfusion/ej2-base';

TreeGrid.Inject(Page);

let data: DataManager = new DataManager({
    url: 'http://localhost:51473/api/Tasks',     //// url for fetching the data from server
    adaptor: new WebApiAdaptor,
    crossDomain: true
});

            /// filter query for fetching only the root level records

data.executeQuery(new Query().where('ParentId', 'equal', null).take(3).skip(0).requiresCount()).then((e: any) => {

    let treegrid: TreeGrid = new TreeGrid({
        dataSource: { result: e.result, count: e.count },
        hasChildMapping: 'IsParent',
        idMapping: 'TaskId',
        parentIdMapping: 'ParentId',
        allowPaging: true,
        pageSettings: { pageSize: 3, pageSizeMode: 'Root' },
        dataStateChange: function (state: any) {
            if (!isNullOrUndefined(state.requestType) && state.requestType === 'expand') {

                //// filter query for fetching the child records of the expanded record

                data.executeQuery(new Query().where('ParentId', 'equal', state.data.TaskId)).then(function (e: any) {
                    state.childData = e.result;
                    state.childDataBind();
                });
            } else {
                data.executeQuery(new Query().skip(state.skip).take(state.take).requiresCount()).then(function (e: any) {
                    this.dataSource = { result: e.result, count: e.count };
                });
            }
        },
        treeColumnIndex: 1,
        columns: [
            { field: 'TaskId', headerText: 'Task ID', isPrimaryKey: true, textAlign: 'Right', width: 120 },
            { field: 'TaskName', headerText: 'Task Name', width: 150 },
            { field: 'StartDate', headerText: 'Start Date', textAlign: 'Right', width: 120, format: { skeleton: 'yMd', type: 'date' } },
            { field: 'Duration', headerText: 'Duration', width: 110, textAlign: 'Right' },
            { field: 'Progress', headerText: 'Progress', width: 110 },
        ]
    });
    treegrid.appendTo('#TreeGrid');
});

````

### Handling TreeGrid Actions

For TreeGrid actions such as paging, sorting, etc dataStateChange event will be invoked. You have to query and resolve data using Ajax in this event based on the state arguments.

```typescript

import { TreeGrid, Page, Toolbar, Sort } from '../src';
import { DataManager, WebApiAdaptor, Query } from '@syncfusion/ej2-data';
import { isNullOrUndefined } from '@syncfusion/ej2-base';

TreeGrid.Inject(Page);

let data: DataManager = new DataManager({
    url: 'http://localhost:51473/api/Tasks',     //// url for fetching the data from server
    adaptor: new WebApiAdaptor,
    crossDomain: true
});

            /// filter query for fetching only the root level records

data.executeQuery(new Query().where('ParentId', 'equal', null).take(3).skip(0).requiresCount()).then((e: any) => {

    let treegrid: TreeGrid = new TreeGrid({
        dataSource: { result: e.result, count: e.count },
        hasChildMapping: 'IsParent',
        idMapping: 'TaskId',
        parentIdMapping: 'ParentId',
        allowPaging: true,
        allowSorting: true,
        pageSettings: { pageSize: 3, pageSizeMode: 'Root' },
        dataStateChange: function (state: any) {
            if (!isNullOrUndefined(state.requestType) && state.requestType === 'expand') {

                             //// filter query for fetching the child records of the expanded record

                data.executeQuery(new Query().where('ParentId', 'equal', state.data.TaskId)).then(function (e: any) {
                    state.childData = e.result;
                    state.childDataBind();
                });
            }
            if (state.action.requestType === 'paging') {
                data.executeQuery(new Query().skip(state.skip).take(state.take).requiresCount()).then(function (e: any) {
                    this.dataSource = { result: e.result, count: e.count };
                });
            }
            if (state.action.requestType === 'sorting') {

                    //// sort query for getting the sorted records from server

                data.executeQuery(new Query().sortBy('TaskId', 'descending').addParams('IdMapping','TaskId').skip(state.skip).take(state.take).requiresCount()).then(function (e: any) {
                        this.dataSource = { result: e.result, count: e.count };
                });
            }
        },
        treeColumnIndex: 1,
        columns: [
            { field: 'TaskId', headerText: 'Task ID', isPrimaryKey: true, textAlign: 'Right', width: 120 },
            { field: 'TaskName', headerText: 'Task Name', width: 150 },
            { field: 'StartDate', headerText: 'Start Date', textAlign: 'Right', width: 120, format: { skeleton: 'yMd', type: 'date' } },
            { field: 'Duration', headerText: 'Duration', width: 110, textAlign: 'Right' },
            { field: 'Progress', headerText: 'Progress', width: 110 },
        ]
    });
    treegrid.appendTo('#TreeGrid');
});

```

### Performing CRUD Actions

The [`dataSourceChanged`](../api/treegrid/#datasourcechanged) event will be triggered for updating the treegrid data. You can perform the save operation based on the event arguments and call the endEdit method to indicate the completion of save operation.

````typescript

import { TreeGrid, Page, Toolbar, Sort, Filter, Edit } from '../src';
import { DataManager, WebApiAdaptor, Query } from '@syncfusion/ej2-data';
import { isNullOrUndefined } from '@syncfusion/ej2-base';

TreeGrid.Inject(Page, Toolbar, Sort, Filter, Edit);

let data: DataManager = new DataManager({
    url: 'http://localhost:51473/api/Tasks',
    adaptor: new WebApiAdaptor,
    crossDomain: true
});

data.executeQuery(new Query().where('ParentId', 'equal', null).take(3).skip(0).requiresCount()).then((e: any) => {

    let treegrid: TreeGrid = new TreeGrid({
        dataSource: { result: e.result, count: e.count },
        hasChildMapping: 'IsParent',
        idMapping: 'TaskId',
        parentIdMapping: 'ParentId',
        allowPaging: true,
        toolbar: ['Add', 'Edit', 'Delete', 'Update', 'Cancel'],
        editSettings: { allowEditing: true, allowAdding: true, allowDeleting: true, mode: 'Row' },
        pageSettings: { pageSize: 3, pageSizeMode: 'Root' },
        dataSourceChanged: function (state: any) {
            if (state.action == 'add') {
                state.endEdit();
            }
            else if (state.action == 'edit') {
                state.endEdit();
            }
            else if (state.requestType == 'delete') {
                state.endEdit();
            }
        },
        dataStateChange: function (state: any) {
            if (!isNullOrUndefined(state.requestType) && state.requestType === 'expand') {
                data.executeQuery(new Query().where('ParentId', 'equal', state.data.TaskId)).then(function (e: any) {
                    state.childData = e.result;
                    state.childDataBind();
                });
            } else {
                data.executeQuery(new Query().where('ParentId', 'equal', null).take(3).skip(0).requiresCount()).then(function (e: any) {
                    this.dataSource = { result: e.result, count: e.count };
                });
            }
        },
        treeColumnIndex: 1,
        columns: [
            { field: 'TaskId', headerText: 'Task ID', isPrimaryKey: true, textAlign: 'Right', width: 120 },
            { field: 'TaskName', headerText: 'Task Name', width: 150 },
            { field: 'StartDate', headerText: 'Start Date', textAlign: 'Right', width: 120, format: { skeleton: 'yMd', type: 'date' } },
            { field: 'Duration', headerText: 'Duration', width: 110, textAlign: 'Right' },
            { field: 'Progress', headerText: 'Progress', width: 110 },
        ]
    });
    treegrid.appendTo('#TreeGrid');
});

````

### Calculate aggregates

The footer aggregate values  should be calculated and sent along with the **dataSource** property as follows. The aggregate property of the data source should contain the aggregate value assigned to the property named in the **field – type** format. For example, the **Sum** aggregate value for the **Duration** field should be assigned to the property named as **Duration - sum**.

```json
{
    result: [{..}, {..}, {..}, ...],
    count: 830,
    aggregates: { 'Freight - sum' : 450,'EmployeeID - min': 1 }
}
```

### Provide Excel Filter data source

The [`dataStateChange`](../api/treegrid/#datastatechange) event will be triggered with appropriate arguments when the excel filter requests the filter choice data source. You need to resolve the excel filter data source using the **dataSource** resolver function from the state argument as follows.

```typescript

import { TreeGrid, Page, Filter} from '../src';
import { DataManager, WebApiAdaptor, Query } from '@syncfusion/ej2-data';
import { isNullOrUndefined } from '@syncfusion/ej2-base';

TreeGrid.Inject(Page, Filter);

let data: DataManager = new DataManager({
    url: 'http://localhost:51473/api/Tasks',    ////   url for fetching the data from server
    adaptor: new WebApiAdaptor,
    crossDomain: true
});

            ///// filter query for fetching the root level records only

data.executeQuery(new Query().where('ParentId', 'equal', null).take(3).skip(0).requiresCount()).then((e: any) => {

    let treegrid: TreeGrid = new TreeGrid({
        dataSource: { result: e.result, count: e.count },
        hasChildMapping: 'IsParent',
        idMapping: 'TaskId',
        parentIdMapping: 'ParentId',
        allowPaging: true,
        allowFiltering: true,
        filterSettings: { type: 'Excel' },
        pageSettings: { pageSize: 3, pageSizeMode: 'Root' },
        dataStateChange: function (state: any) {
            if (state.action && (state.action.requestType === 'filterchoicerequest'
                || state.action.requestType ==='filtersearchbegin')) {
                data.executeQuery(new Query().skip(state.skip).take(state.take).requiresCount()).then(function (e: any) {
                    state.dataSource && state.dataSource(e);  /// resolve the excel filter dataSource
                });
            }
            else {
                /// take value must be always be equal to the pageSize value of pageSetings
                data.executeQuery(new Query().skip(state.skip).take(state.take).requiresCount()).then(function (e: any) {
                    this.dataSource = { result: e.result, count: e.count };
                });
            }
        },
        treeColumnIndex: 1,
        columns: [
            { field: 'TaskId', headerText: 'Task ID', isPrimaryKey: true, textAlign: 'Right', width: 120 },
            { field: 'TaskName', headerText: 'Task Name', width: 150 },
            { field: 'StartDate', headerText: 'Start Date', textAlign: 'Right', width: 120, format: { skeleton: 'yMd', type: 'date' } },
            { field: 'Duration', headerText: 'Duration', width: 110, textAlign: 'Right' },
            { field: 'Progress', headerText: 'Progress', width: 110 },
        ]
    });
    treegrid.appendTo('#TreeGrid');
});

```