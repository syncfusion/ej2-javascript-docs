
# Ranges

You can categories certain interval on gauge axis using [`ranges`](../api/circular-gauge/range#properties) property.

## Start and End

Start and end value of a range in an axis can be customized by using [`start`](../api/circular-gauge/range#start-number) and [`end`](../api/circular-gauge/range#end-number) properties.

{% tab template= "circular-gauge/gauge-ranges", sourceFiles="index.ts,index.html", es5Template="es5Range" %}

```typescript

import { CircularGauge } from '@syncfusion/ej2-circulargauge';
let gauge: CircularGauge = new CircularGauge({
    axes: [{
        ranges: [{
            start: 40,
            end: 80
        }]
    }]
});
gauge.appendTo('#element');

```

{% endtab %}

## Customization

Color and thickness of the range can be customized by using [`color`](../api/circular-gauge/range#color-string),[`startWidth`](../api/circular-gauge/range#startwidth-number) and [`endWidth`](../api/circular-gauge/range#endwidth-number) property.

{% tab template= "circular-gauge/gauge-ranges", sourceFiles="index.ts,index.html", es5Template="es5RangeCustomization" %}

```typescript

import { CircularGauge } from '@syncfusion/ej2-circulargauge';
let gauge: CircularGauge = new CircularGauge({
    axes: [{
        ranges: [{
            start: 40,
            end: 80, endWidth: 15,
            startWidth: 15,
            color: '#ff5985'
        }]
    }]
});
gauge.appendTo('#element');

```

{% endtab %}

<!-- markdownlint-disable MD036 -->

## Radius

You can place the range inside or outside of the axis by using [`radius`](../api/circular-gauge/range#radius-string)
property. The radius of the range can takes value either in percentage or in pixels. By default, ranges
take 100% of the axis radius.

**In Pixel**

You can set the radius of the range in pixel as demonstrated below,

{% tab template= "circular-gauge/gauge-ranges", sourceFiles="index.ts,index.html", es5Template="es5RadiusInPixel" %}

```typescript

import { CircularGauge } from '@syncfusion/ej2-circulargauge';
let gauge: CircularGauge = new CircularGauge({
    axes: [{
        minimum: 0,
        maximum: 100,
        ranges: [{
            start: 40,
            end: 80,
            radius: '100'
        }]
    }]
});
gauge.appendTo('#element');

```

{% endtab %}

<!-- markdownlint-disable MD036 -->

**In Percentage**

By setting value in percentage, range gets its dimension with respect to its axis radius.
For example, when the radius is ‘50%’, range renders to half of the axis radius.

{% tab template= "circular-gauge/gauge-ranges", sourceFiles="index.ts,index.html", es5Template="es5RadiusInPercentage" %}

```typescript

import { CircularGauge } from '@syncfusion/ej2-circulargauge';
let gauge: CircularGauge = new CircularGauge({
    axes: [{
        minimum: 0,
        maximum: 100,
        ranges: [{
            start: 40,
            end: 80,
            radius: '50%'
        }]
    }]
});
gauge.appendTo('#element');

```

{% endtab %}

## Dragging Range

The ranges can be dragged over the axis line by clicking and dragging the same. To enable or disable the range drag, use the [`enableRangeDrag`](../api/circular-gauge/circularGaugeModel/#enablerangedrag) property.

{% tab template= "circular-gauge/gauge-pointers", sourceFiles="index.ts,index.html", es5Template="es5DragRange" %}

```typescript

import { CircularGauge } from '@syncfusion/ej2-circulargauge';
let gauge: CircularGauge = new CircularGauge({
    enableRangeDrag:true,
    height:'250px',
    width:'250px',
    axes: [{
        ranges: [{
            start: 0,
            end: 100,
            startWidth: 8, endWidth: 8,
            radius: '108%',
            color: '#30B32D'
        }],
        pointers: [{
            value: 50
        }]
    }]
});
gauge.appendTo('#element');

```

{% endtab %}

## Multiple Ranges

You can add multiple ranges to an axis with the above customization as demonstrated below.

>Note: You can set the range color to axis ticks and labels by enabling `useRangeColor` property in [`majorTicks`](../api/circular-gauge/tick),
[`minorTicks`](../api/circular-gauge/tick) and [`labelStyle`](../api/circular-gauge/label) object.

{% tab template= "circular-gauge/gauge-ranges", sourceFiles="index.ts,index.html", es5Template="es5MultipleRanges" %}

```typescript

import { CircularGauge } from '@syncfusion/ej2-circulargauge';
let gauge: CircularGauge = new CircularGauge({
    axes: [{
        minimum: 0,
        maximum: 100,
        majorTicks: {
            useRangeColor: true
        },
        minorTicks: {
            useRangeColor: true
        },
        labelStyle: {
            useRangeColor: true
        },
        ranges: [{
            start: 0,
            end: 25,
            radius: '108%'
        },{
            start: 25,
            end: 50,
            radius: '70%'
        },{
            start: 50,
            end: 75,
            radius: '70%'
        },{
            start: 75,
            end: 100,
            radius: '108%'
        }]
    }]
});
gauge.appendTo('#element');

```

{% endtab %}

## Rounded corner radius

You can customize the corner radius using the `roundedCornerRadius` property in `ranges`.

{% tab template= "circular-gauge/gauge-ranges", sourceFiles="index.ts,index.html", es5Template="es5RoundedCornerRadius" %}

```typescript

import { CircularGauge } from '@syncfusion/ej2-circulargauge';
let gauge: CircularGauge = new CircularGauge({
    axes: [{
        minimum: 0,
        maximum: 100,
        ranges: [{
            start: 40,
            end: 80,
            radius: '50%',
            roundedCornerRadius: 5,
        }]
    }]
});
gauge.appendTo('#element');

```

{% endtab %}

## Gradient Color

Gradient support allows to add multiple colors in the ranges and pointers of the circular gauge. The following gradient types are supported in the circular gauge.

* Linear Gradient
* Radial Gradient

### Linear Gradient

Using linear gradient, colors will be applied in a linear progression. The start value of the linear gradient will be set using the [`startValue`](../api/circular-gauge/linearGradient/#startvalue) property. The end value of the linear gradient will be set using the [`endValue`](../api/circular-gauge/linearGradient/#endvalue) property. The color stop values such as color, opacity and offset are set using [`colorStop`](../api/circular-gauge/linearGradient/#colorstop) property.

To apply linear gradient to the range, follow the below code sample.

{% tab template= "circular-gauge/gauge-ranges", sourceFiles="index.ts,index.html", es5Template="es5LinearGradient" %}

```typescript

import { CircularGauge, Gradient } from '@syncfusion/ej2-circulargauge';
CircularGauge.Inject(Gradient);
let rangeLinearGradient: Object = {
    startValue: '0%',
    endValue: '100%',
    colorStop: [
        { color: '#9E40DC', offset: '0%', opacity: 0.9 },
        { color: '#E63B86', offset: '70%', opacity: 0.9 }
    ]
};
let gauge: CircularGauge = new CircularGauge(
  {
    axes: [
    {
        lineStyle: { width: 0 },
        labelStyle: {
            position: 'Inside',
            useRangeColor: true,
            font: {
                size: '0px',
                color: 'white',
                fontFamily: 'Roboto',
                fontStyle: 'Regular'
            }
        },
        majorTicks: { height: 0 },
        minorTicks: { height: 0 },
        startAngle: 200,
        endAngle: 160,
        minimum: 0,
        maximum: 100,
        radius: '80%',
        ranges: [
        {
            start: 0,
            end: 100,
            radius: '90%',
            startWidth: 30,
            endWidth: 30,
            color: '#E0E0E0',
            roundedCornerRadius: 20,
            linearGradient: rangeLinearGradient
        }
        ],
        pointers: [
          {
            cap: {
                radius: 0
            },
            pointerWidth: 0
          }
        ]
      }
    ]
  }
);
gauge.appendTo('#element');

```

{% endtab %}

### Radial Gradient

Using radial gradient, colors will be applied in circular progression. The inner circle position of the radial gradient will be set using the [`innerPosition`](../api/circular-gauge/radialGradient/#innerposition) property. The outer circle position of the radial gradient can be set using the [`outerPosition`](../api/circular-gauge/radialGradient/#outerposition) property. The color stop values such as color, opacity and offset are set using [`colorStop`](../api/circular-gauge/radialGradient/#colorstop) property.

To apply radial gradient to the range, follow the below code sample.

{% tab template= "circular-gauge/gauge-ranges", sourceFiles="index.ts,index.html", es5Template="es5RadialGradient"%}

```typescript

import { CircularGauge, Gradient } from '@syncfusion/ej2-circulargauge';
CircularGauge.Inject(Gradient);
let rangeRadialGradient: Object = {
    radius: '50%',
    innerPosition: { x: '50%', y: '50%' },
    outerPosition: { x: '50%', y: '50%' },
    colorStop: [
        { color: '#9E40DC', offset: '90%', opacity: 0.9 },
        { color: '#E63B86', offset: '160%', opacity: 0.9 }
    ]
};
let gauge: CircularGauge = new CircularGauge(
  {
    axes: [
    {
        lineStyle: { width: 0 },
        labelStyle: {
            position: 'Inside',
            useRangeColor: true,
            font: {
                size: '0px',
                color: 'white',
                fontFamily: 'Roboto',
                fontStyle: 'Regular'
            }
        },
        majorTicks: { height: 0 },
        minorTicks: { height: 0 },
        startAngle: 200,
        endAngle: 160,
        minimum: 0,
        maximum: 100,
        radius: '80%',
        ranges: [
        {
            start: 0,
            end: 100,
            radius: '90%',
            startWidth: 30,
            endWidth: 30,
            color: '#E0E0E0',
            roundedCornerRadius: 20,
            radialGradient: rangeRadialGradient
        }
        ],
        pointers: [
          {
            cap: {
                radius: 0
            },
            pointerWidth: 0
          }
        ]
      }
    ]
  }
);
gauge.appendTo('#element');

```

{% endtab %}

## See also

* [Tooltip for Ranges](https://ej2.syncfusion.com/documentation/circular-gauge/gauge-user-interaction/tooltip-for-ranges-and-annotations/)