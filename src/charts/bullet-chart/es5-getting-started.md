---
title: "BulletChart Getting Started | JavaScript "

component: "BulletChart"

description: "Getting started file explains how to configure and install chart packages and also how to create basic bullet chart."
---

# Getting Started

This section explains you the steps required to create a simple bullet chart and demonstrate the basic usage of the bullet chart control.

## Dependencies

Below is the list of minimum dependencies required to use the Bullet Chart.

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

**Step 3:** Create **myapp/index.js** and **myapp/index.html** files for initializing Essential JS 2 Bullet Chart control.

## Adding Syncfusion resources

The Essential JS 2 Bullet Chart control can be initialized by using either of the following ways.

* Using local script.
* Using CDN link for script.

### Using local script

You can get the global scripts and styles from the [Essential Studio JavaScript (Essential JS 2)](https://www.syncfusion.com/downloads/essential-js2) build installed location.

After installing the Essential JS 2 product build, you can copy the bullet chart and its dependencies scripts and style file into the **resources/scripts** and **resources/styles** folder.

Refer the below code to find location bullet chart's script and style file.

**Syntax:**

> Script: `**(installed location)**/Syncfusion/Essential Studio/{RELEASE_VERSION}/Essential JS 2/{PACKAGE_NAME}/dist/global/{PACKAGE_NAME}.min.js`
>

**Example:**

> Script: `C:/Program Files (x86)/Syncfusion/Essential Studio/15.4.30/Essential JS 2/ej2-charts/dist/global/ej2-charts.min.js`
>

After copying the files, then you can refer the bullet chart's scripts into the `index.html` file.
The below html code example shows the minimal dependency of bullet chart.

```html

<!DOCTYPE html>
  <html xmlns="http://www.w3.org/1999/xhtml">
       <head>
            <title>Essential JS 2 Bullet Chart</title>
            <!-- Essential JS 2 Bullet Chart's global script -->
            <script src="resources/scripts/ej2-charts.min.js" type="text/javascript"></script>
       </head>
       <body>
       </body>
  </html>

```

### Using CDN link for script

Using CDN link, you can directly refer the bullet chart control's script into the `index.html`.

Refer the bullet chart's CDN links as below

**Syntax:**

> Script: `http://cdn.syncfusion.com/ej2/{PACKAGE_NAME}/dist/global/{PACKAGE_NAME}.min.js`

**Example:**

> Script: [`http://cdn.syncfusion.com/ej2/ej2-charts/dist/global/ej2-charts.min.js`](http://cdn.syncfusion.com/ej2/ej2-charts/dist/global/ej2-charts.min.js)

The below html code example shows the minimal dependency of bullet chart.

```html
<!DOCTYPE html>
  <html xmlns="http://www.w3.org/1999/xhtml">
       <head>
            <title>Essential JS 2 Bullet Chart</title>
            <!-- Essential JS 2 Bullet Chart's global script -->
            <script src="http://cdn.syncfusion.com/ej2/ej2-charts/dist/global/ej2-charts.min.js" type="text/javascript"></script>
       </head>
       <body>
       </body>
  </html>

```

## Adding Bullet Chart control

Now, you can start adding Bullet Chart control in the application. For getting started, add a **div** element for Bullet Chart control in **index.html**. Then refer the **index.js** file into the **index.html** file.

In this document context we are going to use **ej2.min.js** which includes all the Essential JS 2 components and its dependent scripts.

```html
<!DOCTYPE html>
  <html xmlns="http://www.w3.org/1999/xhtml">
       <head>
            <title>Essential JS 2 Bullet Chart</title>
            <!-- Essential JS 2 all script -->
            <script src="http://cdn.syncfusion.com/ej2/dist/ej2.min.js" type="text/javascript"></script>
       </head>
       <body>
           <!-- Add the HTML <div> element for bullet chart  -->
             <div id="element"></div>
             <script src="index.js" type="text/javascript"></script>
       </body>
  </html>

```

Place the following bullet chart code in the **index.js**.

```javascript

var bulletChart = new ej.charts.BulletChart();
bulletChart.appendTo('#element');

```

The below example shows a basic Bullet Chart.

{% tab template= "bullet-chart/getting-started", es5Template="es5default" %}

```javascript

var bulletChart = new ej.charts.BulletChart();
bulletChart.appendTo('#element');

```

{% endtab %}

## BulletChart With Data

This section explains how to plot local data to the bullet chart.

```javascript

var data = [
       { value: 100, target: 80 },
       { value: 200, target: 180 },
       { value: 300, target: 280 },
       { value: 400, target: 380 },
       { value: 500, target: 480 },
];
```

Now assign the local data to `dataSource` property. `value` and `target` values should be mapped with `valueName` and `targetName` respectively.

{% tab template= "bullet-chart/getting-started", es5Template="es5localData" %}

```javascript
var bulletChart = new ej.charts.BulletChart({
    dataSource: [{ value: 100, target: 80 },
            { value: 200, target: 180 },
            { value: 300, target: 280 },
            { value: 400, target: 380 },
            { value: 500, target: 480 }],
    valueName: 'value',
    targetName: 'target',
    height: '300',
    minimum: 0, maximum: 300, interval: 50,
});
bulletChart.appendTo('#element');
```

{% endtab %}

## Add Bullet Chart Title

You can add a title using `title` property to the bullet chart to provide quick
information to the user about the data plotted in the bullet chart.

{% tab template= "bullet-chart/getting-started", es5Template="es5chartTitle"%}

```javascript

var bulletChart = new ej.charts.BulletChart({
    dataSource: [{ value: 270, target: 250 },],
    valueName: 'value',
    targetName: 'target',
    title: 'Revenue',
    minimum: 0, maximum: 300, interval: 50,
});
bulletChart.appendTo('#element');
```

{% endtab %}

## Ranges

You can add a range using `ranges` property to the bullet chart.

{% tab template= "bullet-chart/getting-started", es5Template="es5bulletRanges"%}

```javascript

var bulletChart = new ej.charts.BulletChart({
    dataSource: [{ value: 270, target: 250 },],
    valueName: 'value',
    targetName: 'target',
    title: 'Revenue',
    minimum: 0, maximum: 300, interval: 50,
    ranges: [{ end: 100, color: 'red' },
        { end: 200, color: 'blue' },
        { end: 300, color: 'green' }
        ],
});
bulletChart.appendTo('#element');
```

{% endtab %}

## Tooltip

You can use tooltip for the bullet chart by setting the `enable` property to true in `tooltip` object and by injecting the `BulletTooltip` module using `BulletChart.Inject(BulletTooltip)` method.

{% tab template= "bullet-chart/getting-started", es5Template="es5bulletTooltip"%}

```javascript

var bulletChart = new ej.charts.BulletChart({
        dataSource: [{ value: 270, target: 250 },],
        valueName: 'value',
        targetName: 'target',
        title: 'Revenue',
        minimum: 0, maximum: 300, interval: 50,
        ranges: [{ end: 100, color: 'red' },
        { end: 200, color: 'blue' },
        { end: 300, color: 'green' }
        ],
        tooltip: {
            enable: true
        }
});
bulletChart.appendTo('#element');
```

{% endtab %}