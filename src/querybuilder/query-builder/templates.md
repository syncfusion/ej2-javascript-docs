---
title: "Templates"
component: "QueryBuilder"
description: "Documentation on templates in the Essential JS 2 QueryBuilder control."
---

# Templates

Templates allows users to define customized header and own user interface for columns.

## Header Template

Header Template allows to define your own user interface for Header, which includes creating or deleting rules and groups and to customize the AND/OR condition and NOT condition options. To implement header template in querybuilder, you can create the user interface using `x-template` and assign the values when requestType is header-template-create in  `actionBegin` event.

In the following sample dropdown, splitbutton and button are used as the custom components in the header.

{% tab template= "query-builder/header-template", sourceFiles="app.ts,index.html,styles.css",
es5Template="qb-template" %}

```typescript
import { QueryBuilder, RuleModel, ColumnsModel, ActionEventArgs} from  '@syncfusion/ej2-querybuilder'
import { closest } from '@syncfusion/ej2-base';
import { DropDownButton, ItemModel, MenuEventArgs } from '@syncfusion/ej2-splitbuttons';
import { DropDownList } from '@syncfusion/ej2-dropdowns';
import { CheckBox } from '@syncfusion/ej2-buttons';

let filter: ColumnsModel [] = [
    { field: 'EmployeeID', label: 'EmployeeID', type: 'number'},
    { field: 'FirstName', label: 'FirstName', type: 'string'},
    { field: 'LastName', label: 'LastName', type: 'string'},
    { field: 'Age', label: 'Age', type: 'number'},
    { field: 'City', label: 'City', type: 'string'},
    { field: 'Country', label: 'Country', type: 'string'},
];

let importRules: RuleModel = {
    'condition': 'and', 'not': true,
    'rules': [{
        'label': 'Age',
        'field': 'Age',
        'type': 'number',
        'operator': 'equal',
        'value': 34
    },
    {
        'label': 'LastName',
        'field': 'LastName',
        'type': 'string',
        'operator': 'equal',
        'value': 'vinit'
    },
    {
    'condition': 'or',
    'rules': [{
        'label': 'Age',
        'field': 'Age',
        'type': 'number',
        'operator': 'equal',
        'value': 34
    }]
}]
};

let queryBldrObj: QueryBuilder = new QueryBuilder({
    columns: filter,
    width: '100%',
    rule: importRules,
    headerTemplate: '#headerTemplate',
    actionBegin: actionBegin,
    enableNotCondition: true
});
queryBldrObj.appendTo('#querybuilder');

    function actionBegin(args: ActionEventArgs): void {
        if (args.requestType === 'header-template-create') {
            let checkBoxObj: CheckBox = new CheckBox({
                label: 'NOT',
                checked: args.notCondition,
                change: function(e:any){
                    queryBldrObj.notifyChange(e.checked,e.event.target, 'not')
                }
             });
            checkBoxObj.appendTo('#' + args.ruleID + '_notoption');
            let ds: { [key: string]: Object }[] = [{'key': 'AND', 'value': 'and'},{'key': 'OR', 'value': 'or'}];
            let btnObj: DropDownList= new DropDownList({
                dataSource: ds,
                fields: { text: 'key', value: 'value' },
                value: args.condition,
                cssClass: 'e-custom-group-btn e-active-toggle',
                change: (e: any) => {
                    queryBldrObj.notifyChange(e.value, e.element, 'condition');
                }
            });
            btnObj.appendTo('#' + args.ruleID + '_cndtnbtn');
            let ddbitems: ItemModel[] = [
                { text: 'AddGroup', iconCss: 'e-icons e-add-icon e-addgroup' },
                { text: 'AddCondition', iconCss: 'e-icons e-add-icon e-addrule' }
            ];
            let addbtn: DropDownButton = new DropDownButton({
                items: ddbitems,
                cssClass: 'e-round e-small e-caret-hide e-addrulegroup',
                iconCss: 'e-icons e-add-icon',
                select: function(event: MenuEventArgs) {
                    let addbtn: Element = closest(event.element,'.e-dropdown-popup');  let ddb: string[]= addbtn.id.split('_');
                    if (event.item.text === 'AddGroup') {
                        queryBldrObj.addGroups([{condition: 'and', 'rules': [{}], not: false}], ddb[1]);
                    } else if (event.item.text === 'AddCondition') {
                        queryBldrObj.addRules([{}], ddb[1]);
                    }
                }
            });
            addbtn.appendTo('#' + args.ruleID + '_addbtn');
            let deleteGroup: Element =  document.getElementById(args.ruleID).querySelector('.e-delete-btn');
            if (deleteGroup) {
                (deleteGroup as HTMLElement).onclick = function (e:any) {
                    queryBldrObj.deleteGroup(closest(e.target.offsetParent, '.e-group-container'));
                }
            }
        }
    }
```

{% endtab %}

## Column Template

Column Template allows you to define your own input widgets for columns. To implement [`template`](https://ej2.syncfusion.com/documentation/api/query-builder/columnsModel/#template), you can define the following functions

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
    let columnData: ColumnsModel[] = [
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
        columns: columnData,
        width: '70%',
        rule: importRules
    });
    qryBldrObj.appendTo('#querybuilder');

```

{% endtab %}

### Using Template

Template allows you to define your own input widgets for columns. To implement template in querybuilder, you can create the user interface using `x-template` and assign the values through `actionBegin` event.

{% tab template= "query-builder/template", sourceFiles="app.ts,index.html,styles.css",
es5Template="qb-template" %}

```typescript
import { QueryBuilder, RuleModel, ColumnsModel, ActionEventArgs} from '@syncfusion/ej2-querybuilder';
import { DropDownList } from '@syncfusion/ej2-dropdowns';
import { CheckBox } from '@syncfusion/ej2-buttons';

let filter: ColumnsModel [] = [
    { field:"Category" label:"Category" type:"string"},
    { field: 'PaymentMode', label: 'PaymentMode', type: 'string', operators: customOperators , template:"#paymentTemplate"},
    { field: 'TransactionType', label: 'TransactionType', type: 'string',  operators: customOperators, template:"#transactionTemplate"},
    { field: 'Description', label: 'Description', type: 'string' },
    { field: 'Date', label: 'Date', type: 'string'},
    { field: 'Amount', label: 'Amount', type: 'string'},
];

let customOperators: { [key: string]: Object }[] = [{value: 'equal', key: 'Equal'},
  {value: 'notequal', key: 'Not Equal'}];
let importRules: RuleModel = {
    'condition': 'and',
    'rules': [{
        'label': 'Transaction Type',
        'field': 'TransactionType',
        'type': 'string',
        'operator': 'equal',
        'value': 'Expense'
  },
  {
        'label': 'Payment Mode',
        'field': 'PaymentMode',
        'type': 'string',
        'operator': 'equal',
        'value': 'Cash'
  }]
};

let valueObj: Slider;
let queryBldrObj: QueryBuilder = new QueryBuilder({
    columns: filter,
    rule: importRules,
    width: '100%',
    actionBegin: actionBegin
});
queryBldrObj.appendTo('#querybuilder');


function actionBegin(args: ActionEventArgs): void {
    let ruleID: string = args.ruleID
    if (args.requestType === 'value-template-create') {
        let checkBoxObj: CheckBox = new CheckBox({
            label: 'Is Expense',
            checked: args.rule.value === "Expense" ? true: false,
            change: function(e:any){
                let elem: HTMLElement = document.getElementById(ruleID).querySelector('.e-rule-value');qryBldrObj.notifyChange(e.checked === true ? 'Expense' : 'Income', elem, 'value');
            }
        });
        checkBoxObj.appendTo('#' + args.ruleID + '_checkbox');
        let ds: string[] = ['Cash', 'Debit Card', 'Credit Card', 'Net Banking'];
        let btnObj: DropDownList= new DropDownList({
                dataSource: ds,
                fields: { text: 'key', value: 'value' },
                value: args.rule.value,
                change: (e: any) => {
                 let elem: HTMLElement = document.getElementById(ruleID).querySelector('.e-rule-value');qryBldrObj.notifyChange(e.value as string, elem, 'value');
                }
        });
        btnObj.appendTo('#' + args.ruleID + '_paymentlist');
    }
}
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