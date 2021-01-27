---
title: "Server actions"
component: "In-place Editor"
description: "Learn how to modify and submit a value to the server, and handle success and failure events in the Essential JS 2 In-place Editor control."
---

# Server actions

By passing In-place Editor control value to the server, the [primaryKey](../api/inplace-editor/#primarykey) property value must require, otherwise action not performed for remote data.

If the [URL](../api/inplace-editor/#url) property value is empty, data passing will handled at local and also the [actionSuccess](../api/inplace-editor/#actionsuccess) event will trigger with `null` as argument value.

> The following arguments are passed to the server when submit actions perform.

| Arguments  | Explanations                                              |
|------------|-----------------------------------------------------------|
| value      | For processing edited value, like DB value updating.      |
| primaryKey | For value mapping to the server, like selecting DB.            |
| name       | For field mapping to the server, like DB column field mapping. |

Find the following sample server codes for defining models and controller functions to configure processing data.

```C#
    public class SubmitModel
        {
            public string Name { get; set; }
            public string PrimaryKey { get; set; }
            public string Value { get; set; }
        }
```

```C#

public IEnumerable<SubmitModel> UpdateData([FromBody]SubmitModel value)
        {
         // User can process data
          return value;
        }

```

* Server actions successfully done, the [actionSuccess](../api/inplace-editor/#actionsuccess) event will be fired with returned server data.

* If the server is not responding, the [actionFailure](../api/inplace-editor/#actionfailure) event will be fired with data, but value not updated in the Editor.

In the following sample, the `actionSuccess` event will trigger once the value submitted successfully into the server. In this sample, both `actionSuccess` and `actionFailure` were configured and resulted value will be converted to chips.

{% tab template="in-place-editor/server-actions", es5Template="es5_server_actions", sourceFiles="index.ts,index.html" %}

```typescript
import { InPlaceEditor, ActionEventArgs, MultiSelect } from '@syncfusion/ej2-inplace-editor';
InPlaceEditor.Inject(MultiSelect);

let serviceUrl: string = 'https://ej2services.syncfusion.com/development/web-services/api/Editor/UpdateData';

let frameWorkList: string[] = ['Android', 'JavaScript', 'jQuery', 'TypeScript', 'Angular', 'React', 'Vue', 'Ionic'];

let editObj: InPlaceEditor = new InPlaceEditor({
    mode: 'Inline',
    type: 'MultiSelect',
    value: ['JavaScript', 'jQuery'],
    name: 'skill',
    url: serviceUrl,
    primaryKey: "FrameWork",
    adaptor: 'UrlAdaptor',
    model: {
        mode: 'Box',
        dataSource: frameWorkList,
        placeholder: 'Select skill'
    },
    actionSuccess: onActionSuccess,
    actionFailure: onActionFailure
});
editObj.appendTo('#element');

chipOnCreate(); // Initialize chips customization at initial load

function chipOnCreate(): void {
    editObj.element.querySelector('.e-editable-value').innerHTML = chipCreation(editObj.value);
}

function onActionSuccess(e: ActionEventArgs): void {
    e.value = chipCreation(e.value.split(','), true);
}

function onActionFailure(e: ActionEventArgs): void {
    e.value = chipCreation(e.value.split(','), false);
}

function chipCreation(data: string[], isSuccess: boolean): string {
    let value: string = '<div class="e-chip-list">';
    [].slice.call(data).forEach((val: string) => {
        value += '<div class="e-chip"> <span class="e-chip-text' + (!isSuccess ? 'e-highlight' : '') + '"> ' + val + '</span></div>';
    });
    value += '</div>';
    return value;
}
```

{% endtab %}

## See Also

* [Indicate the server actions in the editor](./how-to/custom-indication)