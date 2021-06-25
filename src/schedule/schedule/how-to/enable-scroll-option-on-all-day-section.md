---
title: "All-day scroller"
component: "Scheduler"
description: "This section explains how to enable scroller for all-day row in the scheduler"
---

# Enable scroll option on all-day section

When you have larger number of appointments in all-day row, it is difficult to view all the appointments properly. In that case you can enable scroller option for all-day row by setting true to `enableAllDayScroll` whereas its default value is false. When setting this property to true, individual scroller for all-day row is enabled when it reaches its maximum height on expanding.

> Note: This property is not applicable for Scheduler with height `auto`.

{% tab template="schedule/event", es5Template="all-day-scroll", iframeHeight="588px",  isDefaultActive= false, sourceFiles="index.ts,index.html"  %}

```typescript
import { Schedule, Day, Week, WorkWeek, Month, Agenda} from '@syncfusion/ej2-schedule';
import { generateObject } from './datasource.ts';

Schedule.Inject(Day, Week, WorkWeek, Month, Agenda);

let data: Object[] = generateObject();
let scheduleObj: Schedule = new Schedule({
    height: '550px',
    selectedDate: new Date(2021, 3, 28),
    enableAllDayScroll: true,
    eventSettings: { dataSource: data }
});
scheduleObj.appendTo('#Schedule');
```

{% endtab %}