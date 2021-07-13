---
title: " Internationalization in EJ2 Linear Gauge component | Syncfusion "

component: "Linear Gauge"

description: "Learn here all about the Internationalization feature of Syncfusion EJ2 Linear Gauge component and more."
---

# Internationalization in EJ2 Linear Gauge

Globalization is the process of designing and developing a component that works in different cultures. Internationalization is used to globalize the number content in Linear Gauge component using [`format`](../api/linear-gauge/label/#format) property in Linear Gauge component. It has static text on some features such as

* Axis label
* Tooltip

The static text on above features can be changed to any culture such as Arabic, Deutsch and French. To know more about the globalization in JavaScript components, refer [here](https://ej2.syncfusion.com/documentation/common/internationalization/)

## Numeric Format

The text in axis labels and tooltip can be displayed in the numeric format such as currency, percentage and so on. To know more about the numeric formats in axis labels, refer [here](axis/#displaying-numeric-format-in-labels). In the below example, the axis label is displayed in the currency format.

{% tab template= "linear-gauge/getting-started", sourceFiles="index.ts,index.html", es5Template="es5NumericFormat" %}

```typescript
import { LinearGauge } from '@syncfusion/ej2-lineargauge';
import { loadCldr, setCulture, Ajax, setCurrencyCode } from '@syncfusion/ej2-base';
setCulture("de");
setCurrencyCode('EUR');
let gauge: LinearGauge = new LinearGauge({
    locale: "de",
    format:'c',
    axes: [{
      labelStyle: {
        font: {
          color: 'red'
        }
      }
    }]
}, '#element');

```

{% endtab %}