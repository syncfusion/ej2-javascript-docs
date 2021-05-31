# Compatibility with Syncfusion JavaScript (Essential JS 1)

This article provides a step-by-step introduction to configure the Essential JS 1 and Essential JS 2 JavaScript controls in a same web page.

## Prerequisites

To work with the Essential JS 1 and the Essential JS 2 controls compatibility in JavaScript (ES5), the below mentioned System requirements are necessary,

* [Essential JS 1 Dependencies](https://help.syncfusion.com/js/dependencies)
* [Visual Studio Code](https://code.visualstudio.com/)

## Creating JavaScript application with Syncfusion JavaScript (Essential JS 2) control

1. Create a JavaScript (ES5) application with the help of the given Essential JS 2 [Getting Started Documentation](./quick-start).

2. Now, the Syncfusion (Essential JS 2) JavaScript Button control rendered successfully in the web page.

## Adding Syncfusion JavaScript (Essential JS 1) control in the application

1. Before adding the Essential JS 1 control in the application, you should change the Essential JS 2 compatibility styles in the application.

    > The compatibility styles of Essential JS 1 and Essential JS 2 must be added in the application to prevent the UI conflicts between the Essential JS 1 and Essential JS 2 controls.

    Replace the style file in the `resources` folder from the below location.

    **Syntax:**
    > Styles: `**(installed location)**\Syncfusion\Essential Studio\JavaScript - EJ2\{RELEASE_VERSION}\Web (Essential JS 2)\JavaScript\ej2\styles\compatibility\material.css`

    **Example:**
    > Styles: `C:\Program Files (x86)\Syncfusion\Essential Studio\JavaScript - EJ2\16.3.0.17\Web (Essential JS 2)\JavaScript\ej2\styles\compatibility\material.css`

    If the CDN link is used in the application, then replace it with below link.

    > Styles: `https://cdn.syncfusion.com/ej2/styles/compatibility/material.css`

2. Now, add the Essential JS 1 script and compatibility styles with its dependencies in the `resources/ej1` location. You can get the Essential JS 1 scripts and styles from the below installed location.

    **Syntax:**
    > Script:
    > `**(installed location)**\Syncfusion\Essential Studio\{RELEASE_VERSION}\Web (Essential JS 1)\JavaScript\assets\scripts\web\ej.web.all.min.js`
    >
    > Styles:
    >`**(installed location)**\Syncfusion\Essential Studio\{RELEASE_VERSION}\Web (Essential JS 1)\JavaScript\assets\css\web\default-theme\ej.web.all.compatibility.min`

    **Example:**

    > Script:
    > `C:\Program Files (x86)\Syncfusion\Essential Studio\16.3.0.17\Web (Essential JS 1)\JavaScript\assets\scripts\web\ej.web.all.min.js`
    >
    > Styles:
    > `C:\Program Files (x86)\Syncfusion\Essential Studio\16.3.0.17\Web (Essential JS 1)\JavaScript\assets\css\web\default-theme\ej.web.all.compatibility.min`

3. Add the Essential JS 1 file references in the `index.html` with the HTML Button element for rendering Essential JS 1 Button control.

    > The Essential JS 1 scripts must be added before the Essential JS 2 script reference.

    ```html
    <!DOCTYPE html>
    <html xmlns="http://www.w3.org/1999/xhtml">

        <head>
            <title>Essential JS 2 - Essential JS 1</title>

            <!-- Essential JS 1 default theme -->
            <link href="resources/ej1/default-theme/ej.web.all.compatibility.min.css" rel="stylesheet" type="text/css" />
            <!-- Essential JS 2 material theme -->
            <link href="resources/material.css" rel="stylesheet" type="text/css" />

            <!-- Essential JS 1 scripts -->
            <script src="https://cdn.syncfusion.com/js/assets/external/jquery-1.10.2.min.js" type="text/javascript"></script>
            <script src="https://cdn.syncfusion.com/js/assets/external/jquery.easing.1.3.min.js" type="text/javascript"></script>
            <script src="resources/ej1/ej.web.all.min.js" type="text/javascript"></script>

            <!-- Essential JS 2 script -->
            <script src="resources/ej2.min.js" type="text/javascript"></script>
        </head>

        <body>
            <div style="margin: 50px;">
                <!-- Add HTML Button element for Essential JS 2 -->
                <button id="btn2">Essential JS 2</button>
            </div>

            <div style="margin: 50px;">
                <!-- Add HTML Button element for Essential JS 1 -->
                <button id="btn1">Essential JS 1</button>
            </div>
        </body>

    </html>
    ```

4. Initialize the Essential JS 1 and Essential JS 2 Button control inside the `<script>` element in `~/quickstart/index.html` file.

    ```html
        <script>
            // Extend ej namespace with Syncfusion
            $.extend(ej, Syncfusion);

            // Initialize Essential JS 2 JavaScript Button control
            var button = new ej.buttons.Button({
                isPrimary: true
            });
            button.appendTo('#btn2');

            // Initialize Essential JS 1 JavaScript Button control
            $("#btn1").ejButton();
        </script>
    ```

    > The `ej` namespace should be extend with `Syncfusion` before initializing the Essential JS 1 and Essential JS 2 controls.

5. Run `~/quickstart/index.html` in the web browser and the Essential JS 1 and Essential JS 2 Button controls will be rendered in the same web page.

    ![#ej1-ej2-button](./images/ej1-ej2-es5.png)
