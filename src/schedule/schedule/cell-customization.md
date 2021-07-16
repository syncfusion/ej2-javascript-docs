---
title: "Customizing Scheduler Cells"
component: "Scheduler"
description: "This topic demonstrates how to customize the cells of Scheduler using template option, methods and events available in Scheduler."
---

# Cell Customization

The cells of the Scheduler can be easily customized either using the cell template or `renderCell` event.

## Setting cell dimensions in all views

The height and width of the Scheduler cells can be customized either to increase or reduce its size through the `cssClass` property, which overrides the default CSS applied on cells.

{% tab template="schedule/cell-dimension", es5Template="cell-dimension-template", iframeHeight="588px",  sourceFiles="index.ts,index.html,index.css"  %}

```typescript
import { Schedule, Day, Week, WorkWeek, Month, ActionEventArgs } from '@syncfusion/ej2-schedule';
import { scheduleData } from './datasource.ts';

Schedule.Inject(Day, Week, WorkWeek, Month);
let scheduleObj: Schedule = new Schedule({
    height: '550px',
    width: '100%',
    views: ['Day', 'Week', 'WorkWeek', 'Month'],
    cssClass: 'schedule-cell-dimension',
    selectedDate: new Date(2018, 1, 15),
    eventSettings: { dataSource: scheduleData }
});
scheduleObj.appendTo('#Schedule');
```

{% endtab %}

## Check for cell availability

You can check whether the given time range slots are available for event creation or already occupied by other events using the `isSlotAvailable` method. In the following code example, if a specific time slot already contains an appointment, then no more appointments can be added to that cell.

{% tab template="schedule/cell-dimension", es5Template="is-slot-available", iframeHeight="588px",  sourceFiles="index.ts,index.html"  %}

```typescript
import { Schedule, Day, Week, WorkWeek, Month, ActionEventArgs, EventFieldsMapping } from '@syncfusion/ej2-schedule';
import { scheduleData } from './datasource.ts';

Schedule.Inject(Day, Week, WorkWeek, Month);
let scheduleObj: Schedule = new Schedule({
    height: '550px',
    selectedDate: new Date(2018, 1, 15),
    views: ['Day', 'Week', 'WorkWeek', 'Month'],
    actionBegin: (args: ActionEventArgs) => {
        if (args.requestType === 'eventCreate' && (<Object[]>args.data).length > 0) {
            let eventData: { [key: string]: Object } = args.data[0] as { [key: string]: Object };
            let eventField: EventFieldsMapping = scheduleObj.eventFields;
            let startDate: Date = eventData[eventField.startTime] as Date;
            let endDate: Date = eventData[eventField.endTime] as Date;
            args.cancel = !scheduleObj.isSlotAvailable(startDate, endDate);
        }
    },
    eventSettings: { dataSource: scheduleData }
});
scheduleObj.appendTo('#Schedule');
```

{% endtab %}

## Customizing cells in all the views

It is possible to customize the appearance of the cells using both template options and `renderCell` event on all the views.

### Using template

The `cellTemplate` option accepts the template string and is used to customize the cell background with specific images or appropriate text on the given date values.

{% tab template="schedule/cell-dimension", es5Template="cell-template", iframeHeight="588px",  sourceFiles="index.ts,index.html,index.css"  %}

```typescript
import { Schedule, Day, Week, Month, TimelineViews } from '@syncfusion/ej2-schedule';

Schedule.Inject(Day, Week, Month, TimelineViews);
(window as TemplateFunction).getMonthCellText = (date: Date) => {
    if (date.getMonth() === 10 && date.getDate() === 23) {
        return '<img src= "https://ej2.syncfusion.com/demos/src/schedule/images/birthday.svg" />';
    } else if (date.getMonth() === 11 && date.getDate() === 9) {
        return '<img src= "https://ej2.syncfusion.com/demos/src/schedule/images/get-together.svg" />';
    } else if (date.getMonth() === 11 && date.getDate() === 13) {
        return '<img src= "https://ej2.syncfusion.com/demos/src/schedule/images/birthday.svg" />';
    } else if (date.getMonth() === 11 && date.getDate() === 22) {
        return '<img src= "https://ej2.syncfusion.com/demos/src/schedule/images/thanksgiving-day.svg" />';
    } else if (date.getMonth() === 11 && date.getDate() === 24) {
        return '<img src="https://ej2.syncfusion.com/demos/src/schedule/images/christmas-eve.svg" />';
    } else if (date.getMonth() === 11 && date.getDate() === 25) {
        return '<img src= "https://ej2.syncfusion.com/demos/src/schedule/images/christmas.svg" />';
    } else if (date.getMonth() === 0 && date.getDate() === 1) {
        return '<img src= "https://ej2.syncfusion.com/demos/src/schedule/images/newyear.svg" />';
    } else if (date.getMonth() === 0 && date.getDate() === 14) {
        return '<img src= "https://ej2.syncfusion.com/demos/src/schedule/images/birthday.svg" />';
    }
    return '';
};
(window as TemplateFunction).getWorkCellText = (date: Date) => {
    let weekEnds: number[] = [0, 6];
    if (weekEnds.indexOf(date.getDay()) >= 0) {
        return "<img src='https://ej2.syncfusion.com/demos/src/schedule/images/newyear.svg' />";
    }
    return '';
};

interface TemplateFunction extends Window {
    getWorkCellText?: Function;
    getMonthCellText?: Function;
}
let scheduleObj: Schedule = new Schedule({
        width: '100%',
        height: '550px',
        views: ['Day','Week', 'TimelineWeek', 'Month'],
        cssClass: 'schedule-cell-template',
        cellTemplate: '${if(type === "workCells")}<div class="templatewrap">${getWorkCellText(data.date)}</div>${/if}${if(type === "monthCells")}<div class="templatewrap">${getMonthCellText(data.date)}</div>${/if}',
        selectedDate: new Date(2017, 11, 16)
});
scheduleObj.appendTo('#Schedule');
```

{% endtab %}

### Using renderCell event

An alternative to `cellTemplate` is the `renderCell` event, which can also be used to customize the cells with appropriate images or formatted text values.

{% tab template="schedule/cell-dimension", es5Template="render-cell", iframeHeight="588px",  sourceFiles="index.ts,index.html"  %}

```typescript
import { createElement } from '@syncfusion/ej2-base';
import { Schedule, Day, Week, Month, RenderCellEventArgs } from '@syncfusion/ej2-schedule';
import { scheduleData } from './datasource.ts';

Schedule.Inject(Day, Week, Month);
let scheduleObj: Schedule = new Schedule({
    height: '550px',
    selectedDate: new Date(2018, 1, 14),
    currentView: 'Month',
    views: ['Day','Week', 'Month'],
    renderCell: (args: RenderCellEventArgs) => {
        if (args.elementType == 'workCells' || args.elementType == 'monthCells') {
            let weekEnds: number[] = [0, 6];
            if (weekEnds.indexOf((args.date).getDay()) >= 0) {
                let ele: HtmlElement = createElement('div', {
                    innerHTML: "<img src='https://ej2.syncfusion.com/demos/src/schedule/images/newyear.svg' />",
                    className: 'templatewrap'
                });
                (args.element).appendChild(ele);
            }
        }
    },
    eventSettings: { dataSource: scheduleData }
});
scheduleObj.appendTo('#Schedule');
```

{% endtab %}

You can customize cells such as work cells, month cells, all-day cells, header cells, resource header cells using `renderCell` event by checking the `elementType` option within the event. You can check elementType with any of the following.

| Element type | Description |
|-------|---------|
| dateHeader | triggers on header cell rendering.|
| monthDay | triggers on header cell in month view rendering.|
| resourceHeader | triggers on resource header cell rendering.|
| alldayCells | triggers on all day cell rendering.|
| emptyCells | triggers on empty cell rendering on header bar.|
| resourceGroupCells | triggers on rendering of work cells for parent resource.|
| workCells | triggers on work cell rendering.|
| monthCells | triggers on month cell rendering.|
| majorSlot | triggers on major time slot cell rendering.|
| minorSlot | triggers on minor time slot cell rendering.|
| weekNumberCell | triggers on cell displaying week number.|

## Customizing cell header in month view

The month header of each date cell in the month view can be customized using the `cellHeaderTemplate` option which accepts the string or HTMLElement. The corresponding date can be accessed with the template.

{% tab template="schedule/cell-dimension", es5Template="cell-header-template", iframeHeight="588px",  sourceFiles="index.ts,index.html"  %}

```typescript
import { Internationalization } from "@syncfusion/ej2-base";
import { Schedule, Month } from '@syncfusion/ej2-schedule';

Schedule.Inject(Month);

let instance: Internationalization = new Internationalization();
(window as TemplateFunction).getDate = (date: Date) => {
  return instance.formatDate(date, { skeleton: "Ed" });
};
interface TemplateFunction extends Window {
    getDate?: Function;
}

let scheduleObj: Schedule = new Schedule({
        width: '100%',
        height: '550px',
        views: ['Month'],
        cssClass: 'schedule-cell-header-template',
        cellHeaderTemplate: '<div class="cell-header-wrap">${getDate(data.date)}</div>'
});
scheduleObj.appendTo('#Schedule');
```

{% endtab %}

## Customizing the minimum and maximum date values

Providing the `minDate` and `maxDate` property with some date values, allows the Scheduler to set the minimum and maximum date range. The Scheduler date that lies beyond this minimum and maximum date range will be in a disabled state so that the date navigation will be blocked beyond the specified date range.

{% tab template="schedule/cell-dimension", es5Template="min-max-date", iframeHeight="588px",  sourceFiles="index.ts,index.html"  %}

```typescript
import { Schedule, Day, Week, WorkWeek, Month, Agenda, Year } from '@syncfusion/ej2-schedule';
import { scheduleData } from './datasource.ts';

Schedule.Inject(Day, Week, WorkWeek, Month, Agenda, Year);
let scheduleObj: Schedule = new Schedule({
    width: '100%',
    height: '550px',
    views: ['Day','Week', 'Month', 'Agenda', 'Year'],
    selectedDate: new Date(2018, 1, 17),
    minDate:new Date(2017, 4, 17),
    maxDate:new Date(2018, 5, 17)
    eventSettings: { dataSource: scheduleData }
});
scheduleObj.appendTo('#Schedule');
```

{% endtab %}

>By default, the `minDate` property value is set to new Date(1900, 0, 1) and `maxDate` property value is set to new Date(2099, 11, 31). The user can also set the customized `minDate` and `maxDate` property values.

## How to disable multiple cell and row selection in Schedule

By default, the `allowMultiCellSelection` and `allowMultiRowSelection` properties of the Schedule are set to `true`. So, the Schedule allows user to select multiple cells and rows. If the user want to disable this multiple cell and row selection. The user can disable this feature by setting up `false` to these properties.

> You can refer to our [JavaScript Scheduler](https://www.syncfusion.com/javascript-ui-controls/js-scheduler) feature tour page for its groundbreaking feature representations. You can also explore our [JavaScript Scheduler example](https://ej2.syncfusion.com/demos/#/material/schedule/overview.html) to knows how to present and manipulate data.