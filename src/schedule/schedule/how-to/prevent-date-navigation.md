# Prevent the Date Navigation

We can prevent navigation while clicking on the date header by simply removing `e-navigate` class from header cells which can be achieved in the `renderCell` event as shown in the following code example.

{% tab template="schedule/how-to", es5Template="navigation-prevent", iframeHeight="588px", sourceFiles="index.ts,index.html"  %}

```typescript
import { removeClass } from '@syncfusion/ej2-base';
import { Schedule, Day, Week, WorkWeek, Month, Agenda, RenderCellEventArgs } from '@syncfusion/ej2-schedule';
import { scheduleData } from './datasource.ts';

Schedule.Inject(Day, Week, WorkWeek, Month, Agenda);
let scheduleObj: Schedule = new Schedule({
    width: '100%',
    height: '500px',
    selectedDate: new Date(2018, 1, 15),
    currentView: 'WorkWeek',
    renderCell: (args: RenderCellEventArgs) => {
      if(args.elementType === "dateHeader" || args.elementType === "monthCells") {
        removeClass(args.element.childNodes, "e-navigate");
      }
    },
    eventSettings: {
        dataSource: scheduleData
    }
});
scheduleObj.appendTo('#Schedule');
```

{% endtab %}