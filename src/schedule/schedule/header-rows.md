---
title: "Timeline header rows in Scheduler"
component: "Scheduler"
description: "This section explains how to display the additional header rows on timeline view of Scheduler."
---

# Timeline header rows

The Timeline views can have additional header rows other than its default date and time header rows. It is possible to show individual header rows for displaying year, month and week separately using the `headerRows` property. This property is applicable only on the timeline views. The possible rows which can be added using `headerRows` property are as follows.

* `Year`
* `Month`
* `Week`
* `Date`
* `Hour`

> The `Hour` row is not applicable for Timeline month view.

The following example shows the Scheduler displaying all the available header rows on timeline views.

{% tab template="schedule/header-rows", es5Template="header-rows", iframeHeight="588px", sourceFiles="index.ts,index.html"  %}

```typescript
import { Schedule, TimelineViews } from '@syncfusion/ej2-schedule';
import { scheduleData } from './datasource.ts';

Schedule.Inject(TimelineViews);
let scheduleObj: Schedule = new Schedule({
    width: '100%', height: '550px',
    selectedDate: new Date(2018, 11, 31),
    startHour: '09:00',
    endHour: '13:00',
    headerRows: [
        { option: 'Year' },
        { option: 'Month' },
        { option: 'Week' },
        { option: 'Date' },
        { option: 'Hour' }
    ],
    views: ['TimelineWeek'],
    eventSettings: { dataSource: scheduleData }
});
scheduleObj.appendTo('#Schedule');
```

{% endtab %}

## Display year and month rows in timeline views

To display the timeline Scheduler simply with year and month names alone, define the option `Year` and `Month` within the `headerRows` property.

{% tab template="schedule/header-rows", es5Template="year-month", iframeHeight="588px", sourceFiles="index.ts,index.html"  %}

```typescript
import { Schedule, TimelineMonth } from '@syncfusion/ej2-schedule';
import { scheduleData } from './datasource.ts';

Schedule.Inject(TimelineMonth);
let scheduleObj: Schedule = new Schedule({
    width: '100%', height: '550px',
    selectedDate: new Date(2018, 11, 31),
    headerRows: [{ option: 'Year' }, { option: 'Month' }],
    currentView: 'TimelineMonth',
    views: [{ option: 'TimelineMonth', interval: 24 }],
    eventSettings: { dataSource: scheduleData }
});
scheduleObj.appendTo('#Schedule');
```

{% endtab %}

## Display week numbers in timeline views

The week number can be displayed in a separate header row of the timeline Scheduler by setting `Week` option within `headerRows` property.

{% tab template="schedule/header-rows", es5Template="week-number", iframeHeight="588px", sourceFiles="index.ts,index.html"  %}

```typescript
import { Schedule, TimelineViews,TimelineMonth } from '@syncfusion/ej2-schedule';
import { scheduleData } from './datasource.ts';

Schedule.Inject(TimelineViews, TimelineMonth);
let scheduleObj: Schedule = new Schedule({
    width: '100%', height: '550px',
    selectedDate: new Date(2018, 1, 15),
    headerRows: [{ option: 'Week' }, { option: 'Date' }, { option: 'Hour' }],
    currentView: 'TimelineMonth',
    views: [{ option: 'TimelineMonth', interval: 24 }, { option: 'TimelineWeek', interval: 3 }, { option: 'TimelineDay', interval: 4 }],
    eventSettings: { dataSource: scheduleData }
});
scheduleObj.appendTo('#Schedule');
```

{% endtab %}

## Timeline view displaying dates of a complete year

It is possible to display a complete year in a timeline view by setting `interval` value as 12 and defining **TimelineMonth** view option within the `views` property of Scheduler.

{% tab template="schedule/header-rows", es5Template="complete-year", iframeHeight="588px", sourceFiles="index.ts,index.html"  %}

```typescript
import { Schedule,TimelineMonth } from '@syncfusion/ej2-schedule';
import { eventData } from './datasource.ts';

Schedule.Inject(TimelineMonth);
let scheduleObj: Schedule = new Schedule({
    width: '100%', height: '550px',
    selectedDate: new Date(2018, 0, 1),
    headerRows: [{ option: 'Month' }, { option: 'Date' }],
    views: [{ option: 'TimelineMonth', interval: 12 }],
    eventSettings: { dataSource: eventData }
});
scheduleObj.appendTo('#Schedule');
```

{% endtab %}

## Customizing the header rows using template

You can customize the text of the header rows and display any images or formatted text on each individual header rows using the built-in `template` option available within the `headerRows` property.

{% tab template="schedule/header-rows", es5Template="header-row-template", iframeHeight="588px", sourceFiles="index.ts,index.html"  %}

```typescript
import { Schedule, TimelineMonth, CellTemplateArgs, getWeekNumber } from '@syncfusion/ej2-schedule';
import { Internationalization } from '@syncfusion/ej2-base';
import { eventData } from './datasource.ts';

Schedule.Inject(TimelineMonth);

interface TemplateFunction extends Window {
    getYearDetails?: Function;
    getMonthDetails?: Function;
    getWeekDetails?: Function;
}
let instance: Internationalization = new Internationalization();
(window as TemplateFunction).getYearDetails = (value: CellTemplateArgs) => {
    return 'Year: ' + instance.formatDate((value as CellTemplateArgs).date, { skeleton: 'y' });
};
(window as TemplateFunction).getMonthDetails = (value: CellTemplateArgs) => {
    return 'Month: '+ instance.formatDate((value as CellTemplateArgs).date, { skeleton: 'M' });
};
(window as TemplateFunction).getWeekDetails = (value: CellTemplateArgs) => {
    return 'Week ' + getWeekNumber((value as CellTemplateArgs).date);
};
let scheduleObj: Schedule = new Schedule({
    width: '100%',
    height: '550px',
    selectedDate: new Date(2018, 0, 1),
    headerRows: [
        { option: 'Year', template: '#year-template' },
        { option: 'Month', template: '#month-template' },
        { option: 'Week', template: '#week-template' },
        { option: 'Date' }
    ],
    views: [{ option: 'TimelineMonth' }],
    eventSettings: { dataSource: eventData }
};
scheduleObj.appendTo('#Schedule');
```

{% endtab %}

> You can refer to our [JavaScript Scheduler](https://www.syncfusion.com/javascript-ui-controls/js-scheduler) feature tour page for its groundbreaking feature representations. You can also explore our [JavaScript Scheduler example](https://ej2.syncfusion.com/demos/#/material/schedule/overview.html) to knows how to present and manipulate data.
