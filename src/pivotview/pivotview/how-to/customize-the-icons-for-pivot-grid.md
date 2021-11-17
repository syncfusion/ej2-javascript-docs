# Customize the icons for pivot grid

You can customize the pivot button icons in the pivot grid by overriding the class **.pivot-button** with a custom property content as mentioned below.

```typescript

#PivotView_PivotFieldList .e-icons.e-toggle-field-list::before {
    content: '\e337';
}

```

In the below sample, pivot grid is rendered with a customized pivot button icons.

{% tab template="pivot-grid/icon-customize", es5Template="icon-customize", sourceFiles="index.ts,index.html" %}

```typescript
import { PivotView, IDataSet, FieldList } from '@syncfusion/ej2-pivotview';
import { pivotData } from './datasource.ts';

PivotView.Inject(FieldList);
let pivotGridObj: PivotView = new PivotView({
    dataSource: {
        data: pivotData as IDataSet[],
        expandAll: false,
        enableSorting: true,
        allowLabelFilter: true,
        allowValueFilter: true,
        columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
        values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }],
        rows: [{ name: 'Country' }, { name: 'Products' }],
        formatSettings: [{ name: 'Amount', format: 'C0' }],
        filters: []
    },
    showFieldList: true,
});
pivotGridObj.appendTo('#PivotGrid');

```

{% endtab %}
