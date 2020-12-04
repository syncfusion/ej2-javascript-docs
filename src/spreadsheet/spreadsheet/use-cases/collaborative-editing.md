---
title: "Collaborative Editing in Spreadsheet"
component: "Spreadsheet"
description: "This section helps to learn how to collaborative editing in Spreadsheet control"
---

# Collaborative Editing

The collaborative editing support allows you to work at a spreadsheet collaboratively with other users. Multiple users can access to the the same spreadsheet simultaneously.

> * To use Collaborative editing, inject the `CollaborativeEditing` module in the spreadsheet.

## Dependencies

The following dependent script is required to use the collaborative editing support in spreadsheet.

```js
<script src="https://cdnjs.cloudflare.com/ajax/libs/aspnet-signalr/1.1.4/signalr.js"></script>
```

## Server configuration

To make the communication between the server to the connected clients and from clients to the server, you need to configure the signalR Hubs using the following code.

```js

// For signalR Hub connection

var connection = new signalR.HubConnectionBuilder().withUrl('https://ej2services.syncfusion.com/production/web-services/hubs/spreadsheethub',{
    skipNegotiation: true,
    transport: signalR.HttpTransportType.WebSockets
  }).build();

```

## Client configuration

To broadcast the data for every action is spreadsheet, you need to transfer the data to the server through `send` method in `actionComplete` event and receive the same data by using the `dataReceived` method. In the `dataReceived` method, you need to update the action to the connected clients through `updateAction` method.

The following code example shows `Collaborative Editing` support in the Spreadsheet control.

{% tab template="spreadsheet/collaborative-editing" es5Template="collaborative-editing" sourceFiles="app.ts,index.html,datasource.ts", iframeHeight="450px", isDefaultActive=true %}

```javascript

var sheet = [{
                ranges: [{ dataSource: defaultData }],
                columns: [{ width: 130 }, { width: 110 },{ width: 110},
                          { width: 90 }, { width: 90 }, {width: 90}, { width: 90 }, {width: 90}]
            }]
// To Inject CollaborativeEditing module.
ej.spreadsheet.Spreadsheet.Inject(ej.spreadsheet.CollaborativeEditing);

// For signalR Hub connection
var connection = new signalR.HubConnectionBuilder().withUrl('https://ej2services.syncfusion.com/production/web-services/hubs/spreadsheethub',{
    skipNegotiation: true,
    transport: signalR.HttpTransportType.WebSockets
  }).build();

var spreadsheet = new ej.spreadsheet.Spreadsheet({
    sheets: sheet,
    actionComplete: function (args) {
       connection.send('BroadcastData', JSON.stringify(args)); // send the action data to the server
       },
 });

// Render initialized Spreadsheet.
spreadsheet.appendTo('#spreadsheet');

connection.on('dataReceived', (data) => {
    spreadsheet.updateAction(data);
});
connection.start().then(() => {
    console.log('server connected!!!');
}).catch((err) => console.log(err));


```

{% endtab %}

## Prevent the particular action update for collaborative client

Using the `action` argument from the `actionComplete` event, you can prevent the particular action update for collaborative client.

The following code example shows how to prevent collaborative client from updating the `format` action.

{% tab template="spreadsheet/collaborative-prevent-action" sourceFiles="app.ts,index.html,datasource.ts", iframeHeight="450px",es5Template="collaborative-prevent-action" %}

```javascript

var sheet = [{
                ranges: [{ dataSource: defaultData }],
                columns: [{ width: 130 }, { width: 110 },{ width: 110},
                          { width: 90 }, { width: 90 }, {width: 90}, { width: 90 }, {width: 90}]
            }]
// To Inject CollaborativeEditing module.
ej.spreadsheet.Spreadsheet.Inject(ej.spreadsheet.CollaborativeEditing);

// For signalR Hub connection
var connection = new signalR.HubConnectionBuilder().withUrl('https://ej2services.syncfusion.com/production/web-services/hubs/spreadsheethub',{
    skipNegotiation: true,
    transport: signalR.HttpTransportType.WebSockets
  }).build();

var spreadsheet = new ej.spreadsheet.Spreadsheet({
    sheets: sheet,
    actionComplete: function (args) {
            if (args.action != 'format'){  // prevent the format action
               connection.send('BroadcastData', JSON.stringify(args)); // send the action data to the server
         }
       },
 });

// Render initialized Spreadsheet.
spreadsheet.appendTo('#spreadsheet');

connection.on('dataReceived', (data) => {
    spreadsheet.updateAction(data);
});
connection.start().then(() => {
    console.log('server connected!!!');
}).catch((err) => console.log(err));

```

{% endtab %}