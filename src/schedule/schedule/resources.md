---
title: "Multiple Resources and Grouping | Scheduler"
component: "Scheduler"
description: "This article demonstrates how to assign a single or multiple resources to events and also shows how to group them in both hierarchical and vertical mode."
---

# Multiple resources and grouping

Resources and grouping support allows the Scheduler to be shared by multiple resources. Also, the appointments of each resources are displayed under relevant resources. Each resource in the Scheduler is arranged in a column/row wise order, with individual spacing to display all its respective appointments on a single page. It also supports the multiple levels of grouping of resources, thus enabling the categorization of resources in a hierarchical structure and shows it either in expandable groups (Timeline views) or else vertical hierarchy one after the other (Calendar views).

It is also possible to assign one or more resources to the same appointment, by allowing multiple selection of resource options available in the event editor window.

The HTML5 JavaScript Scheduler groups the resources based on different criteria. It includes grouping appointments based on resources, grouping resources based on dates, and timeline scheduling. Also, the data for resources bind with Scheduler either as a local JSON collection or URL, retrieving data from remote data services.

## Resource fields

The default options available within the `resources` collection are as follows,

| Field name | Type | Description |
|-------|---------| --------------- |
| `field` | String | A value that binds to the resource field of event object. |
| `title` | String | It holds the title of the resource field to be displayed on the event editor window. |
| `name` | String | A unique resource name used for differentiating various resource objects while grouping. |
| `allowMultiple` | Boolean | When set to `true`, allows multiple selection of resource names, thus creating multiple instances of same appointment for the selected resources. |
| `dataSource` | Object | Assigns the resource `dataSource`, where data can be passed either as an array of JavaScript objects, or else can create an instance of [`DataManager`](http://ej2.syncfusion.com/documentation/data/api-dataManager.html) in case of processing remote data and can be assigned to the `dataSource` property. With the remote data assigned to `dataSource`, check the available [adaptors](http://ej2.syncfusion.com/documentation/data/adaptors.html) to customize the data processing. |
| `query` | Query | Defines the external [`query`](http://ej2.syncfusion.com/documentation/data/api-query.html) that will be executed along with the data processing. |
| `idField` | String | Binds the resource ID field name from the resources `dataSource`. |
| `expandedField` | Boolean | Binds the `expandedField` name from the resources `dataSource`. It usually holds boolean value which decide whether the resource of timeline views is in collapse or expand state on initial load. |
| `textField` | String | Binds the text field name from the resources `dataSource`. It usually holds the resource names. |
| `groupIDField` | String | Binds the group ID field name from the resource `dataSource`. It usually holds the value of resource IDs of parent level resources. |
| `colorField` | String | Binds the color field name from the resource `dataSource`. The color value mapped in this field will be applied to the events of resources. |
| `startHourField` | String | Binds the start hour field name from the resource `dataSource`. It allows to provide different work start hour for the resources. |
| `endHourField` | String | Binds the end hour field name from the resource `dataSource`. It allows to provide different work end hour for the resources. |
| `workDaysField` | String | Binds the work days field name from the resources `dataSource`. It allows to provide different working days collection for the resources. |
| `cssClassField` | String | Binds the custom CSS class field name from the resources `dataSource`. It maps the CSS class written for the specific resources and applies it to the events of those resources. |

## Resource data binding

The data for resources can bind with Scheduler either as a local JSON collection or a service URL, retrieving resource data from remote data services.

### Using local JSON data

The following code example depicts how to bind the local JSON data to the `dataSource` of `resources` collection.

```typescript
import { Schedule, Week, Month, Agenda, TimelineViews, TimelineMonth } from '@syncfusion/ej2-schedule';
import { resourceData } from './datasource.ts';

Schedule.Inject( Week, Month, TimelineViews, TimelineMonth, Agenda);
let scheduleObj: Schedule = new Schedule({
    width: '100%',
    height: '550px',
    currentView: 'Week',
    views: ['Week', 'Month', 'TimelineWeek','TimelineMonth', 'Agenda'],
    selectedDate: new Date(2018, 3, 1),
    resources: [{
        field: 'OwnerId', title: 'Owner',
        name: 'Owners', allowMultiple: true,
        dataSource: [
            { OwnerText: 'Nancy', Id: 1, OwnerColor: '#ffaa00' },
            { OwnerText: 'Steven', Id: 2, OwnerColor: '#f8a398' },
            { OwnerText: 'Michael', Id: 3, OwnerColor: '#7499e1' }
        ],
        textField: 'OwnerText', idField: 'Id', colorField: 'OwnerColor'
    }],
    eventSettings: { dataSource: resourceData }
});
scheduleObj.appendTo('#Schedule');
```

### Using remote service URL

The following code example depicts how to bind the remote data for resources `dataSource`.

```typescript
import { DataManager, UrlAdaptor } from '@syncfusion/ej2-data';
import { Schedule, Week, Month, Agenda, TimelineViews, TimelineMonth } from '@syncfusion/ej2-schedule';
import { resourceData } from './datasource.ts';

let resource: DataManager = new DataManager({
    url: 'Home/GetResourceData',
    adaptor: new UrlAdaptor,
    crossDomain: true
});

Schedule.Inject( Week, Month, TimelineViews, TimelineMonth, Agenda);
let scheduleObj: Schedule = new Schedule({
    width: '100%',
    height: '550px',
    currentView: 'Week',
    views: ['Week', 'Month', 'TimelineWeek','TimelineMonth', 'Agenda'],
    selectedDate: new Date(2018, 3, 1),
    resources: [{
        field: 'OwnerId', title: 'Owner',
        name: 'Owners', allowMultiple: true,
        dataSource: resource,
        textField: 'OwnerText', idField: 'Id', colorField: 'OwnerColor'
    }],
    eventSettings: { dataSource: resourceData }
});
scheduleObj.appendTo('#Schedule');
```

## Scheduler with multiple resources

It is possible to display the Scheduler in default mode without visually showcasing all the resources in it, but allowing to assign the required resources to the appointments through the event editor resource options.

The appointments belonging to the different resources will be displayed altogether on the default Scheduler, which will be differentiated based on the resource color assigned in the **resources** (depicting to which resource that particular appointment belongs) collection.

**Example:** To display default Scheduler with multiple resource options in the event editor, ignore the group option and simply define the `resources` property with all its internal options.

{% tab template="schedule/multiple-resource", es5Template="multiple-resource-template", iframeHeight="588px", sourceFiles="index.ts,index.html"  %}

```typescript
import { Schedule, Week, Month, Agenda, TimelineViews, TimelineMonth } from '@syncfusion/ej2-schedule';
import { resourceData } from './datasource.ts';

Schedule.Inject( Week, Month, TimelineViews, TimelineMonth, Agenda);
let scheduleObj: Schedule = new Schedule({
    width: '100%',
    height: '550px',
    currentView: 'Week',
    views: ['Week', 'Month', 'TimelineWeek','TimelineMonth', 'Agenda'],
    selectedDate: new Date(2018, 3, 1),
    resources: [{
        field: 'OwnerId', title: 'Owner',
        name: 'Owners', allowMultiple: true,
        dataSource: [
            { OwnerText: 'Nancy', Id: 1, OwnerColor: '#ffaa00' },
            { OwnerText: 'Steven', Id: 2, OwnerColor: '#f8a398' },
            { OwnerText: 'Michael', Id: 3, OwnerColor: '#7499e1' }
        ],
        textField: 'OwnerText', idField: 'Id', colorField: 'OwnerColor'
    }],
    eventSettings: { dataSource: resourceData }
});
scheduleObj.appendTo('#Schedule');
```

{% endtab %}

> Setting `allowMultiple` to `true` in the above code example allows you to select multiple resources from the event editor and also creates multiple copies of the same appointment in the Scheduler for each resources while rendering.

## Resource grouping

Resource grouping support allows the Scheduler to group the resources in a hierarchical structure both as an expandable groups (Timeline views) and as vertical hierarchy displaying resources one after the other (Resources view).

Scheduler supports both single and multiple levels of resource grouping that can be customized both in timeline and vertical Scheduler views.

### Vertical resource view

The following code example displays how the multiple resources are grouped and its events are portrayed in the default calendar views.

{% tab template="schedule/resource-grouping", es5Template="horizontal-group-template", iframeHeight="588px", sourceFiles="index.ts,index.html"  %}

```typescript
import { Schedule, Week, Month, Agenda } from '@syncfusion/ej2-schedule';
import { resourceConferenceData } from './datasource.ts';

Schedule.Inject( Week, Month, Agenda );
let scheduleObj: Schedule = new Schedule({
    width: '100%',
    height: '550px',
    currentView: 'Week',
    views: ['Week', 'Month', 'Agenda'],
    selectedDate: new Date(2018, 3, 4),
    group: {
        byGroupID: false,
        resources: ['Projects', 'Categories']
    },
    resources: [
        {
            field: 'ProjectId', title: 'Choose Project', name: 'Projects',
            dataSource: [
                { text: 'PROJECT 1', id: 1, color: '#cb6bb2' },
                { text: 'PROJECT 2', id: 2, color: '#56ca85' },
                { text: 'PROJECT 3', id: 3, color: '#df5286' }
            ],
            textField: 'text', idField: 'id', colorField: 'color'
        }, {
            field: 'TaskId', title: 'Category',
            name: 'Categories', allowMultiple: true,
            dataSource: [
                { text: 'Development', id: 1, color: '#df5286' },
                { text: 'Testing', id: 2, color: '#7fa900' }
            ],
            textField: 'text', idField: 'id', colorField: 'color'
        }
    ],
    eventSettings: { dataSource: resourceConferenceData }
    });
    scheduleObj.appendTo('#Schedule');
```

{% endtab %}

### Timeline resource view

The following code example depicts how to group the multiple resources on Timeline Scheduler views and its relevant events are displayed accordingly under those resources.

{% tab template="schedule/resource-grouping", es5Template="timeline-group-template", iframeHeight="588px", sourceFiles="index.ts,index.html"  %}

```typescript
import { Schedule, TimelineViews, TimelineMonth, Agenda } from '@syncfusion/ej2-schedule';
import { resourceData } from './datasource.ts';

Schedule.Inject(TimelineViews, TimelineMonth, Agenda );
let scheduleObj: Schedule = new Schedule({
    width: '100%',
    height: '550px',
    currentView: 'TimelineWeek',
    views: ['TimelineWeek', 'TimelineMonth', 'Agenda'],
    selectedDate: new Date(2018, 3, 4),
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
    eventSettings: { dataSource: resourceData }
});
scheduleObj.appendTo('#Schedule');
```

{% endtab %}

### Grouping single-level resources

This kind of grouping allows the Scheduler to display all the resources at a single level simultaneously. The appointments mapped under resources will be displayed with the colors as per the `colorField` defined on the resources collection.

**Example:** To display the Scheduler with single level resource grouping,

{% tab template="schedule/single-level-resource", es5Template="single-level-template", iframeHeight="588px", sourceFiles="index.ts,index.html"  %}

```typescript
import { Schedule, Week, Month, Agenda, TimelineViews, TimelineMonth } from '@syncfusion/ej2-schedule';
import { resourceData } from './datasource.ts';

Schedule.Inject(Month, Week, Agenda, TimelineViews, TimelineMonth);
let scheduleObj: Schedule = new Schedule({
    width: '100%',
    height: '550px',
    views: ['Week', 'Month', 'TimelineWeek', 'TimelineMonth', 'Agenda'],
    selectedDate: new Date(2018, 3, 1),
    group: {
            resources: ['Owners']
        },
    resources: [{
        field: 'OwnerId', title: 'Owner',
        name: 'Owners', allowMultiple: true,
        dataSource: [
            { OwnerText: 'Nancy', Id: 1, OwnerColor: '#ffaa00' },
            { OwnerText: 'Steven', Id: 2, OwnerColor: '#f8a398' },
            { OwnerText: 'Michael', Id: 3, OwnerColor: '#7499e1' }
        ],
        textField: 'OwnerText', idField: 'Id', colorField: 'OwnerColor'
    }],
    eventSettings: { dataSource: resourceData }
});
scheduleObj.appendTo('#Schedule');
```

{% endtab %}

> The `name` field defined in the **resources** collection namely `Owners` will be mapped within the `group` property, in order to enable the grouping option with those resource levels on the Scheduler.

### Grouping multi-level resources

It is possible to group the resources of Scheduler in multiple levels, by mapping the child resources to each parent resource. In the following example, there are 2 levels of resources, on which the second level resources are defined with `groupID` mapping to the first level resource's ID so as to establish the parent-child relationship between them.

**Example:** To display the Scheduler with multiple level resource grouping options,

{% tab template="schedule/multi-level-resource", es5Template="multi-level-template", iframeHeight="588px", sourceFiles="index.ts,index.html"  %}

```typescript
import { Schedule, Week, Month, Agenda, TimelineViews, TimelineMonth } from '@syncfusion/ej2-schedule';
import { resourceData } from './datasource.ts';

Schedule.Inject(Month, Week, Agenda, TimelineViews, TimelineMonth);
let scheduleObj: Schedule = new Schedule({
    width: '100%',
    height: '550px',
    views: ['Week', 'Month', 'TimelineWeek', 'TimelineMonth', 'Agenda'],
    selectedDate: new Date(2018, 3, 1),
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
    eventSettings: { dataSource: resourceData }
});
scheduleObj.appendTo('#Schedule');
```

{% endtab %}

### One-to-One grouping

In multi-level grouping, Scheduler usually groups the resources on the child level based on the `GroupID` that maps with the `Id` field of parent level resources (as `byGroupID` set to true by default). There are also option which allows you to group all the child resource(s) against each of its parent resource(s). To enable this kind of grouping, set `false` to the `byGroupID` option within the `group` property. In the following code example, there are two levels of resources, on which all the 3 resources at the child level is mapped one to one with each resource on the first level.

{% tab template="schedule/multi-level-resource", es5Template="one-to-one-level", iframeHeight="588px", sourceFiles="index.ts,index.html"  %}

```typescript
import { Schedule, Week, Month, TimelineViews, TimelineMonth, Agenda } from '@syncfusion/ej2-schedule';
import { resourceData } from './datasource.ts';

Schedule.Inject(Week, Month, TimelineViews, TimelineMonth, Agenda );
let scheduleObj: Schedule = new Schedule({
    width: '100%',
    height: '550px',
    currentView: 'Week',
    views: ['Week' , 'Month','TimelineWeek', 'TimelineMonth', 'Agenda'],
    selectedDate: new Date(2018, 3, 1),
    group: {
        byGroupID: false,
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
        },{
        field: 'OwnerId', title: 'Owner',
        name: 'Owners', allowMultiple: true,
        dataSource: [
            { OwnerText: 'Nancy', Id: 1, OwnerColor: '#ffaa00' },
            { OwnerText: 'Steven', Id: 2, OwnerColor: '#f8a398' },
            { OwnerText: 'Michael', Id: 3, OwnerColor: '#7499e1' }
        ],
        textField: 'OwnerText', idField: 'Id', colorField: 'OwnerColor'
    }],
    eventSettings: { dataSource: resourceData }
});
scheduleObj.appendTo('#Schedule');
```

{% endtab %}

### Grouping resources by date

It groups the number of resources under each date and is applicable only on the calendar views such as Day, Week, Work Week, Month, Agenda and Month-Agenda. To enable such grouping, set `byDate` option to `true` within the `group` property.

**Example:** To display the Scheduler with resources grouped by date,

{% tab template="schedule/group-by-date", es5Template="date-template", iframeHeight="588px", sourceFiles="index.ts,index.html"  %}

```typescript
import { Schedule, Week, Month, Agenda } from '@syncfusion/ej2-schedule';
import { resourceData } from './datasource.ts';

Schedule.Inject(Month, Week, Agenda);
let scheduleObj: Schedule = new Schedule({
    width: '100%',
    height: '550px',
    views: ['Week', 'Month', 'Agenda'],
    selectedDate: new Date(2018, 3, 1),
    group: {
        byDate: true,
        resources: ['Owners']
    },
    resources: [{
        field: 'OwnerId', title: 'Owner',
        name: 'Owners', allowMultiple: true,
        dataSource: [
            { text: 'Alice', id: 1, color: '#1aaa55' },
            { text: 'Smith', id: 2, color: '#7fa900' }
        ],
        textField: 'text', idField: 'id', colorField: 'color'
    }],
    eventSettings: { dataSource: resourceData }
});
scheduleObj.appendTo('#Schedule');
```

{% endtab %}

> This kind of grouping by date is not applicable on any of the timeline views.

### Grouping with empty resource datasource

When using grouping, it is mandatory to provide at least one resource data in dataSource collection this is the default behavior of our scheduler. If the resource does not have a dataSource, scheduler rendered like below image.

![Grouping with empty resource](./images/empty-datasource.png)

To handle this case you can make the default schedule by emptying the group property.

{% tab template="schedule/resource-grouping", es5Template="group-cells", iframeHeight="588px", sourceFiles="index.ts,index.html"  %}

```typescript
import { Schedule, Week, Month, ResourceDetails, TreeViewArgs, Agenda, Resize, DragAndDrop } from "@syncfusion/ej2-schedule";

Schedule.Inject(Week, Month, Agenda, Resize, DragAndDrop);import { resourceData } from './datasource.ts';
let scheduleObj: Schedule = new Schedule({
width: "100%",
  height: "650px",
  selectedDate: new Date(2018, 3, 1),
  views: ["Week", "Month", "Agenda"],
  group: {
    resources: ["Airlines"]
  },
  resources: [
    {
      field: "AirlineId",
      title: "Airline Name",
      name: "Airlines",
      allowMultiple: true,
      dataSource: [],
      textField: "AirlineName",
      idField: "AirlineId",
      colorField: "AirlineColor"
    }
  ],
  eventSettings: {
    dataSource: [],
    fields: {
      subject: { title: "Travel Summary", name: "Subject" },
      location: { title: "Source", name: "Location" },
      description: { title: "Comments", name: "Description" },
      startTime: { title: "Departure Time", name: "StartTime" },
      endTime: { title: "Arrival Time", name: "EndTime" }
    }
  },
  dataBinding(args) {
    //check the resource count
    if ((this.resourceCollection[0].dataSource as any).length === 0 && this.group.resources.length > 0) {
      // Render default scheduler to handle above case.
      this.group.resources = [];
    }
  }
});
scheduleObj.appendTo('#Schedule');
```

{% endtab %}

## Customizing parent resource cells

In timeline view work cells of parent resource can be customized by checking the `elementType` as `resourceGroupCells` in the event `renderCell`. In the following code example, background color of the work hours has been changed.

{% tab template="schedule/resource-grouping", es5Template="group-cells", iframeHeight="588px", sourceFiles="index.ts,index.html"  %}

```typescript
import { Schedule, TimelineViews, TimelineMonth, RenderCellEventArgs } from '@syncfusion/ej2-schedule';
import { resourceData } from './datasource.ts';

Schedule.Inject(TimelineViews, TimelineMonth );
let scheduleObj: Schedule = new Schedule({
    width: '100%',
    height: '550px',
    currentView: 'TimelineWeek',
    views: ['TimelineDay', 'TimelineWeek', 'TimelineMonth'],
    selectedDate: new Date(2018, 3, 4),
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
    eventSettings: { dataSource: resourceData },
    renderCell: (args: RenderCellEventArgs) {
      if (args.elementType == 'resourceGroupCells' &&
       args.element.className.indexOf('e-work-hours') > 0) {
          args.element.style.background = "#FAFAE3";
      }
    }
});
scheduleObj.appendTo('#Schedule');
```

{% endtab %}

## Working with shared events

Multiple resources can share the same events, thus allowing the CRUD action made on it to reflect on all other shared instances simultaneously. To enable such option, set `allowGroupEdit` option to `true` within the `group` property. With this property enabled, a single appointment
object will be maintained within the appointment collection, even if it is shared by more than one resource – whereas the resource fields of such appointment object will be in array which hold the IDs of the multiple resources.

> Any actions such as create, edit or delete held on any one of the shared event instances, will be reflected on all other related instances visible on the UI.

**Example:** To edit all the resource events simultaneously,

{% tab template="schedule/resource-grouping", es5Template="group-edit", iframeHeight="588px", sourceFiles="index.ts,index.html"  %}

```typescript
import { Schedule, Week, Month, Agenda, TimelineViews, TimelineMonth, Resize } from '@syncfusion/ej2-schedule';

Schedule.Inject(Month, Week, Agenda, TimelineViews, TimelineMonth, Resize);
let resourceConferenceData: Object[] = [
    {
        Id: 1,
        Subject: 'Burning Man',
        StartTime: new Date(2018, 5, 1, 15, 0),
        EndTime: new Date(2018, 5, 1, 17, 0),
        ConferenceId: [1, 2, 3]
    }, {
        Id: 2,
        Subject: 'Data-Driven Economy',
        StartTime: new Date(2018, 5, 2, 12, 0),
        EndTime: new Date(2018, 5, 2, 14, 0),
        ConferenceId: [1, 2]
    }, {
        Id: 3,
        Subject: 'Techweek',
        StartTime: new Date(2018, 5, 2, 15, 0),
        EndTime: new Date(2018, 5, 2, 17, 0),
        ConferenceId: [2, 3]
    }, {
        Id: 4,
        Subject: 'Content Marketing World',
        StartTime: new Date(2018, 5, 2, 18, 0),
        EndTime: new Date(2018, 5, 2, 20, 0),
        ConferenceId: [1, 3]
    }, {
        Id: 5,
        Subject: 'B2B Marketing Forum',
        StartTime: new Date(2018, 5, 3, 10, 0),
        EndTime: new Date(2018, 5, 3, 12, 0),
        ConferenceId: [1, 2, 3]
    }];
let scheduleObj: Schedule = new Schedule({
    width: '100%',
    height: '550px',
    selectedDate: new Date(2018, 5, 5),
    views: ['Week', 'Month', 'TimelineWeek', 'TimelineMonth', 'Agenda'],
    currentView: 'Week',
    group: {
        allowGroupEdit: true,
        resources: ['Conferences']
    },
    resources: [{
        field: 'ConferenceId', title: 'Conference',
        name: 'Conferences', allowMultiple: true,
        dataSource: [
            { Text: 'Margaret', Id: 1, Color: '#1aaa55' },
            { Text: 'Robert', Id: 2, Color: '#357cd2' },
            { Text: 'Laura', Id: 3, Color: '#7fa900' }
        ],
        textField: 'Text', idField: 'Id', colorField: 'Color'
    }],
    eventSettings: { dataSource: resourceConferenceData }
});
scheduleObj.appendTo('#Schedule');
```

{% endtab %}

## Simple resource header customization

It is possible to customize the resource header cells using built-in template option and change the look and appearance of it in both the vertical and timeline view modes. All the resource related fields and other information can be accessed within the resource header template option.

**Example:** To customize the resource header and display it along with designation field, refer the below code example.

{% tab template="schedule/resource-header", es5Template="resource-template", iframeHeight="588px", sourceFiles="index.ts,index.html"  %}

```typescript
import {
    Schedule, Week, Month, TimelineViews, TimelineMonth, Agenda
} from '@syncfusion/ej2-schedule';
import { doctorData } from './datasource.ts';
Schedule.Inject(Week, Month, TimelineViews, TimelineMonth, Agenda);

let scheduleObj: Schedule = new Schedule({
    width: '100%',
    height: '550px',
    selectedDate: new Date(2018, 3, 1),
    resourceHeaderTemplate: '#resourceTemplate',
    views: ['Week', 'Month', 'TimelineWeek', 'TimelineMonth', 'Agenda'],
    group: {
        resources: ['Doctors']
    },
    resources: [{
        field: 'DoctorId', title: 'Doctor Name', name: 'Doctors',
            dataSource: [
                { text: 'Will Smith', id: 1, color: '#ea7a57', designation: 'Cardioligst' },
                { text: 'Alice', id: 2, color: '#7fa900', designation: 'Neurologist' },
                { text: 'Robson', id: 3, color: '#7fa900', designation: 'Orthopedic Surgeon'  }
            ],
        textField: 'text', idField: 'id', colorField: 'color', designationField: 'designation'
    }],
    eventSettings: { dataSource: doctorData }
});
scheduleObj.appendTo('#Schedule');
```

{% endtab %}

> To customize the resource header in compact mode properly make use of the class `e-device` as in the code example.

![Resource header template in compact mode](./images/header-template.png)

## Customizing resource header with multiple columns

It is possible to customize the resource headers to display with multiple columns such as Room, Type and Capacity. The following code example depicts the way to achieve it and is applicable only on timeline views.

{% tab template="schedule/resource-header-column-customization", es5Template="header-column-template", iframeHeight="588px", sourceFiles="index.ts,index.html"  %}

```typescript

import {
    Schedule, RenderCellEventArgs, TimelineViews, TimelineMonth
} from '@syncfusion/ej2-schedule';
import {  roomData } from './datasource.ts';
Schedule.Inject(TimelineViews, TimelineMonth);

let scheduleObj: Schedule = new Schedule({
    width: '100%',
    height: '550px',
    selectedDate: new Date(2018, 7, 1),
    resourceHeaderTemplate: '#resourceTemplate',
    views: ['TimelineWeek', 'TimelineMonth'],
    group: {
        resources: ['MeetingRoom']
    },
    resources: [{
        field: 'RoomId', title: 'Room Type',
        name: 'MeetingRoom', allowMultiple: true,
        dataSource: [
            { text: 'Jammy', id: 1, color: '#ea7a57', capacity: 20, type: 'Conference' },
            { text: 'Tweety', id: 2, color: '#7fa900', capacity: 7, type: 'Cabin' },
            { text: 'Nestle', id: 3, color: '#5978ee', capacity: 5, type: 'Cabin' },
            { text: 'Phoenix', id: 4, color: '#fec200', capacity: 15, type: 'Conference' },
            { text: 'Mission', id: 5, color: '#df5286', capacity: 25, type: 'Conference' },
            { text: 'Hangout', id: 6, color: '#00bdae', capacity: 10, type: 'Cabin' },
            { text: 'Rick Roll', id: 7, color: '#865fcf', capacity: 20, type: 'Conference' },
            { text: 'Rainbow', id: 8, color: '#1aaa55', capacity: 8, type: 'Cabin' },
            { text: 'Swarm', id: 9, color: '#df5286', capacity: 30, type: 'Conference' },
            { text: 'Photogenic', id: 10, color: '#710193', capacity: 25, type: 'Conference' }
        ],
        textField: 'text', idField: 'id', colorField: 'color'
    }],
    renderCell: (args: RenderCellEventArgs) => {
        if (args.elementType === 'emptyCells' && args.element.classList.contains('e-resource-left-td')) {
            let target: HTMLElement = args.element.querySelector('.e-resource-text') as HTMLElement;
            target.innerHTML = '<div class="name">Rooms</div><div class="type">Type</div><div class="capacity">Capacity</div>';
        }
    },
    eventSettings: { dataSource: roomData }
});
scheduleObj.appendTo('#Schedule');
```

{% endtab %}

## Hide child resources in timeline views

It is possible to expand and collapse the resources which have child resource in timeline views dynamically. By default, resources are in expanded state with their child resource. We can collapse and hide the child resources in UI by setting `expandedField` option as `false` whereas its default value is `true`.

{% tab template="schedule/resource-grouping", es5Template="timeline-group-template", iframeHeight="588px", sourceFiles="index.ts,index.html"  %}

```typescript
import { Schedule, TimelineViews, TimelineMonth, Agenda } from '@syncfusion/ej2-schedule';
import { resourceData } from './datasource.ts';

Schedule.Inject(TimelineViews, TimelineMonth, Agenda);
let scheduleObj: Schedule = new Schedule({
  width: "100%",
  height: "550px",
  currentView: "TimelineWeek",
  views: ["TimelineWeek", "TimelineMonth", "Agenda"],
  selectedDate: new Date(2018, 3, 4),
  group: {
    resources: ["Rooms", "Owners"]
  },
  resources: [
    {
      field: "RoomId", title: "Room",
      name: "Rooms", allowMultiple: false,
      dataSource: [
        { RoomText: "ROOM 1", Id: 1, RoomColor: "#cb6bb2", IsExpand: false },
        { RoomText: "ROOM 2", Id: 2, RoomColor: "#56ca85" }
      ],
      textField: "RoomText", idField: "Id", colorField: "RoomColor", expandedField: "IsExpand"
    },
    {
      field: "OwnerId", title: "Owner",
      name: "Owners", allowMultiple: true,
      dataSource: [
        { OwnerText: "Nancy", Id: 1, OwnerGroupId: 1, OwnerColor: "#ffaa00" },
        { OwnerText: "Steven", Id: 2, OwnerGroupId: 2, OwnerColor: "#f8a398" },
        { OwnerText: "Michael", Id: 3, OwnerGroupId: 1, OwnerColor: "#7499e1" },
        { OwnerText: "Alice", Id: 4, OwnerGroupId: 2, OwnerColor: "#7fa900" }
      ],
      textField: "OwnerText", idField: "Id", groupIDField: "OwnerGroupId", colorField: "OwnerColor"
    }
  ],
  eventSettings: { dataSource: resourceData }
});
scheduleObj.appendTo("#Schedule");
```

{% endtab %}

## Displaying tooltip for resource headers

It is possible to display tooltips over the resource headers showing the resource information. By default, there won't be any tooltips displayed on the resource headers, and to enable it, you need to assign the customized template design to the `headerTooltipTemplate` option within the `group` property.

{% tab template="schedule/header-tooltip", es5Template="tooltip-enable", iframeHeight="588px", sourceFiles="index.ts,index.html"  %}

```typescript
import {
    Schedule, Week, Month, TimelineViews, TimelineMonth
} from '@syncfusion/ej2-schedule';
import { resourceData } from './datasource.ts';
Schedule.Inject(Week, Month, TimelineViews, TimelineMonth);

let scheduleObj: Schedule = new Schedule({
    width: '100%',
    height: '550px',
    selectedDate: new Date(2018, 3, 1),
    views: ['Week', 'Month', 'TimelineWeek', 'TimelineMonth'],
    group: {
        resources: ['Rooms', 'Owners'],
        headerTooltipTemplate: '#tooltipTemplate'
    },
    resources: [
        {
            field: 'OwnerId', title: 'Owner',
            name: 'Owners', allowMultiple: true,
            dataSource: [
                { OwnerText: 'Nancy', Id: 1, OwnerGroupId: 1, OwnerColor: '#ffaa00' },
                { OwnerText: 'Steven', Id: 2, OwnerGroupId: 2, OwnerColor: '#f8a398' },
                { OwnerText: 'Michael', Id: 3, OwnerGroupId: 1, OwnerColor: '#7499e1' }
            ],
            textField: 'OwnerText', idField: 'Id', groupIDField: 'OwnerGroupId', colorField: 'OwnerColor'
        }
    ],
    eventSettings: { dataSource: resourceData }
});
scheduleObj.appendTo('#Schedule');
```

{% endtab %}

## Choosing among resource colors for appointments

By default, the colors defined on the top level resources collection will be applied for the events. In case, if you want to apply specific resource color to events irrespective of its top-level parent resource color, it can be achieved by defining `resourceColorField` option within the `eventSettings` property.

In the following example, the colors mentioned in the second level will get applied over the events.

{% tab template="schedule/resource-color", es5Template="resource-color", iframeHeight="620px", sourceFiles="index.ts,index.html"  %}

```typescript
import { RadioButton, ChangeArgs } from '@syncfusion/ej2-buttons';
import { Schedule, Week, Month, Agenda, TimelineViews, TimelineMonth } from '@syncfusion/ej2-schedule';
import { resourceData } from './datasource.ts';

Schedule.Inject(Month, Week, Agenda, TimelineViews, TimelineMonth);
let scheduleObj: Schedule = new Schedule({
    width: '100%',
    height: '550px',
    views: ['Week', 'Month', 'TimelineWeek', 'TimelineMonth', 'Agenda'],
    selectedDate: new Date(2018, 3, 1),
    group: {
        resources: ['Rooms', 'Owners']
    },
    resources: [{
        field: 'RoomId', title: 'Room',
        name: 'Rooms', allowMultiple: false,
        dataSource: [
            { RoomText: 'ROOM 1', Id: 1, RoomGroupId: 1, RoomColor: '#cb6bb2' },
            { RoomText: 'ROOM 2', Id: 2, RoomGroupId: 2, RoomColor: '#56ca85' }
        ],
        textField: 'RoomText', idField: 'Id', groupIDField: 'RoomGroupId', colorField: 'RoomColor'
        },{
        field: 'OwnerId', title: 'Owner',
        name: 'Owners', allowMultiple: true,
        dataSource: [
            { OwnerText: 'Nancy', Id: 1, OwnerGroupId: 1, OwnerColor: '#ffaa00' },
            { OwnerText: 'Steven', Id: 2, OwnerGroupId: 2, OwnerColor: '#f8a398' },
            { OwnerText: 'Michael', Id: 3, OwnerGroupId: 1, OwnerColor: '#7499e1' }
        ],
        textField: 'OwnerText', idField: 'Id', groupIDField: 'OwnerGroupId', colorField: 'OwnerColor'
    }],
    eventSettings: { dataSource: resourceData, resourceColorField: 'Rooms' }
});
scheduleObj.appendTo('#Schedule');

new RadioButton({  value: 'Rooms', name: 'default', label: 'Rooms', checked: true,  change: onChange }, '#room');
new RadioButton({  value: 'Owners', name: 'default', label: 'Owners', checked: false, change: onChange }, '#owner');

function onChange(args: ChangeArgs): void {
    scheduleObj.eventSettings.resourceColorField = args.value;
}
```

{% endtab %}

> The value of the `resourceColorField` field should be mapped with the `name` value given within the `resources` property.

## Setting different style to each resource appointments

By default, the appearance of events is the same for all resource events. In case, if you want to apply the different styles to each resource event, you can do this by defining the `cssClassField` option within the `resource` property that maps the different cssClass fields from the resource dataSource as depicted in the following example.

{% tab template="schedule/resource-css-class-field-api", es5Template="resource-css-class-field-api", iframeHeight="620px", sourceFiles="index.ts,index.html"  %}

```typescript
import { Schedule, Week, Month, Agenda, TimelineViews, TimelineMonth } from '@syncfusion/ej2-schedule';
import { resourceData } from './datasource.ts';

Schedule.Inject(Month, Week, Agenda, TimelineViews, TimelineMonth);
let scheduleObj: Schedule = new Schedule({
    width: '100%',
    height: '550px',
    views: ['Week', 'Month', 'TimelineWeek', 'TimelineMonth', 'Agenda'],
    selectedDate: new Date(2018, 3, 1),
    group: {
        resources: ['Owners']
    },
    resources: [
      {
        field: 'OwnerId', title: 'Owner',
        name: 'Owners', allowMultiple: true,
        dataSource: [
            { OwnerText: 'Nancy', Id: 1, OwnerGroupId: 1, OwnerColor: '#ffaa00', ResourceCssClass: "NancyResource" },
            { OwnerText: 'Steven', Id: 2, OwnerGroupId: 2, OwnerColor: '#f8a398', ResourceCssClass: "StevenResource" },
            { OwnerText: 'Michael', Id: 3, OwnerGroupId: 1, OwnerColor: '#7499e1', ResourceCssClass: "MichaelResource" }
        ],
        textField: 'OwnerText', idField: 'Id', groupIDField: 'OwnerGroupId', colorField: 'OwnerColor', cssClassField: "ResourceCssClass"
    }],
    eventSettings: { dataSource: resourceData, resourceColorField: 'Rooms' }
});
scheduleObj.appendTo('#Schedule');

```

{% endtab %}

## Dynamically add and remove resources

It is possible to add or remove the resources dynamically to and from the Scheduler respectively. In the following example, when the checkboxes are checked and unchecked, the respective resources gets added up or removed from the Scheduler layout. To add new resource dynamically, `addResource` method is used which accepts the arguments such as resource object, resource name (within which level, the resource object to be added) and index (position where the resource needs to be added).

To remove the resources dynamically, `removeResource` method is used which accepts the index (position from where the resource to be removed) and resource name (within which level, the resource object presents) as parameters.

{% tab template="schedule/dynamic-resource", es5Template="dynamic-resource-template", iframeHeight="620px", sourceFiles="index.ts,index.html"  %}

```typescript

import { CheckBox, ChangeEventArgs } from '@syncfusion/ej2-buttons';
import { Schedule, Month, TimelineMonth } from '@syncfusion/ej2-schedule';
import { holidayData, birthdayData, companyData, personalData } from './datasource.ts';

Schedule.Inject(Month, TimelineMonth);

let calendarCollections: Object[] = [
    { CalendarText: 'My Calendar', CalendarId: 1, CalendarColor: '#c43081' },
    { CalendarText: 'Company', CalendarId: 2, CalendarColor: '#ff7f50' },
    { CalendarText: 'Birthday', CalendarId: 3, CalendarColor: '#AF27CD' },
    { CalendarText: 'Holiday', CalendarId: 4, CalendarColor: '#808000' }
];

let scheduleObj: Schedule = new Schedule({
    width: '100%',
    height: '550px',
    selectedDate: new Date(2018, 3, 1),
    group: {
        resources: ['Calendars']
    },
    resources: [{
        field: 'CalendarId', title: 'Calendar',
        name: 'Calendars', allowMultiple: true,
        dataSource: [calendarCollections[0]],
        textField: 'CalendarText', idField: 'CalendarId', colorField: 'CalendarColor'
    }],
    views: ['Month', 'TimelineMonth'],
    eventSettings: { dataSource: generateCalendarData() }
});
scheduleObj.appendTo('#Schedule');

function onChange(args: ChangeEventArgs): void {
    let value: number = parseInt((<Element>args.event.target).getAttribute('value'), 10);
    let resourceData: Object[] = calendarCollections.filter((calendar: { [key: string]: Object }) => calendar.CalendarId === value);
    if (args.checked) {
        scheduleObj.addResource(resourceData[0], 'Calendars', value - 1);
    } else {
        scheduleObj.removeResource(value, 'Calendars');
    }
}

new CheckBox({ value: '1', label: 'My Calendar', checked: true, disabled: true, change: onChange }, '#personal');
new CheckBox({ value: '2', label: 'Company', checked: false, change: onChange }, '#company');
new CheckBox({ value: '3', label: 'Birthday', checked: false, change: onChange }, '#birthdays');
new CheckBox({ value: '4', label: 'Holiday', checked: false, change: onChange }, '#holidays');

function generateCalendarData(): Object[] {
    let collections: Object[] = [];
    let dataCollections: Object[][] = [personalData, companyData, birthdayData, holidayData];
    for (let data of dataCollections) {
        collections = collections.concat(data);
    }
    return collections;
}
```

{% endtab %}

## Setting different working days and hours for resources

Each resource in the Scheduler can have different working hours as well as different working days set to it. There are default options available within the `resources` collection, to customize the default working hours and days of the Scheduler.

### Set different work days

Different working days can be set for the resources of Scheduler using the `workDaysField` property which maps the working days field from the resource dataSource. This field accepts the collection of day indexes (from 0 to 6) of a week. By default, it is set to [1, 2, 3, 4, 5] and in the following example, each resource has been set with different values and therefore each of them will render only those working days. This option is applicable only on the calendar views and is not applicable on timeline views.

{% tab template="schedule/multiple-resource", es5Template="work-days", iframeHeight="588px", sourceFiles="index.ts,index.html"  %}

```typescript
import { Schedule, Week,WorkWeek, Month } from '@syncfusion/ej2-schedule';
import { doctorData } from './datasource.ts';

Schedule.Inject(Month, Week, WorkWeek);
let scheduleObj: Schedule = new Schedule({
    width: '100%',
    height: '550px',
    selectedDate: new Date(2018, 3, 1),
    views: ['Week', 'WorkWeek', 'Month'],
    currentView: 'WorkWeek',
    group: {
        resources: ['Doctors']
    },
    resources: [{
        field: 'DoctorId', title: 'Choose Doctor',
        name: 'Doctors', allowMultiple: true,
        dataSource: [
            { text: 'Will Smith', id: 1, color: '#ea7a57', workDays: [1, 2, 4, 5] },
            { text: 'Alice', id: 2, color: 'rgb(53, 124, 210)', workDays: [1, 3, 5] },
            { text: 'Robson', id: 3, color: '#7fa900' , workDays: [2,6]}
        ],
        textField: 'text', idField: 'id', colorField: 'color', workDaysField: 'workDays'
    }],
    eventSettings: { dataSource: doctorData }
});
scheduleObj.appendTo('#Schedule');
```

{% endtab %}

### Set different work hours

Working hours indicates the work hour duration of a day, which is highlighted visually with active color over the work cells. Each resource on the Scheduler can be defined with its own set of working hours as depicted in the following example.

* `startHourField` - Denotes the start time of the working/business hour in a day.
* `endHourField` - Denotes the end time limit of the working/business hour in a day.

{% tab template="schedule/multiple-resource", es5Template="work-hours", iframeHeight="588px", sourceFiles="index.ts,index.html"  %}

```typescript
import { Schedule, Week, Month, TimelineViews, TimelineMonth } from '@syncfusion/ej2-schedule';
import { doctorData } from './datasource.ts';

Schedule.Inject(Week, Month, TimelineViews, TimelineMonth);
let scheduleObj: Schedule = new Schedule({
    width: '100%',
    height: '550px',
    selectedDate: new Date(2018, 3, 1),
    views: ['Week', 'Month', 'TimelineWeek', 'TimelineMonth'],
    group: {
        resources: ['Doctors']
    },
    resources: [{
        field: 'DoctorId', title: 'Doctor Name',
        name: 'Doctors', allowMultiple: true,
        dataSource: [
            { text: 'Will Smith', id: 1, color: '#ea7a57', startHour: '08:00', endHour: '15:00' },
            { text: 'Alice', id: 2, color: '#357cd2', startHour: '10:00', endHour: '18:00'},
            { text: 'Robson', id: 3, color: '#7fa900', startHour: '06:00', endHour: '13:00' }
        ],
        textField: 'text', idField: 'id', colorField: 'color', startHourField: 'startHour', endHourField: 'endHour'
    }],
    eventSettings: { dataSource: doctorData }
});
scheduleObj.appendTo('#Schedule');
```

{% endtab %}

In this example, a resource named `Will Smith` is depicted with working hours ranging from 8.00 AM to 3.00 PM and is visually illustrated with active colors, whereas the other two resources have different working hours set.

## Scroll to specific resource

You can manually scroll to a specific resource on Scheduler by making use of the `scrollToResource` method as depicted in the following code example.

{% tab template="schedule/scroll-to-resource", es5Template="scroll-to-resource", iframeHeight="588px", sourceFiles="index.ts,index.html"  %}

```typescript
import { Schedule, Week, Month, Agenda, TimelineViews, TimelineMonth } from '@syncfusion/ej2-schedule';
import { Button } from '@syncfusion/ej2-buttons';
import { resourceData } from './datasource.ts';

Schedule.Inject(Month, Week, Agenda, TimelineViews, TimelineMonth);
let scheduleObj: Schedule = new Schedule({
    width: '100%',
    height: '550px',
    views: ['Week', 'Month', 'TimelineWeek', 'TimelineMonth', 'Agenda'],
    selectedDate: new Date(2018, 3, 1),
    group: {
        resources: ['Owners']
    },
    resources: [
      {
        field: 'OwnerId', title: 'Owner',
        name: 'Owners', allowMultiple: true,
        dataSource: [
            { OwnerText: 'Jammy', Id: 1, OwnerColor: '#ffaa00' },
            { OwnerText: 'Steven', Id: 2,  OwnerColor: '#f8a398' },
            { OwnerText: 'Tweety', Id: 3, OwnerColor: '#7499e1'},
            { OwnerText: 'Jammy', Id: 4,  OwnerColor: '#ffaa00' },
            { OwnerText: 'Nestle', Id: 5, OwnerGroupId: 2, OwnerColor: '#f8a398' },
            { OwnerText: 'Phoenix', Id: 6,  OwnerColor: '#7499e1'},
            { OwnerText: 'Hangout', Id: 7,  OwnerColor: '#ffaa00' },
            { OwnerText: 'Rainbow', Id: 8, OwnerGroupId: 2, OwnerColor: '#f8a398' },
            { OwnerText: 'Photogenic', Id: 9,  OwnerColor: '#7499e1'}
        ],
        textField: 'OwnerText', idField: 'Id', colorField: 'OwnerColor'
    }],
    eventSettings: { dataSource: resourceData }
});
scheduleObj.appendTo('#Schedule');

let button1: Button = new Button();
button1.appendTo('#btn1');

button1.element.onclick = (): void => {
  scheduleObj.scrollToResource(6, 'Owners');
};
```

{% endtab %}

## Compact view in mobile

Although the Scheduler views are designed keeping in mind the responsiveness of the control in mobile devices, however when using Scheduler with multiple resources - it is difficult to view all the resources and its relevant events at once on the mobile. Therefore, we have introduced a new compact mode specially for displaying multiple resources of Scheduler on mobile devices. By default, this mode is enabled while using Scheduler with multiple resources on mobile devices. If in case, you need to disable this compact mode, set `false` to the `enableCompactView` option within the `group` property. Disabling this option will display the exact desktop mode of Scheduler view on mobile devices.

With this compact view enabled on mobile, you can view only single resource at a time and to switch to other resources, there is a treeview at the left listing out all other available resources - clicking on which will display that particular resource and its related appointments.

![Resources in compact mode](./images/resource-mobile.png)

Clicking on the menu icon before the resource text will show the resources available in the Scheduler as following.

![Resources menu option in compact mode](./images/resource-menu.png)

## Adaptive UI in desktop

By default, the Scheduler layout adapts automatically in the desktop and mobile devices with appropriate UI changes. In case, if the user wants to display the Adaptive scheduler in desktop mode with adaptive enhancements, then the property `enableAdaptiveUI` can be set to true. Enabling this option will display the exact mobile mode of Scheduler view on desktop devices.

Some of the default changes made for compact Scheduler to render in desktop devices are as follows,
* View options displayed in the Navigation drawer.
* Plus icon is added to the header for new event creation.
* Today icon is added to the header instead of the Today button.
* With Multiple resources – only one resource has been shown to enhance the view experience of resource events details clearly. To switch to other resources, there is a TreeView on the left that lists all other available resources, clicking on which will display that particular resource and its related events.

{% tab template="schedule/resource-grouping", es5Template="adaptive-grouping", iframeHeight="588px", sourceFiles="index.ts,index.html"  %}

```typescript
import { Schedule, Day, Week, Month, Resize, DragAndDrop } from '@syncfusion/ej2-schedule';
import { extend } from '@syncfusion/ej2-base';
import { timelineResourceData, resourceData } from './datasource.ts';

Schedule.Inject(Day, Week, Month, Resize, DragAndDrop);
let scheduleObj: Schedule = new Schedule({
    width: '100%', height: '555px',
    views: ['Day', 'Week', 'Month'],
    currentView: 'Month',
    selectedDate: new Date(2018, 3, 4),
    enableAdaptiveUI: true,
    group: {
        resources: ['Projects', 'Categories']
    },
    resources: [
        {
            field: 'ProjectId', title: 'Choose Project', name: 'Projects',
            dataSource: [
                { text: 'PROJECT 1', id: 1, color: '#cb6bb2' },
                { text: 'PROJECT 2', id: 2, color: '#56ca85' },
                { text: 'PROJECT 3', id: 3, color: '#df5286' }
            ],
            textField: 'text', idField: 'id', colorField: 'color'
        }, {
            field: 'TaskId', title: 'Category',
            name: 'Categories', allowMultiple: true,
            dataSource: [
                { text: 'Nancy', id: 1, groupId: 1, color: '#df5286' },
                { text: 'Steven', id: 2, groupId: 1, color: '#7fa900' },
                { text: 'Robert', id: 3, groupId: 2, color: '#ea7a57' },
                { text: 'Smith', id: 4, groupId: 2, color: '#5978ee' },
                { text: 'Michael', id: 5, groupId: 3, color: '#df5286' },
                { text: 'Root', id: 6, groupId: 3, color: '#00bdae' }
            ],
            textField: 'text', idField: 'id', groupIDField: 'groupId', colorField: 'color'
        }
    ],
    eventSettings: {
        dataSource: <Object[]> extend([], resourceData.concat(timelineResourceData), null, true)
    }
});
scheduleObj.appendTo('#Schedule');
```

{% endtab %}
