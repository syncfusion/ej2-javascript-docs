---
title: "Scheduler Year view customization"
component: "Scheduler"
description: "This section explains how to customize the Year view using different properties in the scheduler"
---

# Half-yearly view

The year view of our scheduler displays all the 365 days and their related appointments of a particular year. You can customize the year view by using the following properties.

* [`firstMonthOfYear`](../api/schedule#firstmonthofyear)
* [`monthsCount`](../api/schedule#monthscount)
* [`monthHeaderTemplate`](../api/schedule#monthheadertemplate)

In the following code example, you can see how to render only the last six months of a year in the scheduler. To start with the month of  June, `firstMonthYear` is set to 6 and `monthsCount` is set to 6 to render only 6 months.

{% tab template="schedule/year-customizations", es5Template="year-customization", iframeHeight="616px", sourceFiles="index.ts,index.html" %}

```typescript

import { Schedule, Year, TimelineYear, DragAndDrop, Resize } from '@syncfusion/ej2-schedule';
import { Internationalization } from '@syncfusion/ej2-base';
import { resourceData } from './datasource.ts';

Schedule.Inject(Year, TimelineYear, DragAndDrop, Resize);

interface TemplateFunction extends Window {
    getMonthHeaderText?: Function;
}
let instance: Internationalization = new Internationalization();

(window as TemplateFunction).getMonthHeaderText = (instance: Date) => { return instance.toLocaleString("en-us", { month: "long" }) + " " + instance.getFullYear(); };

let scheduleObj: Schedule = new Schedule({
    width: '100%',
    height: '555px',
    selectedDate: new Date(2018, 7, 4),
    firstMonthOfYear: 6,
    monthsCount: 6,
    monthHeaderTemplate: '<div class="date-text">${getMonthHeaderText(data.date)}</div>',
    resourceHeaderTemplate: '#resourceTemplate',
    views: [
        { option: 'Year'},
        { option: 'TimelineYear', displayName: 'Horizontal Year', isSelected: true  },
        { option: 'TimelineYear', displayName: 'Vertical Year', orientation: 'Vertical' }
    ],
    group: {
        resources: ['Projects', 'Categories']
    },
    resources: [
        {
            field: 'ProjectId', title: 'Choose Project', name: 'Projects',
            dataSource: [
                { text: 'PROJECT 1', id: 1, color: '#cb6bb2' },
                { text: 'PROJECT 2', id: 2, color: '#56ca85' },
                { text: 'PROJECT 3', id: 3, color: '#df5286' }
            ],
            textField: 'text', idField: 'id', colorField: 'color'
        }, {
            field: 'TaskId', title: 'Category',
            name: 'Categories', allowMultiple: true,
            dataSource: [
                { text: 'Nancy', id: 1, groupId: 1, color: '#df5286' },
                { text: 'Steven', id: 2, groupId: 2, color: '#7fa900' },
                { text: 'Robert', id: 3, groupId: 3, color: '#ea7a57' },
                { text: 'Smith', id: 4, groupId: 1, color: '#5978ee' },
                { text: 'Micheal', id: 5, groupId: 2, color: '#df5286' },
                { text: 'Root', id: 6, groupId: 3, color: '#00bdae' }
            ],
            textField: 'text', idField: 'id', groupIDField: 'groupId', colorField: 'color'
        }
    ],
    eventSettings: { dataSource: resourceData }
});
scheduleObj.appendTo('#Schedule');

```

{% endtab %}