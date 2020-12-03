---
title: "ListView how to trace events of listview"
component: "ListView"
description: "ListView how to section, get selected item, dual list, listview filtering, add & remove items from listview, grid layout using listview, listview drag & drop."
---

# How to trace events of listview

The ListView control triggers events based on its actions. The events can be used as extension points to perform
custom operations. Refer to the following steps to trace the ListView events:

1. Render the ListView with
[dataSource](../../api/list-view#datasource), and
bind the [`actionBegin`](../../api/list-view#actionbegin),
[`actionComplete`](../../api/list-view#actioncomplete),
and [`select`](../../api/list-view#select) events.

2. Perform custom operations in actionBegin, actionComplete, and select events.

3. Provide event log details for actionBegin and actionComplete events, and they will be displayed in the event trace panel
when the ListView action starts and the dataSource bound successfully.

4. Get the selected item details from the
[`SelectEventArgs`](../../api/list-view/selectEventArgs) in the
select event, and display the selected list item text in the event trace panel while selecting list items.

5. Use clear button to remove event trace information.

{% tab template="listview/events", isDefaultActive=true, sourceFiles="index.ts,index.html,index.css", es5Template="events-template" %}

```typescript

import { ListView, SelectEventArgs } from "@syncfusion/ej2-lists";
import { Button } from "@syncfusion/ej2-buttons";

//Define an array of JSON data
let data: { [key: string]: Object }[] = [
  { text: "Hennessey Venom", id: "list-01" },
  { text: "Bugatti Chiron", id: "list-02" },
  { text: "Bugatti Veyron Super Sport", id: "list-03" },
  { text: "SSC Ultimate Aero", id: "list-04" },
  { text: "Koenigsegg CCR", id: "list-05" },
  { text: "McLaren F1", id: "list-06" },
  { text: "Aston Martin One- 77", id: "list-07" },
  { text: "Jaguar XJ220", id: "list-08" },
  { text: "McLaren P1", id: "list-09" },
  { text: "Ferrari LaFerrari", id: "list-10" }
];
let clear: Button = new Button();
clear.appendTo('#clear');

//Initialize the ListView control
let listObj: ListView = new ListView({
  //Set the defined data to the dataSource property
  dataSource: data,
  actionBegin: onActionBegin,
  actionComplete: onActionComplete,
  select: onSelect,
  width:"250"
});
//Render the initialized ListView control
listObj.appendTo("#listview-def");

//Clears the event log details
document.getElementById("clear").onclick = () => {
  document.getElementById("EventLog").innerHTML = "";
};
//Handler for actionBegin event trace
function onActionBegin(): void {
  appendElement("<b>actionBegin </b> event is triggered<hr>");
}
//Handler for select event trace
function onSelect(args: SelectEventArgs): void {
  appendElement(args.text + "<b>&nbsp;&nbsp;is selected</b><hr>");
}
//Handler for actionComplete event trace
function onActionComplete(): void {
  appendElement("<b>actionComplete</b> is triggered <hr>");
}

//Display event log
function appendElement(html: string): void {
  let span: HTMLElement = document.createElement("span");
  span.innerHTML = html;
  let log: HTMLElement = document.getElementById("EventLog");
  log.insertBefore(span, log.firstChild);
}

```

{% endtab %}
