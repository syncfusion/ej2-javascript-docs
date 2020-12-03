---
title: "JavaScript Scheduler - Getting Started"
component: "Scheduler"
description: "This article demonstrates how to create a simple Scheduler and configure its available features."
---

# Getting Started

This section briefly explains how to create the **Scheduler** component and configure its available functionalities in a JavaScript application.

## Dependencies

The following list of dependencies are required to use the Scheduler component in your application.

```javascript
|-- @syncfusion/ej2-schedule
    |-- @syncfusion/ej2-base
    |-- @syncfusion/ej2-buttons
    |-- @syncfusion/ej2-calendars
    |-- @syncfusion/ej2-data
    |-- @syncfusion/ej2-dropdowns
    |-- @syncfusion/ej2-excel-export
    |-- @syncfusion/ej2-inputs
    |-- @syncfusion/ej2-lists
    |-- @syncfusion/ej2-popups
    |-- @syncfusion/ej2-navigations
```

## Setup for local environment

Refer the following steps for setup your local environment.

**Step 1:** Create a root folder `myapp` for your application.

**Step 2:** Create `myapp/resources` folder to store local scripts and styles files.

**Step 3:** Create `myapp/index.js` and `myapp/index.html` files for initializing Essential JS 2 Scheduler control.

## Adding Syncfusion resources

The Essential JS 2 Scheduler control can be initialized by using either of the following ways.

* Using local scripts and styles.
* Using CDN links for scripts and styles.

### Using local scripts and styles

You can get the global scripts and styles from the [Essential Studio JavaScript (Essential JS 2)](https://www.syncfusion.com/downloads/essential-js2) build installed location.

After installing the Essential JS 2 product build, you can copy the Scheduler and its dependency scripts and style files into the `resources/scripts` and `resources/styles` folder respectively.

Refer the below location from where the Scheduler's script and styles can be referenced.

**Syntax:**

> Script: `**(installed location)**/Syncfusion/Essential Studio/{RELEASE_VERSION}/Essential JS 2/{PACKAGE_NAME}/dist/global/{PACKAGE_NAME}.min.js`
>
> Styles: `**(installed location)**/Syncfusion/Essential Studio/{RELEASE_VERSION}/Essential JS 2/{PACKAGE_NAME}/styles/material.css`

**Example:**

> Script: `C:/Program Files (x86)/Syncfusion/Essential Studio/15.4.30/Essential JS 2/ej2-schedule/dist/global/ej2-schedule.min.js`
>
> Styles: `C:/Program Files (x86)/Syncfusion/Essential Studio/15.4.30/Essential JS 2/ej2-schedule/styles/material.css`

After copying the files, you can refer the Scheduler's scripts and styles into the `index.html` file.
The below html code example shows the dependency of Scheduler.

```html

<!DOCTYPE html>
  <html xmlns="https://www.w3.org/1999/xhtml">
       <head>
            <title>Essential JS 2 Scheduler</title>
            <!-- Essential JS 2 Scheduler's dependent material theme -->
            <link href="resources/base/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="resources/buttons/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="resources/calendars/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="resources/dropdowns/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="resources/inputs/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="resources/splitbuttons/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="resources/lists/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="resources/popups/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="resources/navigations/styles/material.css" rel="stylesheet" type="text/css"/>
            <!-- Essential JS 2 Scheduler's material theme -->
            <link href="resources/schedule/styles/material.css" rel="stylesheet" type="text/css"/>

            <!-- Essential JS 2 Scheduler's dependent scripts -->
            <script src="resources/scripts/ej2-base.min.js" type="text/javascript"></script>
            <script src="resources/scripts/ej2-data.min.js" type="text/javascript"></script>
            <script src="resources/scripts/ej2-inputs.min.js" type="text/javascript"></script>
            <script src="resources/scripts/ej2-buttons.min.js" type="text/javascript"></script>
            <script src="resources/scripts/ej2-dropdowns.min.js" type="text/javascript"></script>
            <script src="resources/scripts/ej2-compression.min.js" type="text/javascript"></script>
            <script src="resources/scripts/ej2-file-utils.min.js" type="text/javascript"></script>
            <script src="resources/scripts/ej2-splitbuttons.min.js" type="text/javascript"></script>
            <script src="resources/scripts/ej2-lists.min.js" type="text/javascript"></script>
            <script src="resources/scripts/ej2-popups.min.js" type="text/javascript"></script>
            <script src="resources/scripts/ej2-navigations.min.js" type="text/javascript"></script>
            <script src="resources/scripts/ej2-calendars.min.js" type="text/javascript"></script>
            <script src="resources/scripts/ej2-excel-export.min.js" type="text/javascript"></script>
            <!-- Essential JS 2 Scheduler's global script -->
            <script src="resources/scripts/ej2-schedule.min.js" type="text/javascript"></script>
       </head>
       <body>
       </body>
  </html>

```

### Using CDN links for scripts and styles

Using CDN link, you can directly refer the Scheduler's script and styles into the `index.html` file.

Refer the Scheduler's CDN links as given below.

**Syntax:**

> Script: `https://cdn.syncfusion.com/ej2/{PACKAGE_NAME}/dist/global/{PACKAGE_NAME}.min.js`
>
> Styles: `https://cdn.syncfusion.com/ej2/{PACKAGE_NAME}/styles/material.css`

**Example:**

> Script: [`https://cdn.syncfusion.com/ej2/ej2-schedule/dist/global/ej2-schedule.min.js`](https://cdn.syncfusion.com/ej2/ej2-schedule/dist/global/ej2-schedule.min.js)
>
> Styles: [`https://cdn.syncfusion.com/ej2/ej2-schedule/styles/material.css`](https://cdn.syncfusion.com/ej2/ej2-schedule/styles/material.css)

The below html code example shows the dependency of Scheduler with `ej2-schedule.min.js`.

```html
<!DOCTYPE html>
  <html xmlns="https://www.w3.org/1999/xhtml">
       <head>
            <title>Essential JS 2 Scheduler</title>
            <!-- Essential JS 2 Scheduler's dependent material theme -->
            <link href="https://cdn.syncfusion.com/ej2/ej2-base/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="https://cdn.syncfusion.com/ej2/ej2-buttons/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="https://cdn.syncfusion.com/ej2/ej2-calendars/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="https://cdn.syncfusion.com/ej2/ej2-dropdowns/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="https://cdn.syncfusion.com/ej2/ej2-inputs/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="https://cdn.syncfusion.com/ej2/ej2-splitbuttons/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="https://cdn.syncfusion.com/ej2/ej2-lists/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="https://cdn.syncfusion.com/ej2/ej2-popups/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="https://cdn.syncfusion.com/ej2/ej2-navigations/styles/material.css" rel="stylesheet" type="text/css"/>
            <!-- Essential JS 2 Scheduler's material theme -->
            <link href="https://cdn.syncfusion.com/ej2/ej2-schedule/styles/material.css" rel="stylesheet" type="text/css"/>

            <!-- Essential JS 2 Scheduler's dependent script -->
            <script src="https://cdn.syncfusion.com/ej2/ej2-base/dist/global/ej2-base.min.js" type="text/javascript"></script>
            <script src="https://cdn.syncfusion.com/ej2/ej2-data/dist/global/ej2-data.min.js" type="text/javascript"></script>
            <script src="https://cdn.syncfusion.com/ej2/ej2-inputs/dist/global/ej2-inputs.min.js" type="text/javascript"></script>
            <script src="https://cdn.syncfusion.com/ej2/ej2-buttons/dist/global/ej2-buttons.min.js" type="text/javascript"></script>
            <script src="https://cdn.syncfusion.com/ej2/ej2-dropdowns/dist/global/ej2-dropdowns.min.js" type="text/javascript"></script>
            <script src="https://cdn.syncfusion.com/ej2/ej2-compression/dist/global/ej2-dropdowns.min.js" type="text/javascript"></script>
            <script src="https://cdn.syncfusion.com/ej2/ej2-file-utils/dist/global/ej2-dropdowns.min.js" type="text/javascript"></script>
            <script src="https://cdn.syncfusion.com/ej2/ej2-splitbuttons/dist/global/ej2-splitbuttons.min.js" type="text/javascript"></script>
            <script src="https://cdn.syncfusion.com/ej2/ej2-lists/dist/global/ej2-lists.min.js" type="text/javascript"></script>
            <script src="https://cdn.syncfusion.com/ej2/ej2-popups/dist/global/ej2-popups.min.js" type="text/javascript"></script>
            <script src="https://cdn.syncfusion.com/ej2/ej2-navigations/dist/global/ej2-navigations.min.js" type="text/javascript"></script>
            <script src="https://cdn.syncfusion.com/ej2/ej2-calendars/dist/global/ej2-calendars.min.js" type="text/javascript"></script>
            <script src="https://cdn.syncfusion.com/ej2/ej2-exel-export/dist/global/ej2-lists.min.js" type="text/javascript"></script>
            <!-- Essential JS 2 Scheduler's global script -->
            <script src="https://cdn.syncfusion.com/ej2/ej2-schedule/dist/global/ej2-schedule.min.js" type="text/javascript"></script>
       </head>
       <body>
           <!-- Add the HTML <div> element for scheduler  -->
             <div id="Schedule"></div>
             <script src="index.js" type="text/javascript"></script>
       </body>
  </html>

```

Place the following Scheduler code in the `index.js` file.

```javascript
ej.schedule.Schedule.Inject(ej.schedule.Day, ej.schedule.Week, ej.schedule.WorkWeek, ej.schedule.Month, ej.schedule.Agenda);
var scheduleObj = new ej.schedule.Schedule();
scheduleObj.appendTo('#Schedule');
```

## Initialize the Scheduler

Now, you can start adding Scheduler control in the application. For getting started, add a `div` element for Scheduler control in `index.html`. Then refer the `index.js` file into the `index.html` file.

In this document context we are going to use `ej2.min.js` which includes all the Essential JS 2 components and its dependent scripts.

```html
<!DOCTYPE html>
  <html xmlns="https://www.w3.org/1999/xhtml">
       <head>
            <title>Essential JS 2 Scheduler</title>
            <!-- Essential JS 2 Scheduler's dependent material theme -->
            <link href="https://cdn.syncfusion.com/ej2/ej2-base/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="https://cdn.syncfusion.com/ej2/ej2-buttons/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="https://cdn.syncfusion.com/ej2/ej2-calendars/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="https://cdn.syncfusion.com/ej2/ej2-dropdowns/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="https://cdn.syncfusion.com/ej2/ej2-inputs/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="https://cdn.syncfusion.com/ej2/ej2-splitbuttons/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="https://cdn.syncfusion.com/ej2/ej2-lists/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="https://cdn.syncfusion.com/ej2/ej2-popups/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="https://cdn.syncfusion.com/ej2/ej2-navigations/styles/material.css" rel="stylesheet" type="text/css"/>
            <!-- Essential JS 2 Scheduler's material theme -->
            <link href="https://cdn.syncfusion.com/ej2/ej2-schedule/styles/material.css" rel="stylesheet" type="text/css"/>

            <!-- Essential JS 2 all script -->
            <script src="https://cdn.syncfusion.com/ej2/dist/ej2.min.js" type="text/javascript"></script>
       </head>
       <body>
           <!-- Add the HTML <div> element for scheduler  -->
             <div id="Schedule"></div>
             <script src="index.js" type="text/javascript"></script>
       </body>
  </html>

```

Place the following Scheduler code in the `index.js` file.

```javascript
var scheduleObj = new ej.schedule.Schedule();
scheduleObj.appendTo('#Schedule');
```

## Populating appointments

To populate the empty Scheduler with appointments, define either the local JSON data or remote data through the `dataSource` property available within the `eventSettings` option. To define any appointments, start and end time fields are mandatory. In the following example, you can see the appointment defined with default fields such as Id, Subject, StartTime and EndTime.

```typescript
var scheduleObj = new ej.schedule.Schedule({
    height: '550px',
    selectedDate: new Date(2018, 1, 15),
    eventSettings: {
        dataSource: [{
            id: 1,
            subject: 'Meeting',
            startTime: new Date(2018, 1, 15, 10, 0),
            endTime: new Date(2018, 1, 15, 12, 30)
        }];
    }
});
scheduleObj.appendTo('#Schedule');
```

You can also provide different names to these default fields, for which the custom names of those fields must be mapped appropriately within `fields` property as shown below.

```typescript
var data = [{
    Id: 2,
    EventName: 'Meeting',
    StartTime: new Date(2018, 1, 15, 10, 0),
    EndTime: new Date(2018, 1, 15, 12, 30),
    IsAllDay: false,
    Status: 'Completed',
    Priority: 'High'
}];
var scheduleObj = new ej.schedule.Schedule({
    height: '550px',
    selectedDate: new Date(2018, 1, 15),
    eventSettings: {
        dataSource: data,
        fields: {
              id: 'Id',
              subject: { name: 'EventName' },
              isAllDay: { name: 'IsAllDay' },
              startTime: { name: 'StartTime' },
              endTime: { name: 'EndTime' },
            }
    }
});
scheduleObj.appendTo('#Schedule');
```

The other fields available in Scheduler can be referred from [here](./appointments#event-fields).

## Setting date

Scheduler usually displays the system date as its current date. To change the current date of Scheduler with specific date, define the `selectedDate` property.

```typescript
var scheduleObj = new ej.schedule.Schedule({
    height: '550px',
    selectedDate: new Date(2018, 1, 15)
    }
});
scheduleObj.appendTo('#Schedule');
```

## Setting view

Scheduler displays `Week` view by default. To change the current view, define the applicable view name to the `currentView` property. The applicable view names are,

* Day
* Week
* Workweek
* Month
* Year
* Agenda
* MonthAgenda
* TimelineDay
* TimelineWeek
* TimelineWorkWeek
* TimelineMonth
* TimelineYear

```typescript
var scheduleObj = new ej.schedule.Schedule({
    height: '550px',
    selectedDate: new Date(2018, 1, 15),
    currentView: 'Month'
});
scheduleObj.appendTo('#Schedule');
```

## Individual view customization

Each individual Scheduler views can be customized with its own options such as setting different start and end hour on Week and Work Week views, whereas hiding the weekend days on Month view alone.
This can be achieved by defining views property to accept the array of object type, where each object depicts the individual view customization.

Now, run the application in the browser using the following command.

```sh
npm start
```

The output will display the Scheduler with the specified view configuration.

{% tab template="schedule/views-model", es5Template="default-template", isDefaultActive=true, iframeHeight="588px", sourceFiles="index.ts,index.html"  %}

{% endtab %}
