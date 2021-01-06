---
title: "Editor Window and Quick Popup of Scheduler"
component: "Scheduler"
description: "This topic demonstrates how to customize the default event editor and quick pop-up using templates and also explains how to design the custom modal popup."
---

# Editor window and quick popups

Scheduler makes use of popups and dialog to display the required notifications, as well as includes an editor window with event fields for making the appointment creation and editing process easier. You can also easily customize the editor window and the fields present in it, and can also apply validations on those fields.

## Event editor

The editor window usually opens on the Scheduler, when a cell or event is double clicked. When a cell is double clicked, the detailed editor window opens in "Add new" mode, whereas when an event is double clicked, the same is opened in an "Edit" mode.

In mobile devices, you can open the detailed editor window in edit mode by clicking the edit icon on the popup, that opens on single tapping an event. You can also open it in add mode by single tapping a cell, which will display a `+` indication, clicking on it again will open the editor window.

> You can also prevent the editor window from opening, by rendering Scheduler in a `readonly` mode or by doing code customization within the `popupOpen` event.

### How to change the editor window header title and text of footer buttons

You can change the header title and the text of buttons displayed at the footer of the editor window by changing the appropriate localized word collection used in the Scheduler.

{% tab template="schedule/editor-window", es5Template="local-word", iframeHeight="588px"  sourceFiles="index.ts,index.html"  %}

```typescript
import { L10n } from '@syncfusion/ej2-base';
import { Schedule, Day, Week, TimelineViews, Month, Agenda } from '@syncfusion/ej2-schedule';
import { scheduleData } from './datasource.ts';

Schedule.Inject(Day, Week, TimelineViews, Month, Agenda);
L10n.load({
    'en-US': {
        'schedule': {
            'saveButton': 'Add',
            'cancelButton': 'Close',
            'deleteButton': 'Remove',
            'newEvent': 'Add Event',
        },
    }
});
let scheduleObj: Schedule = new Schedule({
    width: '100%',
    height: '550px',
    selectedDate: new Date(2018, 1, 15),
    views: ['TimelineDay', 'Day', 'Week', 'Month', 'Agenda'],
    eventSettings: { dataSource: scheduleData }
});
scheduleObj.appendTo('#Schedule');
```

{% endtab %}

### How to change the label text of default editor fields

To change the default labels such as Subject, Location and other field names in the editor window, make use of the `title` property available within the field option of `eventSettings`.

{% tab template="schedule/editor-window", es5Template="field-label", iframeHeight="588px"  sourceFiles="index.ts,index.html"  %}

```typescript
import { Schedule, Day, Week, TimelineViews, Month, Agenda } from '@syncfusion/ej2-schedule';
import { scheduleData } from './datasource.ts';

Schedule.Inject(Day, Week, TimelineViews, Month, Agenda);
let scheduleObj: Schedule = new Schedule({
    width: '100%',
    height: '550px',
    selectedDate: new Date(2018, 1, 15),
    views: ['Day', 'Week', 'TimelineWeek', 'Month', 'Agenda'],
    eventSettings: {
        dataSource: scheduleData,
        fields: {
            id: 'Id',
            subject: { name: 'Subject', title: 'Event Name' },
            location: { name: 'Location', title: 'Event Location'},
            description: { name: 'Description', title: 'Event Description' },
            startTime: { name: 'StartTime', title: 'Start Duration' },
            endTime: { name: 'EndTime', title: 'End Duration'  }
        }
    }
});
scheduleObj.appendTo('#Schedule');
```

{% endtab %}

### Field validation

It is possible to validate the required fields of the editor window from client-side before submitting it, by adding appropriate validation rules to each field. The appointment fields have been extended to accept both `string` and `object` type values. To perform validations, it is necessary to specify object values for the event fields.

{% tab template="schedule/editor-window", es5Template="field-validation", iframeHeight="588px"  sourceFiles="index.ts,index.html"  %}

```typescript
import { Schedule, Day, Week, WorkWeek, Month, Agenda } from '@syncfusion/ej2-schedule';
import { scheduleData } from './datasource.ts';

Schedule.Inject(Day, Week, WorkWeek, Month, Agenda);
let minValidation: (args: { [key: string]: string }) => boolean = (args: { [key: string]: string }) => {
    return args['value'].length >= 5;
};
let scheduleObj: Schedule = new Schedule({
    width: '100%',
    height: '500px',
    selectedDate: new Date(2018, 1, 15),
    eventSettings: {
        dataSource: scheduleData,
        fields: {
            id: 'Id',
            subject: { name: 'Subject', validation: { required: true } },
            location: { name: 'Location', validation: { required: true } },
            description: {
                name: 'Description', validation: {
                    required: true, minLength: [minValidation, 'Need atleast 5 letters to be entered']
                }
            },
            startTime: { name: 'StartTime', validation: { required: true } },
            endTime: { name: 'EndTime', validation: { required: true } }
        }
    }
});
scheduleObj.appendTo('#Schedule');
```

{% endtab %}

> Applicable validation rules can be referred from [form validation](http://ej2.syncfusion.com/documentation/form-validator/#validation-rules) documentation.

### Add additional fields to the default editor

The additional fields can be added to the default event editor by making use of the `popupOpen` event which gets triggered before the event editor opens on the Scheduler. The `popupOpen` is a client-side event that triggers before any of the generic popups opens on the Scheduler. The additional field (any of the form elements) should be added with a common class name `e-field`, so as to handle and process those additional data along with the default event object. In the following example, an additional field `Event Type` has been added to the default event editor and its value is processed accordingly.

{% tab template="schedule/editor-window", es5Template="additional-field", iframeHeight="588px"  sourceFiles="index.ts,index.html"  %}

```typescript
import { DropDownList } from '@syncfusion/ej2-dropdowns';
import { createElement } from '@syncfusion/ej2-base';
import { Schedule, Day, Week, WorkWeek, Month, PopupOpenEventArgs } from '@syncfusion/ej2-schedule';
import { scheduleData } from './datasource.ts';

Schedule.Inject(Day, Week, WorkWeek);
let scheduleObj: Schedule = new Schedule({
    width: '100%',
    height: '550px',
    selectedDate: new Date(2018, 1, 15),
    views: ['Day', 'Week', 'WorkWeek', 'Month'],
    popupOpen: (args: PopupOpenEventArgs) => {
        if (args.type === 'Editor') {
            // Create required custom elements in initial time
          if (!args.element.querySelector('.custom-field-row')) {
              let row: HTMLElement = createElement('div', { className: 'custom-field-row' });
              let formElement: HTMLElement = args.element.querySelector('.e-schedule-form');
              formElement.firstChild.insertBefore(row, args.element.querySelector('.e-title-location-row'));
              let container: HTMLElement = createElement('div', { className: 'custom-field-container' });
              let inputEle: HTMLInputElement = createElement('input', {
                  className: 'e-field', attrs: { name: 'EventType' }
              }) as HTMLInputElement;
              container.appendChild(inputEle);
              row.appendChild(container);
              let dropDownList: DropDownList = new DropDownList({
                  dataSource: [
                    { text: 'Public Event', value: 'public-event' },
                    { text: 'Maintenance', value: 'maintenance' },
                    { text: 'Commercial Event', value: 'commercial-event' },
                    { text: 'Family Event', value: 'family-event' }
                  ],
                    fields: { text: 'text', value: 'value' },
                    value: (<{ [key: string]: Object }>(args.data)).EventType as string,
                    floatLabelType: 'Always', placeholder: 'Event Type'
              });
              dropDownList.appendTo(inputEle);
              inputEle.setAttribute('name', 'EventType');
        }
      }
    },
    eventSettings: { dataSource: scheduleData }
});
scheduleObj.appendTo('#Schedule');
```

{% endtab %}

### Customizing the default time duration in editor window

In default event editor window, start and end time duration are processed based on the `interval` value set within the `timeScale` property. By default, `interval` value is set to 30, and therefore the start/end time duration within the event editor will be in a 30 minutes time difference. You can change this duration value by changing the `duration` option within the `popupOpen` event as shown in the following code example.

{% tab template="schedule/editor-window", es5Template="duration", iframeHeight="588px"  sourceFiles="index.ts,index.html"  %}

```typescript
import { Schedule, Day, Week, WorkWeek, Month, PopupOpenEventArgs } from '@syncfusion/ej2-schedule';
import { scheduleData } from './datasource.ts';

Schedule.Inject(Day, Week, WorkWeek);
let scheduleObj: Schedule = new Schedule({
    width: '100%',
    height: '550px',
    selectedDate: new Date(2018, 1, 15),
    views: ['Day', 'Week', 'WorkWeek', 'Month'],
    popupOpen: (args: PopupOpenEventArgs) => {
        if (args.type === 'Editor') {
          args.duration = 60;
        }
    },
    eventSettings: { dataSource: scheduleData }
});
scheduleObj.appendTo('#Schedule');
```

{% endtab %}

### How to prevent the display of editor and quick popups

It is possible to prevent the display of editor and quick popup windows by passing the value `true` to `cancel` option within the `popupOpen` event.

{% tab template="schedule/editor-window", es5Template="prevention", iframeHeight="588px"  sourceFiles="index.ts,index.html"  %}

```typescript
import { Schedule, Day, Week, WorkWeek, Month, PopupOpenEventArgs } from '@syncfusion/ej2-schedule';
import { scheduleData } from './datasource.ts';

Schedule.Inject(Day, Week, WorkWeek);
let scheduleObj: Schedule = new Schedule({
    width: '100%',
    height: '550px',
    selectedDate: new Date(2018, 1, 15),
    views: ['Day', 'Week', 'WorkWeek', 'Month'],
    popupOpen: (args: PopupOpenEventArgs) => {
        args.cancel = true;
    },
    eventSettings: { dataSource: scheduleData }
});
scheduleObj.appendTo('#Schedule');
```

{% endtab %}

In case, if you need to prevent only specific popups on Scheduler, then you can check the condition based on the popup type. The types of the popup that can be checked within the `popupOpen` event are as follows.

| Type | Description |
|------|-------------|
| Editor | For Detailed editor window.|
| QuickInfo | For Quick popup which opens on cell click.|
| EditEventInfo |For  Quick popup which opens on event click.|
| ViewEventInfo | For Quick popup which opens on responsive mode.|
| EventContainer | For more event indicator popup.|
| RecurrenceAlert | For edit recurrence event alert popup.|
| DeleteAlert | For delete confirmation popup.|
| ValidationAlert | For validation alert popup.|
| RecurrenceValidationAlert | For recurrence validation alert popup.|

## Customizing event editor using template

The event editor window can be customized by making use of the `editorTemplate` option. Here, the custom window design is built with the required fields using the script template and its type should be of **text/x-template**.

Each field defined within template should contain the **e-field** class, so as to allow the processing of those field values internally. The ID of this customized script template section is assigned to the `editorTemplate` option, so that these customized fields will be replaced onto the default editor window.

As we are using our Syncfusion sub-components within our editor using template in the following example, the custom defined form elements needs to be configured as required Syncfusion components such as **DropDownList** and **DateTimePicker** within the `popupOpen` event. This particular step can be skipped, if the user needs to simply use the usual form elements.

{% tab template="schedule/editor", es5Template="editor-template", iframeHeight="588px"  sourceFiles="index.ts,index.html"  %}

```typescript
import { DateTimePicker } from '@syncfusion/ej2-calendars';
import { DropDownList } from '@syncfusion/ej2-dropdowns';
import { Schedule, Day, Week, WorkWeek, Month, Agenda, PopupOpenEventArgs } from '@syncfusion/ej2-schedule';
import { eventData } from './datasource.ts';

Schedule.Inject(Day, Week, WorkWeek, Month, Agenda);
let scheduleObj: Schedule = new Schedule({
    width: '100%',
    height: '550px',
    selectedDate: new Date(2018, 1, 15),
    showQuickInfo: false,
    editorTemplate: '#EventEditorTemplate',
        popupOpen: (args: PopupOpenEventArgs) => {
            if (args.type === 'Editor') {
                let statusElement: HTMLInputElement = args.element.querySelector('#EventType') as HTMLInputElement;
                if (!statusElement.classList.contains('e-dropdownlist')) {
                    let dropDownListObject: DropDownList = new DropDownList({
                        placeholder: 'Choose status', value: statusElement.value,
                        dataSource: ['New', 'Requested', 'Confirmed']
                    });
                    dropDownListObject.appendTo(statusElement);
                }
                let startElement: HTMLInputElement = args.element.querySelector('#StartTime') as HTMLInputElement;
                if (!startElement.classList.contains('e-datetimepicker')) {
                    new DateTimePicker({ value: new Date(startElement.value) || new Date() }, startElement);
                }
                let endElement: HTMLInputElement = args.element.querySelector('#EndTime') as HTMLInputElement;
                if (!endElement.classList.contains('e-datetimepicker')) {
                    new DateTimePicker({ value: new Date(endElement.value) || new Date() }, endElement);
                }
            }
        },
    eventSettings: { dataSource: eventData }
});
scheduleObj.appendTo('#Schedule');
```

{% endtab %}

### How to add resource options within editor template

The resource field can be added within editor template with multiselect control for allow multiple resources.

{% tab template="schedule/resource-field", es5Template="editor-resource", iframeHeight="588px"  sourceFiles="index.ts,index.html"  %}

```typescript
import { DateTimePicker } from '@syncfusion/ej2-calendars';
import { MultiSelect } from '@syncfusion/ej2-dropdowns';
import { Schedule, Day, Week, WorkWeek, Month, PopupOpenEventArgs } from '@syncfusion/ej2-schedule';
import { eventData, ownerData } from './datasource.ts';

Schedule.Inject(Day, Week, WorkWeek);
let scheduleObj: Schedule = new Schedule({
    width: '100%',
    height: '550px',
    selectedDate: new Date(2018, 1, 15),
    views: ['Day', 'Week', 'WorkWeek', 'Month'],
    group: { resources: ['Owners'] },
    showQuickInfo: false,
    resources: [{
        field: 'OwnerId', title: 'Owners',
        name: 'Owners', allowMultiple: true,
        dataSource: [
            { text: "Nancy", id: 1, color: "#1aaa55" },
            { text: "Smith", id: 2, color: "#7fa900" },
            { text: "Paul", id: 3, color: "#357cd2" }
        ],
        textField: 'text', idField: 'id', colorField: 'color'
    }],
    editorTemplate: '#EventEditorTemplate',
    popupOpen: (args: PopupOpenEventArgs) => {
        if (args.type === 'Editor') {
            let startElement: HTMLInputElement = args.element.querySelector('#StartTime') as HTMLInputElement;
            if (!startElement.classList.contains('e-datetimepicker')) {
                new DateTimePicker({ value: new Date(startElement.value) || new Date() }, startElement);
            }
            let endElement: HTMLInputElement = args.element.querySelector('#EndTime') as HTMLInputElement;
            if (!endElement.classList.contains('e-datetimepicker')) {
                new DateTimePicker({ value: new Date(endElement.value) || new Date() }, endElement);
            }
            let processElement: HTMLInputElement= args.element.querySelector('#OwnerId');
            if (!processElement.classList.contains('e-multiselect')) {
                let multiSelectObject: MultiSelect = new MultiSelect({
                    placeholder: 'Choose a owner',
                    fields: { text: 'text', value: 'id'},
                    dataSource: ownerData,
                    value: <string[]>((args.data.OwnerId instanceof Array) ? args.data.OwnerId : [args.data.OwnerId])
                });
                multiSelectObject.appendTo(processElement);
            }
        }
    },
    eventSettings: { dataSource: eventData }
});
scheduleObj.appendTo('#Schedule');
```

{% endtab %}

### How to add recurrence options within editor template

The following code example shows how to add recurrence options within the editor template by importing `RecurrenceEditor`.

{% tab template="schedule/editor-recurrence", es5Template="editor-recurrence", iframeHeight="588px"  sourceFiles="index.ts,index.html"  %}

```typescript
import { DateTimePicker } from '@syncfusion/ej2-calendars';
import { Schedule, Day, Week, WorkWeek, Month, RecurrenceEditor, PopupOpenEventArgs } from '@syncfusion/ej2-schedule';
import { eventData } from './datasource.ts';

Schedule.Inject(Day, Week, WorkWeek);
let scheduleObj: Schedule = new Schedule({
    width: '100%',
    height: '550px',
    selectedDate: new Date(2018, 1, 15),
    views: ['Day', 'Week', 'WorkWeek', 'Month'],
    editorTemplate: '#EventEditorTemplate',
    popupOpen: (args: PopupOpenEventArgs) => {
        if (args.type === 'Editor') {
            let startElement: HTMLInputElement = args.element.querySelector('#StartTime') as HTMLInputElement;
            if (!startElement.classList.contains('e-datetimepicker')) {
                new DateTimePicker({ value: new Date(startElement.value) || new Date() }, startElement);
            }
            let endElement: HTMLInputElement = args.element.querySelector('#EndTime') as HTMLInputElement;
            if (!endElement.classList.contains('e-datetimepicker')) {
                new DateTimePicker({ value: new Date(endElement.value) || new Date() }, endElement);
            }
            let recurElement: HTMLElement = args.element.querySelector('#RecurrenceEditor');
            if (!recurElement.classList.contains('e-recurrenceeditor')) {
                let recurrObject: RecurrenceEditor = new RecurrenceEditor({
                });
                recurrObject.appendTo(recurElement);
                (scheduleObj.eventWindow as any).recurrenceEditor = recurrObject;
            }
            document.getElementById('RecurrenceEditor').style.display = (scheduleObj.currentAction == "EditOccurrence") ? 'none' : 'block';
        }
    },
    eventSettings: { dataSource: eventData }
});
scheduleObj.appendTo('#Schedule');
```

{% endtab %}

### Apply validations on editor template fields

In the following code example, validation has been added to the status field.

{% tab template="schedule/editor", es5Template="editor-template-validation", iframeHeight="588px"  sourceFiles="index.ts,index.html"  %}

```typescript
import { DateTimePicker } from '@syncfusion/ej2-calendars';
import { DropDownList } from '@syncfusion/ej2-dropdowns';
import { FormValidator } from '@syncfusion/ej2-inputs';
import { isNullOrUndefined } from '@syncfusion/ej2-base';
import { Schedule, Day, Week, WorkWeek, Month, PopupOpenEventArgs, EJ2Instance } from '@syncfusion/ej2-schedule';
import { eventData } from './datasource.ts';

Schedule.Inject(Day, Week, WorkWeek, Month);
let scheduleObj: Schedule = new Schedule({
    width: '100%',
    height: '550px',
    selectedDate: new Date(2018, 1, 15),
    views: ['Day', 'Week', 'WorkWeek', 'Month'],
    showQuickInfo: false,
    editorTemplate: '#EventEditorTemplate',
    popupOpen: (args: PopupOpenEventArgs) => {
        if (args.type === 'Editor') {
            if (!isNullOrUndefined(document.getElementById("EventType_Error"))) {
                document.getElementById("EventType_Error").style.display = "none";
                document.getElementById("EventType_Error").style.left = "351px";
            }
            let formElement: HTMLElement = <HTMLElement>args.element.querySelector('.e-schedule-form');
            let statusElement: HTMLInputElement = args.element.querySelector('#EventType') as HTMLInputElement;
            if (!statusElement.classList.contains('e-dropdownlist')) {
                let dropDownListObject: DropDownList = new DropDownList({
                    placeholder: 'Choose status', value: statusElement.value,
                    dataSource: ['New', 'Requested', 'Confirmed'],
                    select: function(args) {
                        if (!isNullOrUndefined(document.getElementById("EventType_Error"))) {
                            document.getElementById("EventType_Error").style.display = "none";
                        }
                    }
                });
                dropDownListObject.appendTo(statusElement);
            }
            let validator: FormValidator = ((formElement as EJ2Instance).ej2_instances[0] as FormValidator);
            validator.addRules('EventType', { required: true });
            let startElement: HTMLInputElement = args.element.querySelector('#StartTime') as HTMLInputElement;
            if (!startElement.classList.contains('e-datetimepicker')) {
                new DateTimePicker({ value: new Date(startElement.value) || new Date() }, startElement);
            }
            let endElement: HTMLInputElement = args.element.querySelector('#EndTime') as HTMLInputElement;
            if (!endElement.classList.contains('e-datetimepicker')) {
                new DateTimePicker({ value: new Date(endElement.value) || new Date() }, endElement);
            }
        }
    },
    eventSettings: { dataSource: eventData }
});
scheduleObj.appendTo('#Schedule');
```

{% endtab %}

### How to save the customized event editor using template

The **e-field** class is not added to each field defined within the template, so you should allow to set those field values externally by using the `popupClose` event.

Note: You can allow to retrieve the data only on the `save` and `delete` option. Data cannot be retrieved on the `close` and `cancel` options in the editor window.

The following code example shows how to save the customized event editor using a template by the `popupClose` event.

{% tab template="schedule/editor", es5Template="editor-template", iframeHeight="588px"  sourceFiles="index.ts,index-event.html"  %}

```typescript
import { DateTimePicker } from '@syncfusion/ej2-calendars';
import { DropDownList } from '@syncfusion/ej2-dropdowns';
import { isNullOrUndefined } from '@syncfusion/ej2-base';
import { Schedule, Day, Week, WorkWeek, Month, Agenda, PopupOpenEventArgs, PopupCloseEventArgs } from '@syncfusion/ej2-schedule';
import { eventData } from './datasource.ts';

Schedule.Inject(Day, Week, WorkWeek, Month, Agenda);
let scheduleObj: Schedule = new Schedule({
    width: '100%',
    height: '550px',
    selectedDate: new Date(2018, 1, 15),
    showQuickInfo: false,
    editorTemplate: '#EventEditorTemplate',
        popupOpen: (args: PopupOpenEventArgs) => {
        if (args.type === 'Editor') {
            let subjectElement: HTMLInputElement = args.element.querySelector('#Subject') as HTMLInputElement;
            if (subjectElement) {
                subjectElement.value = ((<{ [key: string]: Object }>(args.data)).Subject as string) || "";
            }
            let statusElement: HTMLInputElement = args.element.querySelector('#EventType') as HTMLInputElement;
            if (!statusElement.classList.contains('e-dropdownlist')) {
                let dropDownListObject: DropDownList = new DropDownList({
                    placeholder: 'Choose status', value: ((<{ [key: string]: Object }>(args.data)).EventType as string),
                    dataSource: ['New', 'Requested', 'Confirmed']
                });
                dropDownListObject.appendTo(statusElement);
            }
            let startElement: HTMLInputElement = args.element.querySelector('#StartTime') as HTMLInputElement;
            if (!startElement.classList.contains('e-datetimepicker')) {
                startElement.value = (<{ [key: string]: Object }>(args.data)).StartTime as string;
                new DateTimePicker({ value: new Date(startElement.value) || new Date() }, startElement);
            }
            let endElement: HTMLInputElement = args.element.querySelector('#EndTime') as HTMLInputElement;
            if (!endElement.classList.contains('e-datetimepicker')) {
                endElement.value = (<{ [key: string]: Object }>(args.data)).EndTime as string;
                new DateTimePicker({ value: new Date(endElement.value) || new Date() }, endElement);
            }
            let descriptionElement: HTMLInputElement = args.element.querySelector('#Description') as HTMLInputElement;
            if (descriptionElement) {
                descriptionElement.value = (<{ [key: string]: Object }>(args.data)).Description as string || "";
            }
        }
    },
    popupClose: (args: PopupCloseEventArgs) => {
        if (args.type === 'Editor' && !isNullOrUndefined(args.data)) {
            let subjectElement: HTMLInputElement = args.element.querySelector('#Subject') as HTMLInputElement;
            if (subjectElement ) {
                (<{ [key: string]: Object }>(args.data)).Subject = subjectElement.value;
            }
            let statusElement: HTMLInputElement = args.element.querySelector('#EventType') as HTMLInputElement;
            if (statusElement) {
                ((<{ [key: string]: Object }>(args.data)).EventType as string) = statusElement.value;
            }
            let startElement: HTMLInputElement = args.element.querySelector('#StartTime') as HTMLInputElement;
            if (startElement) {
                (<{ [key: string]: Object }>(args.data)).StartTime = startElement.value;
            }
            let endElement: HTMLInputElement = args.element.querySelector('#EndTime') as HTMLInputElement;
            if (endElement) {
                (<{ [key: string]: Object }>(args.data)).EndTime = endElement.value;
            }
            let descriptionElement: HTMLInputElement = args.element.querySelector('#Description') as HTMLInputElement;
            if (descriptionElement) {
                ((<{ [key: string]: Object }>(args.data)).Description as string) = descriptionElement.value;
            }
        }
    },
    eventSettings: { dataSource: eventData }
});
scheduleObj.appendTo('#Schedule');
```

{% endtab %}

In case, if you need to prevent only specific popups on Scheduler, then you can check the condition based on the popup type. The types of the popup that can be checked within the `popupClose` event are as follows.

| Type | Description |
|------|-------------|
| Editor | For Detailed editor window.|
| QuickInfo | For Quick popup which opens on cell click.|
| EditEventInfo |For  Quick popup which opens on event click.|
| ViewEventInfo | For Quick popup which opens on responsive mode.|
| EventContainer | For more event indicator popup.|
| RecurrenceAlert | For edit recurrence event alert popup.|
| DeleteAlert | For delete confirmation popup.|
| ValidationAlert | For validation alert popup.|
| RecurrenceValidationAlert | For recurrence validation alert popup.|

## Quick popups

The quick info popups are the ones that gets opened, when a cell or appointment is single clicked on the desktop mode. On single clicking a cell, you can simply provide a subject and save it. Also, while single clicking on an event, a popup will be displayed where you can get the overview of the event information. You can also edit or delete those events through the options available in it.

By default, these popups are displayed over cells and appointments of Scheduler and to disable this action, set `false` to `showQuickInfo` property.

> The quick popup that opens while single clicking on the cells are not applicable on mobile devices.

{% tab template="schedule/editor-window", es5Template="hide-quick-info", iframeHeight="588px"  sourceFiles="index.ts,index.html"  %}

```typescript
import { Schedule, Day, Week, TimelineViews, Month, Agenda } from '@syncfusion/ej2-schedule';
import { scheduleData } from './datasource.ts';

Schedule.Inject(Day, Week, TimelineViews, Month, Agenda);
let scheduleObj: Schedule = new Schedule({
    width: '100%',
    height: '550px',
    selectedDate: new Date(2018, 1, 15),
    showQuickInfo: false,
    views: ['TimelineDay', 'Day', 'Week', 'Month', 'Agenda'],
    eventSettings: { dataSource: scheduleData }
});
scheduleObj.appendTo('#Schedule');
```

{% endtab %}

### Open quick popup on multiple cell selection

You can display the immediate quick popup after multiple cells selected in scheduler, by setting the `quickInfoOnSelectionEnd` property to true. By default, it's value set to false.

{% tab template="schedule/quick-info", es5Template="quick-info-selection-end", iframeHeight="588px"  sourceFiles="index.ts,index.html"  %}

```typescript
import { Schedule, Day, Week, WorkWeek } from '@syncfusion/ej2-schedule';
import { resourceData } from './datasource.ts';

Schedule.Inject(Day, Week, WorkWeek);
    let scheduleObj: Schedule = new Schedule({
      height: '550px',
      selectedDate: new Date(2018, 3, 1),
      quickInfoOnSelectionEnd : true,
      quickInfoTemplates: {
        header: '#headerTemplate',
        content: '#contentTemplate',
        footer: '#footerTemplate'
      },
      group: {
          resources: ['Rooms', 'Owners']
      },
      resources: [
          {
              field: 'RoomId', title: 'Room',
              name: 'Rooms', allowMultiple: false,
              dataSource: [
                  { RoomText: 'ROOM 1', Id: 1, RoomColor: '#cb6bb2' },
                  { RoomText: 'ROOM 2', Id: 2, RoomColor: '#56ca85' }
              ],
              textField: 'RoomText', idField: 'Id', colorField: 'RoomColor'
          }, {
              field: 'OwnerId', title: 'Owner',
              name: 'Owners', allowMultiple: true,
              dataSource: [
                  { OwnerText: 'Nancy', Id: 1, OwnerGroupId: 1, OwnerColor: '#ffaa00' },
                  { OwnerText: 'Steven', Id: 2, OwnerGroupId: 2, OwnerColor: '#f8a398' },
                  { OwnerText: 'Michael', Id: 3, OwnerGroupId: 1, OwnerColor: '#7499e1' }
              ],
              textField: 'OwnerText', idField: 'Id', groupIDField: 'OwnerGroupId', colorField: 'OwnerColor'
          }
      ],
      eventSettings: { dataSource: resourceData }
    });
    scheduleObj.appendTo('#Schedule');
```

{% endtab %}

### How to change the watermark text of quick popup subject

By default, `Add Title` text is displayed on the subject field of quick popup. To change the default watermark text, change the value of the appropriate localized word collection used in the Scheduler.

```typescript
L10n.load({
    'en-US': {
        'schedule': {
          'addTitle' : 'New Title'
        }
    }
});
```

### Customizing quick popups

The look and feel of the built-in quick popup window, which opens when single clicked on the cells or appointments can be customized by making use of the `quickInfoTemplates` property of the Scheduler. There are 3 sub-options available to customize them easily,

* header - Accepts the template design that customizes the header part of the quick popup.
* content - Accepts the template design that customizes the content part of the quick popup.
* footer - Accepts the template design that customizes the footer part of the quick popup.

{% tab template="schedule/quick-info", es5Template="quick-info", iframeHeight="588px"  sourceFiles="index.ts,index.html"  %}

```typescript
import { Schedule, Day, Week, WorkWeek } from '@syncfusion/ej2-schedule';
import { resourceData } from './datasource.ts';

Schedule.Inject(Day, Week, WorkWeek);
    let scheduleObj: Schedule = new Schedule({
      height: '550px',
      selectedDate: new Date(2018, 3, 1),
      quickInfoTemplates: {
        header: '#headerTemplate',
        content: '#contentTemplate',
        footer: '#footerTemplate'
      },
      group: {
          resources: ['Rooms', 'Owners']
      },
      resources: [
          {
              field: 'RoomId', title: 'Room',
              name: 'Rooms', allowMultiple: false,
              dataSource: [
                  { RoomText: 'ROOM 1', Id: 1, RoomColor: '#cb6bb2' },
                  { RoomText: 'ROOM 2', Id: 2, RoomColor: '#56ca85' }
              ],
              textField: 'RoomText', idField: 'Id', colorField: 'RoomColor'
          }, {
              field: 'OwnerId', title: 'Owner',
              name: 'Owners', allowMultiple: true,
              dataSource: [
                  { OwnerText: 'Nancy', Id: 1, OwnerGroupId: 1, OwnerColor: '#ffaa00' },
                  { OwnerText: 'Steven', Id: 2, OwnerGroupId: 2, OwnerColor: '#f8a398' },
                  { OwnerText: 'Michael', Id: 3, OwnerGroupId: 1, OwnerColor: '#7499e1' }
              ],
              textField: 'OwnerText', idField: 'Id', groupIDField: 'OwnerGroupId', colorField: 'OwnerColor'
          }
      ],
      eventSettings: { dataSource: resourceData }
    });
    scheduleObj.appendTo('#Schedule');
```

{% endtab %}

> The quick popup in adaptive mode can also be customized using `quickInfoTemplates` using `e-device` class.

## More events indicator and popup

When the number of appointments count that lies on a particular time range * default appointment height exceeds the default height of a cell in month view and all other timeline views, a `+ more` text indicator will be displayed at the bottom of those cells. This indicator denotes that the cell contains few more appointments in it and clicking on that will display a popup displaying all the appointments present on that day.

> To disable this option of showing popup with all hidden appointments, while clicking on the text indicator, you can do code customization within the `popupOpen` event.

The same indicator is displayed on all-day row in calendar views such as day, week and work week views alone, when the number of appointment count present in a cell exceeds three. Clicking on the text indicator here will not open a popup, but will allow the expand/collapse option for viewing the remaining appointments present in the all-day row.

The following code example shows how to disable the display of such popups while clicking on the more text indicator.

{% tab template="schedule/editor-window", es5Template="more-indicator", iframeHeight="588px"  sourceFiles="index.ts,index.html"  %}

```typescript
import { Schedule, Day, Week, WorkWeek, Month, PopupOpenEventArgs } from '@syncfusion/ej2-schedule';
import { scheduleData } from './datasource.ts';

Schedule.Inject(Day, Week, WorkWeek, Month);
let scheduleObj: Schedule = new Schedule({
    width: '100%',
    height: '550px',
    selectedDate: new Date(2018, 1, 15),
    currentView: 'Month',
    views: ['Day', 'Week', 'WorkWeek', 'Month'],
    popupOpen: (args: PopupOpenEventArgs) => {
        if (args.type === 'EventContainer') {
            args.cancel = true;
        }
    },
    eventSettings: { dataSource: scheduleData }
});
scheduleObj.appendTo('#Schedule');
```

{% endtab %}

### How to customize the popup that opens on more indicator

The following code example shows you how to customize the default more indicator popup in which number of events rendered count on the day has been shown in the header.

{% tab template="schedule/editor-window", es5Template="more-indicator-custom", iframeHeight="588px"  sourceFiles="index.ts,index.html"  %}

```typescript
import { Internationalization } from '@syncfusion/ej2-base';
import { Schedule, Month, PopupOpenEventArgs } from '@syncfusion/ej2-schedule';
import { scheduleData } from './datasource.ts';

Schedule.Inject( Month);
let scheduleObj: Schedule = new Schedule({
    width: '100%',
    height: '550px',
    selectedDate: new Date(2018, 1, 15),
    views: ['Month'],
    popupOpen: (args: PopupOpenEventArgs) => {
        if (args.type === 'EventContainer') {
            let instance: Internationalization = new Internationalization();
            let date: string  = instance.formatDate(args.data.date, { skeleton: 'MMMEd' });
            ((args.element.querySelector('.e-header-date')) as HTMLElement).innerText = date;
            ((args.element.querySelector('.e-header-day')) as HTMLElement).innerText = 'Event count: ' + args.data.event.length;
        }
    },
    eventSettings: { dataSource: scheduleData }
});
scheduleObj.appendTo('#Schedule');
```

{% endtab %}

### How to close the popup manually

The following code example demonstrates the how to close popup manually.

{% tab template="schedule/editor-window", es5Template="more-indicator-custom", iframeHeight="588px"  sourceFiles="index.ts,index.html"  %}

```typescript
import { Schedule, Month, PopupCloseEventArgs } from '@syncfusion/ej2-schedule';
import { scheduleData } from './datasource.ts';

Schedule.Inject( Month);
let scheduleObj: Schedule = new Schedule({
    width: '100%',
    height: '550px',
    selectedDate: new Date(2018, 1, 15),
    views: ['Month'],
    popupClose: (args: PopupCloseEventArgs) => {
        console.log(arg);
    },
    eventSettings: { dataSource: scheduleData }
 });
scheduleObj.appendTo('#Schedule');
```

{% endtab %}

### How to display the popup when clicking on the more text indicator

The following code example demonstrates the open popup when clicking the more text indicator. By default, scheduler set to open the popup on clicking the more text indicator.

{% tab template="schedule/editor-window", es5Template="more-text-indicator", iframeHeight="588px"  sourceFiles="index.ts,index.html"  %}

```typescript
import { Schedule, Day, Week, WorkWeek, Month, MoreEventsClickArgs } from '@syncfusion/ej2-schedule';
import { scheduleData } from './datasource.ts';

Schedule.Inject(Day, Week, WorkWeek, Month);
let scheduleObj: Schedule = new Schedule({
    width: '100%',
    height: '550px',
    selectedDate: new Date(2018, 1, 15),
    currentView: 'Month',
    views: ['Day', 'Week', 'WorkWeek', 'Month'],
    eventSettings: { dataSource: scheduleData }
});
scheduleObj.appendTo('#Schedule');
```

{% endtab %}

### How to prevent the display of popup when clicking on the more text indicator

It is possible to prevent the display of popup window by passing the value `true` to `cancel` option within the `MoreEventsClick` event.

{% tab template="schedule/editor-window", es5Template="more-text-indicator", iframeHeight="588px"  sourceFiles="index.ts,index.html"  %}

```typescript
import { Schedule, Day, Week, WorkWeek, Month, MoreEventsClickArgs } from '@syncfusion/ej2-schedule';
import { scheduleData } from './datasource.ts';

Schedule.Inject(Day, Week, WorkWeek, Month);
let scheduleObj: Schedule = new Schedule({
    width: '100%',
    height: '550px',
    selectedDate: new Date(2018, 1, 15),
    currentView: 'Month',
    views: ['Day', 'Week', 'WorkWeek', 'Month'],
    moreEventsClick: (args: MoreEventsClickArgs) => {
        args.cancel = true;
    },
    eventSettings: { dataSource: scheduleData }
});
scheduleObj.appendTo('#Schedule');
```

{% endtab %}

### How to navigate Day view when clicking on more text indicator

The following code example shows you how to customize the `moreEventsClick` property to navigate to the Day view when clicking on the more text indicator.

{% tab template="schedule/editor-window", es5Template="more-text-indicator", iframeHeight="588px"  sourceFiles="index.ts,index.html"  %}

```typescript
import { Schedule, Day, Week, WorkWeek, Month, MoreEventsClickArgs } from '@syncfusion/ej2-schedule';
import { scheduleData } from './datasource.ts';

Schedule.Inject(Day, Week, WorkWeek, Month);
let scheduleObj: Schedule = new Schedule({
    width: '100%',
    height: '550px',
    selectedDate: new Date(2018, 1, 15),
    currentView: 'Month',
    views: ['Day', 'Week', 'WorkWeek', 'Month'],
    moreEventsClick: (args: MoreEventsClickArgs) => {
        args.isPopupOpen = false;
    },
    eventSettings: { dataSource: scheduleData }
});
scheduleObj.appendTo('#Schedule');
```

{% endtab %}

### How to close the editor window manually

You can close the editor window by using `closeEditor()` public method. The following code example  demonstrates the how to close editor window manually.

{% tab template="schedule/editor-window", es5Template="close-editor", iframeHeight="588px"  sourceFiles="index.ts,index.html"  %}

```typescript
import { Schedule, Day, Week, WorkWeek, Month, MoreEventsClickArgs } from '@syncfusion/ej2-schedule';
import { scheduleData } from './datasource.ts';
import { Button } from '@syncfusion/ej2-buttons';

Schedule.Inject(Day, Week, WorkWeek, Month);
let scheduleObj: Schedule = new Schedule({
    width: '100%',
    height: '550px',
    selectedDate: new Date(2018, 1, 15),
    currentView: 'Month',
    views: ['Day', 'Week', 'WorkWeek', 'Month'],
    eventSettings: { dataSource: scheduleData },
    popupOpen: (args: PopupOpenEventArgs) => {
    if (args.type === 'Editor') {
      if (!args.element.querySelector('#closeEditor')) {
        let btnElement = createElement("BUTTON", { id: 'closeEditor', className: 'e-custom-close' });
        args.element.querySelector('.e-footer-content').appendChild(btnElement)
        let btnObj: Button = new Button();
        btnElement.textContent = "Close Editor";
        btnObj.appendTo('#closeEditor');
        btnObj.element.onclick = (): void => {
          scheduleObj.closeEditor();
        }
      }
    }
  },
});
scheduleObj.appendTo('#Schedule');
```

{% endtab %}

### How to close the quick info popup manually

You can close the quick info popup in scheduler by using the `closeQuickInfoPopup()` public method. The following code example demonstrates the how to close quick info popup manually.

{% tab template="schedule/editor-window", es5Template="close-quickinfo-popup", iframeHeight="588px"  sourceFiles="index.ts,index.html"  %}

```typescript
import { Schedule, Day, Week, WorkWeek, Month, MoreEventsClickArgs } from '@syncfusion/ej2-schedule';
import { scheduleData } from './datasource.ts';
import { Button } from '@syncfusion/ej2-buttons';

Schedule.Inject(Day, Week, WorkWeek, Month);
let scheduleObj: Schedule = new Schedule({
    width: '100%',
    height: '550px',
    selectedDate: new Date(2018, 1, 15),
    currentView: 'Month',
    views: ['Day', 'Week', 'WorkWeek', 'Month'],
    eventSettings: { dataSource: scheduleData }
});
scheduleObj.appendTo('#Schedule');

let btnElement = createElement("BUTTON", { id: 'closeQuickInfo', className: 'e-custom-close' });
args.element.querySelector('.e-content-wrapper').appendChild(btnElement)
btnElement.textContent = "Close Quick Info Popup";
let closeQuickInfoButton: Button = new Button();
closeQuickInfoButton.appendTo('#closeQuickInfo');
closeQuickInfoButton.element.onclick = (): void => {
  scheduleObj.closeQuickInfoPopup();
};
```

{% endtab %}