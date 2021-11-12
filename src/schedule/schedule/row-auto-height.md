---
title: "Auto row height in Scheduler"
component: "Scheduler"
description: "This section shows the way to auto-adjust the height of the work-cells of Scheduler based on the number of appointments present in those time ranges."
---

# Row Auto Height

By default, the height of the Scheduler rows in Timeline views are static and therefore, when the same time range holds multiple overlapping appointments, a `+n more` text indicator will be displayed. With this feature enabled, you can now view all the overlapping appointments present in those specific time range by auto-adjusting the row height based on the presence of the appointments count, instead of displaying the `+n more` text indicators.

To enable auto row height adjustments on Scheduler Timeline views and Month view, set `true` to the `rowAutoHeight` property whose default value is `false`.

> This auto row height adjustment is applicable only on all the Timeline views as well as on the calendar Month view.

Now, let's see how it works on those applicable views with examples.

## Calendar month view

By default, the rows of the calendar Month view can hold only the limited appointments count based on its row height, and the rest of the overlapping appointments are indicated with a `+n more` text indicator. The following example shows how the month view row auto-adjusts based on the number of appointments count, when this `rowAutoHeight` feature is enabled.

{% tab template="schedule/row-auto-height", es5Template="month", iframeHeight="588px" , sourceFiles="index.ts,index.html"  %}

```typescript
import { Schedule, Month } from '@syncfusion/ej2-schedule';
import { scheduleData } from './datasource.ts';

Schedule.Inject(Month);

let scheduleObj: Schedule = new Schedule({
    width: '100%',
    height: '450px',
    selectedDate: new Date(2018, 1, 15),
    currentView: 'Month',
    rowAutoHeight: true,
    views: ['Month'],
    eventSettings: { dataSource: scheduleData }
});
scheduleObj.appendTo('#Schedule');
```

{% endtab %}

## Timeline views

When the feature `rowAutoHeight` is enabled in Timeline views, the row height gets auto-adjusted based on the number of overlapping events occupied on the same time range, which is demonstrated in the following example.

{% tab template="schedule/row-auto-height", es5Template="timeline", iframeHeight="588px" , sourceFiles="index.ts,index.html"  %}

```typescript
import { Schedule, TimelineViews, TimelineMonth, Agenda, Resize, DragAndDrop } from '@syncfusion/ej2-schedule';
import {  scheduleData } from './datasource.ts';

Schedule.Inject(TimelineViews, TimelineMonth, Agenda, Resize, DragAndDrop);
let scheduleObj: Schedule = new Schedule({
    width: '100%',
    height: '450px',
    rowAutoHeight: true,
    selectedDate: new Date(2018, 1, 15),
    currentView: 'TimelineWeek',
    views: [
        { option: 'TimelineDay' },
        { option: 'TimelineWeek' },
        { option: 'TimelineWorkWeek' },
        { option: 'TimelineMonth' },
        { option: 'Agenda' }
    ],
    eventSettings: { dataSource: scheduleData }
});
scheduleObj.appendTo('#Schedule');
```

{% endtab %}

## Timeline views with multiple resources

The following example shows how the auto row adjustment feature works on timeline views with multiple resources.

{% tab template="schedule/row-auto-height", es5Template="timeline-resource", iframeHeight="588px", sourceFiles="index.ts,index.html,index.css"  %}

```typescript
import { Schedule, TimelineViews, Resize, DragAndDrop } from '@syncfusion/ej2-schedule';
import { CheckBox, ChangeEventArgs } from '@syncfusion/ej2-buttons';
import { roomData } from './datasource.ts';

Schedule.Inject(TimelineViews, Resize, DragAndDrop);
let scheduleObj: Schedule = new Schedule({
    width: '100%',
    height: '550px',
    selectedDate: new Date(2018, 7, 1),
    currentView: 'TimelineWeek',
    rowAutoHeight: true,
    views: ['TimelineDay', 'TimelineWeek'],
    group: {
        enableCompactView: false,
        resources: ['MeetingRoom']
    },
    resources: [{
        field: 'RoomId', title: 'Room Type',
        name: 'MeetingRoom', allowMultiple: true,
        dataSource: [
            { text: 'Room A', id: 1, color: '#98AFC7' },
            { text: 'Room B', id: 2, color: '#99c68e' },
            { text: 'Room C', id: 3, color: '#C2B280' },
            { text: 'Room D', id: 4, color: '#3090C7' },
            { text: 'Room E', id: 5, color: '#95b9' },
            { text: 'Room F', id: 6, color: '#95b9c7' },
            { text: 'Room G', id: 7, color: '#deb887' },
            { text: 'Room H', id: 8, color: '#3090C7' },
            { text: 'Room I', id: 9, color: '#98AFC7' },
            { text: 'Room J', id: 10, color: '#778899' }
        ],
        textField: 'text', idField: 'id', colorField: 'color'
    }],
    eventSettings: {
        dataSource: roomData,
        fields: {
            id: 'Id',
            subject: { title: 'Summary', name: 'Subject' },
            location: { title: 'Location', name: 'Location' },
            description: { title: 'Comments', name: 'Description' },
            startTime: { title: 'From', name: 'StartTime' },
            endTime: { title: 'To', name: 'EndTime' }
        }
    }
});
scheduleObj.appendTo('#Schedule');
```

{% endtab %}

## Appointments occupying entire cell

By default, with the feature `rowAutoHeight`, there will be a space in the bottom of the cell when appointment is rendered. To avoid this space, we can set true to the property `ignoreWhitespace` with in `eventSettings` whereas its default property value is false. In the following code example, the whitespace below the appointments has been ignored.

{% tab template="schedule/ignore-whitespace", es5Template="es5-ignore-whitespace", iframeHeight="588px", sourceFiles="index.ts,index.html,index.css"  %}

```typescript
import { Schedule, TimelineViews, TimelineMonth } from '@syncfusion/ej2-schedule';
import { resourceData } from './datasource.ts';

Schedule.Inject(TimelineViews, TimelineMonth, Agenda );
let scheduleObj: Schedule = new Schedule({
    width: '100%',
    height: '550px',
    currentView: 'TimelineWeek',
    rowAutoHeight: true,
    views: ['TimelineWeek', 'TimelineMonth'],
    selectedDate: new Date(2021, 7, 4),
    group: {
        resources: ['Rooms', 'Owners']
    },
    resources: [{
        field: 'RoomId', title: 'Room',
        name: 'Rooms', allowMultiple: false,
        dataSource: [
            { RoomText: 'ROOM 1', Id: 1, RoomColor: '#cb6bb2' },
            { RoomText: 'ROOM 2', Id: 2, RoomColor: '#56ca85' }
            ],
            textField: 'RoomText', idField: 'Id', colorField: 'RoomColor'
        }, {
        field: 'OwnerId', title: 'Owner',
        name: 'Owners', allowMultiple: true,
        dataSource: [
            { OwnerText: 'Nancy', Id: 1, OwnerGroupId: 1, OwnerColor: '#ffaa00' },
            { OwnerText: 'Steven', Id: 2, OwnerGroupId: 2, OwnerColor: '#f8a398' },
            { OwnerText: 'Michael', Id: 3, OwnerGroupId: 1, OwnerColor: '#7499e1' }
        ],
        textField: 'OwnerText', idField: 'Id', groupIDField: 'OwnerGroupId', colorField: 'OwnerColor'
    }],
    eventSettings: { dataSource: resourceData, ignoreWhitespace: true }
});
scheduleObj.appendTo('#Schedule');
```

{% endtab %}

**Note**: The property `ignoreWhitespace` will be applicable only when `rowAutoHeight` feature is enabled in the Scheduler.

> You can refer to our [JavaScript Scheduler](https://www.syncfusion.com/javascript-ui-controls/js-scheduler) feature tour page for its groundbreaking feature representations. You can also explore our [JavaScript Scheduler example](https://ej2.syncfusion.com/demos/#/material/schedule/overview.html) to knows how to present and manipulate data.
