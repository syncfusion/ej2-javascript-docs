---
title: "Kanban drag and drop"
component: "Kanban"
description: "This article explains how to drag and drop the card information from an external source and vice versa."
---

# Drag and drop

All cards can be dragged and dropped across the columns or within the columns or swimlane row or kanban to an external source and vice versa.

The following drag and drop types are available in the Kanban board.

* Internal drag and drop
    * Column drag and drop
    * Swimlane drag and drop
* External drag and drop
    * Kanban to Kanban
    * Kanban to External source and vice versa.

> Dropped card position varies based on the `sortSettings` property.

## Internal drag and drop

Allows the user to drag and drop the cards within the kanban board. Based on this, we can categorize into two ways.

* Column drag and drop
* Swimlane drag and drop

### Column drag and drop

By default, all cards can be dragged and dropped across the columns and within the columns. You cannot drag and drop the cards when disabling the `allowDragAndDrop` property.

> You can prevent the drag or drop behavior of the particular column by disabling the `allowDrag` or `allowDrop` property.
> You can also control the flow of transition cards between the columns by using the `transitionColumns` property.

In the following example, disable the drag and drop behavior on the Kanban board.

{% tab template="kanban/drag-and-drop", es5Template="drag-and-drop", sourceFiles="index.ts,index.html,datasource.ts" %}

```typescript
import { Kanban } from '@syncfusion/ej2-kanban';
import { kanbanData } from './datasource.ts';

let kanbanObj: Kanban = new Kanban({
    dataSource: kanbanData,
    keyField: 'Status',
    columns: [
        { headerText: 'Backlog', keyField: 'Open' },
        { headerText: 'In Progress', keyField: 'InProgress' },
        { headerText: 'Testing', keyField: 'Testing' },
        { headerText: 'Done', keyField: 'Close' }
    ],
    cardSettings: {
        contentField: 'Summary',
        headerField: 'Id'
    },
    allowDragAndDrop: false
});
kanbanObj.appendTo('#Kanban');
```

{% endtab %}

### Swimlane drag and drop

By default, Swimlane allows drag and drop across the columns within the swimlane row. Kanban does not allow dragging the cards across the swimlane rows.

Enabling the `dragAndDrop` property allows you to drag the cards across the swimlane rows, which is specified inside the `swimlaneSettings` property.

{% tab template="kanban/swimlane-drag-and-drop", es5Template="swimlane-drag-and-drop", sourceFiles="index.ts,index.html,datasource.ts" %}

```typescript
import { Kanban } from '@syncfusion/ej2-kanban';
import { kanbanData } from './datasource.ts';

let kanbanObj: Kanban = new Kanban({
    dataSource: kanbanData,
    keyField: 'Status',
    columns: [
        { headerText: 'Backlog', keyField: 'Open' },
        { headerText: 'In Progress', keyField: 'InProgress' },
        { headerText: 'Testing', keyField: 'Testing' },
        { headerText: 'Done', keyField: 'Close' }
    ],
    cardSettings: {
        contentField: 'Summary',
        headerField: 'Id'
    },
    swimlaneSettings: {
        keyField: 'Assignee',
        allowDragAndDrop: true
    }
});
kanbanObj.appendTo('#Kanban');
```

{% endtab %}

## External drag and drop

Allows the user to drag and drop the cards from one kanban to another kanban or Kanban to an external source and vice versa.

### Kanban to kanban

Drag and drop the card from one kanban to another kanban and vice versa. This can be achieved by specifying the `externalDropId` property which is used to specify the id of the dropped kanban element and the `dragStop` event which is used to delete the card on dragged Kanban and add the card on dropped Kanban using the `deleteCard` and `addCard` public methods.

> Before adding a card to dropped kanban, you can manually change the card data `headerField` when the same card data `headerField` is dropped to another Kanban.

In the following example, Drag the card from one Kanban and drop it into another kanban using the `dragStop` event. In this event, remove the card from the dragged Kanban by using the `deleteCard` public method and add the card to the dropped Kanban by using the `addCard` public method.

{% tab template="kanban/kanban-to-kanban", es5Template="kanban-to-kanban", sourceFiles="index.ts,index.html,datasource.ts" %}

```typescript
import { Kanban } from '@syncfusion/ej2-kanban';
import { closest } from '@syncfusion/ej2-base';
import { kanbanData } from './datasource.ts';

const kanbanObjA: Kanban = new Kanban({
    dataSource: kanbanData,
    keyField: 'Status',
    columns: [
        { headerText: 'Backlog', keyField: 'Open' },
        { headerText: 'Done', keyField: 'Close' }
    ],
    externalDropId: ['#kanbanB'],
    cardSettings: {
        contentField: 'Summary',
        headerField: 'Id',
        selectionType: 'Multiple'
    },
    showEmptyColumn: true,
    dragStop: (args: DragEventArgs): void => {
        if (closest(args.event.target as Element, '#kanbanB')) {
            kanbanObjA.deleteCard(args.data);
            args.data.forEach((card: Record<string, any>, i: number) => {
                const index: number = kanbanObjB.kanbanData.findIndex((colData: Record<string, any>) =>
                    colData[kanbanObjB.cardSettings.headerField] === card[kanbanObjB.cardSettings.headerField]);
                if (index !== -1) {
                    card[kanbanObjB.cardSettings.headerField] = Math.max(...kanbanObjB.kanbanData.map(
                        (obj: Record<string, string>) => parseInt(obj[kanbanObjB.cardSettings.headerField], 10))) + ++i;
                }
            });
            kanbanObjB.addCard(args.data, args.dropIndex);
            args.cancel = true;
        }
    }
});
kanbanObjA.appendTo('#kanbanA');

const kanbanObjB: Kanban = new Kanban({
    dataSource: kanbanData,
    keyField: 'Status',
    columns: [
        { headerText: 'Backlog', keyField: 'Open' },
        { headerText: 'Done', keyField: 'Close' }
    ],
    cardSettings: {
        contentField: 'Summary',
        headerField: 'Id'
    },
    externalDropId: ['#kanbanA'],
    showEmptyColumn: true,
    dragStop: (args: DragEventArgs): void => {
        if (closest(args.event.target as Element, '#kanbanA')) {
            kanbanObjB.deleteCard(args.data);
            args.data.forEach((card: Record<string, any>, i: number) => {
                const index: number = kanbanObjA.kanbanData.findIndex((colData: Record<string, any>) =>
                    colData[kanbanObjA.cardSettings.headerField] === card[kanbanObjA.cardSettings.headerField]);
                if (index !== -1) {
                    card[kanbanObjA.cardSettings.headerField] = Math.max(...kanbanObjA.kanbanData.map(
                        (obj: Record<string, string>) => parseInt(obj[kanbanObjA.cardSettings.headerField], 10))) + ++i;
                }
            });
            kanbanObjA.addCard(args.data, args.dropIndex);
            args.cancel = true;
        }
    }
});
kanbanObjB.appendTo('#kanbanB');
```

{% endtab %}

### Treeview to Kanban

Drag the card from the Kanban board and drop it to the Treeview component and vice versa.

In the following sample, remove the data from the Kanban board using the `deleteCard` public method and add to the Treeview component using the `addNodes` public method at Kanban `dragStop` event when dragging the card and dropping it to the Treeview component. Remove the data from Treeview using the `removeNodes` public method and add to Kanban board using the `openDialog` public method when dragging the list from the Treeview component and dropping it to the kanban board.

{% tab template="kanban/kanban-to-treeview", es5Template="kanban-to-treeview", sourceFiles="index.ts,index.html,datasource.ts" %}

```typescript
import { Kanban, KanbanModel, DragEventArgs } from '@syncfusion/ej2-kanban';
import { kanbanData, treeViewData } from './datasource.ts';
import { closest } from '@syncfusion/ej2-base';
import { TreeView, DragAndDropEventArgs } from '@syncfusion/ej2-navigations';

const kanbanOptions: KanbanModel = {
    dataSource: kanbanData,
    keyField: 'Status',
    columns: [
        { headerText: 'Backlog', keyField: 'Open' },
        { headerText: 'Done', keyField: 'Close' }
    ],
    externalDropId: ['#TreeView'],
    cardSettings: {
        contentField: 'Summary',
        headerField: 'Id'
    },
    showEmptyColumn: true,
    dragStop: (args: DragEventArgs): void => {
        if (closest(args.event.target as Element, '#TreeView')) {
            kanbanObj.deleteCard(args.data);
            treeObj.addNodes(args.data);
            args.cancel = true;
        }
    }
};

const kanbanObj: Kanban = new Kanban(kanbanOptions);
kanbanObj.appendTo('#Kanban');

let treeObj: TreeView = new TreeView({
    fields: { dataSource: treeViewData, id: 'Id', text: 'Status' },
    allowDragAndDrop: true,
    nodeDragStop: onTreeDragStop,
    nodeTemplate: '#treeTemplate'
});
treeObj.appendTo('#TreeView');

function onTreeDragStop(args: DragAndDropEventArgs): void {
    if (closest(args.event.target as Element, '#Kanban')) {
        let treeData: { [key: string]: Object }[] =
        treeObj.fields.dataSource as { [key: string]: Object }[];
        const filteredData: { [key: string]: Object }[] =
        treeData.filter((item: any) => item.Id === parseInt(args.draggedNodeData.id as string, 10));
        treeObj.removeNodes([args.draggedNodeData.id] as string[]);
        kanbanObj.openDialog('Add', filteredData[0]);
        args.cancel = true;
    }
}
```

{% endtab %}

### Schedule to Kanban

Drag the card from the Kanban board and drop it to the Schedule component and vice versa.

In the following sample, remove the data from the Kanban board using the `deleteCard` public method and add to the schedule component using the `addNodes` public method at Kanban `dragStop` event when dragging the card and dropping it to the Treeview component. Remove the data from Treeview using the `removeNodes` public method and add to Kanban board using the `addCard` public method when dragging the list from the Treeview component and dropping it to the kanban board.

{% tab template="kanban/kanban-to-schedule", es5Template="kanban-to-schedule", sourceFiles="index.ts,index.html,datasource.ts" %}

```typescript
import { Kanban, KanbanModel, DragEventArgs } from '@syncfusion/ej2-kanban';
import { kanbanData, scheduleData } from './datasource.ts';
import { Schedule, TimelineViews, TimelineMonth, Resize, DragAndDrop } from '@syncfusion/ej2-schedule';
import { closest, removeClass } from '@syncfusion/ej2-base';

const kanbanOptions: KanbanModel = {
    dataSource: kanbanData,
    keyField: 'DepartmentName',
    columns: [
        { headerText: 'DENTAL', keyField: 'DENTAL' },
        { headerText: 'GENERAL', keyField: 'GENERAL' }
    ],
    externalDropId: ['#Schedule'],
    cardSettings: {
        contentField: 'Name',
        headerField: 'Id',
        selectionType: 'Multiple'
    },
    showEmptyColumn: true,
    dragStop: (args: DragEventArgs): void => {
        if (closest(args.event.target as Element, '#Schedule')) {
            kanbanObj.deleteCard(args.data);
            scheduleObj.openEditor(args.data[0],'Add', true);
            args.cancel = true;
        }
    }
};

const kanbanObj: Kanban = new Kanban(kanbanOptions);
kanbanObj.appendTo('#Kanban');

Schedule.Inject(TimelineViews, TimelineMonth, Resize, DragAndDrop);
let scheduleObj: Schedule = new Schedule({
    width: '350px',
    height: '650px',
    selectedDate: new Date(2018, 7, 1),
    currentView: 'TimelineDay',
    eventDragArea: "body",
    cssClass: 'schedule-drag-drop',
    workHours: {
        start: '08:00',
        end: '18:00'
    },
    views: [
        { option: 'TimelineDay' },
        { option: 'TimelineMonth' }
    ],
    group: {
        enableCompactView: false,
        resources: ['Departments', 'Consultants']
    },
    resources: [
        {
            field: 'DepartmentID', title: 'Department',
            name: 'Departments', allowMultiple: false,
            dataSource: [
                { Text: 'GENERAL', Id: 1, Color: '#bbdc00' },
                { Text: 'DENTAL', Id: 2, Color: '#9e5fff' }
            ],
            textField: 'Text', idField: 'Id', colorField: 'Color'
        },
        {
            field: 'ConsultantID', title: 'Consultant',
            name: 'Consultants', allowMultiple: false,
            dataSource: [
                { Text: 'Alice', Id: 1, GroupId: 1, Color: '#bbdc00', Designation: 'Cardiologist' },
                { Text: 'Nancy', Id: 2, GroupId: 2, Color: '#9e5fff', Designation: 'Orthodontist' },
                { Text: 'Robert', Id: 3, GroupId: 1, Color: '#bbdc00', Designation: 'Optometrist' },
                { Text: 'Robson', Id: 4, GroupId: 2, Color: '#9e5fff', Designation: 'Periodontist' },
                { Text: 'Laura', Id: 5, GroupId: 1, Color: '#bbdc00', Designation: 'Orthopedic' },
                { Text: 'Margaret', Id: 6, GroupId: 2, Color: '#9e5fff', Designation: 'Endodontist' }
            ],
            textField: 'Text', idField: 'Id', groupIDField: 'GroupId', colorField: 'Color'
        }
    ],
    eventSettings: {
        dataSource: scheduleData,
        fields: {
            subject: { title: 'Patient Name', name: 'Name' },
            startTime: { title: 'From', name: 'StartTime' },
            endTime: { title: 'To', name: 'EndTime' },
            description: { title: 'Reason', name: 'Description' }
        }
    },
    dragStop: scheduleDragStop
});
scheduleObj.appendTo('#Schedule');

function scheduleDragStop(args: ScheduleDragEventArgs): void {
    if (closest(args.event.target as Element, '#Kanban')) {
        scheduleObj.deleteEvent(args.data.Id);
        removeClass([scheduleObj.element.querySelector('.e-selected-cell')], 'e-selected-cell');
        kanbanObj.openDialog('Add', args.data);
        args.cancel = true;
    }
}
```

{% endtab %}