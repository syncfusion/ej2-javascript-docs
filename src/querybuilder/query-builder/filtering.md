---
title: "Filtering"
component: "QueryBuilder"
description: "Learn how to filtering in the Essential JS 2 QueryBuilder control."
---

# Filtering

Query Builder allows you to create or delete conditions and groups. You can use [`showButtons`](https://ej2.syncfusion.com/documentation/api/query-builder/#showbuttons) to enable/disable these buttons.

You can create or delete conditions by interacting through the user interface and methods.

* Use the [`addRules`](https://ej2.syncfusion.com/documentation/api/query-builder/#addrules), and [`deleteRules`](https://ej2.syncfusion.com/documentation/api/query-builder/#deleterules) methods to create/delete conditions.
* Use [`addGroups`](https://ej2.syncfusion.com/documentation/api/query-builder/#addgroups), and [`deleteGroups`](https://ej2.syncfusion.com/documentation/api/query-builder/#deletegroups) methods to create/delete groups.

{% tab template= "query-builder/filtering", sourceFiles="app.ts,index.html,styles.css",
es5Template="basic-qb-template", isDefaultActive=true %}

```typescript
import { QueryBuilder, ColumnsModel, RuleModel } from '@syncfusion/ej2-querybuilder';
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
        {
            field: 'EmployeeID', label: 'Employee ID', type: 'number'
        },
        { field: 'FirstName', label: 'First Name', type: 'string' },
        { field: 'TitleOfCourtesy', label: 'Title Of Courtesy', type: 'boolean', values: ['Mr.', 'Mrs.'] },
        { field: 'Title', label: 'Title', type: 'string' },
        { field: 'HireDate', label: 'Hire Date', type: 'date', format: 'dd/MM/yyyy' },
        { field: 'Country', label: 'Country', type: 'string' },
        { field: 'City', label: 'City', type: 'string' }
    ];
    let importRules: RuleModel = {
        'condition': 'and',
        'rules': [{
            'label': 'Employee ID',
            'field': 'EmployeeID',
            'type': 'number',
            'operator': 'equal',
            'value': 1001
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
        showButtons: { ruleDelete: true , groupInsert: true, groupDelete: true }
        rule: importRules
    });
    qryBldrObj.appendTo('#querybuilder');
     let button: Button = new Button({cssClass: `e-primary`, content:'Add Rule' }, '#qbaddrule');
     button = new Button({cssClass: `e-primary`, content:'Add Group'}, '#qbaddgroup');
     button = new Button({cssClass: `e-primary`,  content:'Delete Group' }, '#qbdeletegroup');
    document.getElementById('qbaddrule').onclick = (): void => {
        qryBldrObj.addRules([{'label': 'Employee ID','field': 'EmployeeID','type': 'number','operator': 'equal','value': '1091'}], 'group0'});
    }
     document.getElementById('qbaddgroup').onclick = (): void => {
       qryBldrObj.addGroups([{'condition': 'and','rules': [{'label': 'First Name','field': 'FirstName','type': 'string','operator': 'startswith','value': 'v' }]}], 'group0');
    }
     document.getElementById('qbdeletegroup').onclick = (): void => {
       qryBldrObj.deleteGroups(['group1']);
    }
```

{% endtab %}