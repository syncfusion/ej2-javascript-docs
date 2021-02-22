# Zoom in and Zoom out the Schedule using the mouse scrolling event

By default Scheduler component doesn’t have the Zoom in/out support. Using the `timeScale` and `headerRows` properties of our scheduler, we can achieve this.

Refer to the following code example.

{% tab template="schedule/zoom-in-out", es5Template="zoom-in-out", iframeHeight="616px", sourceFiles="index.ts,index.html"  %}

```typescript

import { Schedule, Week, Month, Agenda, TimelineViews, TimelineMonth, NavigatingEventArgs } from '@syncfusion/ej2-schedule';
import { scheduleData } from './datasource.ts';

Schedule.Inject(Month, Week, Agenda, TimelineViews, TimelineMonth);
let scheduleObj: Schedule = new Schedule({
  height: "600px",
  width: "100%",
  selectedDate: new Date(2020, 2, 12),
  currentView: "TimelineWeek",
  views: ["TimelineDay", "TimelineWeek", "TimelineMonth"],
  timeScale: {
    enable: true,
    interval: 60,
    slotCount: 2
  },
   navigating: (args: NavigatingEventArgs) => {
    if (args.currentView != "TimelineMonth") {
      scheduleObj.headerRows = [];
    }
  },
  eventSettings: { dataSource: scheduleData }
});
scheduleObj.appendTo('#Schedule');

window.addEventListener("wheel", event => {
  const delta = Math.sign(event.deltaY);
  if (scheduleObj.currentView === "TimelineMonth") {
    var len = scheduleObj.headerRows.length;
    if (delta < 0) {
      if (len == 0) {
        scheduleObj.setProperties({
          headerRows: [{ option: "Date" }]
        });
      } else if (len == 1) {
        scheduleObj.setProperties({
          headerRows: [{ option: "Week" }, { option: "Date" }]
        });
      } else if (len == 2) {
        scheduleObj.setProperties({
          headerRows: [
            { option: "Month" },
            { option: "Week" },
            { option: "Date" }
          ]
        });
      } else if (len == 3) {
        scheduleObj.setProperties({
          headerRows: [
            { option: "Year" },
            { option: "Month" },
            { option: "Week" },
            { option: "Date" }
          ]
        });
      }
    } else if (delta > 0) {
      if (len == 2) {
        scheduleObj.setProperties({
          headerRows: [{ option: "Date" }]
        });
      } else if (len == 3) {
        scheduleObj.setProperties({
          headerRows: [{ option: "Week" }, { option: "Date" }]
        });
      } else if (len == 4) {
        scheduleObj.setProperties({
          headerRows: [
            { option: "Month" },
            { option: "Week" },
            { option: "Date" }
          ]
        });
      } else if (len == 5) {
        scheduleObj.setProperties({
          headerRows: [
            { option: "Year" },
            { option: "Month" },
            { option: "Week" },
            { option: "Date" }
          ]
        });
      }
    }
  } else {
    if (delta > 0 && scheduleObj.timeScale.slotCount > 1) {
      scheduleObj.timeScale.slotCount -= 1;
    } else if (delta < 0 && scheduleObj.timeScale.slotCount <= 8) {
      scheduleObj.timeScale.slotCount += 1;
    }
  }
});
```

{% endtab %}