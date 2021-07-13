---
title: " Getting Started with JavaScript(ES5) Linear Gauge component | Syncfusion "

component: "Linear Gauge"

description: "Learn here about getting started with Syncfusion JavaScript(ES5) Linear Gauge component, its elements, and more."
---

# Getting Started  with JavaScript(ES5) Linear Gauge

This section explains you the steps to create a simple Linear Gauge and demonstrates the basic usage of the Linear Gauge component.

## Control Initialization

The Essential JS 2 JavaScript controls can be initialized by using either of the following ways.

* Using local script references in a HTML page.
* Using CDN link for script reference.

### Using local script references in a HTML page

**Step 1:** Create an app folder **quickstart** for getting started.

**Step 2:** You can get the global scripts from the [Essential Studio JavaScript (Essential JS 2)](https://www.syncfusion.com/downloads/essential-js2) build installed location.

**Syntax:**
> Dependency Script: `**(installed location)**\Syncfusion\Essential Studio\JavaScript - EJ2\{RELEASE_VERSION}\Web (Essential JS 2)\JavaScript\{DEPENDENCY_PACKAGE_NAME}\dist\global\{DEPENDENCY_PACKAGE_NAME}.min.js`
>
> Control Script: `**(installed location)**\Syncfusion\Essential Studio\JavaScript - EJ2\{RELEASE_VERSION}\Web (Essential JS 2)\JavaScript\{PACKAGE_NAME}\dist\global\{PACKAGE_NAME}.min.js`

**Example:**
> Dependency Script: `C:\Program Files (x86)\Syncfusion\Essential Studio\JavaScript - EJ2\16.3.0.17\Web (Essential JS 2)\JavaScript\ej2-base\dist\global\ej2-base.min.js`
>
> Control Script: `C:\Program Files (x86)\Syncfusion\Essential Studio\JavaScript - EJ2\16.3.0.17\Web (Essential JS 2)\JavaScript\ej2-lineargauge\dist\global\ej2-lineargauge.min.js`

The below located script file contains all Syncfusion JavaScript (ES5) UI control resources in a single file.

> Scripts: `**(installed location)**\Syncfusion\Essential Studio\JavaScript - EJ2\{RELEASE_VERSION}\Web (Essential JS 2)\JavaScript\ej2\dist\ej2.min.js`

The [`Custom Resource Generator (CRG)`](https://crg.syncfusion.com/) is an online web tool, which can be used to generate the custom script for a set of specific controls. This web tool is used to combine the required control scripts in a single file.

**Step 3:** Create a folder **~/quickstart/resources** and copy/paste the global scripts from the above installed location to **~/quickstart/resources/package** corresponding package location.

**Step 4:** Create a HTML page (index.html) in **~/quickstart/index.html** and add the Essentials JS 2 script references.

```html
<!DOCTYPE html>
<html xmlns="http://www.w3.org/1999/xhtml">
    <head>
        <title>Essential JS 2</title>

        <!-- Essential JS 2 Base's global script (Dependency Script) -->
        <script src="resources/base/ej2-base.min.js" type="text/javascript"></script>
        <!-- Essential JS 2 lineargauge's global script (Control Script) -->
        <script src="resources/lineargauge/ej2-lineargauge.min.js" type="text/javascript"></script>
    </head>
    <body>
    </body>
</html>
```

**Step 5:** Add the `LinearGauge` element and initiate the **Syncfusion JavaScript (ES5) LinearGauge** component in the **~/quickstart/index.html** by using the following code.

```html
<!DOCTYPE html>
<html xmlns="http://www.w3.org/1999/xhtml">
    <head>
        <title>Essential JS 2</title>

        <!-- Essential JS 2 Base's global script (Dependency Script) -->
        <script src="resources/base/ej2-base.min.js" type="text/javascript"></script>
        <!-- Essential JS 2 lineargauge's global script (Control Script) -->
        <script src="resources/lineargauge/ej2-lineargauge.min.js" type="text/javascript"></script>
    </head>
    <body>
        <!-- Add the HTML <lineargauge> element  -->
        <lineargauge id="element">Linear Gauge</lineargauge>
        <script>
            // initialize lineargauge control
            var lineargauge = new ej.lineargauge.LinearGauge();
            // Render initialized lineargauge.
            lineargauge.appendTo('#element');
        </script>
    </body>
</html>
```

**Step 6:** Run the `index.html` in web browser, it will render the **Syncfusion JavaScript Lineargauge** control.

### Using CDN link for script reference

**Step 1:** Create an app folder **quickstart** for getting started.

**Step 2:** The Essential JS 2 controls' global scripts is already hosted in the below CDN link formats.

**Syntax:**

> Dependency Script: `https://cdn.syncfusion.com/ej2/{DEPENDENCY_PACKAGE_NAME}/dist/global/{PACKAGE_NAME}.min.js`
> Control Script: `https://cdn.syncfusion.com/ej2/{PACKAGE_NAME}/dist/global/{PACKAGE_NAME}.min.js`

**Example:**

> Script: [`https://cdn.syncfusion.com/ej2/ej2-lineargauge/dist/global/ej2-lineargauge.min.js`](https://cdn.syncfusion.com/ej2/ej2-lineargauge/dist/global/ej2-lineargauge.min.js)

**Step 3:** Create a HTML page (index.html) in **~/quickstart/index.html** location and add the CDN link references. Now, add the `LinearGauge` element and initiate the **Syncfusion JavaScript (ES5) Linear Gauge** control in the **index.html** by using following code.

The below example shows a basic linear gauge component.

{% tab template="linear-gauge/es5-getting-started", es5Template="default" %}

```html
<!DOCTYPE html>
  <html xmlns="http://www.w3.org/1999/xhtml">
       <head>
            <title>Essential JS 2</title>

            <!-- Essential JS 2 Base's global script (Dependency Script) -->
            <script src="https://cdn.syncfusion.com/ej2/ej2-base/dist/global/ej2-base.min.js" type="text/javascript"></script>

            <!-- Essential JS 2 lineargauge's global script (Control Script) -->
            <script src="https://cdn.syncfusion.com/ej2/ej2-lineargauge/dist/global/ej2-lineargauge.min.js" type="text/javascript"></script>

       </head>
       <body>
           <!-- Add the HTML <lineargauge> element  -->
            <div id="element">Linear Gauge</div>
            <script>
                ej.base.enableRipple(true);
                // initialize lineargauge control
                var lineargauge = new ej.lineargauge.LinearGauge();
                // Render initialized lineargauge.
                lineargauge.appendTo('#element');
            </script>
       </body>
  </html>
```

{% endtab %}

**Step 4:** Now, run the **index.html** in web browser, it will render the **Syncfusion JavaScript Linear Gauge** control.

## Adding the Linear Gauge Title

The title can be added to the Linear Gauge component using the [`title`](../api/linear-gauge/linearGaugeModel#title) property in the Linear Gauge.

{% tab template="linear-gauge/es5-getting-started", es5Template="title" %}

{% endtab %}

## Setting the start and end of the axis line

The range of the axis can be set using the [`minimum`](../api/linear-gauge/axis#minimum) and [`maximum`](../api/linear-gauge/axis#maximum) properties in the Linear Gauge.

{% tab template="linear-gauge/es5-getting-started", es5Template="axis" %}

{% endtab %}

To denote the axis values with temperature units, add the °C as suffix to each label. This can be achieved by setting the **{value}°C** to the [`format`](../api/linear-gauge/labelModel/#format) property in the [`labelStyle`](../api/linear-gauge/axis#labelstyle) object of the axis. Here, **{value}** acts as a placeholder for each axis label.

To change the pointer value from the default value of the gauge, set the [`value`](../api/linear-gauge/pointer/#value) property in [`pointers`](../api/linear-gauge/pointerModel/) object of the axis.

{% tab template="linear-gauge/es5-getting-started", es5Template="temperature" %}

{% endtab %}

## Setting the value of the pointer

The pointer value is changed in the below sample using the [`value`](../api/linear-gauge/pointer/#value) property in [`pointers`](../api/linear-gauge/pointer) object of the axis.

{% tab template="linear-gauge/es5-getting-started", es5Template="pointer" %}

{% endtab %}