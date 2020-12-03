---
title: "ListView How to filter and search list items using listview"
component: "ListView"
description: "ListView how to section, get selected item, dual list, listview filtering, add & remove items from listview, grid layout using listview, listview drag & drop."
---

# How To filter and search list items using listview

The filtered data can be displayed in the ListView control depending upon on user inputs using the
[`DataManager`](../../data/getting-started/). Refer to the
following steps to render the ListView with filtered data.

* Render a textbox to get input for filtering data.

* Render ListView with
[`dataSource`](../../api/list-view#datasource), and set
the [`sortOrder`](../../api/list-view#sortorder) property.

* Bind the `keyup` event for textbox to perform filtering operation. To filter list data, pass the list data source to the
`DataManager`, manipulate the data using the
[`executeLocal`](../../api/data/dataManager#executelocal) method,
and then update filtered data as ListView dataSource.

{% tab template="listview/filter", isDefaultActive=true, sourceFiles="index.ts,index.html,index.css", es5Template="filter-template" %}

```typescript

import { ListView } from "@syncfusion/ej2-lists";
import { enableRipple } from "@syncfusion/ej2-base";
import { DataManager, Query } from "@syncfusion/ej2-data";
enableRipple(true);
//Define an array of JSON data
let listData: { [key: string]: Object }[] = [
  { text: "Hennessey Venom", id: "list-01" },
  { text: "Bugatti Chiron", id: "list-02" },
  { text: "Bugatti Veyron Super Sport", id: "list-03" },
  { text: "SSC Ultimate Aero", id: "list-04" },
  { text: "Koenigsegg CCR", id: "list-05" },
  { text: "McLaren F1", id: "list-06" }
];

// Initialize the ListView control
let listObj: ListView = new ListView({
  //Set the defined data to the dataSource property
  dataSource: listData,
  //Map the appropriate columns to the fields property
  fields: { text: "text", id: "id" },
  //Set the sortOrder property
  sortOrder: "Ascending"
});
//Render the initialized ListView control
listObj.appendTo("#list");

document.getElementById("textbox").addEventListener("keyup", onKeyUp);
//Here, the list items are filtered using the DataManager instance for ListView
function onKeyUp() {
  let value = (document.getElementById("textbox") as HTMLInputElement).value;
  let data: Object[] = new DataManager(listData).executeLocal(
    new Query().where("text", "startswith", value, true)
  );
  if (!value) {
    listObj.dataSource = listData.slice();
  } else {
    listObj.dataSource = data as { [key: string]: Object }[];
  }
  listObj.dataBind();
}

```

{% endtab %}

> In this demo, data has been filtered with starting character of the list items. You can also filter list items with ending
character by passing the `endswith` in
[where](../../api/data/query#where)
clause instead of `startswith`.
