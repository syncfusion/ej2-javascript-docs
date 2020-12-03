---
title: " Chart Getting Started | JavaScript "

component: "Chart"

description: "Getting started file explains how to configure and install chart packages and also how to create basic chart"
---

# Getting Started

This section explains you the steps required to create a simple chart and demonstrate the basic usage of the chart control.

## Dependencies

Below is the list of minimum dependencies required to use the Chart.

```javascript
|-- @syncfusion/ej2-charts
    |-- @syncfusion/ej2-base
    |-- @syncfusion/ej2-data
    |-- @syncfusion/ej2-pdf-export
    |-- @syncfusion/ej2-file-utils
    |-- @syncfusion/ej2-compression
    |-- @syncfusion/ej2-svg-base
```

## Setup for local environment

Refer the following steps for setup your local environment.

**Step 1:** Create a root folder **myapp** for your application.

**Step 2:** Create **myapp/resources** folder to store local scripts and styles files.

**Step 3:** Create **myapp/index.js** and **myapp/index.html** files for initializing Essential JS 2 Chart control.

## Adding Syncfusion resources

The Essential JS 2 Chart control can be initialized by using either of the following ways.

* Using local script.
* Using CDN link for script.

### Using local script

You can get the global scripts and styles from the [Essential Studio JavaScript (Essential JS 2)](https://www.syncfusion.com/downloads/essential-js2) build installed location.

After installing the Essential JS 2 product build, you can copy the chart and its dependencies scripts and style file into the **resources/scripts** and **resources/styles** folder.

Refer the below code to find location chart's script and style file.

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
            <title>Essential JS 2 Chart</title>
            <!-- Essential JS 2 Chart's global script -->
            <script src="resources/scripts/ej2-charts.min.js" type="text/javascript"></script>
       </head>
       <body>
       </body>
  </html>

```

### Using CDN link for script

Using CDN link, you can directly refer the chart control's script into the `index.html`.

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
            <title>Essential JS 2 Chart</title>
            <!-- Essential JS 2 Chart's global script -->
            <script src="http://cdn.syncfusion.com/ej2/ej2-charts/dist/global/ej2-charts.min.js" type="text/javascript"></script>
       </head>
       <body>
       </body>
  </html>

```

## Adding Chart control

Now, you can start adding Chart control in the application. For getting started, add a **div** element for Chart control in **index.html**. Then refer the **index.js** file into the **index.html** file.

In this document context we are going to use **ej2.min.js** which includes all the Essential JS 2 components and its dependent scripts.

```html
<!DOCTYPE html>
  <html xmlns="http://www.w3.org/1999/xhtml">
       <head>
            <title>Essential JS 2 Chart</title>
            <!-- Essential JS 2 all script -->
            <script src="http://cdn.syncfusion.com/ej2/dist/ej2.min.js" type="text/javascript"></script>
       </head>
       <body>
           <!-- Add the HTML <div> element for chart  -->
             <div id="element"></div>
             <script src="index.js" type="text/javascript"></script>
       </body>
  </html>

```

Place the following chart code in the **index.js**.

```javascript

var chart = new ej.charts.Chart();
chart.appendTo('#element');

```

The below example shows a basic Chart.

{% tab template= "chart/getting-started", es5Template="es5defaultChart" %}

```javascript

var chart = new ej.charts.Chart();

chart.appendTo('#element');

```

{% endtab %}

## Populate Chart With Data

This section explains how to plot below JSON data to the chart.

```javascript

var chartData = [
      { month: 'Jan', sales: 35 }, { month: 'Feb', sales: 28 },
      { month: 'Mar', sales: 34 }, { month: 'Apr', sales: 32 },
      { month: 'May', sales: 40 }, { month: 'Jun', sales: 32 },
      { month: 'Jul', sales: 35 }, { month: 'Aug', sales: 55 },
      { month: 'Sep', sales: 38 }, { month: 'Oct', sales: 30 },
      { month: 'Nov', sales: 25 }, { month: 'Dec', sales: 32 }
];

```

Add a series object to the chart by using [`series`](../api/chart/series/) property. Now map the field names
`month` and `sales` in the JSON data to the [`xName`](../api/chart/series/#xname)
and [`yName`](../api/chart/series/#yname) properties of the series, then set the JSON data to
[`dataSource`](../api/chart/series/#datasource) property.

Since the JSON contains category data, set the [`valueType`](../api/chart/axisModel/#valuetype) for
horizontal axis to Category. By default, the axis valueType is Numeric.

{% tab template= "chart/getting-started", es5Template="es5populateData" %}

```javascript

var chartData = [
      { month: 'Jan', sales: 35 }, { month: 'Feb', sales: 28 },
      { month: 'Mar', sales: 34 }, { month: 'Apr', sales: 32 },
      { month: 'May', sales: 40 }, { month: 'Jun', sales: 32 },
      { month: 'Jul', sales: 35 }, { month: 'Aug', sales: 55 },
      { month: 'Sep', sales: 38 }, { month: 'Oct', sales: 30 },
      { month: 'Nov', sales: 25 }, { month: 'Dec', sales: 32 }
];
var chart = new ej.charts.Chart({
    primaryXAxis: {
        valueType: 'Category'
    },
    series:[{
        // dataSource for chart series
        dataSource: chartData,
        xName: 'month',
        yName: 'sales',
        type: 'Line'
    }]
}, '#element');

```

{% endtab %}

The sales data are in thousands, so format the vertical axis label by adding `$` as a prefix and `K` as a
suffix to each label. This can be achieved by setting the `${value}K` to the
[`labelFormat`](../api/chart/axisModel/#labelformat) property of axis. Here, `{value}` act as a placeholder
for each axis label.

{% tab template= "chart/getting-started", es5Template="es5Labelformat" %}

```javascript
var chartData = [
      { month: 'Jan', sales: 35 }, { month: 'Feb', sales: 28 },
      { month: 'Mar', sales: 34 }, { month: 'Apr', sales: 32 },
      { month: 'May', sales: 40 }, { month: 'Jun', sales: 32 },
      { month: 'Jul', sales: 35 }, { month: 'Aug', sales: 55 },
      { month: 'Sep', sales: 38 }, { month: 'Oct', sales: 30 },
      { month: 'Nov', sales: 25 }, { month: 'Dec', sales: 32 }
];
var chart = new ej.charts.Chart({
    primaryXAxis: {
        valueType: 'Category',
    },
    primaryYAxis: {
        // label format for axis
        labelFormat: '${value}K'
    },
    series:[{
        dataSource: chartData,
        xName: 'month',
        yName: 'sales',
        type: 'Line'
    }]
}, '#element');

```

{% endtab %}

## Add Chart Title

You can add a title using [`title`](../api/chart/chartModel/#title) property to the chart to provide quick
information to the user about the data plotted in the chart.

{% tab template= "chart/getting-started", es5Template="es5chartTitle"%}

```javascript

var chartData = [
      { month: 'Jan', sales: 35 }, { month: 'Feb', sales: 28 },
      { month: 'Mar', sales: 34 }, { month: 'Apr', sales: 32 },
      { month: 'May', sales: 40 }, { month: 'Jun', sales: 32 },
      { month: 'Jul', sales: 35 }, { month: 'Aug', sales: 55 },
      { month: 'Sep', sales: 38 }, { month: 'Oct', sales: 30 },
      { month: 'Nov', sales: 25 }, { month: 'Dec', sales: 32 }
];
var chart = new ej.charts.Chart({
    // Title for chart
    title: 'Sales Analysis'
    primaryXAxis: {
        valueType: 'Category',
        title: 'Month'
    },
    primaryYAxis: {
        labelFormat: '${value}K'
    },
    series:[{
        dataSource: chartData,
        name:'Sales',
        xName: 'month',
        yName: 'sales',
        type: 'Line'
    }],
}, '#element');

```

{% endtab %}

## Enable Legend

You can use legend for the chart by setting the [`visible`](../api/chart/legendSettingsModel/#visible)
property to true in [`legendSettings`](../api/chart/chartModel/#legendsettings) object.

{% tab template= "chart/getting-started", es5Template="es5Legend" %}

```javascript

var chartData = [
      { month: 'Jan', sales: 35 }, { month: 'Feb', sales: 28 },
      { month: 'Mar', sales: 34 }, { month: 'Apr', sales: 32 },
      { month: 'May', sales: 40 }, { month: 'Jun', sales: 32 },
      { month: 'Jul', sales: 35 }, { month: 'Aug', sales: 55 },
      { month: 'Sep', sales: 38 }, { month: 'Oct', sales: 30 },
      { month: 'Nov', sales: 25 }, { month: 'Dec', sales: 32 }
];
var chart = new ej.charts.Chart({
    // Legend for chart
    legendSettings: {
        visible: true
    },
    primaryXAxis: {
        valueType: 'Category',
    },
    primaryYAxis: {
        labelFormat: '${value}K'
    },
    series:[{
        dataSource: chartData,
        name:'Sales',
        xName: 'month',
        yName: 'sales',
        type: 'Line'
    }],
    title: 'Sales Analysis'
}, '#element');

```

{% endtab %}

## Add Data Label

You can add data labels to improve the readability of the chart. This can be achieved by setting the visible
property to true in the dataLabel object. Now, the data labels are arranged smartly based on series.

{% tab template= "chart/getting-started", es5Template="es5DataLabel" %}

```javascript

var chartData = [
      { month: 'Jan', sales: 35 }, { month: 'Feb', sales: 28 },
      { month: 'Mar', sales: 34 }, { month: 'Apr', sales: 32 },
      { month: 'May', sales: 40 }, { month: 'Jun', sales: 32 },
      { month: 'Jul', sales: 35 }, { month: 'Aug', sales: 55 },
      { month: 'Sep', sales: 38 }, { month: 'Oct', sales: 30 },
      { month: 'Nov', sales: 25 }, { month: 'Dec', sales: 32 }
];
var chart = new ej.charts.Chart({
    primaryXAxis: {
        valueType: 'Category',
    },
    primaryYAxis: {
        labelFormat: '${value}K'
    },
    series:[{
        dataSource: chartData,
        xName: 'month',
        name:'Sales',
        yName: 'sales',
        type: 'Line',
        marker: {
            // Data label for chart series
            dataLabel: {
                visible: true
            }
        }
    }],
    legendSettings: {visible: true},
    title: 'Sales Analysis'
}, '#element');

```

{% endtab %}

## Enable Tooltip

The tooltip is useful when you cannot display information by using the data labels due to space constraints.
You can enable tooltip by setting the [`enable`](../api/chart/tooltipSettingsModel/#enable) property as true
in [`tooltip`](../api/chart/chartModel/#tooltip) object.

{% tab template= "chart/getting-started", es5Template="es5Tooltip" %}

```javascript

var chartData = [
      { month: 'Jan', sales: 35 }, { month: 'Feb', sales: 28 },
      { month: 'Mar', sales: 34 }, { month: 'Apr', sales: 32 },
      { month: 'May', sales: 40 }, { month: 'Jun', sales: 32 },
      { month: 'Jul', sales: 35 }, { month: 'Aug', sales: 55 },
      { month: 'Sep', sales: 38 }, { month: 'Oct', sales: 30 },
      { month: 'Nov', sales: 25 }, { month: 'Dec', sales: 32 }
];
var chart = new ej.charts.Chart({
    // Tooltip for chart
    tooltip: {
        enable: true
    },
    primaryXAxis: {
        valueType: 'Category',
    },
    primaryYAxis: {
        labelFormat: '${value}K'
    },
   series:[{
        dataSource: chartData,
        name:'Sales',
        xName: 'month',
        yName: 'sales',
        type: 'Line',
        marker: {
            // Data label for chart series
            dataLabel: {
                visible: true
            }
        }
    }],
    legendSettings: {visible: true},
    title: 'Sales Analysis'
}, '#element');

```

{% endtab %}