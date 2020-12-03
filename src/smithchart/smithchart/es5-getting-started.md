# Getting Started  with JavaScript(ES5)

The Essential JS 2 for JavaScript (global script) is an ES5 formatted pure JavaScript framework which can be directly used in latest web browsers.

## Control Initialization

The Essential JS 2 JavaScript controls can be initialized by using either of the following ways.

* Using local script references in a HTML page.
* Using CDN link for script.

### Using local script references in a HTML page

**Step 1:** Create an app folder `quickstart` for getting started.

**Step 2:** You can get the global scripts from the [Essential Studio JavaScript (Essential JS 2)](https://www.syncfusion.com/downloads/essential-js2) build installed location.

**Syntax:**
> Dependency Script: `**(installed location)**\Syncfusion\Essential Studio\JavaScript - EJ2\{RELEASE_VERSION}\Web (Essential JS 2)\JavaScript\{DEPENDENCY_PACKAGE_NAME}\dist\global\{DEPENDENCY_PACKAGE_NAME}.min.js`
>
> Control Script: `**(installed location)**\Syncfusion\Essential Studio\JavaScript - EJ2\{RELEASE_VERSION}\Web (Essential JS 2)\JavaScript\{PACKAGE_NAME}\dist\global\{PACKAGE_NAME}.min.js`

**Example:**
> Dependency Script: `C:\Program Files (x86)\Syncfusion\Essential Studio\JavaScript - EJ2\16.3.0.17\Web (Essential JS 2)\JavaScript\ej2-base\dist\global\ej2-base.min.js`
>
> Control Script: `C:\Program Files (x86)\Syncfusion\Essential Studio\JavaScript - EJ2\16.3.0.17\Web (Essential JS 2)\JavaScript\ej2-charts\dist\global\ej2-charts.min.js`

The below located script and style file contains all Syncfusion JavaScript (ES5) UI control resources in a single file.

> Scripts: `**(installed location)**\Syncfusion\Essential Studio\JavaScript - EJ2\{RELEASE_VERSION}\Web (Essential JS 2)\JavaScript\ej2\dist\ej2.min.js`

The [`Custom Resource Generator (CRG)`](https://crg.syncfusion.com/) is an online web tool, which can be used to generate the custom script for a set of specific controls. This web tool is useful to combine the required control scripts in a single file.

**Step 3:** Create a folder `~/quickstart/resources` and copy/paste the global scripts from the above installed location to `~/quickstart/resources/package` corresponding package location.

**Step 4:** Create a HTML page (index.html) in `~/quickstart/index.html` and add the Essentials JS 2 script references.

```html
<!DOCTYPE html>
<html xmlns="http://www.w3.org/1999/xhtml">
    <head>
        <title>Essential JS 2</title>

        <!-- Essential JS 2 Base's global script (Dependency Script) -->
        <script src="resources/base/ej2-base.min.js" type="text/javascript"></script>
        <!-- Essential JS 2 smithchart's global script (Control Script) -->
        <script src="resources/charts/ej2-charts.min.js" type="text/javascript"></script>
    </head>
    <body>
    </body>
</html>
```

**Step 5:** Now, add the `Smithchart` element and initiate the `Syncfusion JavaScript (ES5) Smithchart` control in the `~/quickstart/index.html` by using following code.

```html
<!DOCTYPE html>
<html xmlns="http://www.w3.org/1999/xhtml">
    <head>
        <title>Essential JS 2</title>

        <!-- Essential JS 2 Base's global script (Dependency Script) -->
        <script src="resources/base/ej2-base.min.js" type="text/javascript"></script>
        <!-- Essential JS 2 smithchart's global script (Control Script) -->
        <script src="resources/charts/ej2-charts.min.js" type="text/javascript"></script>
    </head>
    <body>
        <!-- Add the HTML <smithchart> element  -->
        <smithchart id="element">Smithchart</smithchart>
        <script>
            // initialize smithchart control
            var smithchart = new ej.charts.Smithchart();
            // Render initialized smithchart.
            smithchart.appendTo('#element');
        </script>
    </body>
</html>
```

**Step 6:** Now, run the `index.html` in web browser, it will render the **Syncfusion JavaScript Smithchart** control.

### Using CDN link for script reference

**Step 1:** Create an app folder `quickstart` for getting started.

**Step 2:** The Essential JS 2 controls's global scripts is already hosted in the below CDN link formats.

**Syntax:**
> Dependency Script: `https://cdn.syncfusion.com/ej2/{DEPENDENCY_PACKAGE_NAME}/dist/global/{PACKAGE_NAME}.min.js`
>
> Control Script: `https://cdn.syncfusion.com/ej2/{PACKAGE_NAME}/dist/global/{PACKAGE_NAME}.min.js`

**Example:**
> Script: [`https://cdn.syncfusion.com/ej2/ej2-charts/dist/global/ej2-charts.min.js`](https://cdn.syncfusion.com/ej2/ej2-charts/dist/global/ej2-charts.min.js)

**Step 3:** Create a HTML page (index.html) in `~/quickstart/index.html` location and add the CDN link references. Now, add the `Smithchart` element and initiate the `Syncfusion JavaScript (ES5) Smithchart` control in the index.html by using following code.

{% tab template= "smithchart/smithchart-axis",  es5Template="default" %}

{% endtab %}

**Step 4:** Now, run the `index.html` in web browser, it will render the `Syncfusion JavaScript Smithchart` control.

## Add Series to Smithchart

Smithchart had two type of specification for adding series.
* dataSource - Using this, Data object can bind directly by specifying the resistance and reactance values, series add to smithchart.
* points - Using this, collection of resistance and reactance values can bind directly to render series.

Below sample demonstrate adding two series to smithchart both ways.
* First series Transmission1 shows dataSource bound series.
* Second series Transmission2 shows points bound series.

{% tab template= "smithchart/smithchart-axis",  es5Template="series" %}

{% endtab %}

## Add title to SmithChart

smithchart `title` API used to add title for smithchart. In that `text` API used to set text of the title.
API `visible` used to toggle the title.

{% tab template= "smithchart/smithchart-axis", es5Template="title" %}

{% endtab %}

## Enable Marker to Smithchart

To use series marker and it's customization in smithchart, use series `marker`. To display marker for particular series, need to specify  `marker visible` as true. Below sample marker enabled for first series only.

{% tab template= "smithchart/smithchart-axis",  es5Template="marker" %}

{% endtab %}

## Enable DataLabel to Smithchart Marker

To use marker dataLabel and it's customization in smithchart, use marker `dataLabel`. To display dataLabel for particular series marker, need to specify  `dataLabel visible` as true in that series `marker`. Below sample dataLabel enabled for first series.

{% tab template= "smithchart/smithchart-axis",  es5Template="label" %}

{% endtab %}

## Enable Legend for Smithchart

Smithchart had a legend feature, which is used to denote the correspond series. To enable the legend, need to inject `SmithchartLegend` module using `Smithchart.Inject(SmithchartLegend)` method and smithchart `legendSettings` `visible` as true. Following example sample shows enabling legend for smithchart. Series name can customize using series `name`.

{% tab template= "smithchart/smithchart-axis",  es5Template="legend" %}

{% endtab %}

## Enable Tooltip for Smithchart Series

Smithchart had a tooltip feature, which is used to show the current point's values. To enable the tooltip, need to inject `TooltipRender` module using `Smithchart.Inject(TooltipRender)` method and smithchart series `tooltip` `visible` as true. Following example sample shows enabling tooltip for smithchart series collection.

{% tab template= "smithchart/smithchart-axis",  es5Template="tooltip" %}

{% endtab %}