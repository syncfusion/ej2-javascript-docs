---
title: "Columns"
component: "QueryBuilder"
description: "Documentation on column step, format, labels, operators, validations, template in the Essential JS 2 QueryBuilder control."
---

# Column Binding

The column definitions are used as the [`dataSource`](https://ej2.syncfusion.com/documentation/api/query-builder/#datasource) schema in the Query Builder. This plays a vital role in rendering column values. The query builder operations such as create or delete conditions, and create or delete groups, are performed based on the column definitions. The [`field`](https://ej2.syncfusion.com/documentation/api/query-builder/columnsModel/#field) property of the [`columns`](https://ej2.syncfusion.com/documentation/api/query-builder/#columns) is necessary to map the data source values in the query builder columns.

> If the column field is not specified in the dataSource, the column values will be empty.

## Auto generation

The [`columns`](https://ej2.syncfusion.com/documentation/api/query-builder/#columns) are automatically generated when the [`columns`](https://ej2.syncfusion.com/documentation/api/query-builder/#columns) declaration is empty or undefined while initializing the query builder. All the columns in the [`dataSource`](https://ej2.syncfusion.com/documentation/api/query-builder/#datasource) are bound as the query builder columns.

{% tab template= "query-builder/getting-started", sourceFiles="app.ts,index.html,styles.css",
es5Template="column-qb-template", isDefaultActive=true %}

```typescript
import { QueryBuilder } from '@syncfusion/ej2-querybuilder';

let data: Object[] = [
    { OrderID: 10248, CustomerID: 'VINET', EmployeeID: 5, Freight: 32.3800, OrderDate: "07/09/1991" },
    { OrderID: 10249, CustomerID: 'TOMSP', EmployeeID: 6, Freight: 32.3800, OrderDate: "07/09/1991" },
    { OrderID: 10250, CustomerID: 'HANAR', EmployeeID: 4, Freight: 32.3800, OrderDate: "07/09/1991" }];

    let qryBldrObj: QueryBuilder = new QueryBuilder({
        width: '70%',
        dataSource: data,
    });
    qryBldrObj.appendTo('#querybuilder');
```

{% endtab %}

> When columns are auto-generated, the column type will be determined from the first record of the dataSource.

## Labels

By default, the column label is displayed from the column [`field`](https://ej2.syncfusion.com/documentation/api/query-builder/columnsModel/#field) value. To override the default label, you have to define the [`label`](https://ej2.syncfusion.com/documentation/api/query-builder/columnsModel/#label) value.

## Operators

The operator for a column can be defined in the [`operators`](https://ej2.syncfusion.com/documentation/api/query-builder/columnsModel/#operators) property.
The available operators and its supported data types are:

| Operators | Description | Supported Types |
| ------------ | ----------------------- | ------------------ |
| startswith  | Checks whether the value begins with the specified value. | String |
| endswith  | Checks whether the value ends with the specified value. | String |
| contains | Checks whether the value contains the specified value. | String |
| equal | Checks whether the value is equal to the specified value. | String Number Date Boolean |
| notequal | Checks whether the value is not equal to the specified value. | String Number  Date Boolean |
| greaterthan | Checks whether the value is greater than the specified value. | Date Number |
| greaterthanorequal | Checks whether a value is greater than or equal to the specified value. | Date Number |
| lessthan | Checks whether the value is less than the specified value.| Date Number |
| lessthanorequal | Checks whether the value is less than or equal to the specified value. | Date Number |
| between | Checks whether the value is between the two-specific values. | Date Number |
| notbetween | Checks whether the value is not between the two-specific values. | Date Number |
| in | Checks whether the value is one of the specific values. | String Number |
| notin | Checks whether the value is not in the specific values. | String Number |

## Step

The Query Builder allows you to set the step values to the number fields. So that, you can easily access the numeric textbox. Use the [`step`](https://ej2.syncfusion.com/documentation/api/query-builder/columnsModel/#step) property, to set the step value for number values.

## Format

The Query Builder formats date and number values. Use the [`format`](https://ej2.syncfusion.com/documentation/api/query-builder/columnsModel/#format) property to format date and number values.

{% tab template= "query-builder/getting-started", sourceFiles="app.ts,index.html,styles.css",
es5Template="format-qb-template" %}

```typescript
import { QueryBuilder, ColumnsModel, RuleModel } from '@syncfusion/ej2-querybuilder';

let employeeData: Object[] = [{
      'EmployeeID': 1,
      'FirstName': 'Nancy',
      'Title': 'Sales Representative',
      'TitleOfCourtesy': 'Ms.',
      'HireDate': '22/07/2001',
      'City': 'Seattle',
      'Country': 'USA'
    },
    {
      'EmployeeID': 2,
      'FirstName': 'Andrew',
      'Title': 'Vice President',
      'TitleOfCourtesy': 'Dr.',
      'HireDate': '21/04/2003',
      'City': 'Tacoma',
      'Country': 'USA'
    },
    {
      'EmployeeID': 3,
      'FirstName': 'Janet',
      'Title': 'Sales Representative',
      'TitleOfCourtesy': 'Ms.',
      'HireDate': '22/07/2001',
      'City': 'Kirkland',
      'Country': 'USA'
    }];

    let columnData: ColumnsModel[] = [
        {
            field: 'EmployeeID', label: 'EmployeeID', type: 'number', operators: [{ key: 'Equal', value: 'equal' },
            { key: 'Greater than', value: 'greaterthan' }, { key: 'Less than', value: 'lessthan' }], step: 10
        },
        { field: 'FirstName', label: 'FirstName', type: 'string' },
        { field: 'TitleOfCourtesy', label: 'Title Of Courtesy', type: 'boolean', values: ['Mr.', 'Mrs.'] },
        { field: 'Title', label: 'Title', type: 'string' },
        { field: 'HireDate', label: 'HireDate', type: 'date', format: 'dd/MM/yyyy' },
        { field: 'Country', label: 'Country', type: 'string' },
        { field: 'City', label: 'City', type: 'string' }
    ];
    let importRules: RuleModel = {
        'condition': 'and',
        'rules': [{
            'label': 'HireDate',
            'field': 'HireDate',
            'type': 'date',
            'operator': 'equal',
            'value': '07/05/1991'
        },
        {
            'label': 'Title',
            'field': 'Title',
            'type': 'string',
            'operator': 'equal',
            'value': 'Sales Manager'
        }]
    };
    let qryBldrObj: QueryBuilder = new QueryBuilder({
        width: '70%',
        dataSource: employeeData,
        columns: columnData,
        rule: importRules,
    });
    qryBldrObj.appendTo('#querybuilder');
```

{% endtab %}

## Validation

Validation allows you to validate the conditions and it display errors for invalid fields while using the `validateFields` method.  To enable validation in the query builder , set the allowValidation to true. Column fields are validated after setting [`allowValidation`](https://ej2.syncfusion.com/documentation/api/query-builder/#allowvalidation) to true. So, you should manually configure the validation for Operator and Value fields through [`validation`](https://ej2.syncfusion.com/documentation/api/query-builder/columnsModel/#validation).

> Set [`isRequired`](https://ej2.syncfusion.com/documentation/api/query-builder/validation/#isrequired) validation for Operator and Value fields.
> Set [`min`](https://ej2.syncfusion.com/documentation/api/query-builder/validation/#min), [`max`](https://ej2.syncfusion.com/documentation/api/query-builder/validation/#max) values for number values.

{% tab template= "query-builder/validation", sourceFiles="app.ts,index.html,styles.css",
es5Template="basic-qb-template" %}

```typescript
import { QueryBuilder, ColumnsModel } from '@syncfusion/ej2-querybuilder';
import { Button } from '@syncfusion/ej2-buttons';

let employeeData: Object[] = [{
      'EmployeeID': 1,
      'FirstName': 'Nancy',
      'Title': 'Sales Representative',
      'TitleOfCourtesy': 'Ms.',
      'HireDate': '22/07/2001',
      'City': 'Seattle',
      'Country': 'USA'
    },
    {
      'EmployeeID': 2,
      'FirstName': 'Andrew',
      'Title': 'Vice President',
      'TitleOfCourtesy': 'Dr.',
      'HireDate': '21/04/2003',
      'City': 'Tacoma',
      'Country': 'USA'
    },
    {
      'EmployeeID': 3,
      'FirstName': 'Janet',
      'Title': 'Sales Representative',
      'TitleOfCourtesy': 'Ms.',
      'HireDate': '22/07/2001',
      'City': 'Kirkland',
      'Country': 'USA'
    }];

    let columnData: ColumnsModel[] = [
        { field: 'EmployeeID', label: 'EmployeeID', type: 'number', validation: { isRequired: true } },
        { field: 'FirstName', label: 'FirstName', type: 'string' },
        { field: 'TitleOfCourtesy', label: 'Title Of Courtesy', type: 'boolean', values: ['Mr.', 'Mrs.'] },
        { field: 'Title', label: 'Title', type: 'string' , validation: { isRequired: true } },
        { field: 'HireDate', label: 'HireDate', type: 'date', format: 'dd/MM/yyyy' },
        { field: 'Country', label: 'Country', type: 'string', validation: { isRequired: true } },
        { field: 'City', label: 'City', type: 'string', validation: { isRequired: true } }
    ];
    let qryBldrObj: QueryBuilder = new QueryBuilder({
        width: '70%',
        dataSource: employeeData,
        columns: columnData,
        allowValidation: true
    });
    qryBldrObj.appendTo('#querybuilder');
    let button: Button = new Button({cssClass: `e-primary`, content:'Validation'}, '#qbbutton');
    document.getElementById('qbbutton').onclick = (): void => {
        qryBldrObj.validateFields();
    }
```

{% endtab %}

## Template

Template allows you to define your own input widgets for columns. To implement [`template`](https://ej2.syncfusion.com/documentation/api/query-builder/columnsModel/#template), you can define the following functions

* `create`: Creates the custom component.
* `write`: Wire events for the custom component.
* `Destroy`: Destroy the custom component.

In the following sample, dropdown is used as the custom component in the PaymentMode column.

{% tab template= "query-builder/getting-started", sourceFiles="app.ts,index.html,styles.css",
es5Template="qb-template" %}

```typescript
import { QueryBuilder, ColumnsModel, RuleModel } from '@syncfusion/ej2-querybuilder';
import { getComponent } from '@syncfusion/ej2-base';
import { TextBox } from '@syncfusion/ej2-inputs';
import { DropDownList, MultiSelect, CheckBoxSelection } from '@syncfusion/ej2-dropdowns';

let expenseData: Object[]  = [{
    'Category': 'Food',
    'PaymentMode': 'Credit Card',
    'TransactionType': 'Expense',
    'Description': 'Boiled peanuts',
    'Amount': '7',
    'Date': '06/01/2017'
  }, {

    'Category': 'Food',
    'PaymentMode': 'Cash',
    'TransactionType': 'Expense',
    'Description': 'Peanuts in Coke',
    'Amount': '8',
    'Date': '06/04/2017'
  }, {
    'Category': 'Food',
    'PaymentMode': 'Cash',
    'TransactionType': 'Expense',
    'Description': 'Palmetto Cheese, Mint julep',
    'Amount': '11',
    'Date': '06/04/2017'
  }];

    let elem: HTMLElement;
    let inOperators: string [] = ['in', 'notin'];
    let coulumnData: ColumnsModel[] = [
        { field: 'Category', label: 'Category', type: 'string' },
        { field: 'TransactionType', label: 'Transaction Type', type: 'boolean' },
        {
            field: 'PaymentMode', label: 'Payment Mode', type: 'string', template: {
                create: () => {
                    elem = document.createElement('input');
                    elem.setAttribute('type', 'text');
                    return elem;
                },
                destroy: (args: { elementId: string }) => {
                    let multiSelect: MultiSelect = (getComponent(document.getElementById(args.elementId), 'multiselect') as MultiSelect);
                    if (multiSelect) {
                        multiSelect.destroy();
                    }
                    let dropdown: DropDownList = (getComponent(document.getElementById(args.elementId), 'dropdownlist') as DropDownList);
                    if (dropdown) {
                        dropdown.destroy();
                    }
                },
                write: (args: { elements: Element, values: string[] | string, operator: string }) => {
                    let ds: string[] = ['Cash', 'Debit Card', 'Credit Card', 'Net Banking', 'Wallet'];
                    if (inOperators.indexOf(args.operator) > -1) {
                        let multiSelectObj: MultiSelect = new MultiSelect({
                            dataSource: ds,
                            value: args.values as string [],
                            mode: 'CheckBox',
                            placeholder: 'Select Transaction',
                            change: (e: any) => {
                                qryBldrObj.notifyChange(e.value, e.element);
                            }
                        });
                        multiSelectObj.appendTo('#' + args.elements.id);
                    } else {
                        let dropDownObj: DropDownList = new DropDownList({
                            dataSource: ds,
                            value: args.values as string,
                            change: (e: any) => {
                                qryBldrObj.notifyChange(e.itemData.value, e.element);
                            }
                        });
                        dropDownObj.appendTo('#' + args.elements.id);
                    }
                }
            },
            operators: [
                { value: 'equal', key: 'Equal' },
                { value: 'notequal', key: 'Not Equal' },
                { value: 'in', key: 'In' },
                { value: 'notin', key: 'Not In' }
            ],
        },
        { field: 'Description', label: 'Description', type: 'string' },
        { field: 'Date', label: 'Date', type: 'date' },
        { field: 'Amount', label: 'Amount', type: 'number' }
    ];

    let importRules: RuleModel = {
        'condition': 'and',
        'rules': [{
                'label': 'Payment Mode',
                'field': 'PaymentMode',
                'type': 'string',
                'operator': 'equal',
                'value': 'Cash'
            }
        ]
    };
    let qryBldrObj: QueryBuilder = new QueryBuilder({
        dataSource: expenseData,
        columns: coulumnData,
        width: '70%',
        rule: importRules
    });
    qryBldrObj.appendTo('#querybuilder');

```

{% endtab %}

## Rule Template

Rule Template allows to define your own user interface for columns. To implement [`ruleTemplate`](https://ej2.syncfusion.com/documentation/api/query-builder/columnsModel/#ruleTemplate), you can create the user interface using `x-template` and assign the values through `actionBegin` event.

In the following sample, dropdown and slider are used as the custom component in the Age column and we have applied `greaterthanorequal` operator to this column.

{% tab template= "query-builder/rule-template", sourceFiles="app.ts,index.html,styles.css",
es5Template="qb-template" %}

```typescript
import { QueryBuilder, RuleModel, ColumnsModel, ActionEventArgs} from '@syncfusion/ej2-querybuilder';
import { DropDownList } from '@syncfusion/ej2-dropdowns';
import { Slider } from '@syncfusion/ej2-inputs';
import { employeeData } from './datasource.ts';
import { DataManager, Query } from '@syncfusion/ej2-data';
import { compile } from '@syncfusion/ej2-base';

let filter: ColumnsModel [] = [
    { field: 'EmployeeID', label: 'EmployeeID', type: 'number'},
    { field: 'FirstName', label: 'FirstName', type: 'string'},
    { field: 'LastName', label: 'LastName', type: 'string'},
    { field: 'Age', label: 'Age', type: 'number', ruleTemplate: '#ageTemplate'},
    { field: 'City', label: 'City', type: 'string'},
    { field: 'Country', label: 'Country', type: 'string'},
];

let importRules: RuleModel = {
    'condition': 'and',
    'rules': [{
        'label': 'Age',
        'field': 'Age',
        'type': 'number',
        'operator': 'greaterthanorequal',
        'value': 30
    }]
};

let fieldObj: DropDownList;
let valueObj: Slider;
let ruleID: string;

let queryBldrObj: QueryBuilder = new QueryBuilder({
    columns: filter,
    dataSource: employeeData,
    rule: importRules,
    width: '100%',
    actionBegin: actionBegin
});
queryBldrObj.appendTo('#querybuilder');

function actionBegin(args: ActionEventArgs): void {
    ruleID = args.ruleID;
    if (args.requestType === 'template-create') {
        args.rule.operator = 'greaterthanorequal';
        fieldObj = new DropDownList({
            dataSource: this.columns, // tslint:disable-line
            fields: args.fields,
            value: args.rule.field,
            change: (e: any) => {
                queryBldrObj.notifyChange(e.value, e.element, 'field');
            }
        });
        if (args.rule.value === '') {
            args.rule.value = 30;
        }
        valueObj = new Slider({
            value: args.rule.value as number,
            min: 30,
            max: 50,
            ticks: { placement: 'Before', largeStep: 5, smallStep: 1, showSmallTicks: true },
            change: (e: any) => {
                let elem: HTMLElement = valueObj.element;
                queryBldrObj.notifyChange(e.value, elem, 'value');
                refreshTable(queryBldrObj.getRule(elem), elem.id.split('_valuekey0')[0]);
            },
            created: () => {
                let elem: HTMLElement = valueObj.element;
                refreshTable(queryBldrObj.getRule(elem), elem.id.split('_valuekey0')[0]);
            }
        });
        fieldObj.appendTo('#' + args.ruleID + '_filterkey');
        valueObj.appendTo('#' + args.ruleID + '_valuekey0');
    }
}

function refreshTable(rule: RuleModel, ruleID: string) {
    let template: string = '<tr><td>${EmployeeID}</td><td>${FirstName}</td><td>${Age}</td></tr>';
    let compiledFunction: Function = compile(template);
    let predicate = queryBldrObj.getPredicate({condition: 'and', rules: [rule]});
    let dataManagerQuery: Query = new Query().select(['EmployeeID', 'FirstName', 'Age']).where(predicate);
    let result: Object[] = new DataManager(employeeData).executeLocal(dataManagerQuery);
    let table: HTMLElement = (<HTMLElement>document.querySelector('#' + ruleID + '_section #datatable'));
    if (result.length) {
        table.style.display = 'block';
    } else {
        table.style.display = 'none';
    }
    table.querySelector('tbody').innerHTML = '';
    result.forEach((data: Object) => {
        table.querySelector('tbody').appendChild(compiledFunction(data)[0].querySelector('tr'));
    });
}

```

{% endtab %}