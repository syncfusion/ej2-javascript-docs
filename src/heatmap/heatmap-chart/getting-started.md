---
title: "Getting started"
component: "HeatMap Chart"
description: "This section describes on how to visualize a two-dimensional data by enabling the basic features in heatmap"
---

# Getting Started

The Essential JS 2 for JavaScript (global script) is an ES5 formatted pure JavaScript framework which can be directly used in latest web browsers.

## control Initialization

The Essential JS 2 JavaScript controls can be initialized by using either of the following ways.

* Using local script and style references in a HTML page.
* Using CDN link for script and style reference.

### Using local script and style references in a HTML page

**Step 1:** Create an app folder `myapp` for Essential JS 2 JavaScript controls.

**Step 2:** You can get the global scripts and styles from the [Essential Studio JavaScript (Essential JS 2)](https://www.syncfusion.com/downloads/essential-js2) build installed location.

**Syntax:**
> Script: `**(installed location)**/Syncfusion/Essential Studio/{RELEASE_VERSION}/Essential JS 2/{PACKAGE_NAME}/dist/global/{PACKAGE_NAME}.min.js`

**Example:**

> Script: `C:/Program Files (x86)/Syncfusion/Essential Studio/16.2.45/Essential JS 2/ej2-heatmap/dist/global/ej2-heatmap.min.js`

**Step 3:** Create a folder `myapp/resources` and copy/paste the dependent scripts and styles from the above installed location to `myapp/resources` location.

**Step 4:** Create a HTML page (index.html) in `myapp` location and add the Essentials JS 2 script and style references.

```html
<!DOCTYPE html>
  <html xmlns="http://www.w3.org/1999/xhtml">
       <head>
            <title>Essential JS 2</title>
            <script src="resources/ej2-base.min.js" type="text/javascript"></script>
            <script src="resources/ej2-data.min.js" type="text/javascript"></script>
            <script src="resources/ej2-svg-base.min.js" type="text/javascript"></script>
            <script src="resources/ej2-heatmap.min.js" type="text/javascript"></script>
       </head>
       <body>
       </body>
  </html>
```

**Step 5:** Now, add the `div` element and initiate the `Essential JS 2 Heatmap` control in the `index.html` by using following code

```html
<!DOCTYPE html>
  <html xmlns="http://www.w3.org/1999/xhtml">
       <head>
            <title>Essential JS 2</title>
            <script src="resources/ej2-base.min.js" type="text/javascript"></script>
            <script src="resources/ej2-data.min.js" type="text/javascript"></script>
            <script src="resources/ej2-svg-base.min.js" type="text/javascript"></script>
            <script src="resources/ej2-heatmap.min.js" type="text/javascript"></script>
       </head>
       <body>
            <!-- Add the HTML <div> element  -->
             <div id="container"></div>
            <script>
                // initialize heatmap control
                var heatmap = new ej.heatmap.HeatMap();

                // Render initialized heatmap.
                heatmap.appendTo('#container')
            </script>
       </body>
  </html>
```

**Step 6:** Now, run the `index.html` in web browser, it will render the **Essential JS 2 heatmap** control.

### Using CDN link for script and style reference

**Step 1:** Create an app folder `myapp` for the Essential JS 2 JavaScript controls.

**Step 2:** The Essential JS 2 control's global scripts and styles are already hosted in the below CDN link formats.

**Syntax:**
> Script: `http://cdn.syncfusion.com/ej2/{PACKAGE_NAME}/dist/global/{PACKAGE_NAME}.min.js`

**Example:**
> Script: [`http://cdn.syncfusion.com/ej2/ej2-heatmap/dist/global/ej2-heatmap.min.js`](http://cdn.syncfusion.com/ej2/ej2-heatmap/dist/global/ej2-heatmap.min.js)

**Step 3:** Create a HTML page (index.html) in `myapp` location and add the CDN link references. Now, add the `div` element and initiate the `Essential JS 2 Heatmap` control in the index.html by using following code.

{% tab template= "heatmap/es5-getting-started", es5Template="es5populateData" %}

```html
<!DOCTYPE html>
  <html xmlns="http://www.w3.org/1999/xhtml">
       <head>
            <title>Essential JS 2</title>
            <script src="http://cdn.syncfusion.com/ej2/ej2-base/dist/global/ej2-base.min.js" type="text/javascript"></script>
            <script src="http://cdn.syncfusion.com/ej2/ej2-data/dist/global/ej2-data.min.js" type="text/javascript"></script>
            <script src="http://cdn.syncfusion.com/ej2/ej2-svg-base/dist/global/ej2-svg-base.min.js" type="text/javascript"></script>
            <script src="http://cdn.syncfusion.com/ej2/ej2-heatmap/dist/global/ej2-heatmap.min.js" type="text/javascript"></script>
       </head>
       <body>
            <!-- Add the HTML <div> element  -->
            <div id="container"></div>
            <script>
                // initialize heatmap control
                var heatmap = new ej.heatmap.HeatMap();

                // Render initialized heatmap.
                heatmap.appendTo('#container')
            </script>
       </body>
  </html>

```

{% endtab %}

**Step 4:** Now, run the `index.html` in web browser, it will render the `Essential JS 2 Heatmap` control.

## Populate heat map with data

This section explains how to populate the following two-dimensional array data to the heat map.

{% tab template= "heatmap/getting-started", es5Template="es5populateData" %}

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
     dataSource: heatmapData,
     }, '#element');

```

{% endtab %}

## Enable axis labels

You can add axis labels to the heat map and format those labels using the [`xAxis`](../api/heatmap/#xaxis) and [`yAxis`](../api/heatmap/#yaxis) properties.
Axis labels provide additional information about the data points populated in the heat map.

{% tab template= "heatmap/getting-started", es5Template="es5AxisLabel"%}

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
    xAxis: {
        labels: ['Nancy', 'Andrew','Janet', 'Margaret', 'Steven',
        'Michael', 'Robert', 'Laura', 'Anne', 'Paul', 'Karin', 'Mario'],
         },
         yAxis:{
             labels: ['Mon', 'Tues', 'Wed', 'Thurs', 'Fri', 'Sat'],
             },
             dataSource: heatmapData
             }, '#element');

```

{% endtab %}

## Add heat map title

Add a title using the [`titleSettings`](../api/heatmap/#titlesettings) property to the heat map to provide quick information to the user about the data populated in the heat map.

{% tab template= "heatmap/getting-started", es5Template="es5Title"%}

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
     }, '#element');

```

{% endtab %}

## Enable legend

Use a legend for the heat map in the [`legendSettings`](../api/heatmap/#legendsettings) object by setting the [`visible`](../api/heatmap/legendSettings/#visible) property to true and injecting the
 `Legend` module using the `HeatMap.Inject(Legend)` method.

{% tab template= "heatmap/getting-started", es5Template="es5Legend" %}

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
        legendSettings: {
            visible:true,
            position: 'Right',
            showLabel: true,
            height: "150"
        }
}, '#element');


```

{% endtab %}

## Add data label

Add data labels to improve the readability of the heat map.
This can be achieved by setting the  [`showLabel`](../api/heatmap/cellSettings/#showlabel) property to true in the [`cellSettings`](../api/heatmap/#cellsettings) object.

{% tab template= "heatmap/getting-started", es5Template="es5DataLabel" %}

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
                fontStyle: 'Normal',
                fontFamily: 'Segoe UI'
            }
        },
     cellSettings: {
            showLabel: true,
        },
     xAxis: {
            labels: ['Nancy', 'Andrew', 'Janet', 'Margaret', 'Steven',
            'Michael', 'Robert', 'Laura', 'Anne', 'Paul', 'Karin',   'Mario'],
        },
     yAxis: {
            labels: ['Mon', 'Tues', 'Wed', 'Thurs', 'Fri', 'Sat'],
        },
     dataSource: heatmapData,
     legendSettings: {
            position: 'Right',
            showLabel: true,
            height: "150"
     }
}, '#element');


```

{% endtab %}

## Add custom cell palette

The default palette settings of the heat map cells can be customized by using the [`paletteSettings`](../api/heatmap/#palettesettings) property.
Using the [`palette`](../api/heatmap/paletteSettings/#palette) property in `paletteSettings` object, you can change the color set for the cells.
You can change the color mode of the cells to fixed or gradient mode using the [`type`](../api/heatmap/paletteSettings/#type) property.

{% tab template= "heatmap/getting-started", es5Template="es5Palette" %}

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
                fontStyle: 'Normal',
                fontFamily: 'Segoe UI'
            }
        },
    cellSettings: {
            showLabel: true,
        },
     xAxis: {
            labels: ['Nancy', 'Andrew', 'Janet', 'Margaret', 'Steven',
            'Michael', 'Robert', 'Laura', 'Anne', 'Paul', 'Karin',   'Mario'],
        },
      yAxis: {
            labels: ['Mon', 'Tues', 'Wed', 'Thurs', 'Fri', 'Sat'],
        },
      dataSource: heatmapData,
      legendSettings: {
            position: 'Right',
            showLabel: true,
            height: "150"
        },
      paletteSettings: {
            palette: [
                { value: 0, color: '#C06C84' },
                { value: 50, color: '#6C5B7B' },
                { value: 100, color: '#355C7D' }
                ],
            type: "Gradient"
        },
}, '#element');

```

{% endtab %}

## Enable tooltip

The tooltip is used when you cannot display information by using the data labels due to space constraints.
You can enable the tooltip by setting the [`showTooltip`](../api/heatmap/#showtooltip) property to `true` and injecting the `Tooltip` module using
the `HeatMap.Inject(Tooltip)` method.

{% tab template= "heatmap/getting-started", es5Template="es5Tooltip" %}

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
                fontStyle: 'Normal',
                fontFamily: 'Segoe UI'
            }
        },
    cellSettings: {
            showLabel: true,
        },
    xAxis: {
            labels: ['Nancy', 'Andrew', 'Janet', 'Margaret', 'Steven',
            'Michael', 'Robert', 'Laura', 'Anne', 'Paul', 'Karin',   'Mario'],
        },
    yAxis: {
            labels: ['Mon', 'Tues', 'Wed', 'Thurs', 'Fri', 'Sat'],
        },
    dataSource: heatmapData,
    legendSettings: {
            position: 'Right',
            showLabel: true,
            height: "150"
        },
    showTooltip:true,
}, '#element');

```

{% endtab %}