---
title: "HTML5 JavaScript DataManager | Data Adaptors | Syncfusion"
component: "DataManager"
description: "Documentation on how to interact with a variety of services by using data adaptors, including UrlAdaptor, ODataAdaptor, ODataV4Adaptor, and WebApiAdaptor. Also details how to write custom adaptors"
---

# Data Adaptors

Each data source or remote service uses different way in accepting request and sending back the response. **DataManager** cannot anticipate every way a data source works. To tackle this problem the **DataManager** uses the adaptor concept to communicate with particular data source.

For local data sources, the role of the data adaptor is to query the JavaScript object array based on the **Query** object and manipulate them.

When comes with remote datasource, the data adaptor is used to send the request that the server can understand and process the server response.

The adaptor can be assigned using the `adaptor` property of the **DataManager**.

## Json adaptor

`JsonAdaptor` is used to query and manipulate JavaScript object array.

{% tab template="data/getting-started" %}

```typescript
import { DataManager, Query, JsonAdaptor } from '@syncfusion/ej2-data';
import { compile } from '@syncfusion/ej2-base';
import {data} from './datasource.ts';

let template: string = '<tr><td>${OrderID}</td><td>${CustomerID}</td><td>${EmployeeID}</td></tr>';
let compiledFunction: Function = compile(template);

let result: Object[] = new DataManager({ json: data, adaptor: new JsonAdaptor })
                                .executeLocal(new Query().take(8));

let table: HTMLElement = (<HTMLElement>document.getElementById('datatable'));

result.forEach((data: Object) => {
    table.appendChild(compiledFunction(data)[0]);
});

```

{% endtab %}

## Url adaptor

`UrlAdaptor` act as the base adaptor for interacting with remote data services. Most of the built-in adaptors are derived from the `UrlAdaptor`.

```typescript
import { DataManager, Query, UrlAdaptor } from '@syncfusion/ej2-data';

const SERVICE_URI: string = 'http://controller.com/actions';

new DataManager({
        url: SERVICE_URI,
        adaptor: new UrlAdaptor
    }).executeQuery(new Query().take(8)).then((e) => {
        //e.result will contain the records
    });

```

`UrlAdaptor` expects response as a JSON object with properties `result` and `count` which
contains the collection of entities and the total number of records respectively.

The sample response object should be as follows,

```json
{
    "result": [{..}, {..}, {..}, ...],
    "count": 67
}
```

## OData adaptor

[OData](http://www.odata.org/documentation/odata-version-3-0/) is standardized protocol for creating and consuming data. You can retrieve data from OData service using **DataManager**. The `ODataAdaptor` helps you to interact with OData service. You can refer to the following code example of remote Data binding using OData service.

{% tab template="data/getting-started" %}

```typescript
import { DataManager, Query, ReturnOption, ODataAdaptor } from '@syncfusion/ej2-data';
import { compile } from '@syncfusion/ej2-base';

let template: string = '<tr><td>${OrderID}</td><td>${CustomerID}</td><td>${EmployeeID}</td></tr>';

let compiledFunction: Function = compile(template);

const SERVICE_URI: string = 'https://js.syncfusion.com/demos/ejServices/Wcf/Northwind.svc/Orders';

let table: HTMLElement = (<HTMLElement>document.getElementById('datatable'));

new DataManager({ url: SERVICE_URI, adaptor: new ODataAdaptor }).executeQuery(new Query().take(8)).then((e: ReturnOption) => {

        (<Object[]>e.result).forEach((data: Object) => {
            table.appendChild(compiledFunction(data)[0]);
        });
});

```

{% endtab %}

> By default, `ODataAdaptor` is used by **DataManager**.

## ODataV4 adaptor

The ODataV4 is an improved version of OData protocols and the **DataManager** can also retrieve and consume OData v4 services. For more details on OData v4 Services, refer the [odata documentation](http://docs.oasis-open.org/odata/odata/v4.0/errata03/os/complete/part1-protocol/odata-v4.0-errata03-os-part1-protocol-complete.html#_Toc453752197). You can use the `ODataV4Adaptor` to interact with ODataV4 service.

{% tab template="data/getting-started" %}

```typescript
import { DataManager, Query, ReturnOption, ODataV4Adaptor } from '@syncfusion/ej2-data';
import { compile } from '@syncfusion/ej2-base';

let template: string = '<tr><td>${OrderID}</td><td>${CustomerID}</td><td>${EmployeeID}</td></tr>';

let compiledFunction: Function = compile(template);

const SERVICE_URI: string =  'http://services.odata.org/V4/Northwind/Northwind.svc/Orders/';

let table: HTMLElement = (<HTMLElement>document.getElementById('datatable'));

new DataManager({ url: SERVICE_URI, adaptor: new ODataV4Adaptor }).executeQuery(new Query().take(8)).then((e: ReturnOption) => {

        (<Object[]>e.result).forEach((data: Object) => {
            table.appendChild(compiledFunction(data)[0]);
        });
});

```

{% endtab %}

## Web API adaptor

You can use the `WepApiAdaptor` to interact with Web API created with OData endpoint. The `WebApiAdaptor` is extended from the `ODataAdaptor`. Hence to use `WebApiAdaptor`, the endpoint should understand the OData formatted queries send along with request.

To enable OData query option for Web API, please refer to the [documentation](https://docs.microsoft.com/en-us/aspnet/web-api/overview/odata-support-in-aspnet-web-api/supporting-odata-query-options)

```typescript
import { DataManager, Query, WebApiAdaptor } from '@syncfusion/ej2-data';

const SERVICE_URI: string = 'http://controller.com/api';

new DataManager({
        url: SERVICE_URI,
        adaptor: new WebApiAdaptor
    }).executeQuery(new Query().take(8)).then((e) => {
        //e.result will contain the records
    });
```

`WebApiAdaptor` expects JSON response from the server and the response object should contain properties `Items` and `Count` whose values are collection of entities and total count of the entities respectively.

The sample response object should look like below.

```json
{
    Items: [{..}, {..}, {..}, ...],
    Count: 830
}
```

## WebMethod Adaptor

The `WebMethodAdaptor` is used to bind data source from remote services and code behind methods. It can be enabled in Grid using Adaptor property of DataManager as `WebMethodAdaptor`.

For every operations, an AJAX post will be send to the specified data service.

```typescript
import { DataManager, Query, WebMethodAdaptor } from '@syncfusion/ej2-data';

let SERVICE_URI = 'Default.aspx/DataSource';

new DataManager({
        url: SERVICE_URI,
        adaptor: new WebMethodAdaptor
    }).executeQuery(new Query().take(8)).then((e) => {
        //e.result will contain the records
    });
```

`WebMethodAdaptor` expects JSON response from the server and the response object should contain properties `result` and `count`
whose values are collection of entities and total count of the entities respectively.

The sample response object should look like below.

```json
{
    result: [{..}, {..}, {..}, ...],
    count: 830
}
```

> The controller method's data parameter name must be `value`.

## Custom Data Adaptor

The `CustomDataAdaptor` provides an option to send your own request to handle the data operations.

You can get the current action details inside the `getData` method of `CustomDataAdaptor` to build the request. Once the data is fetched from the service successfully, then the `onSuccess` method can be invoked to handle the further data processing. In failure case, invoke the `onFailure` method.

```typescript
import { DataManager, Query, CustomDataAdaptor, AjaxOption } from '@syncfusion/ej2-data';

const SERVICE_URI: string = 'http://controller.com/actions';

new DataManager({
        adaptor: new CustomDataAdaptor({
                getData: function(option: AjaxOption) {
                      let xhttp: XMLHttpRequest = new XMLHttpRequest();
                      xhttp.onreadystatechange = function () {
                        if (this.readyState == 4) {
                             let request: Object = extend({}, option, { httpRequest: xhttp });
                             if ((xhttp.status >= 200 && xhttp.status <= 299) || xhttp.status === 304) {
                             let data: Object = JSON.parse(xhttp.responseText);
                             option.onSuccess(data, request);
                            } else {
                             option.onFailure(request);
                            }
                        }
                    };
                    xhttp.open("POST", SERVICE_URI, true);
                    xhttp.setRequestHeader('Content-Type', 'application/json; charset=utf-8');
                    xhttp.send(option.data);
                }
            })
    }).executeQuery(new Query().take(8)).then((e) => {
        //e.result will contain the records
    });
```

Since the `CustomDataAdaptor` is extended from the `UrlAdaptor`, it expects response as a JSON object with properties `result` and `count` which
contains the collection of entities and the total number of records respectively.

The sample response object should be as follows,

```json
{
    "result": [{..}, {..}, {..}, ...],
    "count": 67
}
```

### Performing CRUD action with CustomDataAdaptor

You can perform the CRUD actions using the `addRecord`, `updateRecord`, `deleteRecord` and `batchUpdate` methods.

```typescript
import { DataManager, Query, CustomDataAdaptor, AjaxOption } from '@syncfusion/ej2-data';

let createRequest: Function = (url: string, option: AjaxOption) => {
    let xhttp: XMLHttpRequest = new XMLHttpRequest();
    xhttp.onreadystatechange = function () {
        if (this.readyState == 4) {
            let request: Object = extend({}, option, { httpRequest: xhttp });
            if ((xhttp.status >= 200 && xhttp.status <= 299) || xhttp.status === 304) {
                let data: Object = JSON.parse(xhttp.responseText);
                option.onSuccess(data, request);
            } else {
                option.onFailure(request);
            }
        }
    };
    xhttp.open("POST", url, true);
    xhttp.setRequestHeader('Content-Type', 'application/json; charset=utf-8');
    xhttp.send(option.data);
};

let baseUrl: string = "http://localhost:65327/Home/";

new DataManager({
        adaptor: new CustomDataAdaptor({
                getData: function (option: AjaxOption) {
                    createRequest(baseUrl + 'UrlDatasource', option);
                },
                addRecord: function (option: AjaxOption) {
                    createRequest(baseUrl + 'Insert', option);
                },
                updateRecord: function (option: AjaxOption) {
                    createRequest(baseUrl + 'Update', option);
                },
                deleteRecord: function (option: AjaxOption) {
                    createRequest(baseUrl + 'Delete', option);
                }
                // to handle Batch operation
                //batchUpdate: function (option: AjaxOption) {
                //  createRequest(baseUrl + 'Delete', option);  
                //}
            })
    }).executeQuery(new Query().take(8)).then((e) => {
        //e.result will contain the records
    });
```

## GraphQL Adaptor

The `GraphQLAdaptor` provides an option to retrieve data from the GraphQL server. It performs CRUD and data operations such as paging, sorting, filtering etc by sending the required arguments to the server.

You can provide the GraphQL query string by using the `query` property of the `GraphQLAdaptor`. Since, the `GraphQLAdaptor` is extended from the `UrlAdaptor`, it expects response as a JSON object with properties `result` and `count` which contains the collection of entities and the total number of records respectively. The GraphQL response should be returned in JSON format like {
  "data": { ... }} with query name as field, you need to set the `result` and `count` properties to map the response.

```typescript
import { DataManager, Query, GraphQLAdaptor } from '@syncfusion/ej2-data';

const SERVICE_URI: string = 'http://controller.com/actions';

new DataManager({
        url: SERVICE_URI, adaptor: new GraphQLAdaptor({
        response: {
            result: 'getOrders.OrderData',
            count: 'getOrders.OrderCount'
        },
        query: `query getOrders($datamanager: String) {
            getOrders(datamanager: $datamanager) {
                OrderCount,
                OrderData{OrderID, CustomerID, EmployeeID, ShipCity, ShipCountry}
             }
    }`
    })
    }).executeQuery(new Query().take(8)).then((e) => {
        //e.result will contain the records
    });
```

The Schema for the GraphQL server is

```typescript

input OrderInput {
  OrderID: Int!
  CustomerID: String!
  EmployeeID: Int!
  ShipCity: String!
  ShipCountry: String!
}

type Order {
  OrderID: Int!
  CustomerID: String!
  EmployeeID: Int!
  ShipCity: String!
  ShipCountry: String!
}

type ReturnType {
  getOrders: [Order]
  count: Int
}

type Query {
  getOrders(datamanager: String): ReturnType
}
type Mutation {
  createOrder(value: OrderInput): Order!
  updateOrder(key: Int!, keyColumn: String, value: OrderInput): Order
  deleteOrder(key: Int!, keyColumn: String, value: OrderInput): Order!
}
```

The resolver for the corresponding action is

```typescript
import { data } from "./db";

const resolvers = {
  Query: {
    getOrders: (parent, { datamanager }, context, info) => {
      if (datamanager.search) {
        // Perform searching
      }
      if (datamanager.sorted) {
        // Perform sorting
      }
      if (datamanager.where) {
        // Perform filtering
      }
      if (datamanager.search) {
        // Perform search
      }
      if (datamanager.skip && datamanager.take) {
        // Perform Paging
      }
      return { OrderData: data, OrderCount: data.length };
    }
  },
  Mutation: {
    createOrder: (parent, { value }, context, info) => {
      // Perform Insert
      return value;
    },
    updateOrder: (parent, { key, keyColumn, value }, context, info) => {
      // Perform Update
      return value;
    },
    deleteOrder: (parent, { key, keyColumn, value }, context, info) => {
      // Perform Delete
      return value;
    },
  }
};

export default resolvers;

```

The query parameters will be send in a string format which contains the below details.

| Parameters | Description |
|-----|-----|
| `RequiresCounts` | If it is `true` then the total count of records will be included in response. |
| `Skip` | Holds the number of records to skip. |
| `Take` | Holds the number of records to take. |
| `Sorted` | Contains details about current sorted column and its direction. |
| `Where` | Contains details about current filter column name and its constraints. |
| `Group` | Contains details about current Grouped column names. |

### Performing CRUD action with GraphQLAdaptor

You can perform the CRUD actions by returning the mutation queries inside the `getMutation` method based on the action.

```typescript
import { DataManager, Query, GraphQLAdaptor } from '@syncfusion/ej2-data';

const SERVICE_URI: string = 'http://controller.com/actions';

new DataManager({
        url: SERVICE_URI, adaptor: new GraphQLAdaptor({
        response: {
            result: 'getOrders.getOrders',
            count: 'getOrders.count'
        },
        query: `query getOrders($datamanager: String) {
            getOrders(datamanager: $datamanager) {
                count,
                getOrders{OrderID, CustomerID, EmployeeID, ShipCity, ShipCountry}
             }
    }`,
    getMutation: function (action): string {
            if (action === 'insert') {
                return `mutation CreateOrderMutation($value: OrderInput!){
                                        createOrder(value: $value){
                                            OrderID, CustomerID, EmployeeID, ShipCity, ShipCountry
                                    }}`;
            }
            if (action === 'update') {
                return `mutation Update($key: ID!, $keyColumn: String,$value: OrderInput){
                            updateOrder(key: $key, keyColumn: $keyColumn, value: $value) {
                                OrderID, CustomerID, EmployeeID, ShipCity, ShipCountry
                            }
                            }`;
            } else {
                return `mutation Remove($key: ID!, $keyColumn: String, $value: OrderInput){
                    deleteOrder(key: $key, keyColumn: $keyColumn, value: $value) {
                                OrderID, CustomerID, EmployeeID, ShipCity, ShipCountry
                            }
                            }`;
            }
        }
    })
    }).executeQuery(new Query().take(8)).then((e) => {
        //e.result will contain the records
    });

```

## Writing custom adaptor

Sometimes the built-in adaptors does not meet your requirement. In such cases you can create your own adaptor.

To create and use custom adaptor, please refer to the below steps.

* Select an built-in adaptor which will act as base class for your custom adaptor.
* Override the desired method to achieve your requirement.
* Assign the custom adaptor to the `adaptor` property of **DataManager**.

For the sake of demonstrating custom adaptor approach, we are going to see how to add serial number for the records by overriding the built-in response processing using `processResponse` method of the `ODataAdaptor`.

{% tab template="data/getting-started" %}

```typescript
import { DataManager, Query, ReturnOption, ODataAdaptor } from '@syncfusion/ej2-data';
import { compile } from '@syncfusion/ej2-base';

class SerialNoAdaptor extends ODataAdaptor {
    public processResponse(): Object {
        let i: number = 0;
        //calling base class processResponse function
        let original: Object[] = super.processResponse.apply(this, arguments);
        //Adding serial number
        original.forEach((item: Object) => item['Sno'] = ++i);
        return original;
    }
}

let template: string = '<tr><td>${Sno}</td><td>${CustomerID}</td><td>${EmployeeID}</td></tr>';

let compiledFunction: Function = compile(template);

const SERVICE_URI: string =  'https://js.syncfusion.com/demos/ejServices/Wcf/Northwind.svc/Orders';

let table: HTMLElement = (<HTMLElement>document.getElementById('datatable'));

table.innerHTML = '<tr><th>SNO</th><th>Customer ID</th><th>Employee ID</th></tr>';

new DataManager({ url: SERVICE_URI, adaptor: new SerialNoAdaptor }).executeQuery(new Query().take(8)).then((e: ReturnOption) => {

        (<Object[]>e.result).forEach((data: Object) => {
            table.appendChild(compiledFunction(data)[0]);
        });
});


```

{% endtab %}