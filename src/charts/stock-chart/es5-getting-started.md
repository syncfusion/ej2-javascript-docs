# Getting Started

This section explains you the steps required to create a simple Stock Chart and demonstrate the basic usage of the Stock Chart control.

## Dependencies

Below is the list of minimum dependencies required to use the Stock Chart.

```javascript
|-- @syncfusion/ej2-charts
    |-- @syncfusion/ej2-base
    |-- @syncfusion/ej2-data
    |-- @syncfusion/ej2-pdf-export
    |-- @syncfusion/ej2-file-utils
    |-- @syncfusion/ej2-compression
    |-- @syncfusion/ej2-svg-base
    |-- @syncfusion/ej2-navigations
    |-- @syncfusion/ej2-calendars
    |-- @syncfusion/ej2-popups
    |-- @syncfusion/ej2-lists
    |-- @syncfusion/ej2-inputs
    |-- @syncfusion/ej2-buttons
    |-- @syncfusion/ej2-splitbuttons

```

## Setup for local environment

Refer the following steps for setup your local environment.

**Step 1:** Create a root folder **myapp** for your application.

**Step 2:** Create **myapp/resources** folder to store local scripts and styles files.

**Step 3:** Create **myapp/index.js** and **myapp/index.html** files for initializing Essential JS 2 Stock Chart control.

## Adding Syncfusion resources

The Essential JS 2 Stock Chart control can be initialized by using either of the following ways.

* Using local script.
* Using CDN link for script.

### Using local script

You can get the global scripts and styles from the [Essential Studio JavaScript (Essential JS 2)](https://www.syncfusion.com/downloads/essential-js2) build installed location.

After installing the Essential JS 2 product build, you can copy the chart and its dependencies scripts and style file into the **resources/scripts** and **resources/styles** folder.

Refer the below code to find location stock chart's script and style file.

**Syntax:**

> Script: `**(installed location)**/Syncfusion/Essential Studio/{RELEASE_VERSION}/Essential JS 2/{PACKAGE_NAME}/dist/global/{PACKAGE_NAME}.min.js`
>
> Styles: `**(installed location)**/Syncfusion/Essential Studio/{RELEASE_VERSION}/Essential JS 2/{PACKAGE_NAME}/styles/material.css`

**Example:**

> Script: `C:/Program Files (x86)/Syncfusion/Essential Studio/15.4.30/Essential JS 2/ej2-charts/dist/global/ej2-charts.min.js`
>
> Styles: `C:/Program Files (x86)/Syncfusion/Essential Studio/15.4.30/Essential JS 2/ej2-charts/styles/material.css`

After copying the files, then you can refer the stock chart's scripts and style into the `index.html` file.
The below html code example shows the minimal dependency of chart.

```html

<!DOCTYPE html>
  <html xmlns="http://www.w3.org/1999/xhtml">
       <head>
            <title>Essential JS 2 Stock Chart</title>
            <!-- Essential JS 2 Stock Chart's global script -->
            <script src="resources/scripts/ej2-charts.min.js" type="text/javascript"></script>
            <link href="resources/styles/material.css" rel="stylesheet" type="text/css"/>
       </head>
       <body>
       </body>
  </html>

```

### Using CDN link for script

Using CDN link, you can directly refer the stock chart control's script and style into the `index.html`.

Refer the chart's CDN links as below

**Syntax:**

> Script: `http://cdn.syncfusion.com/ej2/{PACKAGE_NAME}/dist/global/{PACKAGE_NAME}.min.js`
>
> Styles: `http://cdn.syncfusion.com/ej2/material.css`

**Example:**

> Script: [`http://cdn.syncfusion.com/ej2/ej2-charts/dist/global/ej2-charts.min.js`](http://cdn.syncfusion.com/ej2/ej2-charts/dist/global/ej2-charts.min.js)
>
> Styles: [`http://cdn.syncfusion.com/ej2/material.css`](http://cdn.syncfusion.com/ej2/material.css)

The below html code example shows the minimal dependency of chart.

```html
<!DOCTYPE html>
  <html xmlns="http://www.w3.org/1999/xhtml">
       <head>
            <title>Essential JS 2 Stock Chart</title>
            <!-- Essential JS 2 Stock Chart's global script -->
            <script src="http://cdn.syncfusion.com/ej2/ej2-charts/dist/global/ej2-charts.min.js" type="text/javascript"></script>
            <!-- Essential JS 2 material theme -->
            <link href="http://cdn.syncfusion.com/ej2/material.css" rel="stylesheet" type="text/css"/>
       </head>
       <body>
       </body>
  </html>

```

## Adding Stock Chart control

Now, you can start adding stock chart control in the application. For getting started, add a **div** element for Chart control in **index.html**. Then refer the **index.js** file into the **index.html** file.

In this document context we are going to use **ej2.min.js** which includes all the Essential JS 2 components and its dependent scripts.

```html
<!DOCTYPE html>
  <html xmlns="http://www.w3.org/1999/xhtml">
       <head>
            <title>Essential JS 2 Stock Chart</title>
            <!-- Essential JS 2 material theme -->
            <link href="http://cdn.syncfusion.com/ej2/material.css" rel="stylesheet" type="text/css"/>
            <!-- Essential JS 2 all script -->
            <script src="http://cdn.syncfusion.com/ej2/dist/ej2.min.js" type="text/javascript"></script>
       </head>
       <body>
           <!-- Add the HTML <div> element for stock chart  -->
             <div id="element"></div>
             <script src="index.js" type="text/javascript"></script>
       </body>
  </html>

```

Place the following chart code in the **index.js**.

```javascript

var stockchartData = [{
   x: new Date( '2012-04-02' ),
    open : 85.9757,
    high : 90.6657,
    low : 85.7685,
    close : 90.5257,
    volume : 660187068
  },
  {
   x: new Date( '2012-04-09' ),
    open : 89.4471,
    high : 92,
    low : 86.2157,
    close : 86.4614,
    volume : 912634864
  },
  {
   x: new Date( '2012-04-16' ),
    open : 87.1514,
    high : 88.6071,
    low : 81.4885,
    close : 81.8543,
    volume : 1221746066
  },
  {
   x: new Date( '2012-04-23' ),
    open : 81.5157,
    high : 88.2857,
    low : 79.2857,
    close : 86.1428,
    volume : 965935749
  },
  {
   x: new Date( '2012-04-30' ),
    open : 85.4,
    high : 85.4857,
    low : 80.7385,
    close : 80.75,
    volume : 615249365
  }];
var stockchart = new ej.charts.StockChart({
    series:[{
        // dataSource for stockchart series
        dataSource: stockchartData,
        xName: 'month',
        yName: 'sales',
        type: 'Candle'
    }]
}, '#element');

```

## Populate Stock Chart With Data

This section explains how to plot below JSON data to the  Stock Chart.

```javascript

var stockchartData = [{
   x: new Date( '2012-04-02' ),
    open : 85.9757,
    high : 90.6657,
    low : 85.7685,
    close : 90.5257,
    volume : 660187068
  },
  {
   x: new Date( '2012-04-09' ),
    open : 89.4471,
    high : 92,
    low : 86.2157,
    close : 86.4614,
    volume : 912634864
  },
  {
   x: new Date( '2012-04-16' ),
    open : 87.1514,
    high : 88.6071,
    low : 81.4885,
    close : 81.8543,
    volume : 1221746066
  },
  {
   x: new Date( '2012-04-23' ),
    open : 81.5157,
    high : 88.2857,
    low : 79.2857,
    close : 86.1428,
    volume : 965935749
  },
  {
   x: new Date( '2012-04-30' ),
    open : 85.4,
    high : 85.4857,
    low : 80.7385,
    close : 80.75,
    volume : 615249365
  }];

```

Add a series object to the chart by using [`series`](../api/stock-chart/stockSeries/) property and then set the JSON data to
[`dataSource`](../api/stock-chart/stockSeries/#datasource) property.

Since the JSON contains DateTime data, set the [`valueType`](../api/stock-chart/stockChartAxisModel/#valuetype) for
horizontal axis to DateTime. By default, the axis valueType is Numeric.

{% tab template= "stock-chart/getting-started", es5Template="es5populateData" %}

```javascript

var stockchartData = [{
   x: new Date( '2012-04-02' ),
    open : 85.9757,
    high : 90.6657,
    low : 85.7685,
    close : 90.5257,
    volume : 660187068
  },
  {
   x: new Date( '2012-04-09' ),
    open : 89.4471,
    high : 92,
    low : 86.2157,
    close : 86.4614,
    volume : 912634864
  },
  {
   x: new Date( '2012-04-16' ),
    open : 87.1514,
    high : 88.6071,
    low : 81.4885,
    close : 81.8543,
    volume : 1221746066
  },
  {
   x: new Date( '2012-04-23' ),
    open : 81.5157,
    high : 88.2857,
    low : 79.2857,
    close : 86.1428,
    volume : 965935749
  },
  {
   x: new Date( '2012-04-30' ),
    open : 85.4,
    high : 85.4857,
    low : 80.7385,
    close : 80.75,
    volume : 615249365
  }];
var stockchart = new ej.charts.StockChart({
    series:[{
        // dataSource for stockchart series
        dataSource: stockchartData,
        xName: 'month',
        yName: 'sales',
        type: 'Candle'
    }]
}, '#element');

```

{% endtab %}

## Add Stock Chart Title

You can add a title using [`title`](../api/stock-chart/stockChartModel/#title) property to the Stock Chart to provide quick
information to the user about the data plotted in the Chart.

{% tab template= "stock-chart/getting-started", es5Template= "es5chartTitle" %}

```javascript

var stockChartData = [{
   x: new Date( '2012-04-02' ),
    open : 85.9757,
    high : 90.6657,
    low : 85.7685,
    close : 90.5257,
    volume : 660187068
  },
  {
   x: new Date( '2012-04-09' ),
    open : 89.4471,
    high : 92,
    low : 86.2157,
    close : 86.4614,
    volume : 912634864
  },
  {
   x: new Date( '2012-04-16' ),
    open : 87.1514,
    high : 88.6071,
    low : 81.4885,
    close : 81.8543,
    volume : 1221746066
  },
  {
   x: new Date( '2012-04-23' ),
    open : 81.5157,
    high : 88.2857,
    low : 79.2857,
    close : 86.1428,
    volume : 965935749
  },
  {
   x: new Date( '2012-04-30' ),
    open : 85.4,
    high : 85.4857,
    low : 80.7385,
    close : 80.75,
    volume : 615249365
  }];
var stockChart = new ej.charts.StockChart({
    // Title for chart
    title: 'Sales Analysis'
    series:[{
        dataSource: stockChartData,
        name:'Sales',
        xName: 'month',
        yName: 'sales',
        type: 'Candle'
    }],
}, '#element');

```

{% endtab %}

## Add Crosshair

Crosshair has a vertical and horizontal line to view the value of the axis at mouse or touch position.

Crosshair lines can be enabled by using [`enable`](../api/chart/crosshairSettingsModel/#enable) property in the `crosshair`. Likewise tooltip label for an axis can be enabled by using [`enable`](../api/chart/crosshairTooltipModel/#enable) property of `crosshairTooltip` in the corresponding axis.

{% tab template= "stock-chart/getting-started", es5Template="es5CrossHair" %}

```javascript

var stockChart = new ej.charts.StockChart({
        primaryXAxis: {
            valueType: 'DateTime',
        },
        series: [
            {
                type: 'Candle', width: 2, name: 'Temperature',
                dataSource: series1, xName: 'x', yName: 'y'
            }
        ],
        //crosshair for chart
        crosshair: { enable: true },
        legendSettings: { visible: true },
        title: 'Weather Condition'
}, '#element');

```

{% endtab %}

## Add Trackball

Trackball is used to track a data point closest to the mouse or touch position. Trackball marker indicates the closest point and trackball tooltip displays the information about the point. To use trackball feature, we need to inject `Crosshair` module and `Tooltip` module using
`StockChart.Inject(Crosshair, Tooltip)`.

Trackball can be enabled by setting the [`enable`](../api/chart/crosshairSettings/#enable-boolean) property of the crosshair to true and
[`shared`](../api/chart/tooltipSettings/#shared) property in `tooltip` to true in chart.

{% tab template= "stock-chart/getting-started", es5Template="es5Trackball" %}

```javascript

var stockChart = new ej.charts.StockChart({
        primaryXAxis: {
            valueType: 'DateTime',
        },
        series: [
            {
                dataSource: trackData, name: 'John', xName: 'x',
                 type: 'Line', width: 2,
                yName: 'y'
            },
            {
                dataSource: trackData, name: 'Andrew', xName: 'x',
                type: 'Line', width: 2,
                yName: 'y1'
            },
            {
                dataSource: trackData, name: 'Thomas', xName: 'x',
                type: 'Line', width: 2,
                yName: 'y2'
            },
            {
                dataSource: trackData, name: 'Mark', xName: 'x',
                type: 'Line', width: 2,
                yName: 'y3'
            },
            {
                dataSource: trackData, name: 'William', xName: 'x',
                type: 'Line', width: 2,
                yName: 'y4'
            }
        ],
        // trackball for chart
        tooltip: { enable: true, shared: true, format: '${series.name} : ${point.x} : ${point.y}' },
        crosshair: { enable: true, lineType: 'Vertical' },
        title: 'Average Sales per Person'
}, '#element');

```

{% endtab %}