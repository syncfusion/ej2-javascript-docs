---
title: "ButtonGroup Getting Started"
component: "ButtonGroup"
description: "This section helps to learn how to create the buttongroup in HML5 JavaScript application with its basic features in step-by-step procedure."
---

# Getting Started

This section explains how to create a simple ButtonGroup, and configure its available functionalities by using the Essential JS 2 quickstart seed repository.

## Dependencies

The following list of dependencies are required to use the ButtonGroup component in your application.

```js
|-- @syncfusion/ej2-splitbuttons
```

## Setup your development environment

To get started with the ButtonGroup component, you can clone the
[Essential JS 2 quickstart](https://github.com/syncfusion/ej2-quickstart) project and install the npm packages by
using the following commands.

```cmd

git clone https://github.com/syncfusion/ej2-quickstart.git quickstart
cd quickstart
npm install

```

> The project is preconfigured with common settings (`src/styles/styles.css`, `system.config.js`)
to start all the Essential JS 2 components.

* Refer to the [Button-Group component dependencies](./getting-started#dependencies) in `system.config.js` configuration file.

`[src/system.config.js]`

```js
System.config({
    paths: {
        'npm:': './node_modules/',
        'syncfusion:': 'npm:@syncfusion/'
    },
    map: {
        app: 'app',

        //Syncfusion packages mapping
        "@syncfusion/ej2-base": "syncfusion:ej2-base/dist/ej2-base.umd.min.js",
        "@syncfusion/ej2-data": "syncfusion:ej2-data/dist/ej2-data.umd.min.js",
        "@syncfusion/ej2-inputs": "syncfusion:ej2-inputs/dist/ej2-inputs.umd.min.js",
        "@syncfusion/ej2-buttons": "syncfusion:ej2-buttons/dist/ej2-buttons.umd.min.js",
        "@syncfusion/ej2-splitbuttons": "syncfusion:ej2-splitbuttons/dist/ej2-splitbuttons.umd.min.js",
        "@syncfusion/ej2-lists": "syncfusion:ej2-lists/dist/ej2-lists.umd.min.js",
        "@syncfusion/ej2-popups": "syncfusion:ej2-popups/dist/ej2-popups.umd.min.js",
        "@syncfusion/ej2-dropdowns": "syncfusion:ej2-dropdowns/dist/ej2-dropdowns.umd.min.js",
    },
    packages: {
        'app': { main: 'app', defaultExtension: 'js' }
    }
});

System.import('app.ts').catch(console.error.bind(console)).then(function () {
    document.getElementById('loader').style.display = "none";
    document.getElementById('container').style.visibility = "visible";
});
```

* The ButtonGroup CSS files are available in the `ej2-splitbuttons` package folder. This can be referenced in your application by using the following code.

`[src/styles/styles.css]`

```css
@import '../../node_modules/@syncfusion/ej2-base/styles/material.css';
@import '../../node_modules/@syncfusion/ej2-buttons/styles/material.css';
@import '../../node_modules/@syncfusion/ej2-splitbuttons/styles/material.css';
```

## Add ButtonGroup to the project

Add the HTML div tag with class name as `e-btn-group` and the button elements that should group inside the div element with class name as
`e-btn` to your `index.html` file.

`[src/index.html]`

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <title>Essential JS 2</title>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=no" />
    <meta name="description" content="Essential JS 2" />
    <meta name="author" content="Syncfusion" />
    <link rel="shortcut icon" href="resources/favicon.ico" />
    <link href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/css/bootstrap.min.css" rel="stylesheet" />
    <link href="https://cdn.syncfusion.com/ej2/ej2-base/styles/material.css" rel="stylesheet" />
    <link href="https://cdn.syncfusion.com/ej2/ej2-buttons/styles/material.css" rel="stylesheet" />
    <link href="https://cdn.syncfusion.com/ej2/ej2-splitbuttons/styles/material.css" rel="stylesheet" />

    <!--style reference from app-->
    <link href="/styles/styles.css" rel="stylesheet" />

    <!--system js reference and configuration-->
    <script src="node_modules/systemjs/dist/system.src.js" type="text/javascript"></script>
    <script src="system.config.js" type="text/javascript"></script>
</head>

<body>
    <div>
        <!--element which is going to render-->
        <div class='e-btn-group'>
            <button class='e-btn'>HTML</button>
            <button class='e-btn'>CSS</button>
            <button class='e-btn'>Javascript</button>
        </div>
    </div>

</body>

</html>
```

## Run the application

Run the application in the browser by using the following command.

```cmd
npm start
```

The following example shows a basic ButtonGroup component.

{% tab template= "button-group/getting-started", sourceFiles="index.html,styles.css", isDefaultActive=true %}

{% endtab %}

## Orientation

ButtonGroup can be arranged in a vertical and horizontal orientation. By default, it is horizontally aligned.

### Vertical Orientation

ButtonGroup can be aligned vertically by using the built-in CSS class `e-vertical` to the target element.

The following example illustrates how to achieve vertical orientation in ButtonGroup.

{% tab template= "button-group/vertical", sourceFiles="index.html,styles.css" %}

{% endtab %}

> ButtonGroup does not support SplitButton component nesting in a vertical orientation.

## See Also

* [Initialize ButtonGroup using util function](./how-to/initialize-buttongroup-using-util-function)