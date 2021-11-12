---
title: "State Persistence in Scheduler"
component: "Scheduler"
description: "This section shows the way to maintain and retain the scheduler component states even after refreshing the page."
---

# Set state persistence

State persistence allowed Scheduler to retain the [`currentView`](../../api/schedule/currentview), [`selectedDate`](../../api/schedule/selecteddate) and Scroll position values in the [`localStorage`](https://www.w3schools.com/html/html5_webstorage.asp#) for state maintenance even if the browser is refreshed or if you move to the next page within the browser. This action is handled through the [`enablePersistence`](../../api/schedule/enablepersistence) property which is set to false by default. When it is set to true, `currentView`, `selectedDate` and Scroll position values of the scheduler component will be retained even after refreshing the page.

> **Note**: Scheduler `id` is essential to set state persistence.

The following sample demonstrates how to set state persistence of the Scheduler component.

{% tab template="schedule/row-auto-height", es5Template="persistence", iframeHeight="588px" , sourceFiles="index.ts,index.html"  %}

```typescript
import { Schedule, Day, Week, WorkWeek, Month } from '@syncfusion/ej2-schedule';
import { scheduleData } from './datasource.ts';

Schedule.Inject(Day, Week, WorkWeek, Month);

let scheduleObj: Schedule = new Schedule({
    width: '100%',
    height: '450px',
    selectedDate: new Date(2018, 1, 15),
    currentView: 'Month',
    enablePersistence: true,
    views: [ "Day", "Week", "WorkWeek", "Month"],
    eventSettings: { dataSource: scheduleData }
});
scheduleObj.appendTo('#Schedule');
```

{% endtab %}

> You can refer to our [JavaScript Scheduler](https://www.syncfusion.com/javascript-ui-controls/js-scheduler) feature tour page for its groundbreaking feature representations. You can also explore our [JavaScript Scheduler example](https://ej2.syncfusion.com/demos/#/material/schedule/overview.html) to knows how to present and manipulate data.
