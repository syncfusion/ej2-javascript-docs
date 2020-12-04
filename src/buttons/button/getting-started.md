---
title: "Button Getting Started"
component: "Button"
description: "This section helps to learn how to create the button in HML5 JavaScript application with its basic features in step-by-step procedure."
---

# Getting Started

This section explains how to create a simple Button and to configure the Button component.

## Dependencies

The list of dependencies required to use the Button component in your application is given below:

```js
|-- @syncfusion/ej2-buttons
    |-- @syncfusion/ej2-base
```

## Setup your development environment

To get started with the Button component, you can clone the
[Essential JS 2 quickstart](https://github.com/syncfusion/ej2-quickstart) project using the following commands:

```cmd
git clone https://github.com/syncfusion/ej2-quickstart.git quickstart
cd quickstart
npm install
```

> The project is preconfigured with common settings (`src/styles/styles.css`, `system.config.js`)
to start all the Essential JS 2 components.

* Refer to the [Button component dependencies](./getting-started#dependencies) in `system.config.js` configuration file.

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

## Add Button to the project

Add the HTML Button tag with id attribute as the `element` to your `index.html` file.

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

    <!--Style reference from app-->
    <link href="/styles/styles.css" rel="stylesheet" />

    <!--System js reference and configuration-->
    <script src="node_modules/systemjs/dist/system.src.js" type="text/javascript"></script>
    <script src="system.config.js" type="text/javascript"></script>
</head>

<body>
    <div>
        <!--Element which is going to render-->
        <button id="element">Button</button>
    </div>

</body>

</html>
```

Then, import the Button component in your `app.ts` file, and initialize it with the `#element`.

`[src/app/app.ts]`

```typescript
import { Button } from '@syncfusion/ej2-buttons';

// Initialize Button component.
let button: Button = new Button({ content: 'Button' });

// Render initialized Button.
button.appendTo('#element');
```

## Adding Style sheet to the Application

To render Button component, need to import Button and its dependent components styles as given below in `style.css`.

```css
@import "../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../node_modules/@syncfusion/ej2-buttons/styles/material.css";
```

## Run the application

Run the application in the browser using the following command:

```cmd
npm start
```

The following example shows a basic Button component.

{% tab template= "button/getting-started", sourceFiles="app.ts,index.html,styles.css",
es5Template="basic-btn-template", isDefaultActive=true %}

```typescript
import { Button } from '@syncfusion/ej2-buttons';
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);

// Initialize the Button component.
let button: Button = new Button({ content: 'Button' });

// Render initialized button.
button.appendTo('#element');
```

{% endtab %}

## Change Button type

To change the default Button to flat Button, set the [`cssClass`](../api/button#cssclass) property to `e-flat` and text content of the Button is set using [`content`](../api/button#content) property.

{% tab template= "button/getting-started", sourceFiles="app.ts,index.html,styles.css", es5Template="flat-btn-template" %}

```typescript
import { Button } from '@syncfusion/ej2-buttons';
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);

//To change the Button type.
let button: Button = new Button({ cssClass: 'e-flat', content: 'Button' });

button.appendTo('#element');
```

{% endtab %}

## See Also

* [Types of Button](./types-and-styles#button-types)