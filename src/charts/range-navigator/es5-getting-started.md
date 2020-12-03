---
title: " RangeNavigator Getting Started | JavaScript "

component: "RangeNavigator"

description: "Getting started file explains how to configure and install rangenavigator packages and also how to create basic rangenavigator"
---

# Getting Started

This section explains you the steps required to create a simple range navigator and demonstrate the basic usage of the range navigator control.

## Dependencies

 The list of minimum dependencies required to use a range navigator are follows:

```javascript
    |-- @syncfusion/ej2-charts
    |-- @syncfusion/ej2-base
    |-- @syncfusion/ej2-data
    |-- @syncfusion/ej2-pdf-export
    |-- @syncfusion/ej2-file-utils
    |-- @syncfusion/ej2-compression
    |-- @syncfusion/ej2-navigations
    |-- @syncfusion/ej2-calendars

```

## Setup for local environment

Refer the following steps for setup your local environment.

**Step 1:** Create a root folder **myapp** for your application.

**Step 2:** Create **myapp/resources** folder to store local scripts and styles files.

**Step 3:** Create **myapp/index.js** and **myapp/index.html** files for initializing Essential JS 2 Range Selector control.

## Adding Syncfusion resources

The Essential JS 2 range selector control can be initialized by using either of the following ways.

* Using local script.
* Using CDN link for script.

### Using local script

You can get the global scripts and styles from the [Essential Studio JavaScript (Essential JS 2)](https://www.syncfusion.com/downloads/essential-js2) build installed location.

After installing the Essential JS 2 product build, you can copy the chart and its dependencies scripts and style file into the **resources/scripts** and **resources/styles** folder.

Refer the below code to find location range selector's script and style file.

**Syntax:**

> Script: `**(installed location)**/Syncfusion/Essential Studio/{RELEASE_VERSION}/Essential JS 2/{PACKAGE_NAME}/dist/global/{PACKAGE_NAME}.min.js`
>

**Example:**

> Script: `C:/Program Files (x86)/Syncfusion/Essential Studio/15.4.30/Essential JS 2/ej2-charts/dist/global/ej2-charts.min.js`
>

After copying the files, then you can refer the chart's scripts into the `index.html` file.
The below html code example shows the minimal dependency of chart.

```html

<!DOCTYPE html>
  <html xmlns="http://www.w3.org/1999/xhtml">
       <head>
            <title>Essential JS 2 Range Selector</title>
            <!-- Essential JS 2 Range Selector's global script -->
            <script src="resources/scripts/ej2-charts.min.js" type="text/javascript"></script>
       </head>
       <body>
       </body>
  </html>

```

### Using CDN link for script

Using CDN link, you can directly refer the range selector control's script into the `index.html`.

Refer the chart's CDN links as below

**Syntax:**

> Script: `http://cdn.syncfusion.com/ej2/{PACKAGE_NAME}/dist/global/{PACKAGE_NAME}.min.js`

**Example:**

> Script: [`http://cdn.syncfusion.com/ej2/ej2-charts/dist/global/ej2-charts.min.js`](http://cdn.syncfusion.com/ej2/ej2-charts/dist/global/ej2-charts.min.js)

The below html code example shows the minimal dependency of chart.

```html

<!DOCTYPE html>
  <html xmlns="http://www.w3.org/1999/xhtml">
       <head>
            <title>Essential JS 2 Range Selector</title>
            <!-- Essential JS 2 Range Selector's global script -->
            <script src="http://cdn.syncfusion.com/ej2/ej2-charts/dist/global/ej2-charts.min.js" type="text/javascript"></script>
       </head>
       <body>
       </body>
  </html>
  
```

## Adding Range Selector control

Now, you can start adding range selector control in the application. For getting started, add a **div** element for Chart control in **index.html**. Then refer the **index.js** file into the **index.html** file.

In this document context we are going to use **ej2.min.js** which includes all the Essential JS 2 components and its dependent scripts.

```html
<!DOCTYPE html>
  <html xmlns="http://www.w3.org/1999/xhtml">
       <head>
            <title>Essential JS 2 Range Selector</title>
            <!-- Essential JS 2 all script -->
            <script src="http://cdn.syncfusion.com/ej2/dist/ej2.min.js" type="text/javascript"></script>
       </head>
       <body>
           <!-- Add the HTML <div> element for Range Selector  -->
             <div id="element"></div>
             <script src="index.js" type="text/javascript"></script>
       </body>
  </html>

```

Place the following chart code in the **index.js**.

```javascript

var range = new ej.charts.RangeNavigator();
range.appendTo('#element');

```

The below example shows a basic Range Navigator.

{% tab template= "rangenavigator/getting-started", es5Template="es5LW" %}

```javascript

var range = new ej.charts.RangeNavigator();
range.appendTo('#element');

```

{% endtab %}

## Populate Range Navigator with Data

Now, we are going to provide data to the range navigator. Add a series object to the range navigator  by using `series` property. Now map the field names x and y in the JSON data to the `xName` and `yName` properties of the series, then set the JSON data to dataSource property.
Since the JSON contains Datetime data, set the `valueType` as `DateTime`. By default, the axis valueType is Numeric.

{% tab template= "rangenavigator/getting-started", es5Template="es5default" %}

```javascript

var range = new ej.charts.RangeNavigator({
    valueType: 'DateTime',
    value: [new Date('2017-09-01'), new Date('2018-02-01')],
    labelFormat: 'MMM-yy',
    series: [{
                dataSource: datasrc, xName: 'x', yName: 'y', type: 'Area', width: 2,
            }],
}, '#element');

```

{% endtab %}

>Note: Get data from [here](https://ej2.syncfusion.com/demos/src/range-navigator/data-source/default-data.json).

The sample should look like our [default](https://ej2.syncfusion.com/javascript/demos/#/material/range-navigator/default.html), don’t worry about the gradient color, let it takes the default color.

## Enable Tooltip

The tooltip is useful to show the selected data. You can enable tooltip by setting the enable property as true in `tooltip` object and by injecting `RangeTooltipService` module using `RangeNavigator.Inject(RangeTooltip)` method.

{% tab template= "rangenavigator/getting-started", es5Template="es5Tooltip" %}

```javascript

var range = new ej.charts.RangeNavigator({
    valueType: 'DateTime',
    value: [new Date('2017-09-01'), new Date('2018-02-01')],
    tooltip: { enable: true, displayMode: 'Always' },
    labelFormat: 'MMM-yy',
    series: [{
                dataSource: datasrc, xName: 'x', yName: 'y', type: 'Area', width: 2,
            }],
}, '#element');

```

{% endtab %}