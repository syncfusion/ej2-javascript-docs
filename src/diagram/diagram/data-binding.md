---
title: "Data Binding"
component: "Diagram"
description: "Diagram supports data binding to display the list of items from local array/JSON data or server-side data source using DataManager."
---

# Data Binding

* Diagram can be populated with the `nodes` and `connectors` based on the information provided from an external data source.

* Diagram exposes its specific data-related properties allowing you to specify the data source fields from where the node information has to be retrieved from.

* The [`dataManager`](../api/diagram/dataSourceModel#datamanager-datamanager) property is used to define the data source either as a collection of objects or as an instance of `DataManager` that needs to be populated in the diagram.

* The [`ID`](../api/diagram/dataSourceModel#id-string) property is used to define the unique field of each JSON data.

* The [`parentId`](../api/diagram/dataSourceModel#parentid-string) property is used to defines the parent field which builds the relationship between ID and parent field.

* The [`root`](../api/diagram/dataSourceModel#root-string) property is used to define the root node for the diagram populated from the data source.

* To explore those properties, see [`DataSourceSettings`](../api/diagram/dataSourceModel).

* Diagram supports two types of data binding. They are:

    1. Local data
    2. Remote data

## Local data

Diagram can be populated based on the user defined JSON data (Local Data) by mapping the relevant data source fields.

To map the user defined JSON data with diagram, configure the fields of [`dataSourceSettings`](../api/diagram/dataSourceModel). The following code example illustrates how to bind local data with the diagram.

{% tab template= "diagram/dataBinding", es5Template="es5LocalBinding" %}

```typescript

import {
    Diagram, NodeModel, ConnectorModel, Node, DataBinding, HierarchicalTree, DiagramTools
} from '@syncfusion/ej2-diagrams';

Diagram.Inject(DataBinding, HierarchicalTree);

import { DataManager } from '@syncfusion/ej2-data';

let species: object[] = [
    { 'Name': 'Species', 'fillColor': '#3DD94A' },
    { 'Name': 'Plants', 'Category': 'Species' },
    { 'Name': 'Fungi', 'Category': 'Species' },
    { 'Name': 'Lichens', 'Category': 'Species' },
    { 'Name': 'Animals', 'Category': 'Species' },
    { 'Name': 'Mosses', 'Category': 'Plants' },
    { 'Name': 'Ferns', 'Category': 'Plants' },
    { 'Name': 'Gymnosperms', 'Category': 'Plants' },
    { 'Name': 'Dicotyledens', 'Category': 'Plants' },
    { 'Name': 'Monocotyledens', 'Category': 'Plants' },
    { 'Name': 'Invertebrates', 'Category': 'Animals' },
    { 'Name': 'Vertebrates', 'Category': 'Animals' },
    { 'Name': 'Insects', 'Category': 'Invertebrates' },
    { 'Name': 'Molluscs', 'Category': 'Invertebrates' },
    { 'Name': 'Crustaceans', 'Category': 'Invertebrates' },
    { 'Name': 'Others', 'Category': 'Invertebrates' },
    { 'Name': 'Fish', 'Category': 'Vertebrates' },
    { 'Name': 'Amphibians', 'Category': 'Vertebrates' },
    { 'Name': 'Reptiles', 'Category': 'Vertebrates' },
    { 'Name': 'Birds', 'Category': 'Vertebrates' },
    { 'Name': 'Mammals', 'Category': 'Vertebrates' }
];
//Initializes diagram control
let diagram: Diagram = new Diagram({
    width: '100%', height: 490,
    //Configures data source
    dataSourceSettings: {
        id: 'Name', parentId: 'Category', dataManager: new DataManager(species),
        //binds the external data with node
        doBinding: (nodeModel: NodeModel, data: DataInfo, diagram: Diagram) => {
            nodeModel.annotations = [{
                /* tslint:disable:no-string-literal */
                content: data['Name'], margin: { top: 10, left: 10, right: 10, bottom: 0 },
                style: { color: 'black' }
            }
            ];
            /* tslint:disable:no-string-literal */
            nodeModel.style = { fill: '#ffeec7', strokeColor: '#f5d897', strokeWidth: 1 };
        }
    },
    //Configrues HierarchicalTree layout
    layout: {
        type: 'HierarchicalTree', horizontalSpacing: 15, verticalSpacing: 50,
        margin: { top: 10, left: 10, right: 10, bottom: 0 },
    },
    //Sets the default values of nodes
    getNodeDefaults: (obj: Node, diagram: Diagram) => {
        //Initialize shape
        obj.shape = { type: 'Basic', shape: 'Rectangle' };
        obj.style = { strokeWidth: 1 };
        obj.width = 95;
        obj.height = 30;
    },
    //Sets the default values of connectors
    getConnectorDefaults: (connector: ConnectorModel, diagram: Diagram) => {
        connector.type = 'Orthogonal';
        connector.style.strokeColor = '#4d4d4d';
        connector.targetDecorator.shape = 'None';
    },
    //Disables all interactions except zoom/pan
    tool: DiagramTools.ZoomPan,
    snapSettings: { constraints: 0 }
});
diagram.appendTo('#element');
export interface EmployeeInfo {
    Role: string;
    color: string;
}
export interface DataInfo {
    [key: string]: string;
}

```

{% endtab %}

## Remote data

You can bind the diagram with remote data by using [`dataManager`].

It uses two different classes: `DataManager` for processing and `Query` for serving data. `DataManager` communicates with data source and `Query` generates data queries that are read by the [`dataManager`](../api/diagram/dataSourceModel).

To learn more about data manager, refer to [`Data Manager`](../api/diagram/dataSourceModel).

To bind remote data to the diagram,configure the fields of [`dataSourceSettings`](../api/diagram/dataSourceModel). The following code illustrates how to bind remote data to the diagram.

{% tab template= "diagram/dataBinding", es5Template="es5RemoteBinding" %}

```typescript

import {
    Diagram, NodeModel, Node, Connector, DataBinding, HierarchicalTree, TreeInfo, DiagramTools
} from '@syncfusion/ej2-diagrams';

Diagram.Inject(DataBinding, HierarchicalTree);

import { DataManager, Query } from '@syncfusion/ej2-data';

//Initializes diagram control
let diagram: Diagram = new Diagram({
    width: '100%', height: 490,
    //Configrues hierarchical tree layout
    layout: {
        type: 'HierarchicalTree', margin: { left: 0, right: 0, top: 100, bottom: 0 },
        verticalSpacing: 40,
        getLayoutInfo: (node: Node, options: TreeInfo) => {
            if (options.level === 3) {
                node.style.fill = '#3c418d';
            }
            if (options.level === 2) {
                node.style.fill = '#108d8d';
                options.type = 'Center';
                options.orientation = 'Horizontal';
            }
            if (options.level === 1) {
                node.style.fill = '#822b86';
            }
        }
    },
    //Sets the default values of nodes
    getNodeDefaults: (obj: Node) => {
        obj.width = 80;
        obj.height = 40;
        //Initialize shape
        obj.shape = { type: 'Basic', shape: 'Rectangle' };
        obj.style = { fill: '#048785', strokeColor: 'Transparent' };
    },
    //Sets the default values of connector
    getConnectorDefaults: (connector: Connector) => {
        connector.type = 'Orthogonal';
        connector.style.strokeColor = '#048785';
        connector.targetDecorator.shape = 'None';
    },
    //Configures data source
    dataSourceSettings: {
        id: 'EmployeeID', parentId: 'ReportsTo',
        dataManager: new DataManager(
            { url: 'http://mvc.syncfusion.com/Services/Northwnd.svc/', crossDomain: true },
            new Query().from('Employees').select('EmployeeID,ReportsTo,FirstName').take(9),
        ),
        //binds the external data with node
        doBinding: (nodeModel: NodeModel, data: DataInfo, diagram: Diagram) => {
            nodeModel.annotations = [{
                /* tslint:disable:no-string-literal */
                content: data['FirstName'],
                style: { color: 'white' }
            }];
        }
    },
    //Disables all interactions except zoom/pan
    tool: DiagramTools.ZoomPan,
    snapSettings: { constraints: 0 }
});
diagram.appendTo('#element');

export interface DataInfo {
    [key: string]: string;
}

```

{% endtab %}

## CRUD

This feature allows you to read the data source and perform add or edit or delete the data in data source at runtime.

## Read DataSource

* This feature allows you to define the nodes and connectors collection in the data source and connectionDataSource respectively.

* You can set the data collection in the model’s dataSourceSettings [`dataManager`](../api/diagram/dataSourceModel#dataManager) property. The nodes will be generated based on the data specified in the data source.

* You can set the connector collection in the model’s dataSourceSettings [`connectionDataSource`](../api/diagram/dataSourceModel#connectionDataSource) property.

* The dataSourceSettings connectionDataSource [`dataManager`](../api/diagram/connectionDataSourceModel#dataManager) property is used to set the data source for the connection data source items.

* If you have a data (data will be set in the dataSource property) with parent relationship in the database and also defined the connector in the connectionDataSource simultaneously, then the connectors set in the connectionDataSource will be considered as a priority to render the connector.

* The dataSourceSettings [`crudAction’s`](../api/diagram/dataSourceModel#crudAction) [`read`](../api/diagram/crudActionModel#read) property specifies the method, which is used to read the data source and its populate the nodes in the diagram.

* The connectionDataSource crudAction’s [`read`](../api/diagram/crudActionModel#read) specifies the method, which is used to read the data source and its populates the connectors in the diagram.

* The dataSourceSettings’s [`id`](../api/diagram/dataSourceModel#id) and connectionDataSource’s [`id`](../api/diagram/connectionDataSourceModel#id) properties are used to define the unique field of each JSON data.

* The connectionDataSource’s [`sourceID`](../api/diagram/connectionDataSourceModel#sourceID) and [`targetID`](../api/diagram/connectionDataSourceModel#targetID) properties are used to set the sourceID and targetID for connection data source item.

* The connectionDataSource’s [`sourcePointX`](../api/diagram/connectionDataSourceModel#sourcePointX), [`sourcePointY`](../api/diagram/connectionDataSourceModel#sourcePointY), [`targetPointX`](../api/diagram/connectionDataSourceModel#targetPointX), and [`targetPointY`](../api/diagram/connectionDataSourceModel#targetPointY) properties are used to define the sourcePoint and targetPoint values for connector from data source.

* The dataSourceSettings crudAction’s [`customFields`](../api/diagram/crudActionModel#customFields) property is used to maintain the additional information for nodes.

* Similarly, connectionDataSource’s crudAction’s [`customFields`](../api/diagram/crudActionModel#customFields) is used to maintain the additional information for connectors.

## How to perform Editing at runtime

* The dataSourceSettings crudAction object allows you to define the method, which is used to get the changes done in the data source defined for shapes from the client-side to the server-side.

* Similarly, the connectionDataSource crudAction object allows you to define the method, which is used to get the changes done in the data source defined for connectors from the client-side to the server-side.

## InsertData

* The dataSourceSettings crudAction’s [`create`](../api/diagram/crudActionModel#create) property specifies the method, which is used to get the nodes added from the client-side to the server-side.

* The connectionDataSource crudAction’s  [`create`](../api/diagram/crudActionModel#create) specifies the method, which is used to get the connectors added from the client-side to the server-side.

* The following code example illustrates how to send the newly added or inserted data from the client to server-side.

```typescript

//Initialize diagram
let diagram: Diagram = new Diagram({
     dataSourceSettings: {
       crudAction:
        {
            //Url which triggers the server side AddNodes method
            create: 'https://ej2services.syncfusion.com/development/web-services/api/Crud/AddNodes',
        },
     }
     connectionDataSource: {
            crudAction: {
                //Url which triggers the server side AddConnectors method
                create: 'https://ej2services.syncfusion.com/development/web-services/api/Crud/AddConnectors',
            }
     }
});
diagram.appendTo('#diagram');
//Sends the newly added nodes/connectors from client side to the server side through the URL which is specified in server side.
diagram.insertData();

```

## UpdateData

* The dataSourceSettings crudAction’s [`update`](../api/diagram/crudActionModel#update) property specifies the method, which is used to get the modified nodes from the client-side to the server-side.

* The connectionDataSource crudAction’s [`update`](../api/diagram/crudActionModel#update) specifies the method, which is used to get the modified connectors from the client-side to the server-side.

* The following code example illustrates how to send the updated data from the client to the server side.

```typescript

//Initialize diagram
let diagram: Diagram = new Diagram({
     dataSourceSettings: {
       crudAction:
        {
           //Url which triggers the server side UpdateNodes method
           update: 'https://ej2services.syncfusion.com/development/web-services/api/Crud/UpdateNodes',
        },
     }
     connectionDataSource: {
        crudAction: {
           //Url which triggers the server side UpdateConnectors method
           update: 'https://ej2services.syncfusion.com/development/web-services/api/Crud/UpdateConnectors',
        }
     }
});
diagram.appendTo('#diagram');
//Sends the updated nodes/connectors from client side to the server side through the URL which is specified in server side.
diagram.updateData();

```

## DeleteData

* The dataSourceSettings crudAction’s [`destroy`](../api/diagram/crudActionModel#destroy) property specifies the method, which is used to get the deleted nodes from the client-side to the server-side.

* The connectionDataSource crudAction’s [`destroy`](../api/diagram/crudActionModel#destroy) specifies the method, which is used to get the deleted connectors from the client-side to the server-side.

```typescript

//Initialize diagram
let diagram: Diagram = new Diagram({
     dataSourceSettings: {
       crudAction:
        {
          //Url which triggers the server side DeleteNodes method
          destroy: 'https://ej2services.syncfusion.com/development/web-services/api/Crud/DeleteNodes',
        },
     }
     connectionDataSource: {
        crudAction: {
           //Url which triggers the server side DeleteConnectors method
           destroy: 'https://ej2services.syncfusion.com/development/web-services/api/Crud/DeleteConnectors',
        }
     }
});
diagram.appendTo('#diagram');
//Sends the deleted nodes/connectors from client side to the server side through the URL which is specified in server side.
diagram.removeData();

```

## See Also

* [How to arrange the diagram nodes and connectors using varies layout](./automatic-layout)
