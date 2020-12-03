# Apply hover background color in the whole multi-line of a tree node

This section demonstrates how to hover and select a multi-line tree node. Here, you can set the row height (element class: `e-fullrow`) to be the same as the row content (element class: `e-text-content`)

{% tab template="treeview/how-to/multi-line-tree", sourceFiles="index.ts,index.html,index.css", es5Template="treeview-multi-line-tree-template" %}

```typescript

import { enableRipple } from '@syncfusion/ej2-base';
import { TreeView } from '@syncfusion/ej2-navigations';
enableRipple(true);

/**
 * Hovering multiple line TreeView sample
 */

    // List data source for TreeView component
  let hierarchicalData: { [key: string]: Object }[] = [
        {
            id: 1, name: 'Web Control sWeb ControlsWeb ControlsWeb ControlsWeb ControlsWeb ControlsWeb ControlsWeb Controls', expanded: true,
            child: [
                {
                    id: 2, pid: 1, name: 'CalendarCalendarCalendarCalendarCalendarCalendarCalendarCalendarCalendarCalendarCalendarCalendarCalendar', checked: true, child: [
                        { id: 7, pid: 2, name: 'Constructors' },
                        { id: 8, pid: 2, name: 'Properties' },
                        { id: 9, pid: 2, name: 'Methods' },
                        { id: 10, pid: 2, name: 'Events' }
                    ]
                },
                {
                    id: 3, pid: 1, name: 'Data Grid', child: [
                        { id: 11, pid: 3, name: 'Constructors' },
                        { id: 12, pid: 3, name: 'Fields' },
                        { id: 13, pid: 3, name: 'Properties' },
                        { id: 14, pid: 3, name: 'Methods' },
                        { id: 15, pid: 3, name: 'Events' }
                    ]
                },
                {
                    id: 4, pid: 1, name: 'DropDownList', child: [
                        { id: 16, pid: 4, name: 'Constructors' },
                        { id: 17, pid: 4, name: 'Properties' },
                        { id: 18, pid: 4, name: 'Methods' }
                    ]
                },
                {
                    id: 5, pid: 1, name: 'Menu', child: [
                        { id: 19, pid: 5, name: 'Constructors' },
                        { id: 20, pid: 5, name: 'Fields' },
                        { id: 21, pid: 5, name: 'Properties' },
                        { id: 22, pid: 5, name: 'Methods' },
                        { id: 23, pid: 5, name: 'Events' }
                    ]
                }
            ]
        },
        {
            id: 24, name: 'Web Controls',
            child: [
                {
                    id: 25, pid: 24, name: 'Calendar', checked: true, child: [
                        { id: 26, pid: 25, name: 'Constructors' },
                        { id: 27, pid: 25, name: 'Properties' },
                        { id: 28, pid: 25, name: 'Methods' },
                        { id: 29, pid: 25, name: 'Events' }
                    ]
                },
                {
                    id: 30, pid: 24, name: 'Data Grid', child: [
                        { id: 31, pid: 30, name: 'Constructors' },
                        { id: 32, pid: 30, name: 'Fields' },
                        { id: 33, pid: 30, name: 'Properties' },
                        { id: 34, pid: 30, name: 'Methods' },
                        { id: 35, pid: 30, name: 'Events' }
                    ]
                }
            ]
        }
    ];

    // Render the TreeView by mapping its fields property with data source properties
    let treeObj: TreeView = new TreeView({
        fields: { dataSource:hierarchicalData , id: 'id', text: 'name', child: 'child' },
       nodeSelecting: onselect,
       cssClass: ("customTree")
    });
    treeObj.appendTo('#tree');

    // Triggers on mouse hover/keydown event
     ['mouseover','keydown'].forEach( evt =>
      document.getElementById("tree").addEventListener(evt, (event)=>{setHeight(event.target); }));

    // Triggers on node selection
    function onSelect(arg) {
      setHeight(arg.node);
    }

    // Sets e-fullrow to be the same as e-text-content
    function setHeight(element) {
      if(treeObj.fullRowSelect) {
        if(element.classList.contains("e-treeview")) {
          element = element.querySelector(".e-node-focus").querySelector(".e-fullrow");
        }
        else if(element.classList.contains("e-list-parent")) {
          element = element.querySelector(".e-fullrow");
        }
        else if(element.classList.value != ("e-fullrow") && element.closest(".e-list-item")) {
          element = element.closest(".e-list-item").querySelector(".e-fullrow");
        }
        if(element.nextElementSibling)
          element.style.height = element.nextElementSibling.offsetHeight +"px";
      }
    }
```

{% endtab %}