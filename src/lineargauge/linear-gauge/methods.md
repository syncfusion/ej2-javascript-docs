---
title: " Methods in EJ2 Linear Gauge component | Syncfusion "

component: "Linear Gauge"

description: "Learn here all about the Methods of Syncfusion EJ2 Linear Gauge component and more."
---

# Methods in EJ2 Linear Gauge

The following methods are available in the Linear Gauge component.

## setPointerValue

To change the pointer value dynamically, use the [`setPointerValue`](../api/linear-gauge#setpointervalue) method in the Linear Gauge component. The following are the arguments for this method.

|   Argument name      |   Description                            |
|----------------------| -----------------------------------------|
|     axisIndex        |    Specifies the index of the axis in which the pointer value is to be updated.|
|     pointerIndex     |    Specifies the index of the pointer to be updated.           |
|     pointerValue     |    Specifies the value of the pointer to be updated.           |

{% tab template= "linear-gauge/methods", sourceFiles="index.ts,index.html", es5Template="es5SetPointer" %}

```typescript
import { LinearGauge } from '@syncfusion/ej2-lineargauge';
let gauge: LinearGauge = new LinearGauge({
    axes: [{
        pointers: [{
            value: 80
        }]
    }]
}, '#element');

document.getElementById('btn').onclick = () => {
    gauge.setPointerValue(0, 0, 30);
};
```

{% endtab %}

## setAnnotationValue

To change the annotation content dynamically, use the [`setAnnotationValue`](../api/linear-gauge#setannotationvalue) method in the Linear Gauge component. The following are the arguments for this method.

|   Argument name      |   Description                            |
|----------------------| -----------------------------------------|
|     annotationIndex  |    Specifies the index number of the annotation to be updated. |
|     content          |    Specifies the text for the annotation to be updated.        |
|     axisValue        |    Specifies the value of the axis where the annotation is to be placed.|

{% tab template= "linear-gauge/methods", sourceFiles="index.ts,index.html", es5Template="es5SetAnnotation" %}

```typescript
import { LinearGauge, Annotations } from '@syncfusion/ej2-lineargauge';
LinearGauge.Inject(Annotations);
let gauge: LinearGauge = new LinearGauge({
    annotations: [{
       content: '10',
       zIndex: '1',
       axisValue: 0
    }]
}, '#element');

document.getElementById('btn').onclick = () => {
    gauge.setAnnotationValue(0, '50', 50);
};
```

{% endtab %}

## refresh

The [`refresh`](../api/linear-gauge#refresh) method can be used to change the state of the component and render it again. In the following example, the gauge is rendered again using the [`refresh`](../api/linear-gauge#refresh) method.

{% tab template= "linear-gauge/methods", sourceFiles="index.ts,index.html", es5Template="es5Refresh" %}

```typescript
import { LinearGauge } from '@syncfusion/ej2-lineargauge';
let gauge: LinearGauge = new LinearGauge({
    axes:[{
        pointers:[{
            value: 10
        }]
    }]
}, '#element');

document.getElementById('btn').onclick = () => {
    gauge.refresh();
};
```