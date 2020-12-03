---
title: "Group items in Popup"
component: "SplitButton"
description: "TypeScript SplitButton how to section, group popup items using list view component, dialog open on popup item click."
---

# Group items in Popup

Items in popup can be grouped in SplitButton by templating entire popup with ListView. To achieve grouping in ListView,
check [`ListView Grouping`](../../listview/grouping#grouping) documentation. To template ListView in popup, create
ListView with id `listview` and provide it as [`target`](../../api/split-button#target) for SplitButton.

The following example illustrates how to group items in popup using ListView component.

{% tab template= "split-button/listview", sourceFiles="app.ts,index.html,styles.css", es5Template="grouped-list-view-template" %}

```typescript

import { SplitButton } from '@syncfusion/ej2-splitbuttons';
import { ListView } from '@syncfusion/ej2-lists';
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);

let listItems: { [key: string]: Object }[] = [
    {
        'text': 'Cut',
        'category': 'Basic'
    },
    {
        'text': 'Copy',
        'category': 'Basic'
    },
    {
        'text': 'Paste',
        'category': 'Basic'
    },
    {
        'text': 'Paste as Formula',
        'category': 'Advanced'
    },
    {
        'text': 'Paste as Hyperlink',
        'category': 'Advanced'
    },
];

let listView: ListView = new ListView({
    dataSource: listItems,
    sortOrder: 'Descending',
    fields: { groupBy: 'category' }
}, '#listview');

let splitBtn: SplitButton =  new SplitButton({ content: 'ClipBoard', target: listView.element }, '#element');

```

{% endtab %}