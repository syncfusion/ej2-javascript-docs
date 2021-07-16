---
title: "Scheduler Header customization"
component: "Scheduler"
description: "This section explains how to customize the header bar of Scheduler and to add custom items into it."
---

# Header customization

The header part of Scheduler can be customized easily with the built-in options available.

## Show or Hide header bar

By default, the header bar holds the date and view navigation options, through which the user can switch between the dates and various views. This header bar can be hidden from the UI by setting `false` to the `showHeaderBar` property. It's default value is `true`.

{% tab template="schedule/header-bar", es5Template="header-bar-disable", iframeHeight="588px" , sourceFiles="index.ts,index.html"  %}

```typescript
import { Schedule, Day, Week, WorkWeek } from '@syncfusion/ej2-schedule';
import { scheduleData } from './datasource.ts';

Schedule.Inject(Day, Week, WorkWeek);
let scheduleObj: Schedule = new Schedule({
    width: '100%',
    height: '550px',
    selectedDate: new Date(2018, 1, 15),
    views: ['Day', 'Week', 'WorkWeek'],
    showHeaderBar: false,
    eventSettings: { dataSource: scheduleData }
});
scheduleObj.appendTo('#Schedule');
```

{% endtab %}

## Customizing header bar

Apart from the default date navigation and view options available on the header bar, you can add custom items into the Scheduler header bar by making use of the `actionBegin` event. Here, an employee image is added to the header bar, clicking on which will open the popup showing that person's short profile information.

{% tab template="schedule/header-bar", es5Template="header-bar-custom", iframeHeight="588px" , sourceFiles="index.ts,index.html,index.css"  %}

```typescript
import { createElement, compile } from '@syncfusion/ej2-base';
import { Popup } from '@syncfusion/ej2-popups';
import { ItemModel } from '@syncfusion/ej2-navigations';
import { Schedule, Month, ActionEventArgs, ToolbarActionArgs } from '@syncfusion/ej2-schedule';
import { scheduleData } from './datasource.ts';

Schedule.Inject(Month);
let scheduleObj: Schedule = new Schedule({
    width: '100%',
    height: '550px',
    selectedDate: new Date(2018, 1, 15),
    views: ['Month'],
    currentView: 'Month',
    actionBegin: (args: ActionEventArgs & ToolbarActionArgs) => {
        if (args.requestType === 'toolbarItemRendering') {
            let userIconItem: ItemModel = {
                align: 'Right', prefixIcon: 'user-icon', text: 'Nancy', cssClass: 'e-schedule-user-icon'
            };
            args.items.push(userIconItem);
        }
    },
    actionComplete: (args: ActionEventArgs) => {
        if (args.requestType === 'toolBarItemRendered') {
            let userIconEle: HTMLElement = scheduleObj.element.querySelector('.e-schedule-user-icon') as HTMLElement;
            userIconEle.onclick = () => {
                profilePopup.relateTo = userIconEle;
                profilePopup.dataBind();
                if (profilePopup.element.classList.contains('e-popup-close')) {
                    profilePopup.show();
                } else {
                    profilePopup.hide();
                }
            };
        }
    }
    eventSettings: { dataSource: scheduleData }
});
scheduleObj.appendTo('#Schedule');

let userContentEle: HTMLElement = createElement('div', {
        className: 'e-profile-wrapper'
    });
    scheduleObj.element.parentElement.appendChild(userContentEle);

    let userIconEle: HTMLElement = scheduleObj.element.querySelector('.e-schedule-user-icon') as HTMLElement;
    let getDOMString: (data: object) => HTMLCollection = compile('<div class="profile-container"><div class="profile-image">' +
        '</div><div class="content-wrap"><div class="name">Nancy</div>' +
        '<div class="destination">Product Manager</div><div class="status">' +
        '<div class="status-icon"></div>Online</div></div></div>');
    let output: HTMLCollection = getDOMString({});
    let profilePopup: Popup = new Popup(userContentEle, {
        content: output[0] as HTMLElement,
        relateTo: userIconEle,
        position: { X: 'left', Y: 'bottom' },
        collision: { X: 'flip', Y: 'flip' },
        targetType: 'relative',
        viewPortElement: scheduleObj.element,
        width: 185,
        height: 80
    });
    profilePopup.hide();
```

{% endtab %}

## How to display the view options within the header bar popup

By default, the header bar holds the view navigation options, through which the user can switch between various views. You can move this view options to the header bar popup by setting `true` to the `enableAdaptiveUI` property.

{% tab template="schedule/header-bar", es5Template="header-bar-popup", iframeHeight="588px" , sourceFiles="index.ts,index.html"  %}

```typescript
import { Schedule, Day, Week, WorkWeek, Month, Agenda} from '@syncfusion/ej2-schedule';
import { scheduleData } from './datasource.ts';

Schedule.Inject(Day, Week, WorkWeek, Month, Agenda);

let scheduleObj: Schedule = new Schedule({
    width: '100%',
    height: '550px',
    selectedDate: new Date(2018, 1, 15),
    enableAdaptiveUI: true,
    eventSettings: { dataSource: scheduleData }
});
scheduleObj.appendTo('#Schedule');
```

{% endtab %}

> Refer [here](./resources/#adaptive-ui-in-desktop) to know more about adaptive UI in resources scheduler.

## Date header customization

The Scheduler UI that displays the date text on all views are considered as the date header cells. You can customize the date header cells of Scheduler either using `dateHeaderTemplate` or `renderCell` event.

### Using date header template

The `dateHeaderTemplate` option is used to customize the date header cells of day, week and work-week views.

{% tab template="schedule/date-header", es5Template="header-bar-template", iframeHeight="588px", sourceFiles="index.ts,index.html,index.css"  %}

```typescript
import { Schedule, Day, Week, Agenda, TimelineViews, TimelineMonth } from '@syncfusion/ej2-schedule';
import { scheduleData } from './datasource.ts';
import { Internationalization } from '@syncfusion/ej2-base';

Schedule.Inject(Day, Week, Agenda, TimelineViews, TimelineMonth);
let instance: Internationalization = new Internationalization();
(window as TemplateFunction).getDateHeaderText = (value: Date) => {
    return instance.formatDate(value, { skeleton: 'Ed' });
};
let getWeather: Function = (value: Date) => {
    switch (value.getDay()) {
        case 0:
            return '<div class="weather-text">25°C</div>';
        case 1:
            return '<div class="weather-text">18°C</div>';
        case 2:
            return '<div class="weather-text">10°C</div>';
        case 3:
            return '<div class="weather-text">16°C</div>';
        case 4:
            return '<div class="weather-text">8°C</div>';
        case 5:
            return '<div class="weather-text">27°C</div>';
        case 6:
            return '<div class="weather-text">17°C</div>';
        default:
            return null;
    }
};
(window as TemplateFunction).getWeather = getWeather;
interface TemplateFunction extends Window {
    getDateHeaderText?: Function;
    getWeather?: Function;
}
let scheduleObj: Schedule = new Schedule({
    width: '100%',
    height: '550px',
    selectedDate: new Date(2018, 1, 15),
    dateHeaderTemplate: '<div class="date-text">${getDateHeaderText(data.date)}</div>${getWeather(data.date)}',
    views: ['Day', 'Week', 'Agenda', 'TimelineWorkWeek', 'TimelineMonth'],
    selectedDate: new Date(2018, 1, 15),
    cssClass: 'schedule-date-header-template',
    eventSettings: { dataSource: scheduleData }
});
scheduleObj.appendTo('#Schedule');
```

{% endtab %}

### Using renderCell event

In month view, the date header template is not applicable and therefore the same customization can be added beside the date text in month cells by making use of the `renderCell` event.

{% tab template="schedule/render-cell", es5Template="render-cell", iframeHeight="588px" , sourceFiles="index.ts,index.html,index.css"  %}

```typescript
import { Schedule, Month, RenderCellEventArgs } from '@syncfusion/ej2-schedule';
import { scheduleData } from './datasource.ts';

Schedule.Inject(Month);
let getWeather: Function = (value: Date) => {
    switch (value.getDay()) {
        case 0:
            return '<div class="weather-text">25°C</div>';
        case 1:
            return '<div class="weather-text">18°C</div>';
        case 2:
            return '<div class="weather-text">10°C</div>';
        case 3:
            return '<div class="weather-text">16°C</div>';
        case 4:
            return '<div class="weather-text">8°C</div>';
        case 5:
            return '<div class="weather-text">27°C</div>';
        case 6:
            return '<div class="weather-text">17°C</div>';
        default:
            return null;
    }
};
let scheduleObj: Schedule = new Schedule({
    width: '100%',
    height: '550px',
    selectedDate: new Date(2018, 1, 15),
    views: ['Month'],
    renderCell: (args: RenderCellEventArgs) => {
        if (args.elementType === 'monthCells') {
            let ele: Element = document.createElement('div');
            ele.innerHTML = getWeather(args.date);
            (args.element).appendChild(ele.firstChild);
        }
    },
    eventSettings: { dataSource: scheduleData }
});
scheduleObj.appendTo('#Schedule');
```

{% endtab %}

> You can refer to our [JavaScript Scheduler](https://www.syncfusion.com/javascript-ui-controls/js-scheduler) feature tour page for its groundbreaking feature representations. You can also explore our [JavaScript Scheduler example](https://ej2.syncfusion.com/demos/#/material/schedule/overview.html) to knows how to present and manipulate data.