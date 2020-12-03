# Getting Started

This section explains you the steps required to create a Smith Chart and demonstrate the basic usage of the Smith Chart control.

## Dependencies

Below is the list of minimum dependencies required to use the Smith Chart.

```javascript
|-- @syncfusion/ej2-charts
    |-- @syncfusion/ej2-base
    |-- @syncfusion/ej2-data
    |-- @syncfusion/ej2-svg-base
    |-- @syncfusion/ej2-pdf-export
    |-- @syncfusion/ej2-compression
    |-- @syncfusion/ej2-file-utils
```

## Installation and Configuration

* To get you started with Smith Chart component, you can clone the
[`Essential JS 2 quickstart`](https://github.com/syncfusion/ej2-quickstart.git) project
and install necessary packages by using the following commands.

```sh
git clone https://github.com/syncfusion/ej2-quickstart.git quickstart
cd quickstart
npm install
```

* `Smith Chart packages` need to be mapped in `system.config.js` configuration file.

```javascript
System.config({
    paths: {
        'syncfusion:': './node_modules/@syncfusion/',
    },
    map: {
        app: 'app',

        //Syncfusion packages mapping
        "@syncfusion/ej2-base": "syncfusion:ej2-base/dist/ej2-base.umd.min.js",
        "@syncfusion/ej2-data": "syncfusion:ej2-data/dist/ej2-data.umd.min.js",
        "@syncfusion/ej2-svg-base": "syncfusion:ej2-svg-base/dist/ej2-svg-base.umd.min.js",
        "@syncfusion/ej2-pdf-export": "syncfusion:ej2-pdf-export/dist/ej2-pdf-export.umd.min.js",
        "@syncfusion/ej2-compression": "syncfusion:ej2-compression/dist/ej2-compression.umd.min.js",
        "@syncfusion/ej2-file-utils": "syncfusion:ej2-file-utils/dist/ej2-file-utils.umd.min.js",
        "@syncfusion/ej2-popups": "syncfusion:ej2-popups/dist/ej2-popups.umd.min.js",
        "@syncfusion/ej2-buttons": "syncfusion:ej2-buttons/dist/ej2-buttons.umd.min.js",
        "@syncfusion/ej2-charts": "syncfusion:ej2-charts/dist/ej2-charts.umd.min.js",
    },
    packages: {
        'app': { main: 'app', defaultExtension: 'js' }
    }
});
```

>The [project](https://github.com/syncfusion/ej2-quickstart.git) is preconfigured with common
settings (`src/styles/styles.css`, `system.config.js` ) to start
with all Essential JS 2 components.

## Add Smith Chart to the Project

Add the HTML div element for Smith Chart into your `index.html`. `[src/index.html]`

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <title>EJ2 Animation</title>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <meta name="description" content="Typescript UI Controls" />
    <meta name="author" content="Syncfusion" />
    <link href="index.css" rel="stylesheet" />
    <script src="https://cdnjs.cloudflare.com/ajax/libs/systemjs/0.19.38/system.js"></script>
    <script src="systemjs.config.js"></script>
</head>

<body>
     <!--container which is going to render the Smith Chart-->
     <div id='container'>
     </div>
</body>

</html>
```

Now import the Smithchart component into your `index.ts` to instantiate a smithchart and append the smithchart instance to the `#container`

```javascript
import { Smithchart } from '@syncfusion/ej2-charts';

// initialize Smithchart component
let smithchart: Smithchart = new Smithchart();

// render initialized Smithchart
smithchart.appendTo('#container');
```

Now use the `npm run start` command to run the application in the browser.

```cmd
npm run start
```

The below example shows a basic Smithchart.

{% tab template= "smithchart/getting-started",sourceFiles="index.ts,index.html,index.css" , isDefaultActive=true , es5Template = "es5default" %}

```typescript
import { Smithchart } from '@syncfusion/ej2-charts';

let smithchart: Smithchart = new Smithchart();

smithchart.appendTo('#container');
```

{% endtab %}

## Module Injection

Smithchart component are segregated into individual feature-wise modules. In order to use a particular feature,
you need to inject its feature module using `Smithchart.Inject()` method. In the current application, we are
going to modify the above basic smithchart to visualize transmission lines.
For this application we are going to use  tooltip and legend feature of the smithchart. Please find relevant
feature module name and description as follows.

* SmithchartLegend - Inject this provider to use legend feature.
* TooltipRender - Inject this provider to use tooltip feature.

Now import the above mentioned modules from smithchart package and inject it into the Smithchart component using
`Smithchart.Inject`  method.

```javascript
import { Smithchart, SmithchartLegend, TooltipRender } from '@syncfusion/ej2-charts';
Smithchart.Inject(SmithchartLegend, TooltipRender);
```

## Add Series to Smithchart

Smithchart had two type of specification for adding series.
* dataSource - Using this, Data object can bind directly by specifying the resistance and reactance values, series add to smithchart.
* points - Using this, collection of resistance and reactance values can bind directly to render series.

Below sample demonstrate adding two series to smithchart both ways.
* First series Transmission1 shows dataSource bound series.
* Second series Transmission2 shows points bound series.

{% tab template= "smithchart/getting-started",sourceFiles="index.ts,index.html" , isDefaultActive=true , es5Template = "es5series" %}

```typescript
import { Smithchart } from '@syncfusion/ej2-charts';

let smithchart: Smithchart = new Smithchart({
    series: [
        {
            dataSource: [
                { resistance: 0, reactance: 0.05 }, { resistance: 0, reactance: 0.05 },
                { resistance: 0, reactance: 0.05 }, { resistance: 0, reactance: 0.05 },
                { resistance: 0, reactance: 0.05 }, { resistance: 0, reactance: 0.05 },
                { resistance: 0, reactance: 0.05 }, { resistance: 0, reactance: 0.05 },
                { resistance: 0, reactance: 0.05 }, { resistance: 0, reactance: 0.05 },
                { resistance: 0.3, reactance: 0.1 }, { resistance: 0.5, reactance: 0.2 },
                { resistance: 1.5, reactance: 0.5 }, { resistance: 2.0, reactance: 0.5 },
                { resistance: 2.5, reactance: 0.4 }, { resistance: 3.5, reactance: 0.0 },
                { resistance: 2.5, reactance: 0.4 }, { resistance: 3.5, reactance: 0.0 },
                { resistance: 2.5, reactance: 0.4 }, { resistance: 3.5, reactance: 0.0 },
                { resistance: 4.5, reactance: -0.5 }, { resistance: 5.0, reactance: -1.0 }

            ],
            name: 'Transmission1',
            reactance: 'reactance', resistance: 'resistance'
        },
        {
            points: [{ resistance: 0, reactance: 0.15 }, { resistance: 0, reactance: 0.15 },
            { resistance: 0, reactance: 0.15 }, { resistance: 0.3, reactance: 0.2 },
            { resistance: 0.3, reactance: 0.2 }, { resistance: 0.3, reactance: 0.2 },
            { resistance: 0.3, reactance: 0.2 }, { resistance: 0.3, reactance: 0.2 },
            { resistance: 0.5, reactance: 0.4 }, { resistance: 1.0, reactance: 0.8 },
            { resistance: 2.5, reactance: 1.3 }, { resistance: 3.5, reactance: 1.6 },
            { resistance: 3.5, reactance: 1.6 }, { resistance: 3.5, reactance: 1.6 },
            { resistance: 4.5, reactance: 2.0 }, { resistance: 6.0, reactance: 4.5 },
            { resistance: 8, reactance: 6 }, { resistance: 10, reactance: 25 }],
            name: 'Transmission2'
        }
    ]
});
smithchart.appendTo('#container');
```

{% endtab %}

## Add title to SmithChart

smithchart `title` API used to add title for smithchart. In that `text` API used to set text of the title.
API `visible` used to toggle the title.

{% tab template= "smithchart/getting-started",sourceFiles="index.ts,index.html" , isDefaultActive=true , es5Template = "es5series" %}

```typescript
import { Smithchart } from '@syncfusion/ej2-charts';

let smithchart: Smithchart = new Smithchart({
    title: { text: 'Transmission lines applied for both impedance and admittance'},
    series: [
        {
            dataSource: [
                { resistance: 0, reactance: 0.05 }, { resistance: 0, reactance: 0.05 },
                { resistance: 0, reactance: 0.05 }, { resistance: 0, reactance: 0.05 },
                { resistance: 0, reactance: 0.05 }, { resistance: 0, reactance: 0.05 },
                { resistance: 0, reactance: 0.05 }, { resistance: 0, reactance: 0.05 },
                { resistance: 0, reactance: 0.05 }, { resistance: 0, reactance: 0.05 },
                { resistance: 0.3, reactance: 0.1 }, { resistance: 0.5, reactance: 0.2 },
                { resistance: 1.5, reactance: 0.5 }, { resistance: 2.0, reactance: 0.5 },
                { resistance: 2.5, reactance: 0.4 }, { resistance: 3.5, reactance: 0.0 },
                { resistance: 2.5, reactance: 0.4 }, { resistance: 3.5, reactance: 0.0 },
                { resistance: 2.5, reactance: 0.4 }, { resistance: 3.5, reactance: 0.0 },
                { resistance: 4.5, reactance: -0.5 }, { resistance: 5.0, reactance: -1.0 }

            ],
            name: 'Transmission1',
            reactance: 'reactance', resistance: 'resistance'
        },
        {
            points: [{ resistance: 0, reactance: 0.15 }, { resistance: 0, reactance: 0.15 },
            { resistance: 0, reactance: 0.15 }, { resistance: 0.3, reactance: 0.2 },
            { resistance: 0.3, reactance: 0.2 }, { resistance: 0.3, reactance: 0.2 },
            { resistance: 0.3, reactance: 0.2 }, { resistance: 0.3, reactance: 0.2 },
            { resistance: 0.5, reactance: 0.4 }, { resistance: 1.0, reactance: 0.8 },
            { resistance: 2.5, reactance: 1.3 }, { resistance: 3.5, reactance: 1.6 },
            { resistance: 3.5, reactance: 1.6 }, { resistance: 3.5, reactance: 1.6 },
            { resistance: 4.5, reactance: 2.0 }, { resistance: 6.0, reactance: 4.5 },
            { resistance: 8, reactance: 6 }, { resistance: 10, reactance: 25 }],
            name: 'Transmission2'
        }
    ]
});
smithchart.appendTo('#container');
```

{% endtab %}

## Enable Marker to Smithchart

To use series marker and it's customization in smithchart, use series `marker`. To display marker for particular series, need to specify  `marker visible` as true. Below sample marker enabled for first series only.

{% tab template= "smithchart/getting-started",sourceFiles="index.ts,index.html" , isDefaultActive=true , es5Template = "es5series" %}

```typescript
import { Smithchart } from '@syncfusion/ej2-charts';

let smithchart: Smithchart = new Smithchart({
    title: { text: 'Transmission lines applied for both impedance and admittance'},
    series: [
        {
            dataSource: [
                { resistance: 0, reactance: 0.05 }, { resistance: 0, reactance: 0.05 },
                { resistance: 0, reactance: 0.05 }, { resistance: 0, reactance: 0.05 },
                { resistance: 0, reactance: 0.05 }, { resistance: 0, reactance: 0.05 },
                { resistance: 0, reactance: 0.05 }, { resistance: 0, reactance: 0.05 },
                { resistance: 0, reactance: 0.05 }, { resistance: 0, reactance: 0.05 },
                { resistance: 0.3, reactance: 0.1 }, { resistance: 0.5, reactance: 0.2 },
                { resistance: 1.5, reactance: 0.5 }, { resistance: 2.0, reactance: 0.5 },
                { resistance: 2.5, reactance: 0.4 }, { resistance: 3.5, reactance: 0.0 },
                { resistance: 2.5, reactance: 0.4 }, { resistance: 3.5, reactance: 0.0 },
                { resistance: 2.5, reactance: 0.4 }, { resistance: 3.5, reactance: 0.0 },
                { resistance: 4.5, reactance: -0.5 }, { resistance: 5.0, reactance: -1.0 }
            ],
            name: 'Transmission1',
            reactance: 'reactance', resistance: 'resistance',
            marker: {
                visible: true
            }
        },
        {
            points: [{ resistance: 0, reactance: 0.15 }, { resistance: 0, reactance: 0.15 },
            { resistance: 0, reactance: 0.15 }, { resistance: 0.3, reactance: 0.2 },
            { resistance: 0.3, reactance: 0.2 }, { resistance: 0.3, reactance: 0.2 },
            { resistance: 0.3, reactance: 0.2 }, { resistance: 0.3, reactance: 0.2 },
            { resistance: 0.5, reactance: 0.4 }, { resistance: 1.0, reactance: 0.8 },
            { resistance: 2.5, reactance: 1.3 }, { resistance: 3.5, reactance: 1.6 },
            { resistance: 3.5, reactance: 1.6 }, { resistance: 3.5, reactance: 1.6 },
            { resistance: 4.5, reactance: 2.0 }, { resistance: 6.0, reactance: 4.5 },
            { resistance: 8, reactance: 6 }, { resistance: 10, reactance: 25 }],
            name: 'Transmission2'
        }
    ]
});
smithchart.appendTo('#container');
```

{% endtab %}

## Enable DataLabel to Smithchart Marker

To use marker dataLabel and it's customization in smithchart, use marker `dataLabel`. To display dataLabel for particular series marker, need to specify  `dataLabel visible` as true in that series `marker`. Below sample dataLabel enabled for first series.

{% tab template= "smithchart/getting-started",sourceFiles="index.ts,index.html" , isDefaultActive=true , es5Template = "es5series" %}

```typescript
import { Smithchart } from '@syncfusion/ej2-charts';

let smithchart: Smithchart = new Smithchart({
    title: { text: 'Transmission lines applied for both impedance and admittance'},
    series: [
        {
            dataSource: [
                { resistance: 0, reactance: 0.05 }, { resistance: 0, reactance: 0.05 },
                { resistance: 0, reactance: 0.05 }, { resistance: 0, reactance: 0.05 },
                { resistance: 0, reactance: 0.05 }, { resistance: 0, reactance: 0.05 },
                { resistance: 0, reactance: 0.05 }, { resistance: 0, reactance: 0.05 },
                { resistance: 0, reactance: 0.05 }, { resistance: 0, reactance: 0.05 },
                { resistance: 0.3, reactance: 0.1 }, { resistance: 0.5, reactance: 0.2 },
                { resistance: 1.5, reactance: 0.5 }, { resistance: 2.0, reactance: 0.5 },
                { resistance: 2.5, reactance: 0.4 }, { resistance: 3.5, reactance: 0.0 },
                { resistance: 2.5, reactance: 0.4 }, { resistance: 3.5, reactance: 0.0 },
                { resistance: 2.5, reactance: 0.4 }, { resistance: 3.5, reactance: 0.0 },
                { resistance: 4.5, reactance: -0.5 }, { resistance: 5.0, reactance: -1.0 }
            ],
            name: 'Transmission1',
            reactance: 'reactance', resistance: 'resistance',
            marker: {
                visible: true,
                dataLabel: {
                    visible: true
                }
            }
        },
        {
            points: [{ resistance: 0, reactance: 0.15 }, { resistance: 0, reactance: 0.15 },
            { resistance: 0, reactance: 0.15 }, { resistance: 0.3, reactance: 0.2 },
            { resistance: 0.3, reactance: 0.2 }, { resistance: 0.3, reactance: 0.2 },
            { resistance: 0.3, reactance: 0.2 }, { resistance: 0.3, reactance: 0.2 },
            { resistance: 0.5, reactance: 0.4 }, { resistance: 1.0, reactance: 0.8 },
            { resistance: 2.5, reactance: 1.3 }, { resistance: 3.5, reactance: 1.6 },
            { resistance: 3.5, reactance: 1.6 }, { resistance: 3.5, reactance: 1.6 },
            { resistance: 4.5, reactance: 2.0 }, { resistance: 6.0, reactance: 4.5 },
            { resistance: 8, reactance: 6 }, { resistance: 10, reactance: 25 }],
            name: 'Transmission2'
        }
    ]
});
smithchart.appendTo('#container');
```

{% endtab %}

## Enable Legend for Smithchart

Smithchart had a legend feature, which is used to denote the correspond series. To enable the legend, need to inject `SmithchartLegend` module using `Smithchart.Inject(SmithchartLegend)` method and smithchart `legendSettings` `visible` as true. Following example sample shows enabling legend for smithchart. Series name can customize using series `name`.

{% tab template= "smithchart/getting-started",sourceFiles="index.ts,index.html" , isDefaultActive=true , es5Template = "es5series" %}

```typescript
import { Smithchart, SmithchartLegend} from '@syncfusion/ej2-charts';

Smithchart.Inject(SmithchartLegend);

let smithchart: Smithchart = new Smithchart({
    title: { text: 'Transmission lines applied for both impedance and admittance'},
    legendSettings: {
        visible: true
    },
    series: [
        {
            dataSource: [
                { resistance: 0, reactance: 0.05 }, { resistance: 0, reactance: 0.05 },
                { resistance: 0, reactance: 0.05 }, { resistance: 0, reactance: 0.05 },
                { resistance: 0, reactance: 0.05 }, { resistance: 0, reactance: 0.05 },
                { resistance: 0, reactance: 0.05 }, { resistance: 0, reactance: 0.05 },
                { resistance: 0, reactance: 0.05 }, { resistance: 0, reactance: 0.05 },
                { resistance: 0.3, reactance: 0.1 }, { resistance: 0.5, reactance: 0.2 },
                { resistance: 1.5, reactance: 0.5 }, { resistance: 2.0, reactance: 0.5 },
                { resistance: 2.5, reactance: 0.4 }, { resistance: 3.5, reactance: 0.0 },
                { resistance: 2.5, reactance: 0.4 }, { resistance: 3.5, reactance: 0.0 },
                { resistance: 2.5, reactance: 0.4 }, { resistance: 3.5, reactance: 0.0 },
                { resistance: 4.5, reactance: -0.5 }, { resistance: 5.0, reactance: -1.0 }
            ],
            name: 'Transmission1',
            reactance: 'reactance', resistance: 'resistance',
            marker: {
                visible: true,
                dataLabel: {
                    visible: true
                }
            }
        },
        {
            points: [{ resistance: 0, reactance: 0.15 }, { resistance: 0, reactance: 0.15 },
            { resistance: 0, reactance: 0.15 }, { resistance: 0.3, reactance: 0.2 },
            { resistance: 0.3, reactance: 0.2 }, { resistance: 0.3, reactance: 0.2 },
            { resistance: 0.3, reactance: 0.2 }, { resistance: 0.3, reactance: 0.2 },
            { resistance: 0.5, reactance: 0.4 }, { resistance: 1.0, reactance: 0.8 },
            { resistance: 2.5, reactance: 1.3 }, { resistance: 3.5, reactance: 1.6 },
            { resistance: 3.5, reactance: 1.6 }, { resistance: 3.5, reactance: 1.6 },
            { resistance: 4.5, reactance: 2.0 }, { resistance: 6.0, reactance: 4.5 },
            { resistance: 8, reactance: 6 }, { resistance: 10, reactance: 25 }],
            name: 'Transmission2'
        }
    ]
});
smithchart.appendTo('#container');
```

{% endtab %}

## Enable Tooltip for Smithchart Series

Smithchart had a tooltip feature, which is used to show the current point's values. To enable the tooltip, need to inject `TooltipRender` module using `Smithchart.Inject(TooltipRender)` method and smithchart series `tooltip` `visible` as true. Following example sample shows enabling tooltip for smithchart series collection.

{% tab template= "smithchart/getting-started",sourceFiles="index.ts,index.html" , isDefaultActive=true , es5Template = "es5series" %}

```typescript
import { Smithchart, SmithchartLegend, TooltipRender} from '@syncfusion/ej2-charts';

Smithchart.Inject(SmithchartLegend, TooltipRender);

let smithchart: Smithchart = new Smithchart({
    title: { text: 'Transmission lines applied for both impedance and admittance'},
    legendSettings: {
        visible: true
    },
    series: [
        {
            dataSource: [
                { resistance: 0, reactance: 0.05 }, { resistance: 0, reactance: 0.05 },
                { resistance: 0, reactance: 0.05 }, { resistance: 0, reactance: 0.05 },
                { resistance: 0, reactance: 0.05 }, { resistance: 0, reactance: 0.05 },
                { resistance: 0, reactance: 0.05 }, { resistance: 0, reactance: 0.05 },
                { resistance: 0, reactance: 0.05 }, { resistance: 0, reactance: 0.05 },
                { resistance: 0.3, reactance: 0.1 }, { resistance: 0.5, reactance: 0.2 },
                { resistance: 1.5, reactance: 0.5 }, { resistance: 2.0, reactance: 0.5 },
                { resistance: 2.5, reactance: 0.4 }, { resistance: 3.5, reactance: 0.0 },
                { resistance: 2.5, reactance: 0.4 }, { resistance: 3.5, reactance: 0.0 },
                { resistance: 2.5, reactance: 0.4 }, { resistance: 3.5, reactance: 0.0 },
                { resistance: 4.5, reactance: -0.5 }, { resistance: 5.0, reactance: -1.0 }
            ],
            name: 'Transmission1',
            reactance: 'reactance', resistance: 'resistance',
            tooltip: {
                visible: true
            },
            marker: {
                visible: true,
                dataLabel: {
                    visible: true
                }
            }
        },
        {
            points: [{ resistance: 0, reactance: 0.15 }, { resistance: 0, reactance: 0.15 },
            { resistance: 0, reactance: 0.15 }, { resistance: 0.3, reactance: 0.2 },
            { resistance: 0.3, reactance: 0.2 }, { resistance: 0.3, reactance: 0.2 },
            { resistance: 0.3, reactance: 0.2 }, { resistance: 0.3, reactance: 0.2 },
            { resistance: 0.5, reactance: 0.4 }, { resistance: 1.0, reactance: 0.8 },
            { resistance: 2.5, reactance: 1.3 }, { resistance: 3.5, reactance: 1.6 },
            { resistance: 3.5, reactance: 1.6 }, { resistance: 3.5, reactance: 1.6 },
            { resistance: 4.5, reactance: 2.0 }, { resistance: 6.0, reactance: 4.5 },
            { resistance: 8, reactance: 6 }, { resistance: 10, reactance: 25 }],
            name: 'Transmission2',
            tooltip: {
                visible: true
            }
        }
    ]
});
smithchart.appendTo('#container');
```

{% endtab %}