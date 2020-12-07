---
title: "ProgressBar Getting Started"
component: "ProgressBar"
description: "This section explains how to create the Essential JS 2 ProgressBar component in Typescript application with its basic features."
---

# Getting Started

This section explains you the steps required to create a simple ProgressBar and demonstrate the basic usage of the ProgressBar control.

## Dependencies

The following list of dependencies are required to use the ProgressBar control in your application:

```javascript
|-- @syncfusion/ej2-progressbar
    |-- @syncfusion/ej2-base
    |-- @syncfusion/ej2-data: "*"
    |-- @syncfusion/ej2-svg-base
```

## Setup for local environment

Refer the following steps for setup your local environment.

**Step 1:** Create a root folder **myapp** for your application.

**Step 2:** Create **myapp/resources** folder to store local scripts and styles files.

**Step 3:** Create **myapp/index.js** and **myapp/index.html** files for initializing Essential JS 2 ProgressBar control.

## Adding Syncfusion resources

The Essential JS 2 Progress Bar control can be initialized by using either of the following ways.

* Using local script.
* Using CDN link for script.

### Using local script

You can get the global scripts and styles from the [Essential Studio JavaScript (Essential JS 2)](https://www.syncfusion.com/downloads/essential-js2) build installed location.

After installing the Essential JS 2 product build, you can copy the ProgressBar and its dependencies scripts and style file into the **resources/scripts** and **resources/styles** folder.

Refer the below code to find location ProgressBar script and style file.

**Syntax:**

> Script: `**(installed location)**/Syncfusion/Essential Studio/{RELEASE_VERSION}/Essential JS 2/{PACKAGE_NAME}/dist/global/{PACKAGE_NAME}.min.js`
>

**Example:**

> Script: `C:/Program Files (x86)/Syncfusion/Essential Studio/15.4.30/Essential JS 2/ej2-progressbar/dist/global/ej2-progressbar.min.js`
>

After copying the files, then you can refer the ProgressBar scripts into the `index.html` file.
The below html code example shows the minimal dependency of ProgressBar.

```html

<!DOCTYPE html>
  <html xmlns="http://www.w3.org/1999/xhtml">
  <body>

       <head>
            <title>Essential JS 2 ProgressBar</title>
            <!-- Essential JS 2 ProgressBar's global script -->
            <script src="resources/scripts/ej2.min.js" type="text/javascript"></script>
       </head>

       </body>
  </html>

```

### Using CDN link for script

Using CDN link, you can directly refer the ProgressBar control's script into the `index.html`.

Refer the ProgressBar's CDN links as below

**Syntax:**

> Script: `http://cdn.syncfusion.com/ej2/{PACKAGE_NAME}/dist/global/{PACKAGE_NAME}.min.js`

**Example:**

> Script: [`http://cdn.syncfusion.com/ej2/ej2-progressbar/dist/global/ej2-progressbar.min.js`](http://cdn.syncfusion.com/ej2/ej2-progressbar/dist/global/ej2-progressbar.min.js)

The below html code example shows the minimal dependency of ProgressBar.

```html
<!DOCTYPE html>
  <html xmlns="http://www.w3.org/1999/xhtml">
       <head>
            <title>Essential JS 2 ProgressBar</title>
            <!-- Essential JS 2 ProgressBar global script -->
            <script src="http://cdn.syncfusion.com/ej2/ej2-progressbar/dist/global/ej2-progressbar.min.js" type="text/javascript"></script>
       </head>
       <body>
       </body>
  </html>

```

## Adding Progress Bar control

Now, you can start adding Progress Bar control in the application. For getting started, add a **div** element for Progress Bar control in **index.html**. Then refer the **index.js** file into the **index.html** file.

In this document context we are going to use **ej2.min.js** which includes all the Essential JS 2 components and its dependent scripts.

```html
<!DOCTYPE html>
  <html xmlns="http://www.w3.org/1999/xhtml">
       <head>
            <title>Essential JS 2 ProgressBar</title>
            <!-- Essential JS 2 all script -->
            <script src="http://cdn.syncfusion.com/ej2/dist/ej2.min.js" type="text/javascript"></script>
       </head>
       <body>
           <!-- Add the HTML <div> element for ProgressBar  -->
             <div id="element"></div>
             <script src="index.js" type="text/javascript"></script>
       </body>
  </html>

```

Place the following Progress Bar code in the **index.js**

```javascript

  var percentageProgress = new ej.progressbar.ProgressBar({
      value: 40
  percentageProgress.appendTo('#percentage');

```