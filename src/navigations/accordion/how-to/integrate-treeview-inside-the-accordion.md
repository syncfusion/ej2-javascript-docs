---
title: "Integrate Essential JS 2 TreeView inside the Accordion"
component: "Accordion"
description: "This example demonstrates how to integrate the Essential JS 2 TreeView component inside the Essential JS 2 Accordion component."
---

# Integrate Essential JS 2 TreeView inside the Accordion

Accordion supports to render other Essential JS 2 Components by using content property. You can give content as an element string like below, for initializing the component.

```js
content: '<div id="element"> </div>'
```

The other component can be rendered with the use of provided events, such as [`clicked`](../../api/accordion#clicked) and [`expanding`](../../api/accordion#expanding).
The following procedure is to render a TreeView within the Accordion,

* Import the `TreeView` module from `ej2-navigations`, for adding TreeView. Please refer the [TreeView initialization steps](../../treeview/getting-started/)

* You can initialize the TreeView component in [`expanding`](../../api/accordion#expanding) event, by getting the element and defining the required TreeView properties.

{% tab template="accordion/accordion-treeview", es5Template="es5_accordion_treeview", sourceFiles="index.ts,index.html,datasource.ts" %}

```typescript

import { Accordion, TreeView } from '@syncfusion/ej2-navigations';
import { DocDB, DownloadDB, PicDB} from 'datasource.ts'

  //Initialize Accordion component
    let acrdnObj: Accordion = new Accordion({
    expanding: expand,
    width: 400,
       items : [
           { header: 'Documents', expanded: true, content: '<div id="treeDoc"></div>' },
           { header: 'Downloads', content : '<div id="treeDownload"></div>' },
           { header: 'Pictures', content: '<div id="treePic"></div>' },
       ]
    });
    //Render initialized Accordion component
    acrdnObj.appendTo('#element');

    //Expanding Event function for Accordion component.
    function expand(e: ExpandEventArgs): void {
  if (e.name === 'expanding' && [].indexOf.call(this.items, e.item) === 0 && e.element.querySelector('#treeDoc').childElementCount === 0) {
    //Initialize TreeView component
        let treeObj: TreeView = new TreeView({
        fields: { dataSource: DocDB, id: 'nodeId', text: 'nodeText', child: 'nodeChild', iconCss: 'icon', imageUrl: 'image' },
        sortOrder: 'Ascending'
    });
    //Render initialized TreeView component
    treeObj.appendTo('#treeDoc');
  }
    if (e.name === 'expanding' && [].indexOf.call(this.items, e.item) === 1 && e.element.querySelector('#treeDownload').childElementCount === 0) {
        let treeObj: TreeView = new TreeView({
        fields: { dataSource: DownloadDB, id: 'nodeId', text: 'nodeText', child: 'nodeChild', iconCss: 'icon', imageUrl: 'image' },
        sortOrder: 'Ascending'
    });
    treeObj.appendTo('#treeDownload');
  }
      if (e.name === 'expanding' && [].indexOf.call(this.items, e.item) === 2 && e.element.querySelector('#treePic').childElementCount === 0) {
        let treeObj: TreeView = new TreeView({
        fields: { dataSource: PicDB, id: 'nodeId', text: 'nodeText', child: 'nodeChild', iconCss: 'icon', imageUrl: 'image' },
        sortOrder: 'Ascending'
    });
    treeObj.appendTo('#treePic');
  }
}

```

{% endtab %}
