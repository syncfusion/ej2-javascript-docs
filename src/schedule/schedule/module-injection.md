---
title: "Scheduler Module Injection"
component: "Scheduler"
description: "This section includes the list of modules available in Scheduler and also explains how to inject it in application to use specific functionalities."
---

# Feature Modules

The crucial step on creating a Scheduler with required views, is to import and inject the required modules. The modules that are available on Scheduler to work with its related functionalities are as follows.

* `Day` - Inject this module to work with day view.
* `Week` - Inject this module to work with week view.
* `WorkWeek` - Inject this module to work with work week view.
* `Month` - Inject this module to work with month view.
* `Agenda` - Inject this module to work with agenda view.
* `MonthAgenda` - Inject this module to work with month agenda view.
* `TimelineViews` - Inject this module to work with timeline day, timeline week, and timeline work week views.
* `TimelineMonth` - Inject this module to work with timeline month view.
* `DragAndDrop` - Inject this module to allow drag and drop of appointments on Scheduler.
* `Resize` - Inject this module for enabling the resize functionality of appointments on Scheduler.
* `ExcelExport` - Inject this module for exporting the Scheduler events data as excel file format.
* `ICalendarExport` - Inject this module for exporting the Scheduler events data to an ICS file.
* `ICalendarImport` - Inject this module for importing the Scheduler events data from an ICS file.

## Module injection

The required modules should be injected into the Scheduler using the `ej.schedule.Schedule.Inject` method of Scheduler within the `index.js` file as shown below. On doing so, only the injected module functionalities will be loaded and can be worked with Scheduler.

`[myapp/index.js]`

```typescript
ej.schedule.Schedule.Inject(ej.schedule.Day, ej.schedule.Week, ej.schedule.WorkWeek, ej.schedule.Month, ej.schedule.Agenda, ej.schedule.MonthAgenda);
```

**Note:** This module injection is not necessary in JavaScript.

> You can refer to our [JavaScript Scheduler](https://www.syncfusion.com/javascript-ui-controls/js-scheduler) feature tour page for its groundbreaking feature representations. You can also explore our [JavaScript Scheduler example](https://ej2.syncfusion.com/javascript/demos/#/material/schedule/overview.html) to knows how to present and manipulate data.