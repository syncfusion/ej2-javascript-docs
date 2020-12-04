---
title: "Data Validation"
component: "Spreadsheet"
description: "This section restrict the type of data or the values that users enter into a cell"
---

# Data Validation

Data Validation is used to restrict the user from entering the invalid data. You can use the [`allowDataValidation`](../api/spreadsheet/#allowDataValidation) property to enable or disable data validation.

> * The default value for `allowDataValidation` property is `true`.

## Apply Validation

You can apply data validation to restrict the type of data or the values that users enter into a cell.

You can apply data validation by using one of the following ways,

* Select the Data tab in the Ribbon toolbar, and then choose the Data Validation item.
* Use the [`addDataValidation()`](../api/spreadsheet/#addDataValidation) method programmatically.

## Clear Validation

Clear validation feature is used to remove data validations from the specified ranges or the whole worksheet.

You can clear data validation rule by one of the following ways,

* Select the Data tab in the Ribbon toolbar, and then choose the Clear Validation item.
* Use the [`removeDataValidation()`](../api/spreadsheet/#removeDataValidation) method programmatically.

## Highlight Invalid Data

Highlight invalid data feature is used to highlight the previously entered invalid values.

You can highlight an invalid data by using one of the following ways,

* Select the Data tab in the Ribbon toolbar, and then choose the Highlight Invalid Data item.
* Use the [`addInvalidHighlight()`](../api/spreadsheet/#addInvalidHighlight) method programmatically.

## Clear Highlighted Invalid Data

Clear highlight feature is used to remove the highlight from invalid cells.

You can clear the highlighted invalid data by using the following ways,

* Select the Data tab in the Ribbon toolbar, and then choose the Clear Highlight item.
* Use the [`removeInvalidHighlight()`](../api/spreadsheet/#removeInvalidHighlight) method programmatically.

{% tab template="spreadsheet/data-validation", sourceFiles="app.ts,index.html", es5Template="es5-data-validation", iframeHeight="500px" , isDefaultActive=true %}

```typescript

import { Spreadsheet } from '@syncfusion/ej2-spreadsheet';

let sheet: SheetModel[] = [
    {
        name: 'PriceDetails',
        rows: [
            {
                    index: 0,
                    cells: [{ index: 0, value: 'Seller Name', style:{fontWeight : "bold", textAlign: "center"} },
                    { index: 1, value: 'Customer Id', style:{fontWeight : "bold", textAlign: "center"} },
                    { index: 2, value: 'Customer Name', style:{fontWeight : "bold", textAlign: "center"} },
                    { index: 3, value: 'Product Name', style:{fontWeight : "bold", textAlign: "center"} },
                    { index: 4, value: 'Product Price', style:{fontWeight : "bold", textAlign: "center"} },
                    { index: 5, value: 'Sales Date', style:{fontWeight : "bold", textAlign: "center"} },
                    { index: 5, value: 'Billing Time', style:{fontWeight : "bold", textAlign: "center"} },
                    { index: 6, value: 'Total Price', style:{fontWeight : "bold", textAlign: "center"} }]
                },
                {
                    index: 1,
                    cells: [{ index: 0, value: 'John'},
                    { index: 1, value: '1', validation: { type: 'WholeNumber', operator: 'NotEqualTo', value1: '1'}},
                    { index: 2, value: 'Nash'},
                    { index: 3, value: 'Digger', validation:{ type: 'List', value1: 'Digger, Digger, Cherrypicker' }},
                    { index: 4, value: '50000', validation:{ type: 'List', value1: '50000,50000,45000' }},
                    { index: 5, value: '04/11/2019'},
                    { index: 6, value: '11:34:32 AM'},
                    { index: 7, value: '1,45,000.00'}]
                },
                {
                    index: 2,
                    cells: [{ index: 0, value: 'Mike'},
                    { index: 1, value: '2', validation: { type: 'WholeNumber', operator: 'NotEqualTo', value1: '1'}},
                    { index: 2, value: 'Jim'},
                    { index: 3, value: 'Cherrypicker', validation:{ type: 'List', value1: 'Cherrypicker, JCB, Wheelbarrow' }},
                    { index: 4, value: '45000', validation:{ type: 'List', value1: '45000,90000,40' }},
                    { index: 5, value: '04/11/2019'},
                    { index: 6, value: '10:15:00 AM'},
                    { index: 7, value: '1,40,040.00'}]
                },
                {
                    index: 3,
                    cells: [{ index: 0, value: 'shane' },
                    { index: 1, value: '3', validation: { type: 'WholeNumber', operator: 'NotEqualTo', value1: '1'}},
                    { index: 2, value: 'Sean'},
                    { index: 3, value: 'Kango', validation:{ type: 'List', value1: 'Kango, Ropes' }},
                    { index: 4, value: '450', validation:{ type: 'List', value1: '450, 95' }},
                    { index: 5, value: '06/25/2019'},
                    { index: 6, value: '01:30:11 PM'},
                    { index: 7, value: '545.00'}]
                },
                {
                    index: 4,
                    cells: [{ index: 0, value: 'John' },
                    { index: 1, value: '1', validation: { type: 'WholeNumber', operator: 'NotEqualTo', value1: '1'}},
                    { index: 2, value: 'Nash'},
                    { index: 3, value: 'JCB', validation:{ type: 'List', value1: 'JCB, Ropes, scaffolding' }},
                    { index: 4, value: '90000', validation:{ type: 'List', value1: '90000, 95, 10000' }},
                    { index: 5, value: '09/22/2019'},
                    { index: 6, value: '12:30:02 PM'},
                    { index: 7, value: '1,00,095.00' }]
                }
        ],
        columns: [
            { width: 88,  }, { width: 88 }, { width: 106 }, { width: 98 }, { width: 88 }, { width: 86 }, { width: 107 }, { width: 81}
        ]
    }
];

//Initialize the SpreadSheet control
let spreadsheet: Spreadsheet = new Spreadsheet({
  sheets: sheet,
  created: () => {
            //Add Data validation to range.
            spreadsheet.addDataValidation({ type: 'TextLength' , operator: 'LessThanOrEqualTo' , value1: '4' }, 'A2:A5');
            spreadsheet.addDataValidation({ type: 'WholeNumber', operator: 'NotEqualTo', value1: '1' }, 'B2:B5');
            spreadsheet.addDataValidation({ type: 'Date', operator: 'NotEqualTo', value1: '04/11/2019'}, 'F2:F5');
            spreadsheet.addDataValidation({ type: 'Time', operator: 'Between', value1: '10:00:00 AM', value2: '11:00:00 AM' }, 'G2:G5');
            spreadsheet.addDataValidation({ type: 'Decimal', operator: 'LessThan', value1: '100000.00'}, 'H2:H5');
            //Highlight Invalid Data.
            spreadsheet.addInvalidHighlight('A1:H5');
        }
});

spreadsheet.appendTo('#spreadsheet');
```

{% endtab %}

## See Also

* [Formatting](./formatting)
* [Rows and columns](./rows-and-columns)
* [Hyperlink](./link)
* [Sorting](./sort)
