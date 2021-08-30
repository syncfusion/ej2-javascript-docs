---
title: "Customize the Edit Dialog"
component: "Grid"
description: "Learn how to customize the Edit Dialog."
---

# Customize the Edit Dialog

You can customize the appearance of the edit dialog in the [`actionComplete`](../../api/grid/#actioncomplete) event based on `requestType` as `beginEdit` or `add`.

In the following example, the dialog's properties like header text, showCloseIcon, height have been changed while editing and adding the records.

Also the locale text for the `Save` and `Cancel` buttons has been changed by overriding the default locale strings.

You can refer the Grid [`Default text`](../grid/global-local/) list for more localization.

{% tab template="grid/customizedialog", sourceFiles="index.ts,index.css,index.html",es5Template="customizedialog" %}

```typescript
import { L10n } from '@syncfusion/ej2-base';
import { DialogModel } from '@syncfusion/ej2-popups';
import { Grid, Edit, Toolbar, DialogEditEventArgs } from '@syncfusion/ej2-grids';
import { data } from './datasource.ts';

Grid.Inject(Edit, Toolbar);

L10n.load({
  'en-US': {
    grid: {
      SaveButton: 'Submit',
      CancelButton: 'Discard'
    }
  }
});

let grid: Grid = new Grid({
    dataSource: data,
    toolbar: ['Add', 'Edit', 'Delete'],
    editSettings: { allowEditing: true, allowAdding: true, allowDeleting: true, mode: 'Dialog' },
    columns: [
        { field: 'OrderID', headerText: 'Order ID', textAlign: 'Right', width: 100, isPrimaryKey: true },
        { field: 'CustomerID', headerText: 'Customer ID', width: 120, },
        { field: 'ShipCountry', headerText: 'Ship Country', width: 150 }
    ],
    height: 265,
    actionComplete: (args: DialogEditEventArgs) => {
        if (args.requestType === 'beginEdit' || args.requestType === 'add') {
            let dialog: DialogModel = args.dialog;
            dialog.showCloseIcon = false;
            dialog.height = 400;
            // change the header of the dialog
            dialog.header = args.requestType === 'beginEdit' ? 'Edit Record of ' + args.rowData['CustomerID'] : 'New Customer';
        }
    }
});
grid.appendTo('#Grid');

```

{% endtab %}
