---
title: "Integrate other component inside the card"
component: "Card"
description: "This example demonstrates how to integrate other Essential JS 2 components inside the Essential JS 2 Card component."
---

# Integrate other component inside the card

You can integrate any component inside the card element. Here ListView component is placed inside the card for showcasing the To-Do list.

{% tab template="card/card_with_list" , es5Template="card_with_list", sourceFiles="index.html,index.ts,index.css" %}

```typescript
import { ListView } from '@syncfusion/ej2-lists';

//Define the array of JSON
let todoList: { [key: string]: Object }[] = [
    {  todoList: 'Pay Bills' },
    {  todoList: 'Call Chris' },
    {  todoList: 'Meet Andrew' },
    {  todoList: 'Visit Manager' },
    {  todoList: 'Customer Meeting' },
];

//Initialize ListView component
let listviewInstance: ListView = new ListView({
    dataSource: todoList,
    //Map the appropriate columns to fields property
    fields: { text: 'todoList' },
    showCheckBox: true,
});

//Render initialized ListView
listviewInstance.appendTo("#element");

```

{% endtab %}