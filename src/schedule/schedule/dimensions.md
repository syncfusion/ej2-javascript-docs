---
title: "Height and Width of Scheduler"
component: "Scheduler"
description: "This article demonstrates how to set the height and width of Scheduler in pixels, percentage or auto values."
---

# Scheduler dimensions

The Scheduler dimensions refers to both height and width of the entire layout and it accepts 3 types of values.

* auto
* pixel
* percentage

## Auto Height and Width

When height and width of the Scheduler are set to `auto`, it will try as hard as possible to keep an element the same width as its parent container. In other words, the parent container that holds Scheduler, it's width/height will be the sum of its children. By default, Scheduler is assigned with `auto` values for both height and width properties.

{% tab template="schedule/dimension", es5Template="auto", iframeHeight="1875px" , sourceFiles="index.ts,index.html"  %}

```typescript
import { Schedule, Day, Week, WorkWeek, Month, Agenda } from '@syncfusion/ej2-schedule';
import { scheduleData } from './datasource.ts';

Schedule.Inject(Day, Week, WorkWeek, Month, Agenda);
let scheduleObj: Schedule = new Schedule({
    width:'auto', height: 'auto',
    selectedDate: new Date(2018, 1, 15),
    eventSettings: { dataSource: scheduleData }
});
scheduleObj.appendTo('#Schedule');
```

{% endtab %}

## Height and Width in pixel

The Scheduler height and width will be rendered exactly as per the given pixel values. It accepts both string and number values.

{% tab template="schedule/dimension", es5Template="pixel", iframeHeight="605px" , sourceFiles="index.ts,index.html"  %}

```typescript
import { Schedule, Day, Week, WorkWeek, Month, Agenda } from '@syncfusion/ej2-schedule';
import { scheduleData } from './datasource.ts';

Schedule.Inject(Day, Week, WorkWeek, Month, Agenda);
let scheduleObj: Schedule = new Schedule({
    width:'650px', height: '550px',
    selectedDate: new Date(2018, 1, 15),
    eventSettings: { dataSource: scheduleData }
});
scheduleObj.appendTo('#Schedule');
```

{% endtab %}

## Height and Width in percentage

When height and width of the Scheduler are given as percentage, it will make the Scheduler as wide as the parent container.

{% tab template="schedule/dimension", es5Template="percentage", iframeHeight="1875px" , sourceFiles="index.ts,index.html"  %}

```typescript
import { Schedule, Day, Week, WorkWeek, Month, Agenda } from '@syncfusion/ej2-schedule';
import { scheduleData } from './datasource.ts';

Schedule.Inject(Day, Week, WorkWeek, Month, Agenda);
let scheduleObj: Schedule = new Schedule({
    width:'100%', height: '100%',
    selectedDate: new Date(2018, 1, 15),
    eventSettings: { dataSource: scheduleData }
});
scheduleObj.appendTo('#Schedule');
```

{% endtab %}

> You can refer to our [JavaScript Scheduler](https://www.syncfusion.com/javascript-ui-controls/js-scheduler) feature tour page for its groundbreaking feature representations. You can also explore our [JavaScript Scheduler example](https://ej2.syncfusion.com/demos/#/material/schedule/overview.html) to knows how to present and manipulate data.

## See Also

* [How to Change Scheduler Cell Dimensions](./cell-customization/#setting-cell-dimensions-in-all-views)