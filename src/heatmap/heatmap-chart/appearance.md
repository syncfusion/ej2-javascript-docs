---
title: "Appearance"
component: "HeatMap Chart"
description: "This section describes on how to customize the overall apperance of the Heatmap, like adding borders for heatmap cells or data points, adding margin and title for heatmap layout, mouse hover highligting options for the cells and formatting options for the data labels"
---

# Appearance

## Cell/customizations

You can customize the cell by using the `cellSettings` property.

### Border

Change the width, color, and radius of the heat map cells by using the [`border`](../api/heatmap/cellSettings/#border) property.

{% tab template= "heatmap/appearance", es5Template="es5Border" %}

```typescript

import { HeatMap, Tooltip } from '@syncfusion/ej2-heatmap';
HeatMap.Inject(Tooltip);
let heatmapData: any [] = [
            [73, 39, 26, 39, 94, 0],
            [93, 58, 53, 38, 26, 68],
            [99, 28, 22, 4, 66, 90],
            [14, 26, 97, 69, 69, 3],
            [7, 46, 47, 47, 88, 6],
            [41, 55, 73, 23, 3, 79],
            [56, 69, 21, 86, 3, 33],
            [45, 7, 53, 81, 95, 79],
            [60, 77, 74, 68, 88, 51],
            [25, 25, 10, 12, 78, 14],
            [25, 56, 55, 58, 12, 82],
            [74, 33, 88, 23, 86, 59]];

let heatmap: HeatMap = new HeatMap({
    titleSettings: {
            text: 'Sales Revenue per Employee (in 1000 US$)',
            textStyle: {
                size: '15px',
                fontWeight: '500',
                fontStyle: 'Normal',
                fontFamily: 'Segoe UI'
            }
        },
        xAxis: {
            labels: ['Nancy', 'Andrew', 'Janet', 'Margaret', 'Steven',
            'Michael', 'Robert', 'Laura', 'Anne', 'Paul', 'Karin',   'Mario'],
        },
        yAxis: {
            labels: ['Mon', 'Tues', 'Wed', 'Thurs', 'Fri', 'Sat'],
        },
        dataSource: heatmapData,
        cellSettings: {
            border: {
                width: 1,
                radius: 4,
                color: 'white'
            }
        },
});
heatmap.appendTo('#element');

```

{% endtab %}

### Cell Highlighting

Enable or disable the cell highlighting while hover over the heat map cells by using the [`enableCellHighlighting`](../api/heatmap/cellSettings/#enablecellhighlighting) property.

>Note: The cell highlighting only works in a SVG rendering mode.

{% tab template= "heatmap/appearance", es5Template="es5CellHighlight" %}

```typescript

import { HeatMap, Tooltip } from '@syncfusion/ej2-heatmap';
HeatMap.Inject(Tooltip);

let heatmapData: any [] = [
            [73, 39, 26, 39, 94, 0],
            [93, 58, 53, 38, 26, 68],
            [99, 28, 22, 4, 66, 90],
            [14, 26, 97, 69, 69, 3],
            [7, 46, 47, 47, 88, 6],
            [41, 55, 73, 23, 3, 79],
            [56, 69, 21, 86, 3, 33],
            [45, 7, 53, 81, 95, 79],
            [60, 77, 74, 68, 88, 51],
            [25, 25, 10, 12, 78, 14],
            [25, 56, 55, 58, 12, 82],
            [74, 33, 88, 23, 86, 59]];

let heatmap: HeatMap = new HeatMap({
    titleSettings: {
            text: 'Sales Revenue per Employee (in 1000 US$)',
            textStyle: {
                size: '15px',
                fontWeight: '500',
                fontStyle: 'Normal',
                fontFamily: 'Segoe UI'
            }
        },
        xAxis: {
            labels: ['Nancy', 'Andrew', 'Janet', 'Margaret', 'Steven',
            'Michael', 'Robert', 'Laura', 'Anne', 'Paul', 'Karin',   'Mario'],
        },
        yAxis: {
            labels: ['Mon', 'Tues', 'Wed', 'Thurs', 'Fri', 'Sat'],
        },
        dataSource: heatmapData,
        cellSettings: {
          enableCellHighlighting: true
        },
});
heatmap.appendTo('#element');

```

{% endtab %}

### Color gradient mode

You can set the minimum and maximum value colors based on row and column using the `colorGradientMode` property.
The types of colorGradientMode,

* Table: The minimum and maximum value colors calculated for overall data.
* Row: The minimum and maximum value colors calculated for each row of data.
* Column: The minimum and maximum value colors calculated for each column of data.

>Note: The default value of `colorGradientMode` is Table.

{% tab template= "heatmap/appearance", es5Template="es5ColorMode" %}

```typescript

import { HeatMap, Tooltip } from '@syncfusion/ej2-heatmap';
HeatMap.Inject(Tooltip);

let heatmapData: any [] = [
            [73, 39, 26, 39, 94, 0],
            [93, 58, 53, 38, 26, 68],
            [99, 28, 22, 4, 66, 90],
            [14, 26, 97, 69, 69, 3],
            [7, 46, 47, 47, 88, 6],
            [41, 55, 73, 23, 3, 79],
            [56, 69, 21, 86, 3, 33],
            [45, 7, 53, 81, 95, 79],
            [60, 77, 74, 68, 88, 51],
            [25, 25, 10, 12, 78, 14],
            [25, 56, 55, 58, 12, 82],
            [74, 33, 88, 23, 86, 59]];

let heatmap: HeatMap = new HeatMap({
    titleSettings: {
            text: 'Sales Revenue per Employee (in 1000 US$)',
            textStyle: {
                size: '15px',
                fontWeight: '500',
                fontStyle: 'Normal',
                fontFamily: 'Segoe UI'
            }
        },
        xAxis: {
            labels: ['Nancy', 'Andrew', 'Janet', 'Margaret', 'Steven',
            'Michael', 'Robert', 'Laura', 'Anne', 'Paul', 'Karin',   'Mario'],
        },
        yAxis: {
            labels: ['Mon', 'Tues', 'Wed', 'Thurs', 'Fri', 'Sat'],
        },
        dataSource: heatmapData,
        cellSettings: {
            enableCellHighlighting: true
        },
        paletteSettings: {
            colorGradientMode: 'Column'
        }
});
heatmap.appendTo('#element');

```

{% endtab %}

## Margin

Set the margin for the heat map from its container by using the [`margin`](../api/heatmap/#margin) property.

{% tab template= "heatmap/appearance", es5Template="es5Margin" %}

```typescript

import { HeatMap, Tooltip } from '@syncfusion/ej2-heatmap';
HeatMap.Inject(Tooltip);

let heatmapData: any [] = [
            [73, 39, 26, 39, 94, 0],
            [93, 58, 53, 38, 26, 68],
            [99, 28, 22, 4, 66, 90],
            [14, 26, 97, 69, 69, 3],
            [7, 46, 47, 47, 88, 6],
            [41, 55, 73, 23, 3, 79],
            [56, 69, 21, 86, 3, 33],
            [45, 7, 53, 81, 95, 79],
            [60, 77, 74, 68, 88, 51],
            [25, 25, 10, 12, 78, 14],
            [25, 56, 55, 58, 12, 82],
            [74, 33, 88, 23, 86, 59]];

let heatmap: HeatMap = new HeatMap({
    margin: { left: 15, right: 15, top: 15, bottom: 15 },
    titleSettings: {
            text: 'Sales Revenue per Employee (in 1000 US$)',
            textStyle: {
                size: '15px',
                fontWeight: '500',
                fontStyle: 'Normal',
                fontFamily: 'Segoe UI'
            }
        },
        xAxis: {
            labels: ['Nancy', 'Andrew', 'Janet', 'Margaret', 'Steven',
            'Michael', 'Robert', 'Laura', 'Anne', 'Paul', 'Karin',   'Mario'],
        },
        yAxis: {
            labels: ['Mon', 'Tues', 'Wed', 'Thurs', 'Fri', 'Sat'],
        },
        dataSource: heatmapData,
});
heatmap.appendTo('#element');

```

{% endtab %}

## Title

The title is used to provide a quick information about the data plotted in heat map. The [`text`](../api/heatmap/title/#text) property is used to set the title for heat map. You can also customize text style of a title by using the [`textStyle`](../api/heatmap/title/#textstyle) property.

{% tab template= "heatmap/appearance", es5Template="es5Title"%}

```typescript

import { HeatMap, Legend, Tooltip } from '@syncfusion/ej2-heatmap';
HeatMap.Inject(Legend, Tooltip);

let heatmapData: any [] = [
            [73, 39, 26, 39, 94, 0],
            [93, 58, 53, 38, 26, 68],
            [99, 28, 22, 4, 66, 90],
            [14, 26, 97, 69, 69, 3],
            [7, 46, 47, 47, 88, 6],
            [41, 55, 73, 23, 3, 79],
            [56, 69, 21, 86, 3, 33],
            [45, 7, 53, 81, 95, 79],
            [60, 77, 74, 68, 88, 51],
            [25, 25, 10, 12, 78, 14],
            [25, 56, 55, 58, 12, 82],
            [74, 33, 88, 23, 86, 59]];

let heatmap: HeatMap = new HeatMap({
    titleSettings: {
            text: 'Sales Revenue per Employee (in 1000 US$)',
            textStyle: {
                size: '15px',
                fontWeight: '500',
                fontStyle: 'Italic',
                fontFamily: 'Segoe UI'
            }
        },
        xAxis: {
            labels: ['Nancy', 'Andrew', 'Janet', 'Margaret', 'Steven',
            'Michael', 'Robert', 'Laura', 'Anne', 'Paul', 'Karin',   'Mario'],
        },
        yAxis: {
            labels: ['Mon', 'Tues', 'Wed', 'Thurs', 'Fri', 'Sat'],
        },
     dataSource: heatmapData,
});
heatmap.appendTo('#element');
```

{% endtab %}

## Data label

You can toggle the visibility of data labels by using the [`showLabel`](../api/heatmap/cellSettings/#showlabel) property . By default, the data label will be visible.

{% tab template= "heatmap/appearance", es5Template="es5DataLabel" %}

```typescript

import { HeatMap, Tooltip } from '@syncfusion/ej2-heatmap';
HeatMap.Inject(Tooltip);

let heatmapData: any [] = [
            [73, 39, 26, 39, 94, 0],
            [93, 58, 53, 38, 26, 68],
            [99, 28, 22, 4, 66, 90],
            [14, 26, 97, 69, 69, 3],
            [7, 46, 47, 47, 88, 6],
            [41, 55, 73, 23, 3, 79],
            [56, 69, 21, 86, 3, 33],
            [45, 7, 53, 81, 95, 79],
            [60, 77, 74, 68, 88, 51],
            [25, 25, 10, 12, 78, 14],
            [25, 56, 55, 58, 12, 82],
            [74, 33, 88, 23, 86, 59]];

let heatmap: HeatMap = new HeatMap({
    titleSettings: {
            text: 'Sales Revenue per Employee (in 1000 US$)',
            textStyle: {
                size: '15px',
                fontWeight: '500',
                fontStyle: 'Normal',
                fontFamily: 'Segoe UI'
            }
        },
        xAxis: {
            labels: ['Nancy', 'Andrew', 'Janet', 'Margaret', 'Steven',
            'Michael', 'Robert', 'Laura', 'Anne', 'Paul', 'Karin',   'Mario'],
        },
        yAxis: {
            labels: ['Mon', 'Tues', 'Wed', 'Thurs', 'Fri', 'Sat'],
        },
        dataSource: heatmapData,
        cellSettings: {
          showLabel: false
        },
});
heatmap.appendTo('#element');
```

{% endtab %}

### Text style

You can customize the font family, font size, and color of the data label by using the [`textStyle`](../api/heatmap/cellSettings/#textstyle) in the `cellSettings` property.

{% tab template= "heatmap/appearance", es5Template="es5TextStyle" %}

```typescript

import { HeatMap, Tooltip } from '@syncfusion/ej2-heatmap';
HeatMap.Inject(Tooltip);

let heatmapData: any [] = [
            [73, 39, 26, 39, 94, 0],
            [93, 58, 53, 38, 26, 68],
            [99, 28, 22, 4, 66, 90],
            [14, 26, 97, 69, 69, 3],
            [7, 46, 47, 47, 88, 6],
            [41, 55, 73, 23, 3, 79],
            [56, 69, 21, 86, 3, 33],
            [45, 7, 53, 81, 95, 79],
            [60, 77, 74, 68, 88, 51],
            [25, 25, 10, 12, 78, 14],
            [25, 56, 55, 58, 12, 82],
            [74, 33, 88, 23, 86, 59]];

let heatmap: HeatMap = new HeatMap({
    titleSettings: {
            text: 'Sales Revenue per Employee (in 1000 US$)',
            textStyle: {
                size: '15px',
                fontWeight: '500',
                fontStyle: 'Normal',
                fontFamily: 'Segoe UI'
            }
        },
        xAxis: {
            labels: ['Nancy', 'Andrew', 'Janet', 'Margaret', 'Steven',
            'Michael', 'Robert', 'Laura', 'Anne', 'Paul', 'Karin',   'Mario'],
        },
        yAxis: {
            labels: ['Mon', 'Tues', 'Wed', 'Thurs', 'Fri', 'Sat'],
        },
        dataSource: heatmapData,
        cellSettings: {
          textStyle: {
                fontStyle: 'Italic',
                fontFamily: 'Segoe UI'
            }
        },
});
heatmap.appendTo('#element');
```

{% endtab %}

### Format

You can change the format of the data label, such as currency, decimal, percent etc. by using [`format`](../api/heatmap/cellSettings/#format) property.

{% tab template= "heatmap/appearance", es5Template="es5CellFormat" %}

```typescript

import { HeatMap, Tooltip } from '@syncfusion/ej2-heatmap';
HeatMap.Inject(Tooltip);

let heatmapData: any [] = [
            [73, 39, 26, 39, 94, 0],
            [93, 58, 53, 38, 26, 68],
            [99, 28, 22, 4, 66, 90],
            [14, 26, 97, 69, 69, 3],
            [7, 46, 47, 47, 88, 6],
            [41, 55, 73, 23, 3, 79],
            [56, 69, 21, 86, 3, 33],
            [45, 7, 53, 81, 95, 79],
            [60, 77, 74, 68, 88, 51],
            [25, 25, 10, 12, 78, 14],
            [25, 56, 55, 58, 12, 82],
            [74, 33, 88, 23, 86, 59]];

let heatmap: HeatMap = new HeatMap({
    titleSettings: {
            text: 'Sales Revenue per Employee (in 1000 US$)',
            textStyle: {
                size: '15px',
                fontWeight: '500',
                fontStyle: 'Normal',
                fontFamily: 'Segoe UI'
            }
        },
        xAxis: {
            labels: ['Nancy', 'Andrew', 'Janet', 'Margaret', 'Steven',
            'Michael', 'Robert', 'Laura', 'Anne', 'Paul', 'Karin',   'Mario'],
        },
        yAxis: {
            labels: ['Mon', 'Tues', 'Wed', 'Thurs', 'Fri', 'Sat'],
        },
        dataSource: heatmapData,
        cellSettings: {
          format: '{value} $'
        },
});
heatmap.appendTo('#element');
```

{% endtab %}

## Customize the cell value

In the HeatMap, you can customize the cell value using the [`cellRender`](../api/heatmap/#cellrender)client-side event.

{% tab template= "heatmap/appearance", es5Template="es5CellRender" %}

```typescript

import { HeatMap, Tooltip, ICellEventArgs } from '@syncfusion/ej2-heatmap';
HeatMap.Inject(Tooltip);

let heatmapData: any [] = [
            [73, 39, 26, 39, 94, 1],
            [93, 58, 53, 38, 26, 68],
            [99, 28, 22, 4, 66, 90],
            [14, 26, 97, 69, 69, 3],
            [7, 46, 47, 47, 88, 6],
            [41, 55, 73, 23, 3, 79],
            [56, 69, 21, 86, 3, 33],
            [45, 7, 53, 81, 95, 79],
            [60, 77, 74, 68, 88, 51],
            [25, 25, 10, 12, 78, 14],
            [25, 56, 55, 58, 12, 82],
            [74, 33, 88, 23, 86, 59]];

let heatmap: HeatMap = new HeatMap({
    titleSettings: {
            text: 'Sales Revenue per Employee (in US$)',
            textStyle: {
                size: '15px',
                fontWeight: '500',
                fontStyle: 'Normal',
                fontFamily: 'Segoe UI'
            }
        },
        xAxis: {
            labels: ['Nancy', 'Andrew', 'Janet', 'Margaret', 'Steven',
            'Michael', 'Robert', 'Laura', 'Anne', 'Paul', 'Karin',   'Mario'],
        },
        yAxis: {
            labels: ['Mon', 'Tues', 'Wed', 'Thurs', 'Fri', 'Sat'],
        },
        dataSource: heatmapData,
        cellRender: (args: ICellEventArgs) => {
            args.displayText = (args.value as number) + 'K';
        },
}); heatmap.appendTo('#element');

```

{% endtab %}

## See Also

* [To customize the appearance of tool tip](./tooltip/#customize-the-appearance-of-tooltip)
