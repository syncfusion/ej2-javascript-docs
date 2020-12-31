---
title: "Binding data to Kanban"
component: "Kanban"
description: "This section includes the data binding topics explaining how to bind various data sources to Kanban using DataManager adaptors."
---

# Data binding

The Kanban uses `DataManager`, which supports both RESTful data service binding and JavaScript object array binding. The [`dataSource`](../api/kanban#datasource) property of Kanban can be assigned either with the instance of `DataManager` or JavaScript object array collection, as it supports the following two data binding methods:

* Local data
* Remote data

## Local data

To bind local JSON data to the Kanban, you can simply assign a JavaScript object array to the [`dataSource`](../api/kanban#datasource) property. The JSON object dataSource can also be provided as an instance of `DataManager` and assigned to the Kanban `dataSource` property.

{% tab template="kanban/local-data", es5Template="local-data", sourceFiles="index.ts,index.html,datasource.ts"  %}

```typescript
import { Kanban } from '@syncfusion/ej2-kanban';
import { kanbanData } from './datasource.ts';

let kanbanObj: Kanban = new Kanban({
    dataSource: kanbanData,
    keyField: 'Status',
    columns: [
        { headerText: 'Backlog', keyField: 'Open' },
        { headerText: 'In Progress', keyField: 'InProgress' },
        { headerText: 'Testing', keyField: 'Testing' },
        { headerText: 'Done', keyField: 'Close' }
    ],
    cardSettings: {
        contentField: 'Summary',
        headerField: 'Id'
    }
});
kanbanObj.appendTo('#Kanban');
```

{% endtab %}

> By default, `DataManager` uses `JsonAdaptor` for binding local data.

## Remote data

To bind remote data to kanban component, assign service data as an instance of [`DataManager`](../data) to the [`dataSource`](../api/kanban#datasource) property. To interact with remote data source,  provide the endpoint **url**.

{% tab template="kanban/remote-data", es5Template="remote-data", sourceFiles="index.ts,index.html" %}

```typescript
import { Kanban, DialogEventArgs } from '@syncfusion/ej2-kanban';
import { DataManager, ODataAdaptor } from '@syncfusion/ej2-data';

let data: DataManager = new DataManager({
    url: 'https://ej2services.syncfusion.com/production/web-services/api/Kanban',
    adaptor: new ODataAdaptor
});
let kanbanObj: Kanban = new Kanban({
    dataSource: data,
    keyField: 'Status',
    columns: [
        { headerText: 'Backlog', keyField: 'Open' },
        { headerText: 'In Progress', keyField: 'InProgress' },
        { headerText: 'Testing', keyField: 'Testing' },
        { headerText: 'Done', keyField: 'Close' }
    ],
    cardSettings: {
        contentField: 'Summary',
        headerField: 'Id'
    },
    allowDragAndDrop: false,
    dialogOpen: dialogOpen
});
kanbanObj.appendTo('#Kanban');

function dialogOpen(args: DialogEventArgs): void {
    args.cancel = true;
}
```

{% endtab %}

> By default, [`DataManager`](../data) uses **ODataAdaptor** for remote data-binding.

### OData services

[`OData`](http://www.odata.org/documentation/odata-version-3-0/) is a standardized protocol for creating and consuming data. You can retrieve data from OData service using the DataManager. Refer to the following code example for remote Data binding using OData service.

{% tab template="kanban/odata", es5Template="odata" %}

```typescript
import { Kanban } from '@syncfusion/ej2-kanban';
import { DataManager, ODataAdaptor } from '@syncfusion/ej2-data';

let data: DataManager = new DataManager({
    url: 'https://ej2services.syncfusion.com/production/web-services/api/Kanban',
    adaptor: new ODataAdaptor,
    crossDomain: true
});
let kanbanObj: Kanban = new Kanban({
    dataSource: data,
    keyField: 'Status',
    columns: [
        { headerText: 'Backlog', keyField: 'Open' },
        { headerText: 'In Progress', keyField: 'InProgress' },
        { headerText: 'Testing', keyField: 'Testing' },
        { headerText: 'Done', keyField: 'Close' }
    ],
    cardSettings: {
        contentField: 'Summary',
        headerField: 'Id'
    },
    allowDragAndDrop: false,
    dialogOpen: dialogOpen
});
kanbanObj.appendTo('#Kanban');
function dialogOpen(args: DialogEventArgs): void {
    args.cancel = true;
}
```

{% endtab %}

### OData v4 services

The ODataV4 is an improved version of OData protocols, and the [`DataManager`](../data) can also retrieve and consume OData v4 services. For more details on OData v4 services, refer to the [`odata documentation`](http://docs.oasis-open.org/odata/odata/v4.0/errata03/os/complete/part1-protocol/odata-v4.0-errata03-os-part1-protocol-complete.html#_Toc453752197). To bind OData v4 service, use the **ODataV4Adaptor**.

{% tab template="kanban/odataV4", es5Template="odataV4" %}

```typescript
import { Kanban } from '@syncfusion/ej2-kanban';
import { DataManager, ODataV4Adaptor } from '@syncfusion/ej2-data';

let data: DataManager = new DataManager({
    url: 'https://services.odata.org/v4/northwind/northwind.svc/Suppliers',
    adaptor: new ODataV4Adaptor
});
let kanbanObj: Kanban = new Kanban({
    dataSource: data,
    keyField: 'ContactTitle',
    columns: [
        { headerText: 'Order Administrator', keyField: 'Order Administrator' },
        { headerText: 'Sales Representative', keyField: 'Sales Representative' },
        { headerText: 'Export Administrator', keyField: 'Export Administrator' }
    ],
    cardSettings: {
        contentField: 'ContactName',
        headerField: 'SupplierID'
    },
    allowDragAndDrop: false,
    dialogOpen: dialogOpen
});
kanbanObj.appendTo('#Kanban');
function dialogOpen(args: DialogEventArgs): void {
    args.cancel = true;
}
```

{% endtab %}

### Web API

You can use **WebApiAdaptor** to bind kanban with Web API created using OData endpoint.

```typescript
import { Kanban } from '@syncfusion/ej2-kanban';
import { DataManager, WebApiAdaptor  } from '@syncfusion/ej2-data';

let data: DataManager = new DataManager({
    url: '/api/Tasks',
    adaptor: new WebApiAdaptor
});
let kanbanObj: Kanban = new Kanban({
    dataSource: data,
    keyField: 'Status',
    columns: [
        { headerText: 'Backlog', keyField: 'Open' },
        { headerText: 'In Progress', keyField: 'InProgress' },
        { headerText: 'Testing', keyField: 'Testing' },
        { headerText: 'Done', keyField: 'Close' }
    ],
    cardSettings: {
        contentField: 'Summary',
        headerField: 'Id'
    },
    allowDragAndDrop: false,
    dialogOpen: dialogOpen
});
kanbanObj.appendTo('#Kanban');
function dialogOpen(args: DialogEventArgs): void {
    args.cancel = true;
}

```

Below server-side controller code to get the Kanban data.

```typescript

[HttpGet]
        public object Get()
        {
            var data = OrdersDetails.GetAllRecords().ToList();
            return data;
        }

```

### URL adaptor

The CRUD (Create, Read, Update and Delete) actions can be performed easily on Kanban cards using the various adaptors available within the `DataManager`. Most preferably, we will be using `UrlAdaptor` for performing CRUD actions on Kanban.

```typescript
import { Kanban } from '@syncfusion/ej2-kanban';
import { DataManager, UrlAdaptor } from '@syncfusion/ej2-data';

let data: DataManager = new DataManager({
    url: "DataSource",
    crudUrl: "UpdateData",
    adaptor: new UrlAdaptor
});
let kanbanObj: Kanban = new Kanban({
    dataSource: data,
    keyField: 'Status',
    columns: [
        { headerText: 'Backlog', keyField: 'Open' },
        { headerText: 'In Progress', keyField: 'InProgress' },
        { headerText: 'Testing', keyField: 'Testing' },
        { headerText: 'Done', keyField: 'Close' }
    ],
    cardSettings: {
        contentField: 'Summary',
        headerField: 'Id'
    }
});
kanbanObj.appendTo('#Kanban');

```

The server-side controller code to handle the CRUD operations are as follows.

```typescript

private NORTHWNDEntities db = new NORTHWNDEntities();
public ActionResult DataSource() {
    var DataSource = db.Tasks.ToList();
    return Json(DataSource, JsonRequestBehavior.AllowGet);
}
public ActionResult UpdateData(EditParams param) {
    if (param.action == "insert" || (param.action == "batch" && param.added != null)) {
        //Insert record in database
    }
    if (param.action == "update" || (param.action == "batch" && param.changed != null)) {
        //Update record in database
    }
    if (param.action == "remove" || (param.action == "batch" && param.deleted != null)) {
        //Delete record in database
    }
    db.SaveChanges();
    var data = db.Tasks.ToList();
    return Json(data, JsonRequestBehavior.AllowGet);
}

public class EditParams {
    public string key { get; set; }
    public string action { get; set; }
    public List<Tasks> added { get; set; }
    public List<Tasks> changed { get; set; }
    public List<Tasks> deleted { get; set; }
    public Tasks value { get; set; }
}

```

### Custom adaptor

It is possible to create your own custom adaptor by extending the built-in available adaptors. The following example demonstrates the custom adaptor usage and how to add a custom field `TaskId` for the cards by overriding the built-in response processing using the `processResponse` method of the `ODataAdaptor`.

{% tab template="kanban/custom", es5Template="custom" %}

```typescript
import { Kanban } from '@syncfusion/ej2-kanban';
import { DataManager, ODataAdaptor } from '@syncfusion/ej2-data';

class TaskIdAdaptor extends ODataAdaptor {
    processResponse(): Object {
        let i: number = 0;
        // calling base class processResponse function
        let original: Object[] = super.processResponse.apply(this, arguments);
        // adding Task Id
        original.forEach((item: { [key: string]: Object }) => item['Id'] = 'Task - ' + ++i);
        return original;
    }
}
let data: DataManager = new DataManager({
    url: 'https://ej2services.syncfusion.com/production/web-services/api/Kanban',
    adaptor: new TaskIdAdaptor
});
let kanbanObj: Kanban = new Kanban({
    dataSource: data,
    keyField: 'Status',
    columns: [
        { headerText: 'Backlog', keyField: 'Open' },
        { headerText: 'In Progress', keyField: 'InProgress' },
        { headerText: 'Testing', keyField: 'Testing' },
        { headerText: 'Done', keyField: 'Close' }
    ],
    cardSettings: {
        contentField: 'Summary',
        headerField: 'Id'
    },
    allowDragAndDrop: false,
    dialogOpen: dialogOpen
});
kanbanObj.appendTo('#Kanban');
function dialogOpen(args: DialogEventArgs): void {
    args.cancel = true;
}

```

{% endtab %}

### Sending additional parameters to the server

To add a custom parameter to the data request, use the **addParams** method of **Query** class. Assign the **Query** object with additional parameters to the kanban [`query`](../api/kanban#query) property.

{% tab template="kanban/additional", es5Template="additional" %}

```typescript
import { Kanban, DialogEventArgs } from '@syncfusion/ej2-kanban';
import { DataManager, ODataAdaptor, Query } from '@syncfusion/ej2-data';

let data: DataManager = new DataManager({
    url: 'https://ej2services.syncfusion.com/production/web-services/api/Kanban',
    adaptor: new ODataAdaptor
});
let kanbanObj: Kanban = new Kanban({
    dataSource: data,
    query: new Query().addParams('ej2kanban', 'true'),
    keyField: 'Status',
    columns: [
        { headerText: 'Backlog', keyField: 'Open' },
        { headerText: 'In Progress', keyField: 'InProgress' },
        { headerText: 'Testing', keyField: 'Testing' },
        { headerText: 'Done', keyField: 'Close' }
    ],
    cardSettings: {
        contentField: 'Summary',
        headerField: 'Id'
    },
    allowDragAndDrop: false,
    dialogOpen: dialogOpen
});
kanbanObj.appendTo('#Kanban');

function dialogOpen(args: DialogEventArgs): void {
    args.cancel = true;
}

```

{% endtab %}

> The parameters added using the [`query`](../api/kanban#query) property will be sent along with the data request for every kanban action.

### Handling HTTP error

During server interaction from the kanban, some server-side exceptions may occur, and you can acquire those error messages or exception details
in client-side using the [`actionFailure`](../api/kanban#actionfailure) event.

The argument passed to the [`actionFailure`](../api/kanban#actionfailure) event contains the error details returned from the server.

{% tab template="kanban/error", es5Template="error" %}

```typescript
import { Kanban, DialogEventArgs } from '@syncfusion/ej2-kanban';
import { DataManager } from '@syncfusion/ej2-data';

let data: DataManager = new DataManager({
    url: 'http://some.com/invalidUrl'
});
let kanbanObj: Kanban = new Kanban({
    dataSource: data,
    keyField: 'Status',
    columns: [
        { headerText: 'Backlog', keyField: 'Open' },
        { headerText: 'In Progress', keyField: 'InProgress' },
        { headerText: 'Testing', keyField: 'Testing' },
        { headerText: 'Done', keyField: 'Close' }
    ],
    cardSettings: {
        contentField: 'Summary',
        headerField: 'Id'
    },
    actionFailure: (e) => {
       let span: HTMLElement = document.createElement('span');
       kanbanObj.element.parentNode.insertBefore(span, kanbanObj.element);
       span.style.color = '#FF0000'
       span.innerHTML = 'Server exception: 404 Not found';
    }
});
kanbanObj.appendTo('#Kanban');

```

{% endtab %}

> The [`actionFailure`](../api/kanban#actionfailure) event will be triggered not only for the server errors, but
also when there is an exception while processing the kanban actions.

## Loading data via ajax

You can use Kanban [`dataSource`](../api/kanban#datasource) property to bind the datasource to Kanban from external ajax request. In the following code, we have fetched the datasource from the server using ajax request and provided that to the [`dataSource`](../api/kanban#datasource) property by using the **onSuccess** event of ajax.

{% tab template="kanban/ajax", es5Template="ajax" %}

```typescript
import { Kanban, DialogEventArgs } from '@syncfusion/ej2-kanban';
import { Ajax } from '@syncfusion/ej2-base';

let kanbanObj: Kanban = new Kanban({
    keyField: 'ShipCountry',
    columns: [
        { headerText: 'Denmark', keyField: 'Denmark' },
        { headerText: 'Brazil', keyField: 'Brazil' },
        { headerText: 'Switzerland', keyField: 'Switzerland' },
        { headerText: 'Germany', keyField: 'Germany' }
    ],
    cardSettings: {
        contentField: 'ShippedDate',
        headerField: 'OrderID'
    }
});
kanbanObj.appendTo('#Kanban');

let button = document.getElementById('btn');
button.addEventListener("click", function(e) {
    let ajax = new Ajax("https://ej2services.syncfusion.com/production/web-services/api/Orders", "GET");
    ajax.send();
    ajax.onSuccess = function (data: string) {
        kanbanObj.dataSource = JSON.parse(data);
    };
});
```

{% endtab %}

> * If you bind the dataSource from this way, then it acts like a local dataSource. So you cannot perform any server-side crud actions.
