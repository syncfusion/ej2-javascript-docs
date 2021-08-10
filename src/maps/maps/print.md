---
title: " Print And Export in EJ2 Maps control | Syncfusion "

component: "Maps"

description: "Learn here all about Print And Export feature of Syncfusion EJ2 Maps control and more."
---

# Print and Export in EJ2 Maps control

## Print

The rendered Maps can be printed directly from the browser by calling the [`print`](../api/maps/#print) method. To use the print functionality in Maps, set the [`allowPrint`](../api/maps/#allowprint) property to **true**.

{% tab template="maps/print", sourceFiles="index.ts,index.html", es5Template="print" %}

{% endtab %}

## Export

### Image Export

To use the image export functionality, set the [`allowImageExport`](../api/maps/#allowimageexport) property to **true**. The rendered Maps can be exported as an image using the [`export`](../api/maps/#export) method. The method requires two parameters: image type and file name. The Maps can be exported as an image in the following formats.

* JPEG
* PNG
* SVG

{% tab template="maps/export", sourceFiles="index.ts,index.html", es5Template="export" %}

{% endtab %}

### Exporting Maps as base 64 string of the file

The image can be exported as base64 string for the JPEG and PNG formats. The rendered Maps can be exported to image as a base64 string using the [`export`](../api/maps/#export) method. There are four parameters required: image type, file name, orientation of the exported PDF document which must be set as **null** for image export and finally **allowDownload** which should be set as **false** to return base64 string.

{% tab template="maps/export", sourceFiles="index.ts,index.html", es5Template="base64" %}

{% endtab %}

### PDF Export

To use the PDF export functionality, set the [`allowPdfExport`](../api/maps/#allowpdfexport) property to **true**. The rendered Maps can be exported as PDF using the [`export`](../api/maps/#export) method. The [`export`](../api/maps/#export) method requires three parameters: file type, file name and orientation of the PDF document. The orientation setting is optional and "0" indicates portrait and "1" indicates landscape.

{% tab template="maps/export", sourceFiles="index.ts,index.html", es5Template="exportPdf" %}

{% endtab %}

> Note: The exporting of the Maps as base64 string is not supported for the PDF export.

<!-- markdownlint-disable MD010 -->

### Export the tile Maps

The rendered Maps with providers such as OSM, Bing and Google static Maps can be exported using the [`export`](../api/maps/#export) method. It supports the following export formats.

* JPEG
* PNG
* PDF

{% tab template="maps/OSMPrintExport", sourceFiles="index.ts,index.html", es5Template="OSMPrintExport" %}

{% endtab %}