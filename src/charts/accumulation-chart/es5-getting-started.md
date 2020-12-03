---
title: " Accumulation Chart Getting Started | JavaScript "

component: "Accumulation Chart"

description: "Getting started file explains how configure and install chart packages and also how to create basic accumulation chart."
---
<!-- markdownlint-disable MD036 -->

# Getting Started

In EJ2, accumulation chart is implemented as a separate control to avoid the axis related logics.
The dependencies for accumulation chart is same as chart control.

## Dependencies

The list of minimum dependencies required to use an accumulation chart are follows:

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

**Step 3:** Create **myapp/index.js** and **myapp/index.html** files for initializing Essential JS 2 Accumulation Chart control.

## Adding Syncfusion resources

The Essential JS 2 Accumulation Chart control can be initialized by using either of the following ways.

* Using local script.
* Using CDN link for script.

### Using local script

You can get the global scripts and styles from the [Essential Studio JavaScript (Essential JS 2)](https://www.syncfusion.com/downloads/essential-js2) build installed location.

After installing the Essential JS 2 product build, you can copy the chart and its dependencies scripts and style file into the **resources/scripts** and **resources/styles** folder.

Refer the below code to find location accumulation chart's script and style file.

**Syntax:**

> Script: `**(installed location)**/Syncfusion/Essential Studio/{RELEASE_VERSION}/Essential JS 2/{PACKAGE_NAME}/dist/global/{PACKAGE_NAME}.min.js`
>

**Example:**

> Script: `C:/Program Files (x86)/Syncfusion/Essential Studio/15.4.30/Essential JS 2/ej2-charts/dist/global/ej2-charts.min.js`
>

After copying the files, then you can refer the accumulation chart's scripts into the `index.html` file.
The below html code example shows the minimal dependency of chart.

```html

<!DOCTYPE html>
  <html xmlns="http://www.w3.org/1999/xhtml">
       <head>
            <title>Essential JS 2 Accumulation Chart</title>
            <!-- Essential JS 2 Accumulation Chart's global script -->
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

## Adding Accumulation Chart control

Now, you can start adding accumulation chart control in the application. For getting started, add a **div** element for Chart control in **index.html**. Then refer the **index.js** file into the **index.html** file.

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

var piechart = new ej.charts.AccumulationChart({
    series: [
        {
            dataSource: [{ x: 'Jan', y: 3 }, { x: 'Feb', y: 3.5 }, { x: 'Mar', y: 7 }, { x: 'Apr', y: 13.5 },
            { x: 'May', y: 19 }, { x: 'Jun', y: 23.5 }, { x: 'Jul', y: 26 }, { x: 'Aug', y: 25 },
            { x: 'Sep', y: 21 }, { x: 'Oct', y: 15 }],
            xName: 'x',
            yName: 'y'
        }
    ]
});
piechart.appendTo('#element');

```

**Pie Series**

By default, the pie series will be rendered when assigning the JSON data to the series using the
[`dataSource`](../api/accumulation-chart/accumulationSeries/#datasource) property. Map the field names
in the JSON data to the [`xName`](../api/accumulation-chart/accumulationSeries/#xname) and
[`yName`](../api/accumulation-chart/accumulationSeries/#yname) properties of the series.

{% tab template="chart/chart-types",  isDefaultActive=true , es5Template="es5AccChart" %}

```javascript

var piechart = new ej.charts.AccumulationChart({
    series: [
        {
            dataSource: [{ x: 'Jan', y: 3 }, { x: 'Feb', y: 3.5 }, { x: 'Mar', y: 7 }, { x: 'Apr', y: 13.5 },
            { x: 'May', y: 19 }, { x: 'Jun', y: 23.5 }, { x: 'Jul', y: 26 }, { x: 'Aug', y: 25 },
            { x: 'Sep', y: 21 }, { x: 'Oct', y: 15 }],
            xName: 'x',
            yName: 'y'
        }
    ]
}, '#element');

```

{% endtab %}
