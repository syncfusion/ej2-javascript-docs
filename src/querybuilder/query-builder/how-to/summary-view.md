---
title: "How To"
component: "QueryBuilder"
description: "Learn how to enable summary view in the Essential JS 2 QueryBuilder control."
---

# Summary View

Summary view allows you to show or hide the filtered query. By default, the value is false. You can enable this feature by setting the [`summaryView`](https://ej2.syncfusion.com/documentation/api/query-builder/#summaryview) property to true.

{% tab template= "query-builder/getting-started", sourceFiles="app.ts,index.html,styles.css,datasource.ts",
es5Template="summaryview-qb-template", isDefaultActive=true %}

```typescript
import { QueryBuilder, ColumnsModel, RuleModel } from '@syncfusion/ej2-querybuilder';
import { employeeData } from './datasource.ts';

    let columnData: ColumnsModel[] = [
        {
            field: 'EmployeeID', label: 'EmployeeID', type: 'number'
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
        'label': 'EmployeeID',
        'field': 'EmployeeID',
        'type': 'number',
        'operator': 'notequal',
        'value': '5'
    },
    {
        'condition': 'or',
        'rules': [{
            'label': 'Title Of Courtesy',
                'field': 'TitleOfCourtesy',
                'type': 'string',
                'operator': 'equal',
                'value': 'Mr.'
        },
        {
            'label': 'Country',
            'field': 'Country',
            'type': 'string',
            'operator': 'equal',
            'value': 'USA'
        },
        {
        'condition': 'and',
            'rules': [{
                'label': 'City',
                'field': 'City',
                'type': 'string',
                'operator': 'equal',
                'value': 'London'
            }]
        }]
    }]
    };
    let qryBldrObj: QueryBuilder = new QueryBuilder({
        width: '30%',
        dataSource: employeeData,
        columns: columnData,
        rule: importRules,
        summaryView: "true"
    });
    qryBldrObj.appendTo('#querybuilder');
```

{% endtab %}