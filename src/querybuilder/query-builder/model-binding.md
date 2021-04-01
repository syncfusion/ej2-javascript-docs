---
title: "Model Binding"
component: "QueryBuilder"
description: "Documentation on model binding in the Essential JS 2 QueryBuilder control."
---

# Model Binding

Model binding allows to bind properties for the components used in field, operator, and value columns. To implement model binding, assign fieldModel, operatorModel, and valueModel properties in QueryBuilder.

{% tab template= "query-builder/model-binding", sourceFiles="app.ts,index.html,styles.css",
es5Template="qb-template" %}

```typescript
import { QueryBuilder , RuleModel, ColumnsModel} from '@syncfusion/ej2-querybuilder';
import { getComponent, extend } from '@syncfusion/ej2-base';
import { DropDownList } from '@syncfusion/ej2-dropdowns';

let filter: ColumnsModel [] = [
    { field: 'EmployeeID', label: 'EmployeeID', type: 'number'},
    { field: 'FirstName', label: 'FirstName', type: 'string'},
    { field: 'LastName', label: 'LastName', type: 'string'},
    { field: 'Age', label: 'Age', type: 'number'},
    { field: 'City', label: 'City', type: 'string'},
    { field: 'Country', label: 'Country', type: 'string'},
];
let importRules: RuleModel = {
    'condition': 'and',
    'rules': [{
        'label': 'Employee ID',
        'field': 'EmployeeID',
        'type': 'number',
        'operator': 'equal',
        'value': 1001
    }]
};
let qryBldrObj: QueryBuilder = new QueryBuilder({
    columns: filter,
    rule: importRules,
    enableNotCondition: true,
    displayMode: "Horizontal",
    allowValidation: true,
    fieldModel: {
        allowFiltering: true,
        popupHeight:'400px'
    },
    operatorModel: {
        allowFiltering: true,
        popupHeight:'400px'
    },
    valueModel: {
        numericTextBoxModel: {
            cssClass: 'e-custom'
        },
        multiSelectModel: {
            cssClass: 'e-custom'
        },
        datePickerModel: {
            cssClass: 'e-custom'
        },
        textBoxModel: {
            cssClass: 'e-custom'
        },
        radioButtonModel: {
            cssClass: 'e-custom'
        }
    }
});
qryBldrObj.appendTo('#querybuilder');
```

{% endtab %}