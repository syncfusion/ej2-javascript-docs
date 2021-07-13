---
title: " Print and Export in EJ2 Linear Gauge component | Syncfusion "

component: "Linear Gauge"

description: "Learn here all about the Print and Export feature of Syncfusion EJ2 Linear Gauge component and more."
---

# Print and Export in EJ2 Linear Gauge

## Print

The rendered linear gauge can be printed directly from the browser by calling the [`print`](../api/linear-gauge/#print) method. To use the print functionality, set the [`allowPrint`](../api/linear-gauge/#allowprint) property as "**true**".

<!-- markdownlint-disable MD036 -->

{% tab template= "linear-gauge/lineargauge-print", sourceFiles="index.ts,index.html", es5Template="es5Print" %}

```typescript
import { LinearGauge, Print } from '@syncfusion/ej2-lineargauge';
LinearGauge.Inject(Print);

let gauge: LinearGauge = new LinearGauge({
  allowPrint: true
}, '#element');

document.getElementById('print').onclick = () => {
    gauge.print();
};
```

{% endtab %}

## Export

### Image Export

To use the image export functionality, set the [`allowImageExport`](../api/linear-gauge/#allowimageexport) property as "**true**". The rendered linear gauge can be exported as an image using the [`export`](../api/linear-gauge/#export) method. This method requires two parameters: export type and file name. The Linear Gauge can be exported as an image with the following formats.

* JPEG
* PNG
* SVG

{% tab template= "linear-gauge/lineargauge-export", sourceFiles="index.ts,index.html", es5Template="es5Export" %}

```typescript
import { LinearGauge, ImageExport } from '@syncfusion/ej2-lineargauge';
LinearGauge.Inject(ImageExport);

let gauge: LinearGauge = new LinearGauge({
    allowImageExport: true
}, '#element');

document.getElementById('export').onclick = () => {
    gauge.export("PNG","Gauge");
};
```

{% endtab %}

### PDF Export

To use the PDF export functionality, set the [`allowPdfExport`](../api/linear-gauge/#allowpdfexport) property as "**true**". The rendered Linear Gauge can be exported as PDF using the [`export`](../api/linear-gauge/#export) method. The [`export`](../api/linear-gauge/#export) method requires three parameters: file type, file name, and orientation of the PDF document. The orientation of the PDF document can be set as "**Portrait**" or "**Landscape**".

{% tab template= "linear-gauge/lineargauge-export", sourceFiles="index.ts,index.html", es5Template="es5ExportPdf" %}

```typescript
import { LinearGauge, PdfExport } from '@syncfusion/ej2-lineargauge';
LinearGauge.Inject(PdfExport);

let gauge: LinearGauge = new LinearGauge({
    allowPdfExport: true
}, '#element');

document.getElementById('export').onclick = () => {
        gauge.export("PDF", "Gauge", 0);
};
```

{% endtab %}

### Exporting Linear Gauge as base64 string of the file

The Linear Gauge can be exported as base64 string for the JPEG, PNG and PDF formats. The rendered Linear Gauge can be exported as base64 string of the exported image or PDF document used in the [`export`](../api/linear-gauge/#export) method. The arguments that are required for this method is export type, file name, orientation of the exported PDF document and "**allowDownload**" boolean value that is set as "**false**" to return base64 string. The value for the orientation of the exported PDF document is set as "**null**" for image export and "**Portrait**" or "**Landscape**" for the PDF document.

{% tab template= "linear-gauge/lineargauge-export", sourceFiles="index.ts,index.html", es5Template="es5Base64" %}

```typescript
import { LinearGauge, ImageExport } from '@syncfusion/ej2-lineargauge';
LinearGauge.Inject(ImageExport);
let gauge: LinearGauge = new LinearGauge({
    allowImageExport: true
}, '#element');
document.getElementById('export').onclick = () => {
        gauge.export('JPEG', 'Gauge', null, false).then((data) => {
            let base64 = data;
            document.writeln(base64);
        });
};
```

{% endtab %}

>Note: The exporting of the Linear Gauge as base64 string is not applicable for the SVG format.