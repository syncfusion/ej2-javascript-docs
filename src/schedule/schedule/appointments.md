---
title: "Handling Appointments of Scheduler"
component: "Scheduler"
description: "This section explains about the types of Scheduler events, recurring events, customization options available in it, and also drag and resize options."
---

# Appointments

Appointments can be anything that are scheduled for a specific time period. It can be created on varied time range and each appointments are categorized based on this range. The Scheduler events can be categorized as,

* Normal events
* Spanned events
* All-day events
* Recurring events

## Normal events

Represents an appointment that is created for any specific time interval within a day.

### Creating a normal event

The following example depicts how to define a normal event on the Scheduler, with event data being loaded from simple JSON data.

{% tab template="schedule/event", es5Template="normal-event", iframeHeight="588px", sourceFiles="index.ts,index.html"  %}

```typescript
import { Schedule, Day, Week, TimelineViews, Month, Agenda } from '@syncfusion/ej2-schedule';

let data: object [] = [{
    Subject: 'Paris',
    StartTime: new Date(2018, 1, 15, 10, 0),
    EndTime: new Date(2018, 1, 15, 12, 30)
}];

Schedule.Inject(Day, Week, TimelineViews, Month, Agenda);
let scheduleObj: Schedule = new Schedule({
    height: '550px',
    selectedDate: new Date(2018, 1, 15),
    views: ['Day', 'Week', 'TimelineWeek', 'Month', 'Agenda'],
    eventSettings: {
        dataSource: data
    }
});
scheduleObj.appendTo('#Schedule');
```

{% endtab %}

## Spanned events

Represents an appointment that is created for more than 24 hours, and usually displayed on the all-day row. Also, represents another type of appointment that is created for more than one day but less than 24 hours, and usually displayed appropriately on both the days.

> For example, if an appointment is created for two days say from November 25, 2018 – 11.00 PM to November 26, 2018 2.00 AM but less than 24 hours time interval, then the appointment is split into two partitions and will be displayed on both the days.

## All-day events

Represents an appointment that is created for an entire day such as holiday events. It is usually displayed separately in an all-day row, a separate row for all-day appointments below the date header section. In Timeline views, the all-day appointments displays in the working space area, and no separate all-day row is present in that view.

> To change normal appointment into all-day event, set `isAllDay` field to true.

### Hide all-day row events

You can make use of the CSS customization to prevent the display of all-day row appointments on the Scheduler UI.

```typescript
    <style>
        .e-schedule .e-date-header-wrap .e-schedule-table thead {
           display: none;
        }
    </style>
```

## Recurring events

Represents an appointment that is created for a certain time interval and occurring repeatedly on a daily, weekly, monthly or yearly basis at the same time interval based on the provided recurrence rule. Usually, the recurring events are indicated by a repeat marker added at the bottom-right position.

### Creating a recurring event

The following example depicts how to create a recurring event on Scheduler with the specific recurrence rule. In the following example, an event is made to repeat on daily mode and ends after 5 occurrences.

{% tab template="schedule/event", es5Template="recurring-event", iframeHeight="588px" sourceFiles="index.ts,index.html"  %}

```typescript
import { Schedule, Day, Week, TimelineMonth, Month, Agenda } from '@syncfusion/ej2-schedule';

let data: object [] = [{
    Id: 1,
    Subject: 'Paris',
    StartTime: new Date(2018, 1, 15, 10, 0),
    EndTime: new Date(2018, 1, 15, 12, 30),
    IsAllDay: false,
    RecurrenceRule: 'FREQ=DAILY;INTERVAL=1;COUNT=5'
}];
Schedule.Inject(Day, Week, TimelineMonth, Month, Agenda);
let scheduleObj: Schedule = new Schedule({
    height: '550px',
    selectedDate: new Date(2018, 1, 15),
    views: ['Day', 'Week', 'TimelineMonth', 'Month', 'Agenda'],
    eventSettings: {
        dataSource: data
    }
});
scheduleObj.appendTo('#Schedule');
```

{% endtab %}

### Adding exceptions

A few instance of the recurrence series can be excluded on specific dates, by adding those exceptional dates to the `recurrenceException` field. These date values should be given in the ISO date time format with no hyphens(-) separating the date elements.

For example, 22nd February 2018 can be represented as 20180222. Also, the time part being represented in UTC format needs to add "Z" after the time portion with no space. "07:30:00 UTC" is therefore represented as "073000Z".

{% tab template="schedule/event", es5Template="exception-event", iframeHeight="588px", sourceFiles="index.ts,index.html"  %}

```typescript
import { Schedule, Day, Week, WorkWeek, Month, Agenda } from '@syncfusion/ej2-schedule';

let data: object [] = [{
    Id: 1,
    Subject: 'Paris',
    StartTime: new Date(2018, 0, 28, 10, 0),
    EndTime: new Date(2018, 0, 28, 12, 30),
    IsAllDay: false,
    RecurrenceRule: 'FREQ=DAILY;INTERVAL=1;COUNT=8',
    RecurrenceException:'20180129T043000Z,20180131T043000Z,20180202T043000Z'
}];
Schedule.Inject(Day, Week, WorkWeek, Month, Agenda);
let scheduleObj: Schedule = new Schedule({
    height: '550px',
    selectedDate: new Date(2018, 0, 28),
    eventSettings: {
        dataSource: data
    }
});
scheduleObj.appendTo('#Schedule');
```

{% endtab %}

### Editing an occurrence from a series

To dynamically edit a particular occurrence from an event series and display it on the initial load of Scheduler, the edited occurrence needs to be added as a new event to the dataSource collection, with an additional `recurrenceID` field defined to it. The `recurrenceID` field of edited occurrence usually maps the ID value of the parent event.

In this example, a recurring instance that displays on the date 30th Jan 2018 is edited with different timings. Therefore, this particular date is excluded from the parent recurring event that repeats from 28th January 2018 to 4th February 2018. This can be done by adding the `recurrenceException` field with the excluded date value on the parent event. Also, the edited occurrence event which is created as a new event should carry the `recurrenceID` field pointing to the parent event's `Id` value.

{% tab template="schedule/event", es5Template="occurrence-exception", iframeHeight="588px"  sourceFiles="index.ts,index.html"  %}

```typescript
import { Schedule, Day, Week, WorkWeek, Month, Agenda } from '@syncfusion/ej2-schedule';

let data: object [] = [{
    Id: 1,
    Subject: 'Scrum Meeting',
    StartTime: new Date(2018, 0, 28, 10, 0),
    EndTime: new Date(2018, 0, 28, 12, 30),
    IsAllDay: false,
    RecurrenceRule: 'FREQ=DAILY;INTERVAL=1;COUNT=8',
    RecurrenceException:'20180130T043000Z'
},
{
    Id: 2,
    Subject: 'Scrum Meeting',
    StartTime: new Date(2018, 0, 30, 9, 0),
    EndTime: new Date(2018, 0, 30, 10, 30),
    Description: "Meeting time changed based on team activities.",
    RecurrenceID: 1
}];
Schedule.Inject(Day, Week, WorkWeek, Month, Agenda);
let scheduleObj: Schedule = new Schedule({
    height: '550px',
    selectedDate: new Date(2018, 0, 28),
    eventSettings: {
        dataSource: data
    }
});
scheduleObj.appendTo('#Schedule');
```

{% endtab %}

### Edit only the current and following events

To edit only the current and following events enable the property `editFollowingEvents` within `eventSettings` property. The edited occurrence needs to be added as a new event to the dataSource collection, with an additional `followingID` field defined to it. The `followingID` field of edited occurrence usually maps the ID value of the immediate parent event.

In this example, a recurring instance that displays on the date 30th Jan 2018 and its following dates are edited with different subject. Therefore, this particular date and its following dates are excluded from the parent recurring event that repeats from 28th January 2018 to 4th February 2018. This can be done by updating the `recurrenceRule` field with the until date value on the parent event. Also, the edited events which is created as a new event should carry the `followingID` field pointing to the immediate parent event's `Id` value.

{% tab template="schedule/event", iframeHeight="588px"  sourceFiles="app.ts,index.html"  %}

```typescript
import { Schedule, Day, Week, WorkWeek, Month, Agenda } from '@syncfusion/ej2-schedule';

let data: object[] = [{
    Id: 1,
    Subject: 'Scrum Meeting',
    StartTime: new Date(2018, 0, 28, 10, 0),
    EndTime: new Date(2018, 0, 28, 12, 30),
    IsAllDay: false,
    RecurrenceRule: 'FREQ=DAILY;INTERVAL=1;UNTIL=20180129T043000Z;',
},
{
    Id: 2,
    Subject: 'Scrum Meeting - Following Edited',
    StartTime: new Date(2018, 0, 30, 10, 0),
    EndTime: new Date(2018, 0, 30, 12, 30),
    IsAllDay: false,
    RecurrenceRule: 'FREQ=DAILY;INTERVAL=1;UNTIL=20180204T043000Z;',
    FollowingID: 1
}];
Schedule.Inject(Day, Week, WorkWeek, Month, Agenda);
let scheduleObj: Schedule = new Schedule({
    height: '550px',
    selectedDate: new Date(2018, 0, 28),
    eventSettings: {
        dataSource: data,
        editFollowingEvents: true
    }
});
scheduleObj.appendTo('#Schedule');
```

{% endtab %}

### Recurrence options and rules

Events can be repeated on a daily, weekly, monthly or yearly basis based on the recurrence rule which accepts the string value. The following details should be assigned to the `recurrenceRule` property to generate the recurring instances.

* Repeat type - daily/weekly/monthly/yearly.
* How many times it needs to be repeated?
* The interval duration.
* The time period to render the appointment, etc.

There are four repeat types available namely,

* **Daily** - Creates the recurring instances on daily basis.
* **Weekly** - Creates the recurring instances on weekly basis for the selected days.
* **Monthly** - Creates the recurring instances on monthly basis for the selected months and other provided recurrence criteria.
* **Yearly** - Creates the recurring instances on yearly basis.

### Recurrence properties

 The properties based on which the recurrence appointments are created with its respective time period are depicted in the following table. Also, the valid rule string can be referred from [iCalendar](https://tools.ietf.org/html/rfc5545#section-3.3.10) specifications.

 > Refer [iCalendar](https://tools.ietf.org/html/rfc5545#section-3.3.10) specifications for valid recurrence rule string.

| Property | Purpose | Example |
|-------|---------| --------- |
| FREQ | Maintains the repeat type (Daily, Weekly, Monthly, Yearly) value of the appointment. | FREQ=DAILY;INTERVAL=1|
| INTERVAL | Maintains the interval value of the appointments. When you create the daily appointment at an interval of 2, the appointments are rendered on the days Monday, Wednesday and Friday (Creates an appointment on all days by leaving the interval of one day gap). | FREQ=DAILY;INTERVAL=2|
| COUNT | It holds the appointment’s count value. When the COUNT value is 10, then 10 instances of appointments are created in the recurrence series. | FREQ=DAILY;INTERVAL=1;COUNT=10|
| UNTIL | This property holds the end date value (in ISO format) denoting when the recurrence actually ends. | FREQ=DAILY;INTERVAL=1;UNTIL=20180530T041343Z;|
| BYDAY | It holds the day value(s), representing on which the appointments actually renders. Create the weekly appointment, and select the day(s) from the day options (Monday/Tuesday/Wednesday/Thursday/Friday/Saturday/Sunday). When Monday is selected, the first two letters of the selected day "MO" is saved in the BYDAY property. When multiple days are selected, the values are separated by commas. | FREQ=WEEKLY;INTERVAL=1;BYDAY=MO,WE;COUNT=10|
| BYMONTHDAY | This property is used to store the date value of the Month, while creating the Month recurrence appointment. When you create a Monthly recurrence appointment for every 3rd day of the month, then BYMONTHDAY holds the value 3 and creates the appointment on 3rd day of every month. | FREQ=MONTHLY;BYMONTHDAY=3;INTERVAL=1;COUNT=10|
| BYMONTH | This property is used to store the index value of the selected Month while creating the yearly appointments. When you create the yearly appointment on June month, the index value of June month 6 will get stored in the BYMONTH field. The appointment is created on every 6th month of a year. | FREQ=YEARLY;BYMONTHDAY=16;BYMONTH=6;INTERVAL=1;COUNT=10|
| BYSETPOS | This property is used to store the index value of the week. When you create the monthly appointment in second week of a month, the index value of the second week (2) is stored in BYSETPOS. | FREQ=MONTHLY;BYDAY=MO;BYSETPOS=2;COUNT=10|

> The default recurrence related validation has been included for recurrence appointments similar to the one available in Outlook. The validation usually occurs during the recurrence appointment creation, editing, drag and drop or resizing of the recurrence appointments and also if any single occurrence changes.

### Daily Frequency

| Description | Example |
|-------------|---------|
| Daily recurring event that never ends | FREQ=DAILY;INTERVAL=1 |
| Daily recurring event that ends after 5 occurrences | FREQ=DAILY;INTERVAL=1;COUNT=5 |
| Daily recurring event that ends exactly on 12/12/2018 | FREQ=DAILY;INTERVAL=1;UNTIL=20181212T041343Z |
| Daily event that recurs on alternative days and repeats for 10 occurrences | FREQ=DAILY;INTERVAL=2;COUNT=10 |

### Weekly Frequency

| Description | Example |
|-------------|---------|
| Weekly recurring event that repeats on every Monday, Wednesday and Friday and never ends | FREQ=WEEKLY;INTERVAL=1;BYDAY=MO,WE,FR |
| Repeats every week Thursday and ends after 10 occurrences | FREQ=WEEKLY;INTERVAL=1;BYDAY=TH; COUNT=10 |
| Repeats every week Monday and ends on 12/12/2018 | FREQ=WEEKLY;INTERVAL=1;BYDAY=MO; UNTIL=20181212T041343Z |
| Repeats on Monday, Wednesday and Friday of alternative weeks and ends after 10 occurrences | FREQ=WEEKLY;INTERVAL=2;BYDAY=MO,WE,FR;COUNT=10 |

### Monthly Frequency

| Description | Example |
|-------------|---------|
| Monthly recurring event that repeats on every 15th day of a month and never ends | FREQ=MONTHLY; BYMONTHDAY=15;INTERVAL=1 |
| Monthly recurring event that repeats on every 16th day of a month and ends after 10 occurrences | FREQ=MONTHLY;BYMONTHDAY=16;INTERVAL=1;COUNT=10 |
| Repeats every 17th day of a month and ends on 12/12/2018 | FREQ=MONTHLY;BYMONTHDAY=17; INTERVAL=1;UNTIL=20181212T041343Z |
| Repeats every 2nd Friday of a month and never ends | FREQ=MONTHLY;BYDAY=FR;BYSETPOS=2; INTERVAL=1 |
| Repeats every 4th Wednesday of a month and ends after 10 occurrences | FREQ=MONTHLY;BYDAY=WE; BYSETPOS=4;INTERVAL=1;COUNT=10 |
| Repeats every 4th Friday of a month and ends on 12/12/2018 | FREQ=MONTHLY;BYDAY=FR;BYSETPOS=4; INTERVAL=1;UNTIL=20181212T041343Z; |

### Yearly Frequency

| Description | Example |
|-------------|---------|
| Yearly event that repeats on every 15th day of December month and never ends | FREQ=YEARLY; BYMONTHDAY=15;BYMONTH=12;INTERVAL=1 |
| Event that repeats on every 10th day of December month and ends after 10 occurrences | FREQ=YEARLY; BYMONTHDAY=10;BYMONTH=12;INTERVAL=1;COUNT=10 |
| Repeats on every 12th day of December month and ends on 12/12/2025 | FREQ=YEARLY;BYMONTHDAY=12; BYMONTH=12;INTERVAL=1;UNTIL=20251212T041343Z |
| Repeats on every 3rd Friday of December month and never ends | FREQ=YEARLY;BYDAY=FR;BYMONTH=12; BYSETPOS=3;INTERVAL=1 |
| Repeats on every 3rd Tuesday of December month and ends after 10 occurrences | FREQ=YEARLY; BYDAY=TU;BYMONTH=12;BYSETPOS=3;INTERVAL=1;COUNT=10 |
| Repeats on every 4th Wednesday of December month and ends on 12/12/2028 | FREQ=YEARLY;BYDAY=WE; BYMONTH=12;BYSETPOS=4;INTERVAL=1;UNTIL=20281212T041343Z |

### Recurrence Validation

The built-in validation support has been added by default for recurring appointments during its creation, edit, drag and drop or resize action. The following are the possible validation alerts that displays on Scheduler while creating or editing the recurring events.

| Validation messages | Description |
|-------|---------|
| The recurrence pattern is not valid. | This alert will raise, when the selected recurrence rule value is not a valid one. For example, when you try to select the end date value (using `Until` option) for a recurring event, which occurs before the start date, an alert will popup out saying that the chosen pattern is invalid. |
| The changes made to specific instances of this series will be cancelled and those events will match the series again. | This alert will raise, when you try to edit the whole series, whose occurrence might have been already edited. For example, If there are five occurrences and one of the occurrence is already edited. Now, when you try to edit the entire series, you will get this validation alert. |
| The duration of the event must be shorter than how frequently it occurs. Shorten the duration, or change the recurrence pattern in the recurrence event editor. | This validation will occur, if the event duration is longer than the selected frequency. For example, if you create a recurring appointment with two days duration in `Daily` frequency with no intervals set to it, you may get this alert. |
| Some months have fewer than the selected date. For these months, the occurrence will fall on the last date of the month. | When you try to create a recurring appointment on 31st of every month, where few months won’t have 31 days and in this scenario, you will get this alert. |
| Two occurrences of the same event cannot occur on the same day. | This validation will occur, when you try to edit or move any single occurrence to some other date, where another occurrence of the same event is already present. |

## Event fields

The Scheduler dataSource usually holds the event instances, where each of the instance includes a collection of appropriate [fields](../api/schedule/field). It is mandatory to map these fields with the equivalent fields of database, when remote data is bound to it. When the local JSON data is bound, then the field names defined within the instances needs to be mapped with the scheduler event fields correctly.

> To create an event on Scheduler, it is enough to define the `startTime` and `endTime`. Also `id` field becomes mandatory to process CRUD actions on appropriate events.

### Built-in fields

The built-in fields available on Scheduler event object are as follows.

| Field name | Description |
|-------|---------|
| id | The `id` field needs to be defined as mandatory and this field usually assigns a unique ID value to each of the events.|
| subject | The `subject` field is optional, and usually assigns the summary text to each of the events.|
| startTime | The `startTime` field defines the start time of an event and it is mandatory to provide it for any of the valid event objects.|
| endTime | The `endTime` field defines the end time of an event and it is mandatory to provide the end time for any of the valid event objects.|
| startTimezone | It maps the `startTimezone` field from the dataSource and usually accepts the valid IANA timezone names. It is assumed that the value provided for this field is taken into consideration while processing the `startTime` field. When this field is not mapped with any timezone names, then the events will be processed based on the timezone assigned to the Scheduler.|
| endTimezone | It maps the `endTimezone` field from the dataSource and usually accepts the valid IANA timezone names. It is assumed that the value provided for this field is taken into consideration while processing the `endTime` field. When this field is not mapped with any timezone names, then the events will be processed based on the timezone assigned to the Scheduler.|
| location | It maps the `location` field from the dataSource and the location text value will be displayed over the events.|
| description | It maps the `description` field from the dataSource and denotes the event description which is optional.|
| isAllDay | The `isAllDay` field is mapped from the dataSource and is used to denote whether an event is created for an entire day or for specific time alone. Usually, an event with `isAllDay` field set to true will be considered as an all-day event. |
| recurrenceID | It maps the `recurrenceID` field from dataSource and usually holds the ID value of the parent recurrence event. This field is applicable only for the edited occurrence events.|
| recurrenceRule | It maps the `recurrenceRule` field from dataSource and holds the recurrence rule value in a string format. Also, it uniquely identifies whether the event belongs to a recurring type or normal ones. |
| recurrenceException | It maps the `recurrenceException` field from dataSource and is used to hold the collection of exception dates, on which the recurring occurrences needs to be excluded. |
| isReadonly | It maps the `isReadonly` field from dataSource. It is mainly used to make specific appointments as readonly when set to `true`. |
| isBlock | It maps the `isBlock` field from dataSource. It is used to block the particular time ranges in the Scheduler and prevents the event creation on those time slots. |

### Binding different field names

When the fields of event instances has the default mapping name, it is not mandatory to map them manually. If a Scheduler's dataSource holds the events collection with different field names, then it is necessary to map them with its equivalent field name within the `eventSettings` property.

{% tab template="schedule/event", es5Template="default-field", iframeHeight="588px", sourceFiles="index.ts,index.html"  %}

```typescript
import { Schedule, Day, Week, WorkWeek, Month, Agenda } from '@syncfusion/ej2-schedule';

let data: object [] = [{
    TravelId: 2,
    TravelSummary: 'Paris',
    DepartureTime: new Date(2018, 1, 15, 10, 0),
    ArrivalTime: new Date(2018, 1, 15, 12, 30),
    FullDay: false,
    Source: 'London',
    Comments: 'Summer vacation planned for outstation.',
    Origin: 'Asia/Yekaterinburg',
    Destination: 'Asia/Yekaterinburg'
}];
Schedule.Inject(Day, Week, WorkWeek, Month, Agenda);
let scheduleObj: Schedule = new Schedule({
    height: '550px',
    selectedDate: new Date(2018, 1, 15),
    eventSettings: {
        dataSource: data,
        fields: {
            id: 'TravelId',
            subject: { name: 'TravelSummary' },
            isAllDay: { name: 'FullDay' },
            location: { name: 'Source' },
            description: { name: 'Comments' },
            startTime: { name: 'DepartureTime' },
            endTime: { name: 'ArrivalTime' },
            startTimezone: { name: 'Origin' },
            endTimezone: { name: 'Destination' }
        }
    }
});
scheduleObj.appendTo('#Schedule');
```

{% endtab %}

> The mapper field `id` is of string type and has no additional validation options, whereas all other fields are of `Object` type and has additional options.

### Event field settings

Each field of the Scheduler events are provided with additional settings such as options to set default value, to map with appropriate data source fields, to validate every event fields and to provide label values for those fields in the event window.

| Options | Description |
| ------- | ----------- |
| default | Accepts the default value to the applicable fields (Subject, Location and Description), when no values are provided to them from dataSource. |
| name | Accepts the field name to be mapped from the dataSource fields. |
| title | Accepts the label values to be displayed for the fields of event editor. |
| validation | Defines the validation rules to be applied on the event fields within the event editor. |

In following example, the Subject field in event editor will display its appropriate label as **Summary**. When no subject value is provided while saving an event, then the appointment will be saved with the default subject value as **Add Summary**.

{% tab template="schedule/event", es5Template="field-value", iframeHeight="588px", sourceFiles="index.ts,index.html"  %}

```typescript
import { Schedule, Day, Week, WorkWeek, Month, Agenda } from '@syncfusion/ej2-schedule';

let data: object [] = [{
    TravelId: 2,
    TravelSummary: 'Paris',
    DepartureTime: new Date(2018, 1, 15, 10, 0),
    ArrivalTime: new Date(2018, 1, 15, 12, 30),
    Source: 'London',
    Comments: 'Summer vacation planned for outstation.'
}];
Schedule.Inject(Day, Week, WorkWeek, Month, Agenda);
let scheduleObj: Schedule = new Schedule({
    height: '550px',
    selectedDate: new Date(2018, 1, 15),
    eventSettings: {
        dataSource: data,
        fields: {
            id: 'TravelId',
            subject: { name: 'TravelSummary', title: 'Summary', default: 'Add Summary' },
            location: { name: 'Source', default: 'USA' },
            description: { name: 'Comments' },
            startTime: { name: 'DepartureTime' },
            endTime: { name: 'ArrivalTime' }
        }
    }
});
scheduleObj.appendTo('#Schedule');
```

{% endtab %}

## Adding Custom fields

Apart from the default Scheduler fields, the user can include 'n' number of custom fields for appointments. The following code example shows how to include two custom fields namely **Status** and **Priority** within event collection. It is not necessary to bind the custom fields within the `eventSettings`. However, those additional fields can be accessed easily, for internal processing as well as from application end.

{% tab template="schedule/event", es5Template="custom-field", iframeHeight="588px", sourceFiles="index.ts,index.html"  %}

```typescript
import { Schedule, Day, Week, WorkWeek, Month, Agenda } from '@syncfusion/ej2-schedule';

let data: object [] = [{
    Id: 2,
    Subject: 'Meeting',
    StartTime: new Date(2018, 1, 15, 10, 0),
    EndTime: new Date(2018, 1, 15, 12, 30),
    IsAllDay: false,
    Status: 'Completed',
    Priority: 'High'
}];
Schedule.Inject(Day, Week, WorkWeek, Month, Agenda);
let scheduleObj: Schedule = new Schedule({
    height: '550px',
    selectedDate: new Date(2018, 1, 15),
    eventSettings: {
        dataSource: data,
        fields: {
            id: 'Id',
            subject: { name: 'Subject' },
            isAllDay: { name: 'IsAllDay' },
            startTime: { name: 'StartTime' },
            endTime: { name: 'EndTime' }
        }
    }
});
scheduleObj.appendTo('#Schedule');
```

{% endtab %}

## Drag and drop appointments

Appointments can be rescheduled to any time by dragging and dropping them onto the desired location. To work with drag and drop functionality, it is necessary to inject the module `DragAndDrop` and make sure that `allowDragAndDrop` is set to true on Scheduler. In mobile mode, you can drag and drop the events by tap holding an event and dropping them on to the desired location.

> By default, drag and drop action is applicable on all Scheduler views, except Agenda, Month-Agenda and Year view.

{% tab template="schedule/event", es5Template="event-drag", iframeHeight="588px",  isDefaultActive= false, sourceFiles="index.ts,index.html"  %}

```typescript
import { extend } from '@syncfusion/ej2-base';
import { Schedule, Day, Week, TimelineViews, TimelineMonth, Month, Agenda, DragAndDrop} from '@syncfusion/ej2-schedule';
import { scheduleData } from './datasource.ts';

Schedule.Inject(Day, Week, TimelineViews, TimelineMonth, Month, Agenda, DragAndDrop);

let data: Object[] = <Object[]>extend([], scheduleData, null, true);
let scheduleObj: Schedule = new Schedule({
    height: '550px',
    selectedDate: new Date(2018, 1, 15),
    views: ['TimelineDay', 'Day', 'Week', 'TimelineMonth', 'Month', 'Agenda'],
    eventSettings: { dataSource: data }
});
scheduleObj.appendTo('#Schedule');
```

{% endtab %}

### Disable the drag action

By default, you can drag and drop the events within any of the applicable scheduler views, and to disable it, set `false` to the `allowDragAndDrop` property.

{% tab template="schedule/event", es5Template="disable-drag", iframeHeight="588px",sourceFiles="index.ts,index.html"  %}

```typescript
import { extend } from '@syncfusion/ej2-base';
import { Schedule, Day, Week, WorkWeek, Month, Agenda, DragAndDrop} from '@syncfusion/ej2-schedule';
import { scheduleData } from './datasource.ts';

Schedule.Inject(Day, Week, WorkWeek, Month, Agenda, DragAndDrop);

let data: Object[] = <Object[]>extend([], scheduleData, null, true);
let scheduleObj: Schedule = new Schedule({
    height: '550px',
    allowDragAndDrop: false,
    selectedDate: new Date(2018, 1, 15),
    eventSettings: { dataSource: data },
});
scheduleObj.appendTo('#Schedule');
```

{% endtab %}

### Preventing drag and drop on specific targets

It is possible to prevent the drag action on particular target, by passing the target to be excluded in the `excludeSelectors` option within `dragStart` event. In this example, we have prevented the drag action on all-day row.

{% tab template="schedule/event", es5Template="prevent-drag-specific", iframeHeight="588px",sourceFiles="index.ts,index.html"  %}

```typescript
import { extend } from '@syncfusion/ej2-base';
import { Schedule, Day, Week, WorkWeek, Month, Agenda, DragAndDrop, DragEventArgs } from '@syncfusion/ej2-schedule';
import { scheduleData } from './datasource.ts';

Schedule.Inject(Day, Week, WorkWeek, Month, Agenda, DragAndDrop);


let data: Object[] = <Object[]>extend([], scheduleData, null, true);
let scheduleObj: Schedule = new Schedule({
    height: '550px',
    selectedDate: new Date(2018, 1, 15),
    eventSettings: { dataSource: data },
    dragStart: (args: DragEventArgs) => {
        args.excludeSelectors = 'e-header-cells,e-header-day,e-header-date,e-all-day-cells';
    }
});
scheduleObj.appendTo('#Schedule');
```

{% endtab %}

### Disable scrolling on drag action

By default, while dragging an appointment to the edges, either top/bottom in the vertical Scheduler or left/right in the timeline Scheduler, scrolling action takes place automatically. To prevent this scrolling, set `false` to the `scroll` value within the `dragStart` event arguments.

{% tab template="schedule/event", es5Template="disable-scroll-drag", iframeHeight="588px", sourceFiles="index.ts,index.html"  %}

```typescript
import { extend } from '@syncfusion/ej2-base';
import { Schedule, Day, Week, WorkWeek, Month, Agenda, DragAndDrop, DragEventArgs } from '@syncfusion/ej2-schedule';
import { scheduleData } from './datasource.ts';

Schedule.Inject(Day, Week, WorkWeek, Month, Agenda, DragAndDrop);

let data: Object[] = <Object[]>extend([], scheduleData, null, true);
let scheduleObj: Schedule = new Schedule({
    height: '550px',
    selectedDate: new Date(2018, 1, 15),
    eventSettings: { dataSource: data },
    dragStart: (args: DragEventArgs) => {
        args.scroll = { enable: false };
    }
});
scheduleObj.appendTo('#Schedule');
```

{% endtab %}

### Controlling scroll speed while dragging an event

The speed of the scrolling action while dragging an appointment to the Scheduler edges, can be controlled within the `dragStart` event by setting the desired value to the `scrollBy` and `timeDelay` option whereas its default value is 30 minutes and 100ms.

{% tab template="schedule/event", es5Template="scroll-speed-drag", iframeHeight="588px", sourceFiles="index.ts,index.html"  %}

```typescript
import { extend } from '@syncfusion/ej2-base';
import { Schedule, Day, Week, WorkWeek, Month, Agenda, DragAndDrop, DragEventArgs } from '@syncfusion/ej2-schedule';
import { scheduleData } from './datasource.ts';

Schedule.Inject(Day, Week, WorkWeek, Month, Agenda, DragAndDrop);

let data: Object[] = <Object[]>extend([], scheduleData, null, true);
let scheduleObj: Schedule = new Schedule({
    height: '550px',
    selectedDate: new Date(2018, 1, 15),
    eventSettings: { dataSource: data },
    dragStart: (args: DragEventArgs) => {
        args.scroll = { enable: true, scrollBy: 5, timeDelay: 200 };
    }
});
scheduleObj.appendTo('#Schedule');
```

{% endtab %}

### Auto navigation of date ranges on dragging an event

When an event is dragged either to the left or right extreme edges of the Scheduler and kept hold for few seconds without dropping, the auto navigation of date ranges will be enabled allowing the Scheduler to navigate from current date range to back and forth respectively. This action is set to `false` by default and to enable it, you need to set `navigation` to true within the `dragStart` event.

By default, the navigation delay is set to 2000ms. The navigation delay decides how long the user needs to drag and hold the appointments at the extremities. You can also set your own delay value for letting the users to navigate based on it, using the `timeDelay` within the `dragStart` event.

{% tab template="schedule/event", es5Template="auto-navigation", iframeHeight="588px", sourceFiles="index.ts,index.html"  %}

```typescript
import { extend } from '@syncfusion/ej2-base';
import { Schedule, Day, Week, WorkWeek, Month, Agenda, DragAndDrop, DragEventArgs } from '@syncfusion/ej2-schedule';
import { scheduleData } from './datasource.ts';

Schedule.Inject(Day, Week, WorkWeek, Month, Agenda, DragAndDrop);

let data: Object[] = <Object[]>extend([], scheduleData, null, true);
let scheduleObj: Schedule = new Schedule({
    height: '550px',
    selectedDate: new Date(2018, 1, 15),
    eventSettings: { dataSource: data },
    dragStart: (args: DragEventArgs) => {
        args.navigation = { enable: true, timeDelay: 4000 }
    }
});
scheduleObj.appendTo('#Schedule');
```

{% endtab %}

### Setting drag time interval

By default, while dragging an appointment, it moves at an interval of 30 minutes. To change the dragging time interval, pass the appropriate values to the `interval` option within the `dragStart` event.

{% tab template="schedule/event", es5Template="drag-interval", iframeHeight="588px", sourceFiles="index.ts,index.html"  %}

```typescript
import { extend } from '@syncfusion/ej2-base';
import { Schedule, Day, Week, WorkWeek, Month, Agenda, DragAndDrop, DragEventArgs } from '@syncfusion/ej2-schedule';
import { scheduleData } from './datasource.ts';

Schedule.Inject(Day, Week, WorkWeek, Month, Agenda, DragAndDrop);
let data: Object[] = <Object[]>extend([], scheduleData, null, true);
let scheduleObj: Schedule = new Schedule({
    height: '550px',
    selectedDate: new Date(2018, 1, 15),
    eventSettings: { dataSource: data },
    dragStart: (args: DragEventArgs) => {
        args.interval = 10; //drag interval time is changed to 10 minutes
    }
});
scheduleObj.appendTo('#Schedule');
```

{% endtab %}

### Drag and drop items from external source

It is possible to drag and drop the unplanned items from any of the external source into the scheduler, by manually saving those dropped item as a new appointment data through `addEvent` method of Scheduler.

In this example, we have used the tree view control as an external source and the child nodes from the tree view component are dragged and dropped onto the Scheduler. Therefore, it is necessary to make use of the `nodeDragStop` event of the TreeView component, where we can form an event object and save it using the `addEvent` method.

{% tab template="schedule/external-drag", es5Template="external-drag", iframeHeight="620px",sourceFiles="index.ts,index.html,index.css"  %}

```typescript
import { Schedule, Month, Resize, DragAndDrop, CellClickEventArgs } from '@syncfusion/ej2-schedule';
import { ActionEventArgs } from '@syncfusion/ej2-schedule';
import  { eventData, waitingList }from './datasource.ts';
import { DragAndDropEventArgs, TreeView } from '@syncfusion/ej2-navigations';
import { closest, remove, addClass } from '@syncfusion/ej2-base';

Schedule.Inject(Month, Resize, DragAndDrop);
let scheduleObj: Schedule = new Schedule({
    width: '100%',
    height: '550px',
    selectedDate: new Date(2018, 1, 15),
    cssClass: 'schedule-drag-drop',
    views: [ 'Month' ],
    eventSettings: { dataSource: eventData },
    actionBegin: onActionBegin,
    drag: onItemDrag
});
scheduleObj.appendTo('#Schedule');

let treeObj: TreeView = new TreeView({
    fields: { dataSource: waitingList , id: 'Id', text: 'Name' },
    allowDragAndDrop: true,
    nodeDragStop: onTreeDragStop,
    nodeDragging: onItemDrag,
    cssClass: 'treeview-external-drag'
});
treeObj.appendTo('#Tree');

let isTreeItemDropped: boolean = false;
let draggedItemId: string = '';

function onItemDrag(event: any): void {
    if (scheduleObj.isAdaptive) {
        let classElement: HTMLElement = scheduleObj.element.querySelector('.e-device-hover');
        if (classElement) {
            classElement.classList.remove('e-device-hover');
        }
        if (event.target.classList.contains('e-work-cells')) {
            addClass([event.target], 'e-device-hover');
        }
    }
    if (document.body.style.cursor === 'not-allowed') {
        document.body.style.cursor = '';
    }
    if (event.name === 'nodeDragging') {
        let dragElementIcon: NodeListOf<HTMLElement> =
            document.querySelectorAll('.e-drag-item.treeview-external-drag .e-icon-expandable');
        for (let i: number = 0; i < dragElementIcon.length; i++) {
            dragElementIcon[i].style.display = 'none';
        }
    }
}

function onActionBegin(event: ActionEventArgs): void {
    if (event.requestType === 'eventCreate' && isTreeItemDropped) {
        let treeViewdata: { [key: string]: Object }[] = treeObj.fields.dataSource as { [key: string]: Object }[];
        const filteredPeople: { [key: string]: Object }[] =
            treeViewdata.filter((item: any) => item.Id !== parseInt(draggedItemId, 10));
        treeObj.fields.dataSource = filteredPeople;
        let elements: NodeListOf<HTMLElement> = document.querySelectorAll('.e-drag-item.treeview-external-drag');
        for (let i: number = 0; i < elements.length; i++) {
            remove(elements[i]);
        }
    }
}

function onTreeDragStop(event: DragAndDropEventArgs): void {
    let treeElement: Element = <Element>closest(event.target, '.e-treeview');
    let classElement: HTMLElement = scheduleObj.element.querySelector('.e-device-hover');
    if (classElement) {
        classElement.classList.remove('e-device-hover');
    }
    if (!treeElement) {
        event.cancel = true;
        let scheduleElement: Element = <Element>closest(event.target, '.e-content-wrap') ||
            <Element>closest(event.target, '.e-all-day-row');
        if (scheduleElement) {
            let treeviewData: { [key: string]: Object }[] =
                treeObj.fields.dataSource as { [key: string]: Object }[];
            if (event.target.classList.contains('e-work-cells')) {
                const filteredData: { [key: string]: Object }[] =
                    treeviewData.filter((item: any) => item.Id === parseInt(event.draggedNodeData.id as string, 10));
                let cellData: CellClickEventArgs = scheduleObj.getCellDetails(event.target);
                let eventData: { [key: string]: Object } = {
                    Subject: filteredData[0].Name,
                    StartTime: cellData.startTime,
                    EndTime: cellData.endTime,
                    IsAllDay: cellData.isAllDay,
                    Description: filteredData[0].Description
                };
                scheduleObj.addEvent(eventData);
                isTreeItemDropped = true;
                draggedItemId = event.draggedNodeData.id as string;
            }
        }
    }
}
```

{% endtab %}

### Opening the editor window on drag stop

There are scenarios where you want to open the editor filled with data on newly dropped location and may need to proceed to save it, only when `Save` button is clicked on the editor. On clicking the cancel button should revert these changes. This can be achieved using the `dragStop` event of Scheduler.

{% tab template="schedule/event", es5Template="open-editor", iframeHeight="588px",sourceFiles="index.ts,index.html"  %}

```typescript
import { extend } from '@syncfusion/ej2-base';
import { Schedule, Day, Week, WorkWeek, Month, Agenda, DragAndDrop, DragEventArgs } from '@syncfusion/ej2-schedule';
import { scheduleData } from './datasource.ts';

Schedule.Inject(Day, Week, WorkWeek, Month, Agenda, DragAndDrop);
let data: Object[] = <Object[]>extend([], scheduleData, null, true);
let scheduleObj: Schedule = new Schedule({
    height: '550px',
    selectedDate: new Date(2018, 1, 15),
    eventSettings: { dataSource: data },
    dragStop: (args: DragEventArgs) => {
        args.cancel = true; //cancels the drop action
        scheduleObj.openEditor(args.data, "Save"); //open the event window with updated start and end time
    }
});
scheduleObj.appendTo('#Schedule');
```

{% endtab %}

## Inline Appointment

In Scheduler, another easier way for `adding` or `editing` the appointment’s subject alone can be achieved by using the inline Add/Edit support. It allows the user to add and edit the appointments inline. To get familiar with the inline Add mode, single click on any of the Scheduler cells or press enter key on the selected cells.

When the inline adding mode is ON, a text box will get created within the clicked Scheduler cells with a blinking cursor in it, requiring the user to enter the subject of an appointment. Once the subject is entered, the appointment will be saved on pressing the enter key.

To enable the inline edit mode, single click on any of the existing appointment’s subject, so that the user can edit the subject of that appointment. The edited subject of that appointment will be updated on pressing the enter key.

The inline option can be enabled/disabled on the Scheduler by using the allowInline API, whereas its default value is set to false.

While using the `allowInline` the `showQuickInfo` will be turned off. The `quickPopup` will not show on clicking the work cell or clicking the appointment when the `allowInline` property is set to true.
In work cells, select multiple cells using keyboard, and then press enter key. The appointment wrapper will be created, and focus will be on the subject field. Also, consider the overlapping scenarios when creating an inline event.

### Normal Event

While editing appointments, single-click the appointment subject, the `editable` option will be enabled in UI and the cursor will focus at the end of the text. Inline editing will be considered for all possible views.

### Recurrence Event

While editing the occurrence from the recurrence series, it is only possible to edit a `single occurrence`, not an entire series.

{% tab template="schedule/event", es5Template="inline-appointment", iframeHeight="588px", sourceFiles="index.ts,index.html"  %}

```typescript
import { Schedule, Day, Week, TimelineViews, Month, Agenda } from '@syncfusion/ej2-schedule';

let data: object [] = [{
    Subject: 'Paris',
    StartTime: new Date(2018, 1, 15, 10, 0),
    EndTime: new Date(2018, 1, 15, 12, 30)
},{
    Subject: 'Scrum Meeting',
    StartTime: new Date(2018, 1, 11, 9, 30),
    EndTime: new Date(2018, 1, 11, 11, 0)
},{
    Subject: 'Meeting',
    StartTime: new Date(2018, 1, 13, 10, 0),
    EndTime: new Date(2018, 1, 13, 10, 30)
},{
    Subject: 'Inline Editer Window',
    StartTime: new Date(2018, 1, 13, 11, 0),
    EndTime: new Date(2018, 1, 13, 12, 0)
},{
    Subject: 'Validated',
    StartTime: new Date(2018, 1, 17, 11, 0),
    EndTime: new Date(2018, 1, 17, 12, 30)
}];

Schedule.Inject(Day, Week, TimelineViews, Month, Agenda);
let scheduleObj: Schedule = new Schedule({
    height: '550px',
    selectedDate: new Date(2018, 1, 11),
    views: ['Day', 'Week', 'TimelineWeek', 'Month', 'Agenda'],
    allowInline:true,
    eventSettings: {
        dataSource: data
    }
});
scheduleObj.appendTo('#Schedule');
```

{% endtab %}

## Appointment Resizing

Another way of rescheduling an appointment can be done by resizing it through either of its handlers. To work with resizing functionality, it is necessary to inject the module `Resize` and make sure that `allowResizing` property is set to true.

{% tab template="schedule/event", es5Template="event-resize", isDefaultActive=false iframeHeight="588px",sourceFiles="index.ts,index.html"  %}

```typescript
import { extend } from '@syncfusion/ej2-base';
import { Schedule, Day, Week, WorkWeek, Month, Agenda, Resize} from '@syncfusion/ej2-schedule';
import { scheduleData } from './datasource.ts';

Schedule.Inject(Day, Week, WorkWeek, Month, Agenda, Resize);

let data: Object[] = <Object[]>extend([], scheduleData, null, true);
let scheduleObj: Schedule = new Schedule({
    height: '550px',
    selectedDate: new Date(2018, 1, 15),
    eventSettings: { dataSource: data },
});
scheduleObj.appendTo('#Schedule');
```

{% endtab %}

### Disable the resize action

By default, resizing of events is allowed on all Scheduler views except Agenda and Month-Agenda view. To disable this event resizing action, set false to the `allowResizing` property.

{% tab template="schedule/event", es5Template="disable-resize", iframeHeight="588px", sourceFiles="index.ts,index.html"  %}

```typescript
import { extend } from '@syncfusion/ej2-base';
import { Schedule, Day, Week, WorkWeek, Month, Agenda, Resize} from '@syncfusion/ej2-schedule';
import { scheduleData } from './datasource.ts';

Schedule.Inject(Day, Week, WorkWeek, Month, Agenda, Resize);

let data: Object[] = <Object[]>extend([], scheduleData, null, true);
let scheduleObj: Schedule = new Schedule({
    height: '550px',
    allowResizing: false,
    selectedDate: new Date(2018, 1, 15),
    eventSettings: { dataSource: data },
});
scheduleObj.appendTo('#Schedule');
```

{% endtab %}

### Disable scrolling on resize action

By default, while resizing an appointment, when its handler reaches the extreme edges of the Scheduler, scrolling action will takes place along with event resizing. To prevent this scrolling action, set false to `scroll` value within the `resizeStart` event.

{% tab template="schedule/event", es5Template="disable-scroll-resize", iframeHeight="588px", sourceFiles="index.ts,index.html"  %}

```typescript
import { extend } from '@syncfusion/ej2-base';
import { Schedule, Day, Week, WorkWeek, Month, Agenda, Resize, ResizeEventArgs } from '@syncfusion/ej2-schedule';
import { scheduleData } from './datasource.ts';

Schedule.Inject(Day, Week, WorkWeek, Month, Agenda, Resize);

let data: Object[] = <Object[]>extend([], scheduleData, null, true);
let scheduleObj: Schedule = new Schedule({
    height: '550px',
    selectedDate: new Date(2018, 1, 15),
    eventSettings: { dataSource: data },
    resizeStart: (args: ResizeEventArgs) => {
        args.scroll = { enable: false };
    }
});
scheduleObj.appendTo('#Schedule');
```

{% endtab %}

### Controlling scroll speed while resizing an event

The speed of the scrolling action while resizing an appointment to the Scheduler edges, can be controlled within the `resizeStart` event by setting the desired value to the `scrollBy` option.

{% tab template="schedule/event", es5Template="scroll-speed-resize", iframeHeight="588px",sourceFiles="index.ts,index.html"  %}

```typescript
import { extend } from '@syncfusion/ej2-base';
import { Schedule, Day, Week, WorkWeek, Month, Agenda, Resize, ResizeEventArgs } from '@syncfusion/ej2-schedule';
import { scheduleData } from './datasource.ts';

Schedule.Inject(Day, Week, WorkWeek, Month, Agenda, Resize);

let data: Object[] = <Object[]>extend([], scheduleData, null, true);
let scheduleObj: Schedule = new Schedule({
    height: '550px',
    selectedDate: new Date(2018, 1, 15),
    eventSettings: { dataSource: data },
    resizeStart: (args: ResizeEventArgs) => {
        args.scroll = { enable: true, scrollBy: 15 };
    }
});
scheduleObj.appendTo('#Schedule');
```

{% endtab %}

### Setting resize time interval

By default, while resizing an appointment, it extends or shrinks at an interval of 30 minutes. To change this default resize interval, set appropriate values to `interval` option within the `resizeStart` event.

{% tab template="schedule/event", es5Template="resize-interval", iframeHeight="588px", sourceFiles="index.ts,index.html"  %}

```typescript
import { extend } from '@syncfusion/ej2-base';
import { Schedule, Day, Week, WorkWeek, Month, Agenda, Resize, ResizeEventArgs } from '@syncfusion/ej2-schedule';
import { scheduleData } from './datasource.ts';

Schedule.Inject(Day, Week, WorkWeek, Month, Agenda, Resize);

let data: Object[] = <Object[]>extend([], scheduleData, null, true);
let scheduleObj: Schedule = new Schedule({
    height: '550px',
    selectedDate: new Date(2018, 1, 15),
    eventSettings: { dataSource: data },
    resizeStart: (args: ResizeEventArgs) => {
        args.interval = 10; //resize interval time is changed to 10 minutes
    }
});
scheduleObj.appendTo('#Schedule');
```

{% endtab %}

## Appointment customization

The look and feel of the Scheduler events can be customized using any one of the following ways.

* [Using event templates](#using-template)
* [Using eventRendered event](#using-eventrendered-event)
* [Using custom CSS class](#using-custom-css-class)

### Using template

Any kind of text, images and links can be added to customize the look of the events. The user can format and change the default appearance of the events by making use of the `template` option available within the `eventSettings` property. The following code example customizes the appointment's default color and time format.

{% tab template="schedule/event-template", es5Template="event-template", iframeHeight="588px",sourceFiles="index.ts,index.html"  %}

```typescript
import { Schedule, Day, Week, WorkWeek, Month, Agenda } from '@syncfusion/ej2-schedule';
import { webinarData } from './datasource.ts';
import { Internationalization } from '@syncfusion/ej2-base';

Schedule.Inject(Day, Week, WorkWeek, Month, Agenda);
 let instance: Internationalization = new Internationalization();
(window as TemplateFunction).getTimeString = (value: Date) => {
    return instance.formatDate(value, { skeleton: 'hm' });
};
interface TemplateFunction extends Window {
    getTimeString?: Function;
}
let scheduleObj: Schedule = new Schedule({
    width: '100%',
    height: '500px',
    readonly: true,
    selectedDate: new Date(2018, 1, 15),
    eventSettings: {
        dataSource: webinarData,
        template: '#apptemplate'
    }
});
scheduleObj.appendTo('#Schedule');
```

{% endtab %}

> All the built-in fields that are mapped to the appropriate field properties within the `eventSettings`, as well as custom mapped fields from the Scheduler dataSource can be accessed within the template code.

### Using eventRendered event

The `eventRendered` event triggers before the appointment renders on the Scheduler. Therefore, this client-side event can be utilized to customize the look of events based on any specific criteria, before rendering them on the scheduler.

{% tab template="schedule/event", es5Template="event-rendered", iframeHeight="588px",sourceFiles="index.ts,index.html"  %}

```typescript
import { Schedule, Day, Week, WorkWeek, Month, Agenda View, EventRenderedArgs } from '@syncfusion/ej2-schedule';
import { scheduleData } from './datasource.ts';

Schedule.Inject(Day, Week, WorkWeek, Month, Agenda);

let scheduleObj: Schedule = new Schedule({
    height: '550px',
    width: '100%',
    cssClass: 'custom-class',
    selectedDate: new Date(2018, 1, 15),
    eventSettings: { dataSource: scheduleData },
    eventRendered: (args: EventRenderedArgs) => applyCategoryColor(args, scheduleObj.currentView)
});
scheduleObj.appendTo('#Schedule');
function applyCategoryColor(args: EventRenderedArgs, currentView: View): void {
    let categoryColor: string = args.data.CategoryColor as string;
    if (!args.element || !categoryColor) {
        return;
    }
    if (scheduleObj.currentView === 'Agenda') {
        (args.element.firstChild as HTMLElement).style.borderLeftColor = categoryColor;
    } else {
        args.element.style.backgroundColor = categoryColor;
    }
}
```

{% endtab %}

### Using custom CSS class

The customization of events can also be achieved using `cssClass` property of the Scheduler. In the following example, the background of appointments has been changed using the cssClass.

{% tab template="schedule/event", es5Template="css-class", iframeHeight="588px", sourceFiles="index.ts,index.html,index.css"  %}

```typescript
import { Schedule, Day, Week, WorkWeek, Month } from '@syncfusion/ej2-schedule';
import { scheduleData } from './datasource.ts';

Schedule.Inject(Day, Week, WorkWeek, Month);

let scheduleObj: Schedule = new Schedule({
    height: '550px',
    width: '100%',
    cssClass: 'custom-class',
    selectedDate: new Date(2018, 1, 15),
    views: ['Day', 'Week', 'WorkWeek', 'Month'],
    eventSettings: { dataSource: scheduleData }
});
scheduleObj.appendTo('#Schedule');
```

{% endtab %}

## Setting minimum height

It is possible to set minimal height for appointments on Scheduler using `eventRendered` event, when its start and end time duration is less than the default duration of a single slot.

{% tab template="schedule/event", es5Template="minimum-height", iframeHeight="588px" sourceFiles="index.ts,index.html"  %}

```typescript
import { Schedule, Day, Week, WorkWeek, Month, ActionEventArgs} from '@syncfusion/ej2-schedule';

Schedule.Inject(Day, Week, WorkWeek, Month);

let data: object[] = [{
        Id: 13,
        Subject: 'Myths of Andromeda Galaxy',
        StartTime: new Date(2018, 1, 16, 10, 30),
        EndTime: new Date(2018, 1, 16, 10, 40)
    }, {
        Id: 14,
        Subject: 'Aliens vs Humans',
        StartTime: new Date(2018, 1, 15, 10, 0),
        EndTime: new Date(2018, 1, 15, 10, 20)
    }];
let scheduleObj: Schedule = new Schedule({
    height: '550px',
    width: '100%',
    selectedDate: new Date(2018, 1, 15),
    views: ['Day', 'Week', 'WorkWeek', 'Month'],
    eventSettings: { dataSource: data },
    eventRendered: (args: EventRenderedArgs) => {
        let cellHeight: number = (scheduleObj.element.querySelector('.e-work-cells') as HTMLElement).offsetHeight;
        let appHeight: number = (args.data.EndTime.getTime() - args.data.StartTime.getTime()) / (60 * 1000) * (cellHeight * scheduleObj.timeScale.slotCount) / scheduleObj.timeScale.interval;
        args.element.style.height = appHeight+'px';
    }
});
scheduleObj.appendTo('#Schedule');
```

{% endtab %}

## Block Dates and Times

It is possible to block a set of dates or a particular time ranges on the Scheduler. To do so, define an appointment object within `eventSettings` along with the required time range to block and set the `isBlock` field to true. Usually, the event objects defined with isBlock field set to true will block the entire time cells lying within the appropriate time ranges specified through `startTime` and `endTime` fields.

{% tab template="schedule/event", es5Template="block-event", iframeHeight="588px", sourceFiles="index.ts,index.html"  %}

```typescript
import { Schedule, Day, Week, TimelineViews, Month, Agenda, Resize, DragAndDrop } from '@syncfusion/ej2-schedule';
import { blockData } from './datasource.ts';

Schedule.Inject(Day, Week, TimelineViews, Month, Agenda, Resize, DragAndDrop);
let scheduleObj: Schedule = new Schedule({
    height: '550px',
    selectedDate: new Date(2018, 1, 15),
    views: ['Day', 'Week', 'TimelineWeek', 'Month', 'Agenda'],
    eventSettings: {
        dataSource: blockData
    }
});
scheduleObj.appendTo('#Schedule');
```

{% endtab %}

Block events can also be defined to repeat on several days as shown in the following code example.

{% tab template="schedule/event", es5Template="recurrence-block-event", iframeHeight="588px", sourceFiles="index.ts,index.html"  %}

```typescript
import { Schedule, Day, Week, TimelineViews, Month, Agenda, Resize, DragAndDrop } from '@syncfusion/ej2-schedule';

Schedule.Inject(Day, Week, TimelineViews, Month, Agenda, Resize, DragAndDrop);

let data: object [] = [{
    Id: 1,
    Subject: 'Explosion of Betelgeuse Star',
    StartTime: new Date(2018, 1, 15, 9, 30),
    EndTime: new Date(2018, 1, 15, 11, 0),
    RecurrenceRule: 'FREQ=DAILY;INTERVAL=1;COUNT=5',
    IsBlock: true
}, {
    Id: 2,
    Subject: 'Thule Air Crash Report',
    StartTime: new Date(2018, 1, 14, 12, 0),
    EndTime: new Date(2018, 1, 14, 14, 0)
}];
let scheduleObj: Schedule = new Schedule({
    height: '550px',
    selectedDate: new Date(2018, 1, 15),
    views: ['Day', 'Week', 'TimelineWeek', 'Month', 'Agenda'],
    eventSettings: {
        dataSource: data
    }
});
scheduleObj.appendTo('#Schedule');
```

{% endtab %}

## Readonly

An interaction with the appointments of Scheduler can be enabled/disabled using the `readonly` property. With this property enabled, you can simply navigate between the Scheduler dates, views and can be able to view the appointment details in the quick info window. Most importantly, the users are not allowed to perform any CRUD actions on Scheduler, when this property is set to true. By default, it is set as `false`.

{% tab template="schedule/event", es5Template="read-only", iframeHeight="588px",sourceFiles="index.ts,index.html"  %}

```typescript
import { Schedule, Day, Week, WorkWeek, Month, Agenda } from '@syncfusion/ej2-schedule';
import { scheduleData } from './datasource.ts';

Schedule.Inject(Day, Week, WorkWeek, Month, Agenda);
let scheduleObj: Schedule = new Schedule({
    height: '550px',
    readonly: true,
    selectedDate: new Date(2018, 1, 15),
    eventSettings: { dataSource: scheduleData }
});
scheduleObj.appendTo('#Schedule');
```

{% endtab %}

## Make specific events readonly

There are scenarios where you need to restrict the CRUD action on specific appointments alone based on certain conditions. In the following example, the events that has occurred on the past hours from the current date of the Scheduler are made as read-only and the CRUD actions has been prevented only on those appointments. This can be achieved by setting `isReadonly` field of read-only events to `true`.

{% tab template="schedule/event", es5Template="specific-events", iframeHeight="588px",sourceFiles="index.ts,index.html"  %}

```typescript
import { Schedule, Day, Week, WorkWeek } from '@syncfusion/ej2-schedule';
import { readOnlyData } from './datasource.ts';

Schedule.Inject(Day, Week, WorkWeek);

let scheduleObj: Schedule = new Schedule({
    height: '550px',
    width: '100%',
    views: ['Day', 'Week', 'WorkWeek'],
    selectedDate: new Date(2018, 1, 15),
    eventSettings: { dataSource: readOnlyData }
});
scheduleObj.appendTo('#Schedule');
```

{% endtab %}

> By default, the event editor is prevented to open on the read-only events when `isReadonly` field is set to `true`.

## Restricting event creation on specific time slots

You can restrict the users to create and update more than one appointment on specific time slots. Also, you can disable the CRUD action on those time slots if it is already occupied, which can be achieved using Scheduler's public method `isSlotAvailable`.

{% tab template="schedule/cell-dimension", es5Template="is-slot-available", iframeHeight="588px", sourceFiles="index.ts,index.html"  %}

```typescript
import { isNullOrUndefined } from '@syncfusion/ej2-base';
import { Schedule, Day, TimelineViews, WorkWeek, Month, ActionEventArgs} from '@syncfusion/ej2-schedule';
import { scheduleData } from './datasource.ts';

Schedule.Inject(Day, TimelineViews, WorkWeek, Month);

let scheduleObj: Schedule = new Schedule({
    height: '550px',
    width: '100%',
    selectedDate: new Date(2018, 1, 15),
    views: ['Day', 'TimelineWeek', 'WorkWeek', 'Month'],
    currentView: 'TimelineWeek',
    eventSettings: { dataSource: scheduleData },
    actionBegin: (args: ActionEventArgs) => {
        if ((args.requestType === 'eventCreate' || args.requestType === 'eventChange') && (<Object[]>args.data).length > 0 || !isNullOrUndefined(args.data)) {
            let eventData: any = args.data as any;
            let eventField: EventFieldsMapping = scheduleObj.eventFields;
            let startDate: Date = (((<Object[]>args.data).length > 0) ? eventData[0][eventField.startTime] : eventData[eventField.startTime]) as Date;
            let endDate: Date = (((<Object[]>args.data).length > 0) ? eventData[0][eventField.endTime] : eventData[eventField.endTime]) as Date;
            args.cancel = !scheduleObj.isSlotAvailable(startDate, endDate);
        }
    }
});
scheduleObj.appendTo('#Schedule');
```

{% endtab %}

## Differentiate the past time events

To differentiate the appearance of the appointments based on specific criteria such as displaying the past hour appointments with different colors on Scheduler, `eventRendered` event can be used which triggers before the appointment renders on the Scheduler.

{% tab template="schedule/event", es5Template="differ-past", iframeHeight="588px",sourceFiles="index.ts,index.html, index.css"  %}

```typescript
import { Schedule, Day, Week, WorkWeek, Month, ActionEventArgs} from '@syncfusion/ej2-schedule';
import { scheduleData } from './datasource.ts';

Schedule.Inject(Day, Week, WorkWeek, Month);
let isReadOnly: Function = (data: { [key: string]: Object }): boolean => {
    return (data.EndTime < scheduleObj.selectedDate);
};
let scheduleObj: Schedule = new Schedule({
    height: '550px',
    width: '100%',
    views: ['Day', 'Week', 'WorkWeek', 'Month'],
    selectedDate: new Date(2018, 1, 15),
    eventSettings: { dataSource: scheduleData },
    eventRendered: (args: EventRenderedArgs) => {
        if (isReadOnly(args.data)) {
            args.element.classList.add('e-past-app');
        }
    }
});
scheduleObj.appendTo('#Schedule');
```

{% endtab %}

## Display tooltip for appointments

The tooltip shows the Scheduler appointment's information in a formatted style by making use of the tooltip related options.

### Show or hide built-in tooltip

The tooltip can be displayed for appointments by setting `true` to the `enableTooltip` option within the `eventSettings` property.

{% tab template="schedule/event", es5Template="tooltip", iframeHeight="588px", sourceFiles="index.ts,index.html"%}

```typescript
import { Schedule, TimelineViews, Week, WorkWeek, Month, Agenda } from '@syncfusion/ej2-schedule';
import { scheduleData } from './datasource.ts';

Schedule.Inject(TimelineViews, Week, WorkWeek, Month, Agenda);
let scheduleObj: Schedule = new Schedule({
    width: '100%',
    height: '500px',
    views: ['TimelineDay', 'Week', 'WorkWeek', 'Month', 'Agenda'],
    selectedDate: new Date(2018, 1, 15),
    eventSettings: {
        dataSource: scheduleData,
        enableTooltip: true
    }
});
scheduleObj.appendTo('#Schedule');
```

{% endtab %}

### Customizing event tooltip using template

After enabling the default tooltip, it is possible to customize the display of needed event information on tooltip by making use of the `tooltipTemplate` option within the `eventSettings`.

{% tab template="schedule/tooltip", es5Template="tooltip-template", iframeHeight="588px", sourceFiles="index.ts,index.html"%}

```typescript
import { Schedule, Day, Week, WorkWeek, Month, Agenda } from '@syncfusion/ej2-schedule';
import { eventsData } from './datasource.ts';

Schedule.Inject(Day, Week, WorkWeek, Month, Agenda);
let template: string = '<div class="tooltip-wrap">' +
        '<div class="content-area"><div class="name">${Subject}</></div>' +
        '${if(City !== null && City !== undefined)}<div class="city">${City}</div>${/if}' +
        '<div class="time">From : ${StartTime.toLocaleString()} </div>' +
        '<div class="time">To   : ${EndTime.toLocaleString()} </div></div></div>';
let scheduleObj: Schedule = new Schedule({
    width: '100%',
    height: '550px',
    selectedDate: new Date(2018, 1, 15),
    eventSettings: {
        dataSource: eventsData,
        enableTooltip: true,
        tooltipTemplate: template
    }
});
scheduleObj.appendTo('#Schedule');
```

{% endtab %}

> All the field names that are mapped from the Scheduler dataSource to the appropriate field properties such as subject, description, location, startTime and endTime within the `eventSettings` can be accessed within the template.

## Appointment filtering

The appointments can be filtered by passing the predicate value to `query` option in `eventSettings`. The following code example shows how to filter and render the selected appointments alone in the Scheduler.

{% tab template="schedule/event-filter", es5Template="event-filter", iframeHeight="620px", sourceFiles="index.ts,index.html"%}

```typescript
import { CheckBox } from '@syncfusion/ej2-buttons';
import { Query, Predicate } from '@syncfusion/ej2-data';
import { Schedule, Day, Week, WorkWeek, Month, Agenda, EventRenderedArgs } from '@syncfusion/ej2-schedule';
import { scheduleData } from './datasource.ts';

Schedule.Inject(Day, Week, WorkWeek, Month, Agenda);

let scheduleObj: Schedule = new Schedule({
    width: '100%',
    height: '550px',
    selectedDate: new Date(2018, 1, 15),
    eventSettings: { dataSource: scheduleData },
    eventRendered: (args: EventRenderedArgs) => {
    switch (args.data.EventType) {
        case 'Requested':
            (args.element as HTMLElement).style.backgroundColor = '#F57F17';
            break;
        case 'Confirmed':
            (args.element as HTMLElement).style.backgroundColor = '#7fa900';
            break;
        case 'New':
            (args.element as HTMLElement).style.backgroundColor = '#8e24aa';
            break;
    }
}
};
scheduleObj.appendTo('#Schedule');

function onChange(): void {
    let predicate: Predicate;
    let checkBoxes: CheckBox[] = [confirm, request, fresh];
    checkBoxes.forEach((checkBoxObj: CheckBox) => {
        if (checkBoxObj.checked) {
            if (predicate) {
                predicate = predicate.or('EventType', 'equal', checkBoxObj.label);
            } else {
                predicate = new Predicate('EventType', 'equal', checkBoxObj.label);
            }
        }
    });
    scheduleObj.eventSettings.query = new Query().where(predicate);
}

let confirm: CheckBox = new CheckBox({ label: 'Confirmed', checked: true, change: onChange }, '#confirmed');
let request: CheckBox = new CheckBox({ label: 'Requested', checked: true, change: onChange }, '#requested');
let fresh: CheckBox = new CheckBox({ label: 'New', checked: true, change: onChange }, '#new');
```

{% endtab %}

## Appointment selection

Appointment selection can be done either through mouse or keyboard actions. The selected events in UI will have a box shadow effect around to differentiate it from other appointments.

| Action | Description |
|-------|---------|
| Mouse click or Single tap on appointments | Selects single appointment. |
| Ctrl + [Mouse click] or [Single tap] on appointments | Selects multiple appointments.|

## Deleting multiple appointments

With the options available to select multiple appointments, it is also possible to delete the multiple selected appointments simply by pressing the `delete` key. In case of deleting multiple selected occurrences of an event series, only those occurrences will be deleted and not the entire series.

## Retrieve event details from the UI of an event

It is possible to access the information about the event fields of an appointment element displayed on the Scheduler UI. This can be achieved by passing an appointment element as argument to the public method `getEventDetails`.

In the following example, the subject of the appointment clicked has been displayed.

{% tab template="schedule/events-public", es5Template="get-event-details", iframeHeight="588px", sourceFiles="index.ts,index.html"%}

```typescript
import { Button } from '@syncfusion/ej2-buttons';
import { Schedule, Day, Week, WorkWeek, Month, Agenda, EventClickArgs } from '@syncfusion/ej2-schedule';
import { eventData } from './datasource.ts';

Schedule.Inject(Day, Week, WorkWeek, Month, Agenda);
let scheduleObj: Schedule = new Schedule({
    width: '100%',
    height: '550px',
    selectedDate: new Date(2018, 1, 15),
    eventSettings: { dataSource: eventData },
    eventClick: onEventClick
});
scheduleObj.appendTo('#Schedule');
let btn: Button = new Button();
btn.appendTo('#clear');
document.getElementById('clear').onclick = () => {
    document.getElementById('EventLog').innerHTML = '';
};
function onEventClick(args: EventClickArgs): void {
    let event: Object = scheduleObj.getEventDetails(args.element);
    appendElement(event.Subject +'<hr>');
}
function appendElement(html: string): void {
    let span: HTMLElement = document.createElement('span');
    span.innerHTML = html;
    let log: HTMLElement = document.getElementById('EventLog');
    log.insertBefore(span, log.firstChild);
}
```

{% endtab %}

## Get the current view appointments

To retrieve the appointments present in the current view of the Scheduler, you can make use of the `getCurrentViewEvents` public method. In the following example, the count of current view appointment collection rendered has been traced in `dataBound` event.

{% tab template="schedule/events-public", es5Template="current-view-events", iframeHeight="588px", sourceFiles="index.ts,index.html"%}

```typescript
import { Button } from '@syncfusion/ej2-buttons';
import { Schedule, Day, Week, WorkWeek, Month, Agenda } from '@syncfusion/ej2-schedule';
import { eventData } from './datasource.ts';

Schedule.Inject(Day, Week, WorkWeek, Month, Agenda);
    let scheduleObj: Schedule = new Schedule({
        width: '100%',
        height: '550px',
        selectedDate: new Date(2018, 1, 15),
        eventSettings: { dataSource: eventData },
        dataBound: onDataBound
    });
    scheduleObj.appendTo('#Schedule');
    let btn: Button = new Button();
    btn.appendTo('#clear');
    document.getElementById('clear').onclick = () => {
        document.getElementById('EventLog').innerHTML = '';
    };
    function onDataBound(): void {
        let event: Object[] = scheduleObj.getCurrentViewEvents();
        if (event.length > 0) {
           appendElement('Events present on current view <b>' + event.length +'<b><hr>');
        } else {
          appendElement('No Events available in this view.<hr>');
        }
    }
    function appendElement(html: string): void {
        let span: HTMLElement = document.createElement('span');
        span.innerHTML = html;
        let log: HTMLElement = document.getElementById('EventLog');
        log.insertBefore(span, log.firstChild);
    }
```

{% endtab %}

## Get the entire appointment collections

The entire collection of appointments rendered on the Scheduler can be accessed using the `getEvents` public method. In the following example, the count of entire appointment collection rendered on the Scheduler has been traced in `dataBound` event.

{% tab template="schedule/events-public", es5Template="get-events", iframeHeight="588px", sourceFiles="index.ts,index.html"%}

```typescript
import { Button } from '@syncfusion/ej2-buttons';
import { Schedule, Day, Week, WorkWeek, Month, Agenda } from '@syncfusion/ej2-schedule';
import { eventData } from './datasource.ts';

Schedule.Inject(Day, Week, WorkWeek, Month, Agenda);
let scheduleObj: Schedule = new Schedule({
    width: '100%',
    height: '550px',
    selectedDate: new Date(2018, 1, 15),
    eventSettings: { dataSource: eventData },
    dataBound: onDataBound
});
scheduleObj.appendTo('#Schedule');
let btn: Button = new Button();
btn.appendTo('#clear');
document.getElementById('clear').onclick = () => {
    document.getElementById('EventLog').innerHTML = '';
};
function onDataBound(): void {
    let event: Object[] = scheduleObj.getEvents();
    appendElement('Events present on scheduler <b>' + event.length +'<b><hr>');
}
function appendElement(html: string): void {
    let span: HTMLElement = document.createElement('span');
    span.innerHTML = html;
    let log: HTMLElement = document.getElementById('EventLog');
    log.insertBefore(span, log.firstChild);
}
```

{% endtab %}

## Refresh appointments

If your requirement is to simply refresh the appointments instead of refreshing the entire Scheduler elements from your application end, make use of the `refreshEvents` public method.

```typescript
scheduleObj.refreshEvents();
```
