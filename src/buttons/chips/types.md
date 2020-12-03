# Types

The ChipList control has the following types.

* Input Chip
* Choice Chip
* Filter Chip
* Action Chip

## Input Chip

Input Chip holds information in compact form. It converts user input into chips.

{% tab template= "chips/types", sourceFiles="app.ts,index.html,styles.css",
es5Template="es5-inputs" isDefaultActive=true %}

```typescript

import { ChipList } from '@syncfusion/ej2-buttons';
new ChipList({chips: ['Andrew', 'Janet', 'Laura', 'Margaret']}, '#chip');

```

{% endtab %}

## Choice Chip

Choice Chip allows you to select a single chip from the set of ChipList/ChipCollection. It can be enabled by setting the `selection` property to `Single`.

{% tab template= "chips/types", sourceFiles="app.ts,index.html,styles.css",
es5Template="es5-choice" isDefaultActive=true %}

```typescript

import { ChipList } from '@syncfusion/ej2-buttons';
new ChipList({chips: ['Small', 'Medium', 'Large', 'Extra Large'], selection: "Single"}, '#chip');

```

{% endtab %}

## Filter Chip

Filter Chip allows you to select a multiple chip from the set of ChipList/ChipCollection. It can be enabled by setting the `selection` property to `Multiple`.

{% tab template= "chips/types", sourceFiles="app.ts,index.html,styles.css",
es5Template="es5-filter" isDefaultActive=true %}

```typescript

import { ChipList } from '@syncfusion/ej2-buttons';
new ChipList({chips: ['Chai', 'Chang', 'Aniseed Syrup', 'Ikura'], selection: "Multiple"}, '#chip');

```

{% endtab %}

## Action Chip

The Action Chip triggers the event like click or delete, which helps doing action based on the event.

{% tab template= "chips/types", sourceFiles="app.ts,index.html,styles.css",
es5Template="es5-action" isDefaultActive=true %}

```typescript

import { ChipList } from '@syncfusion/ej2-buttons';
new ChipList({chips: ['Send a text', 'Set a remainder', 'Read my emails ', 'Set alarm'],
    click: (e: ClickEventArgs)=>{
       alert('you have clicked ' + e.text)
    } }, '#chip');

```

{% endtab %}

### Deletable Chip

Deletable Chip allows you to delete a chip from ChipList/ChipCollection. It can be enabled by setting the `enableDelete` property to `true`.

{% tab template= "chips/types", sourceFiles="app.ts,index.html,styles.css",
es5Template="es5-delete" isDefaultActive=true %}

```typescript

import { ChipList } from '@syncfusion/ej2-buttons';
new ChipList({chips: ['Send a text', 'Set a remainder', 'Read my emails ', 'Set alarm'], enableDelete: true}, '#chip');

```

{% endtab %}