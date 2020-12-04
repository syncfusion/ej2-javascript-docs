---
title: "Ribbon"
component: "Spreadsheet"
description: "Learn the various operations that you can perform in ribbon of the Essential JS 2 Spreadsheet."
---

# Ribbon

It helps to organize a spreadsheet’s features into a series of tabs. By clicking the expand or collapse icon, you can expand or collapse the ribbon toolbar dynamically.

## Ribbon Customization

You can customize the ribbon using the following methods,

| Method | Action |
|-------|---------|
| [`hideRibbonTabs`](../api/spreadsheet/#hideribbontabs) | Used to show or hide the existing ribbon tabs. |
| [`enableRibbonTabs`](../api/spreadsheet/#enableribbontabs) | Used to enable or disable the existing ribbon tabs. |
| [`addRibbonTabs`](../api/spreadsheet/#addribbontabs) | Used to add custom ribbon tabs. |
| [`hideToolbarItems`](../api/spreadsheet/#hidetoolbaritems) | Used to show or hide the existing ribbon toolbar items. |
| [`enableToolbarItems`](../api/spreadsheet/#enabletoolbaritems) | Used to enable or disable the specified toolbar items. |
| [`addToolbarItems`](../api/spreadsheet/#addtoolbaritems) | Used to add the custom items in ribbon toolbar. |
| [`hideFileMenuItems`](../api/spreadsheet/#hidefilemenuitems) | Used to show or hide the ribbon file menu items. |
| [`enableFileMenuItems`](../api/spreadsheet/#enablefilemenuitems) | Used to enable or disable file menu items. |
| [`addFileMenuItems`](../api/spreadsheet/#addfilemenuitems) | Used to add custom file menu items. |

The following code example shows the usage of ribbon customization.

{% tab template="spreadsheet/ribbon/cutomization", sourceFiles="app.ts,index.html,datasource.ts", es5Template="es5-ribbon-cutomization", iframeHeight="450px", isDefaultActive=true %}

```typescript
import { Spreadsheet, SheetModel, ColumnModel, MenuSelectEventArgs } from '@syncfusion/ej2-spreadsheet';
import { enableRipple, select } from '@syncfusion/ej2-base';
import { ClickEventArgs } from '@syncfusion/ej2-navigations';
import { data } from './datasource.ts';

enableRipple(true);

let columns: ColumnModel[] = [{ width: 180 }, { width: 130 }, { width: 130 }, { width: 180 }, { width: 130 }, { width: 120 }];

let sheets: SheetModel[] = [{ ranges: [{ dataSource: data }], columns: columns }];

let spreadsheet: Spreadsheet = new Spreadsheet({
    sheets: sheets,
    created: (): void => {
        spreadsheet.cellFormat({ fontWeight: 'bold', textAlign: 'center' }, 'A1:F1');
        // Hiding the `Insert` from ribbon.
        spreadsheet.hideRibbonTabs(['Insert']);
        // Set disabled state to `View` ribbon tab.
        spreadsheet.enableRibbonTabs(['View'], false);
        // Adding the `Help` ribbon tab at the last index.
        // Specify the ribbon tab header text in last optional argument(`insertBefore`) for inserting new tab before any existing tab.
        spreadsheet.addRibbonTabs([{ header: { text: 'Help' }, content: [{ text: 'Feedback', tooltipText: 'Feedback',
            click: (args: ClickEventArgs): void => { /* Any click action for this toolbar item will come here. */ } }] }]);
        // Hiding the unwanted toolbar items from `Home` by specifying its index.
        spreadsheet.hideToolbarItems('Home', [0, 1, 2, 4, 14, 15, 21, 24]);
        // Set disable state to `Underline`, 'Wrap text` toolbar items from `Home` by specifying the item id.
        spreadsheet.enableToolbarItems('Home', [`${spreadsheet.element.id}_underline`, `${spreadsheet.element.id}_wrap`], false);
        // Set disable state to `Protect Sheet` toolbar item from `Data` by mentioning its index.
        spreadsheet.enableToolbarItems('Data', [0], false);
        // Adding the new `Custom Formulas` toolbar item under `Formulas` tab for adding custom formulas.
        spreadsheet.addToolbarItems(
            'Formulas', [{ type: 'Separator' }, {
                text: 'Custom Formulas', tooltipText: 'Custom Formulas',
                // You can set click handler for each new custom toolbar item
                click: (args: ClickEventArgs): void => {
                    // You can add custom formulas here.
                }
            }]);
        // Adding new custom item `Import` after the existing `Open` item. By default, new item will add after the specified item.
        spreadsheet.addFileMenuItems([{ text: 'Import', iconCss: 'e-open e-icons' }], 'Open');
        // Adding new custom item `Export As` after the existing `Save As` item.
        // Set `insertAfter` optional argument as `false` for adding new item before the specified item.
        spreadsheet.addFileMenuItems(
            [{
                text: 'Export As', iconCss: 'e-save e-icons', items: [{ text: 'XLSX', iconCss: 'e-xlsx e-icons' },
                    { text: 'XLS', iconCss: 'e-xls e-icons' }, { text: 'CSV', iconCss: 'e-csv e-icons' }]
            }],
            'Save As', false);
    },
    fileMenuBeforeOpen: (): void => {
        // Because the file menu items are created dynamically, you need to perform the hide or show and enable/disable operations
        // under filemenu before open event.
        // Hiding the `Save As` and `Open` item.
        spreadsheet.hideFileMenuItems(['Save As', 'Open']);
         // Set disable state to `New` item. You can perform any file menu items customization by specifying the item id,
        // if it has more than one same item text. Set the last argument `isUniqueId` as true for using the item id.
        spreadsheet.enableFileMenuItems([`${spreadsheet.element.id}_New`], false, true);
    },
    fileMenuItemSelect: (args: MenuSelectEventArgs): void => {
        // Custom file menu items select handler
        switch (args.item.text) {
            case 'Import': select(`#${spreadsheet.element.id}_fileUpload`, spreadsheet.element).click();
                break;
            case 'XLSX': spreadsheet.save({ saveType: 'Xlsx' });
                break;
            case 'XLS': spreadsheet.save({ saveType: 'Xls' });
                break;
            case 'CSV': spreadsheet.save({ saveType: 'Csv' });
                break;
        }
    },
    openUrl: 'https://ej2services.syncfusion.com/production/web-services/api/spreadsheet/open',
    saveUrl: 'https://ej2services.syncfusion.com/production/web-services/api/spreadsheet/save',
    // Removed the unwanted support for this samples
    showFormulaBar: false, showSheetTabs: false, allowInsert: false, allowDelete: false, allowMerge: false
});

spreadsheet.appendTo('#spreadsheet');
```

{% endtab %}

## See Also

* [Worksheet](./worksheet)
* [Rows and columns](./rows-and-columns)
