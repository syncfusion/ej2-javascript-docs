---
title: "Import and Export"
component: "QueryBuilder"
description: "Learn how to import end export the rules in the Essential JS 2 QueryBuilder control."
---

# Importing

Importing allows you to view or edit the predefined conditions which is available in JSON or SQL. You can import the conditions either initial rendering or post rendering.

## Initial rendering

To apply conditions initially, you can define the [`rule`](https://ej2.syncfusion.com/documentation/api/query-builder/#rule). Here, you can import structured JSON object by defining the [`rule`](https://ej2.syncfusion.com/documentation/api/query-builder/#rule) property.

{% tab template= "query-builder/getting-started", sourceFiles="app.ts,index.html,styles.css,datasource.ts",
es5Template="initialrender-qb-template", isDefaultActive=true %}

```typescript
import { QueryBuilder, ColumnsModel, RuleModel } from '@syncfusion/ej2-querybuilder';

let hardwareData: Object[]  = [{
      'TaskID': 1,
      'Name': 'Lenovo Yoga',
      'Category': 'Laptop',
      'SerialNo': 'CB27932009',
      'InvoiceNo': 'INV-2878',
      'Status': 'Assigned'
  },
  {
      'TaskID': 2,
      'Name': 'Acer Aspire',
      'Category': 'Others',
      'SerialNo': 'CB35728290',
      'InvoiceNo': 'INV-3456',
      'Status': 'In-repair'
  },
  {
      'TaskID': 3,
      'Name': 'Apple MacBook',
      'Category': 'Laptop',
      'SerialNo': 'CB35628728',
      'InvoiceNo': 'INV-2763',
      'Status': 'In-repair'
  }];

    let columnData: ColumnsModel[] = [
        { field: 'TaskID', label: 'Task ID', type: 'number' },
        { field: 'Name', label: 'Name', type: 'string' },
        { field: 'Category', label: 'Category', type: 'string' },
        { field: 'SerialNo', label: 'Serial No', type: 'string' },
        { field: 'InvoiceNo', label: 'Invoice No', type: 'string' },
        { field: 'Status', label: 'Status', type: 'string' }
    ];
    let importRules: RuleModel = {
        'condition': 'or',
        'rules': [{
            'label': 'Category',
            'field': 'Category',
            'type': 'string',
            'operator': 'equal',
            'value': 'Laptop'
        },
        {
        'condition': 'and',
            'rules': [{
                'label': 'Status',
                'field': 'Status',
                'type': 'string',
                'operator': 'notequal',
                'value': 'Pending'
            },
            {
                'label': 'Task ID',
                'field': 'TaskID',
                'type': 'number',
                'operator': 'equal',
                'value': 5675
            }]
        }]
    };

    let qryBldrObj: QueryBuilder = new QueryBuilder({
        width: '70%',
        dataSource: hardwareData,
        columns: columnData,
        rule: importRules,
    });
    qryBldrObj.appendTo('#querybuilder');
```

{% endtab %}

## Post rendering

### Importing from JSON

You can set the conditions from structured JSON object through the [`setRules`](https://ej2.syncfusion.com/documentation/api/query-builder/#setrules) method.

{% tab template= "query-builder/import-json", sourceFiles="app.ts,index.html,styles.css",
es5Template="basic-qb-template" %}

```typescript
import { QueryBuilder, ColumnsModel, RuleModel } from '@syncfusion/ej2-querybuilder';
import { Button } from '@syncfusion/ej2-buttons';

let hardwareData: Object[]  = [{
      'TaskID': 1,
      'Name': 'Lenovo Yoga',
      'Category': 'Laptop',
      'SerialNo': 'CB27932009',
      'InvoiceNo': 'INV-2878',
      'Status': 'Assigned'
  },
  {
      'TaskID': 2,
      'Name': 'Acer Aspire',
      'Category': 'Others',
      'SerialNo': 'CB35728290',
      'InvoiceNo': 'INV-3456',
      'Status': 'In-repair'
  },
  {
      'TaskID': 3,
      'Name': 'Apple MacBook',
      'Category': 'Laptop',
      'SerialNo': 'CB35628728',
      'InvoiceNo': 'INV-2763',
      'Status': 'In-repair'
  }];

    let columnData: ColumnsModel[] = [
        { field: 'TaskID', label: 'Task ID', type: 'number' },
        { field: 'Name', label: 'Name', type: 'string' },
        { field: 'Category', label: 'Category', type: 'string' },
        { field: 'SerialNo', label: 'Serial No', type: 'string' },
        { field: 'InvoiceNo', label: 'Invoice No', type: 'string' },
        { field: 'Status', label: 'Status', type: 'string' }
    ];
 let importRules: RuleModel = {
        'condition': 'or',
        'rules': [{
            'label': 'Category',
            'field': 'Category',
            'type': 'string',
            'operator': 'equal',
            'value': 'Laptop'
        },
        {
        'condition': 'and',
            'rules': [{
                'label': 'Status',
                'field': 'Status',
                'type': 'string',
                'operator': 'notequal',
                'value': 'Pending'
            },
            {
                'label': 'Task ID',
                'field': 'TaskID',
                'type': 'number',
                'operator': 'equal',
                'value': 5675
            }]
        }]
    };
    let qryBldrObj: QueryBuilder = new QueryBuilder({
        width: '70%',
        dataSource: hardwareData,
        columns: columnData
    });
    qryBldrObj.appendTo('#querybuilder');
    let button: Button = new Button({cssClass: `e-primary`, content:'set Rules'}, '#importjson');
    document.getElementById('importjson').onclick = (): void => {
        qryBldrObj.setRules(importRules);
    }

```

{% endtab %}

### Importing from SQL

You can set the conditions from SQL query through the [`setRulesFromSql`](https://ej2.syncfusion.com/documentation/api/query-builder/#setrulesfromsql) method.

{% tab template= "query-builder/import-sql", sourceFiles="app.ts,index.html,styles.css",
es5Template="basic-qb-template" %}

```typescript
import { QueryBuilder, ColumnsModel, RuleModel } from '@syncfusion/ej2-querybuilder';
import { Button } from '@syncfusion/ej2-buttons';

let hardwareData: Object[]  = [{
      'TaskID': 1,
      'Name': 'Lenovo Yoga',
      'Category': 'Laptop',
      'SerialNo': 'CB27932009',
      'InvoiceNo': 'INV-2878',
      'Status': 'Assigned'
  },
  {
      'TaskID': 2,
      'Name': 'Acer Aspire',
      'Category': 'Others',
      'SerialNo': 'CB35728290',
      'InvoiceNo': 'INV-3456',
      'Status': 'In-repair'
  },
  {
      'TaskID': 3,
      'Name': 'Apple MacBook',
      'Category': 'Laptop',
      'SerialNo': 'CB35628728',
      'InvoiceNo': 'INV-2763',
      'Status': 'In-repair'
  }];

    let columnData: ColumnsModel[] = [
        { field: 'TaskID', label: 'Task ID', type: 'number' },
        { field: 'Name', label: 'Name', type: 'string' },
        { field: 'Category', label: 'Category', type: 'string' },
        { field: 'SerialNo', label: 'Serial No', type: 'string' },
        { field: 'InvoiceNo', label: 'Invoice No', type: 'string' },
        { field: 'Status', label: 'Status', type: 'string' }
    ];

    let qryBldrObj: QueryBuilder = new QueryBuilder({
        width: '70%',
        dataSource: hardwareData,
        columns: columnData,
    });
    qryBldrObj.appendTo('#querybuilder');
    let button: Button = new Button({cssClass: `e-primary`, content:'set Rules'}, '#importsql');
    document.getElementById('importsql').onclick = (): void => {
        qryBldrObj.setRulesFromSql("TaskID = 1 and Status LIKE ('Assigned%')");
    }
```

{% endtab %}

# Exporting

Exporting allows you to save or maintain the created conditions through the Query Builder. You can export the defined conditions by the following ways.

## Exporting to JSON

You can export the defined conditions to structured JSON object through the [`getRules`](https://ej2.syncfusion.com/documentation/api/query-builder/#getrules) method.

## Exporting to SQL

You can export the defined conditions to SQL query through the [`getRulesFromSql`](https://ej2.syncfusion.com/documentation/api/query-builder/#getrulesfromsql) method.

{% tab template= "query-builder/export", sourceFiles="app.ts,index.html,styles.css",
es5Template="basic-qb-template" %}

```typescript
import { QueryBuilder, ColumnsModel, RuleModel } from '@syncfusion/ej2-querybuilder';
import { Button } from '@syncfusion/ej2-buttons';
import { Dialog } from '@syncfusion/ej2-popups';

let hardwareData: Object[]  = [{
      'TaskID': 1,
      'Name': 'Lenovo Yoga',
      'Category': 'Laptop',
      'SerialNo': 'CB27932009',
      'InvoiceNo': 'INV-2878',
      'Status': 'Assigned'
  },
  {
      'TaskID': 2,
      'Name': 'Acer Aspire',
      'Category': 'Others',
      'SerialNo': 'CB35728290',
      'InvoiceNo': 'INV-3456',
      'Status': 'In-repair'
  },
  {
      'TaskID': 3,
      'Name': 'Apple MacBook',
      'Category': 'Laptop',
      'SerialNo': 'CB35628728',
      'InvoiceNo': 'INV-2763',
      'Status': 'In-repair'
  }];

    let columnData: ColumnsModel[] = [
        { field: 'TaskID', label: 'Task ID', type: 'number' },
        { field: 'Name', label: 'Name', type: 'string' },
        { field: 'Category', label: 'Category', type: 'string' },
        { field: 'SerialNo', label: 'Serial No', type: 'string' },
        { field: 'InvoiceNo', label: 'Invoice No', type: 'string' },
        { field: 'Status', label: 'Status', type: 'string' }
    ];
     let importRules: RuleModel = {
        'condition': 'or',
        'rules': [{
            'label': 'Category',
            'field': 'Category',
            'type': 'string',
            'operator': 'equal',
            'value': 'Laptop'
        }]
    };
    let qryBldrObj: QueryBuilder = new QueryBuilder({
        width: '70%',
        dataSource: hardwareData,
        columns: columnData,
        rule: importRules
    });
     qryBldrObj.appendTo('#querybuilder');
    let dialogObj: Dialog = new Dialog({
        header: 'Query builder',
        height: 'auto',
        animationSettings: { effect: 'Zoom', duration: 400 },
        showCloseIcon: true,
        width: '50%',
        visible: false
    });
    dialogObj.appendTo('#defaultdialog');
    let button: Button = new Button({cssClass: `e-primary`, content:'get sql'}, '#getsql');
    document.getElementById('getsql').onclick = (): void => {
        dialogObj.content = qryBldrObj.getSqlFromRules(qryBldrObj.getRules());
         dialogObj.show();
    }
    button = new Button({cssClass: `e-primary`, content:'get rule'}, '#getrule');
    document.getElementById('getrule').onclick = (): void => {
        let validRule: RuleModel = qryBldrObj.getValidRules(qryBldrObj.rule);
         dialogObj.content = '<pre>' + JSON.stringify(validRule, null, 4) + '</pre>';
         dialogObj.show();
    }
```

{% endtab %}