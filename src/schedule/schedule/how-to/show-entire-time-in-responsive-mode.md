# Show entire time in responsive mode when start hour is set

9 AM is visible since it has enough space in responsive mode, but if you set 08:45 AM as start hour of scheduler then the time slots will not show full time in the time slot of responsive scheduler, for which we can use `majorSlotTemplate` to set proper time slots in scheduler.

{% tab template="schedule/timescale", es5Template="timescale-template", iframeHeight="588px", sourceFiles="index.ts,index.html"  %}

```typescript
import { Schedule, Day, Week, WorkWeek } from "@syncfusion/ej2-schedule";
import { Internationalization } from "@syncfusion/ej2-base";
import { scheduleData } from './datasource.ts';

Schedule.Inject(Day, Week, WorkWeek);
let instance: Internationalization = new Internationalization();
(window as TemplateFunction).majorSlotTemplate = (date: Date) => {
  return instance.formatDate(date, { skeleton: "hm" });
};
interface TemplateFunction extends Window {
  majorSlotTemplate?: Function;
}
let scheduleObj: Schedule = new Schedule({
  width: "100%",
  height: "550px",
  selectedDate: new Date(2018, 1, 15),
  startHour: "08:45",
  views: ["Day", "Week", "WorkWeek"],
  timeScale: {
    majorSlotTemplate: "#majorSlotTemplate"
  },
  eventSettings: { dataSource: scheduleData }
});
scheduleObj.appendTo("#Schedule");
```

{% endtab %}