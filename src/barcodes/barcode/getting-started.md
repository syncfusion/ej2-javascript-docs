---
title: "getting-started"
component: "BarcodeGenerator"
description: "BarcodeGenerator component is a pure JavaScript library which will convert a string to Barcode and show it to the user. This supports major 1D and 2D barcodes including coda bar, code 128, QR Code."
---

# Getting Started

This section explains the steps used to create a simple Barcode and demonstrates the basic usage of the barcode component using Essential JS 2
[quickstart](https://github.com/syncfusion/ej2-quickstart.git) seed repository.
This seed repository is pre-configured with the Essential JS 2 package.

## Dependencies

Following is the list of minimum dependencies required to use the barcode.

```javascript
|-- @syncfusion/ej2-barcode-generator
    |-- @syncfusion/ej2-base
    |-- @syncfusion/ej2-data
```

## Setup for local development

Clone the Essential JS 2 quickstart application project from
[GitHub](https://github.com/syncfusion/ej2-quickstart.git), and
install the necessary npm packages using the following command line scripts.

```sh
git clone https://github.com/syncfusion/ej2-quickstart.git quickstart
cd quickstart
npm install
```

## Configuring system JS

[Syncfusion BarcodeGenerator packages](#dependencies) have to be mapped in the `system.config.js` configuration file.

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
        "@syncfusion/ej2-buttons": "syncfusion:ej2-buttons/dist/ej2-buttons.umd.min.js",
        "@syncfusion/ej2-splitbuttons": "syncfusion:ej2-splitbuttons/dist/ej2-splitbuttons.umd.min.js",
        "@syncfusion/ej2-popups": "syncfusion:ej2-popups/dist/ej2-popups.umd.min.js",
        "@syncfusion/ej2-navigations": "syncfusion:ej2-navigations/dist/ej2-navigations.umd.min.js",
        "@syncfusion/ej2-inputs": "syncfusion:ej2-inputs/dist/ej2-inputs.umd.min.js",
        "@syncfusion/ej2-dropdowns": "syncfusion:ej2-dropdowns/dist/ej2-dropdowns.umd.min.js",
        "@syncfusion/ej2-calendars": "syncfusion:ej2-calendars/dist/ej2-calendars.umd.min.js",
        "@syncfusion/ej2-lists": "syncfusion:ej2-lists/dist/ej2-lists.umd.min.js",
        "@syncfusion/ej2-barcode-generator": "syncfusion:ej2-barcode-generator/dist/ej2-barcode-generator.umd.min.js",
        "@syncfusion/ej2-excel-export": "syncfusion:ej2-excel-export/dist/ej2-excel-export.umd.min.js",
        "@syncfusion/ej2-pdf-export": "syncfusion:ej2-pdf-export/dist/ej2-pdf-export.umd.min.js",
        "@syncfusion/ej2-file-utils": "syncfusion:ej2-file-utils/dist/ej2-file-utils.umd.min.js",
        "@syncfusion/ej2-compression": "syncfusion:ej2-compression/dist/ej2-compression.umd.min.js"
    },
    packages: {
        'app': { main: 'app', defaultExtension: 'js' }
    }
});

System.import('app');
```

## Adding CSS reference

Combined CSS files are available in the Essential JS 2 package root folder.
This can be referenced in your `[src/styles/styles.css]` using the following code.

```css
@import '../../node_modules/@syncfusion/ej2/material.css';
```

> To know about individual component CSS, please refer to
[Individual Component theme files](../../base/theme.html#individual-component-theme-files) section.

## Adding Barcode Generator control

You can start adding Essential JS 2 barcode-generator component to the application. To get started, add the barcode component in `app.ts` and `index.html` files using the following code.

Place the following barcode-generator  code in the `app.ts`.

{% tab template= "barcode/getting-started", es5Template="es5default" %}

```typescript

import { BarcodeGenerator, ValidateEvent } from '@syncfusion/ej2-barcode-generator';

 let barcode = new BarcodeGenerator({
        width: '200px',
        height: '150px',
        mode: 'SVG',
        type: 'Codabar',
        value: '123456789',

    });
    barcode.appendTo('#element');

```

{% endtab %}

Now, add an HTML div element to act as the barcode element in `index.html` using the following code.

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

    <!--style reference from app-->
    <link href="/styles/styles.css" rel="stylesheet" />

    <!--system js reference and configuration-->
    <script src="node_modules/systemjs/dist/system.src.js" type="text/javascript"></script>
    <script src="system.config.js" type="text/javascript"></script>
</head>

<body>
    <!--Element which will render as Barcode-->
    <div id="barcode"></div>
</body>

</html>
```

## Adding QR Generator control

You can add the QR code in our barcode generator component.

{% tab template= "barcode/getting-started", es5Template="es5qrcode" %}

```typescript

import { QRCodeGenerator, ValidateEvent } from '@syncfusion/ej2-barcode-generator';

 let barcode = new QRCodeGenerator({
        width: '200px',
        height: '150px',
        displayText: { visibility: false },
        mode: 'SVG',
        value: 'Syncfusion',

    });
    barcode.appendTo('#element');

```

{% endtab %}

## Adding Datamatrix Generator control

You can add the datamatrix code in our barcode generator component.

{% tab template= "barcode/getting-started", es5Template="es5datamatrix" %}

```typescript

import { DataMatrixGenerator, ValidateEvent } from '@syncfusion/ej2-barcode-generator';

 let barcode = new DataMatrixGenerator({
        width: '200px',
        height: '150px',
        displayText: { visibility: false },
        mode: 'SVG',
        value: 'Syncfusion',

    });
    barcode.appendTo('#element');

```

{% endtab %}