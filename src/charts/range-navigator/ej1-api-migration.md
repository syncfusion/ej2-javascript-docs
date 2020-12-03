---
title: " RangeNavigator API Migration | TypeScript "

component: "RangeNavigator"

description: "This article describes the API migration process of Chart component from Essential JS 1 to Essential JS 2."
---

# Migration from Essential JS 1

This article describes the API migration process of Chart component from Essential JS 1 to Essential JS 2.

## RangeNavigator

<!-- markdownlint-disable MD033 -->
<table>
<tr>
<td><b>Behaviour</b></td>
<td><b>API in Essential JS 1</b></td>
<td><b>API in Essential JS 2</b></td>
</tr>

<tr>
<td><b>Allow snapping</b></td>
<td>
<b>Property</b>:<i>allowSnapping</i>
</br>
</br>
<code>
$("#range").ejRangeNavigator({
    allowSnapping: true;
});
</code>
</td>
<td>
<b>Property</b>:<i>allowSnapping</i>
</br>
</br>
<code>
let range: RangeNavigator = new RangeNavigator({
    allowSnapping: true
});
range.appendTo('#element');
</code></td>
</tr>

<tr>
<td><b>Animation duration</b></td>
<td>
Not Applicable
</td>
<td>
<b>Property</b>:<i>animationDuration</i>
</br>
</br>
<code>
let range: RangeNavigator = new RangeNavigator({
    animationDuration: 2000
});
range.appendTo('#element');
</code></td>
</tr>

<tr>
<td><b>Allow snapping</b></td>
<td>
<b>Property</b>:<i>allowSnapping</i>
</br>
</br>
<code>
$("#range").ejRangeNavigator({
    allowSnapping: true;
});
</code>
</td>
<td>
<b>Property</b>:<i>allowSnapping</i>
</br>
</br>
<code>
let range: RangeNavigator = new RangeNavigator({
    allowSnapping: true
});
range.appendTo('#element');
</code></td>
</tr>

<tr>
<td><b>Border for range navigator</b></td>
<td>
<b>Property</b>:<i>allowSnapping</i>
</br>
</br>
<code>
$("#range").ejRangeNavigator({
    border: { color: 'red', width: 2, opacity: 0.5 }
});
</code>
</td>
<td>
<b>Property</b>:<i>navigatorBorder</i>
</br>
</br>
<code>
let range: RangeNavigator = new RangeNavigator({
    navigatorBorder:{ color: 'pink', width: 2}
});
range.appendTo('#element');
</code></td>
</tr>

<tr>
<td><b>dataSource for range navigator</b></td>
<td>
<b>Property</b>:<i>dataSource</i>
</br>
</br>
<code>
$("#range").ejRangeNavigator({
    dataSource: [{}]
});
</code>
</td>
<td>
<b>Property</b>:<i>dataSource</i>
</br>
</br>
<code>
let range: RangeNavigator = new RangeNavigator({
    dataSource: []
});
range.appendTo('#element');
</code></td>
</tr>

<tr>
<td><b>enabling deffered update for range navigator</b></td>
<td>
<b>Property</b>:<i>enableDeferedUpdate</i>
</br>
</br>
<code>
$("#range").ejRangeNavigator({
    enableDeferedUpdate: true
});
</code>
</td>
<td>
<b>Property</b>:<i>enableDeferredUpdate</i>
</br>
</br>
<code>
let range: RangeNavigator = new RangeNavigator({
    enableDeferredUpdate : false
});
range.appendTo('#element');
</code></td>
</tr>

<tr>
<td><b>multilevel level labels</b></td>
<td>
<b>Property</b>:<i>labelSettings.higherLevelLabels</i>
</br>
</br>
<code>
$("#range").ejRangeNavigator({
    labelSettings.higherLevelLabels: { }
});
</code>
</td>
<td>
<b>Property</b>:<i>enableGrouping</i>
</br>
</br>
<code>
let range: RangeNavigator = new RangeNavigator({
    enableGrouping : false
});
range.appendTo('#element');
</code></td>
</tr>

<tr>
<td><b>enabling scroll bar</b></td>
<td>
<b>Property</b>:<i>enableScrollBar</i>
</br>
</br>
<code>
$("#range").ejRangeNavigator({
    enablescrollBar: true
});
</code>
</td>
<td>
Not Applicable
</td>
</tr>

<tr>
<td><b>enabling auto resizing</b></td>
<td>
<b>Property</b>:<i>enableAutoResize</i>
</br>
</br>
<code>
$("#range").ejRangeNavigator({
    enablescrollBar: true
});
</code>
</td>
<td>
Not Applicable
</td>
</tr>

<tr>
<td><b>responsive of range navigator</b></td>
<td>
<b>Property</b>:<i>isResponsive</i>
</br>
</br>
<code>
$("#range").ejRangeNavigator({
    isResponsive: true
});
</code>
</td>
<td>
Not Applicable
</td>
</tr>

<tr>
<td><b>enabling RTL for range navigator</b></td>
<td>
<b>Property</b>:<i>enableRtl</i>
</br>
</br>
<code>
$("#range").ejRangeNavigator({
    enableRtl: true
});
</code>
</td>
<td>
<b>Property</b>:<i>enableRtl</i>
</br>
</br>
<code>
let range: RangeNavigator = new RangeNavigator({
    enableRtl : false
});
range.appendTo('#element');
</code></td>
</tr>

<tr>
<td><b>interval for range navigator</b></td>
<td>
<b>Property</b>:<i>valueAxisSettings.range.interval</i>
</br>
</br>
<code>
$("#range").ejRangeNavigator({
    valueAxisSettings.range.interval = 1
});
</code>
</td>
<td>
<b>Property</b>:<i>interval</i>
</br>
</br>
<code>
let range: RangeNavigator = new RangeNavigator({
    interval : 1
});
range.appendTo('#element');
</code></td>
</tr>

<tr>
<td><b>intervaltype for range navigator</b></td>
<td>
<b>Property</b>:<i>valueAxisSettings.range.interval</i>
</br>
</br>
<code>
$("#range").ejRangeNavigator({
    valueAxisSettings.intervalType = 'Years'
});
</code>
</td>
<td>
<b>Property</b>:<i>intervalType</i>
</br>
</br>
<code>
let range: RangeNavigator = new RangeNavigator({
    intervalType : 'Months'
});
range.appendTo('#element');
</code></td>
</tr>

<tr>
<td><b>labelformat for range navigator</b></td>
<td>
Not applicable
</td>
<td>
<b>Property</b>:<i>labelFormat</i>
</br>
</br>
<code>
let range: RangeNavigator = new RangeNavigator({
    labelFormat : 'yMd'
});
range.appendTo('#element');
</code></td>
</tr>

<tr>
<td><b>label intersect action for range navigator</b></td>
<td>
Not applicable
</td>
<td>
<b>Property</b>:<i>labelIntersectAction</i>
</br>
</br>
<code>
let range: RangeNavigator = new RangeNavigator({
    labelIntersectAction : 'Hide'
});
range.appendTo('#element');
</code></td>
</tr>

<tr>
<td><b>labelStyle range navigator</b></td>
<td>
<b>Property</b>:<i>valueAxisSettings.font</i>
</br>
</br>
<code>
$("#range").ejRangeNavigator({
    valueAxisSettings.font: { }
});
</code>
</td>
<td>
<b>Property</b>:<i>labelStyle</i>
</br>
</br>
<code>
let range: RangeNavigator = new RangeNavigator({
    labelStyle : 'Hide'
});
range.appendTo('#element');
</code></td>
</tr>

<tr>
<td><b>locale of range navigator</b></td>
<td>
<b>Property</b>:<i>locale</i>
</br>
</br>
<code>
$("#range").ejRangeNavigator({
    locale: 'en-US'
});
</code>
</td>
<td>
<b>Property</b>:<i>labelStyle</i>
</br>
</br>
<code>
let range: RangeNavigator = new RangeNavigator({
    locale: 'en-US'
});
range.appendTo('#element');
</code></td>
</tr>

<tr>
<td><b>major grid lines of range navigator</b></td>
<td>
<b>Property</b>:<i>valueAxisSettings.majorGridLines</i>
</br>
</br>
<code>
$("#range").ejRangeNavigator({
   valueAxisSettings: {
       majorGridLines: {
           width: 2,
           color: 'red'
       }
   }
});
</code>
</td>
<td>
<b>Property</b>:<i>majorGridLines</i>
</br>
</br>
<code>
let range: RangeNavigator = new RangeNavigator({
    majorGridLines: {
        width: 2, color: 'red'
    }
});
range.appendTo('#element');
</code></td>
</tr>

<tr>
<td><b>margin of range navigator</b></td>
<td>
Not Applicable
</td>
<td>
<b>Property</b>:<i>margin</i>
</br>
</br>
<code>
let range: RangeNavigator = new RangeNavigator({
    margin: { }
});
range.appendTo('#element');
</code></td>
</tr>

<tr>
<td><b>maximum value of range navigator</b></td>
<td>
<b>Property</b>:<i>valueAxisSettings.range.max</i>
</br>
</br>
<code>
$("#range").ejRangeNavigator({
   valueAxisSettings: {
       range: {
           max: 34
       }
   }
});
</code>
</td>
<td>
<b>Property</b>:<i>maximum</i>
</br>
</br>
<code>
let range: RangeNavigator = new RangeNavigator({
   maximum: 34
});
range.appendTo('#element');
</code></td>
</tr>

<tr>
<td><b>minimum value of range navigator</b></td>
<td>
<b>Property</b>:<i>valueAxisSettings.range.min</i>
</br>
</br>
<code>
$("#range").ejRangeNavigator({
   valueAxisSettings: {
       range: {
           min: 34
       }
   }
});
</code>
</td>
<td>
<b>Property</b>:<i>minimum</i>
</br>
</br>
<code>
let range: RangeNavigator = new RangeNavigator({
   minimum: 4
});
range.appendTo('#element');
</code></td>
</tr>

<tr>
<td><b>query for data source of range navigator</b></td>
<td>
Not Applicable
</td>
<td>
<b>Property</b>:<i>query</i>
</br>
</br>
<code>
let range: RangeNavigator = new RangeNavigator({
   query: ''
});
range.appendTo('#element');
</code></td>
</tr>

<tr>
<td><b>Secondary label alignment of range navigator</b></td>
<td>
Not Applicable
</td>
<td>
<b>Property</b>:<i>secondaryLabelAlignment</i>
</br>
</br>
<code>
let range: RangeNavigator = new RangeNavigator({
   secondaryLabelAlignment: 'Far'
});
range.appendTo('#element');
</code></td>
</tr>

<tr>
<td><b>Skeleton of range navigator axis</b></td>
<td>
Not Applicable
</td>
<td>
<b>Property</b>:<i>skeleton</i>
</br>
</br>
<code>
let range: RangeNavigator = new RangeNavigator({
   skeleton: ''
});
range.appendTo('#element');
</code></td>
</tr>

<tr>
<td><b>skeletontype of range navigator axis</b></td>
<td>
Not Applicable
</td>
<td>
<b>Property</b>:<i>skeletonType</i>
</br>
</br>
<code>
let range: RangeNavigator = new RangeNavigator({
   skeletonType: ''
});
range.appendTo('#element');
</code></td>
</tr>

<tr>
<td><b>Theme of range navigator</b></td>
<td>
<b>Property</b>:<i>theme</i>
</br>
</br>
<code>
$("#range").ejRangeNavigator({
   theme: ''
   });
</code>
</td>
<td>
<b>Property</b>:<i>theme</i>
</br>
</br>
<code>
let range: RangeNavigator = new RangeNavigator({
  theme: ''
});
range.appendTo('#element');
</code></td>
</tr>

<tr>
<td><b>Default selector value range navigator</b></td>
<td>
<b>Property</b>:<i>selectedRangeSettings</i>
</br>
</br>
<code>
$("#range").ejRangeNavigator({
  selectedRangeSettings: { start: 2, end: 20}
   });
</code>
</td>
<td>
<b>Property</b>:<i>value</i>
</br>
</br>
<code>
let range: RangeNavigator = new RangeNavigator({
    value: [ 2, 10]
});
range.appendTo('#element');
</code></td>
</tr>

<tr>
<td><b>Value type of range navigator</b></td>
<td>
<b>Property</b>:<i>valueType</i>
</br>
</br>
<code>
$("#range").ejRangeNavigator({
  valueType: 'DateTime'
   });
</code>
</td>
<td>
<b>Property</b>:<i>valueType</i>
</br>
</br>
<code>
let range: RangeNavigator = new RangeNavigator({
   valueType: 'Logarithmic'
});
range.appendTo('#element');
</code></td>
</tr>

<tr>
<td><b>Width of range navigator</b></td>
<td>
<b>Property</b>:<i>size.width</i>
</br>
</br>
<code>
$("#range").ejRangeNavigator({
  size: { width: '200'}
   });
</code>
</td>
<td>
<b>Property</b>:<i>width</i>
</br>
</br>
<code>
let range: RangeNavigator = new RangeNavigator({
   width: '400'
});
range.appendTo('#element');
</code></td>
</tr>

<tr>
<td><b>Height of range navigator</b></td>
<td>
<b>Property</b>:<i>size.height</i>
</br>
</br>
<code>
$("#range").ejRangeNavigator({
  size: { height: '200'}
   });
</code>
</td>
<td>
<b>Property</b>:<i>height</i>
</br>
</br>
<code>
let range: RangeNavigator = new RangeNavigator({
   height: '400'
});
range.appendTo('#element');
</code></td>
</tr>

<tr>
<td><b>Series settings for range navigator</b></td>
<td>
<b>Property</b>:<i>seriesSettings</i>
</br>
</br>
<code>
$("#range").ejRangeNavigator({
    seriesSettings: { }
});
</code>
</td>
<td>
Not Applicable
</td>
</tr>

<tr>
<td><b>Range settings for range navigator</b></td>
<td>
<b>Property</b>:<i>rangeSettings</i>
</br>
</br>
<code>
$("#range").ejRangeNavigator({
    rangeSettings: { start: 3, end: 6 }
});
</code>
</td>
<td>
Not Applicable
</td>
</tr>

<tr>
<td><b>Scroll range settings for range navigator</b></td>
<td>
<b>Property</b>:<i>scrollRangeSettings</i>
</br>
</br>
<code>
$("#range").ejRangeNavigator({
    scrollRangeSettings: { start: 3, end: 6 }
});
</code>
</td>
<td>
Not Applicable
</td>
</tr>

</table>

## Series

<!-- markdownlint-disable MD033 -->
<table>
<tr>
<td><b>Behaviour</b></td>
<td><b>API in Essential JS 1</b></td>
<td><b>API in Essential JS 2</b></td>
</tr>

<tr>
<td><b>animation</b></td>
<td>
<b>Property</b>:<i>enableAnimation</i>
</br>
</br>
<code>
$("#range").ejRangeNavigator({
    enableAnimation: true
});
</code>
</td>
<td>
<b>Property</b>:<i>animation</i>
</br>
</br>
<code>
let range: RangeNavigator = new RangeNavigator({
    animation: { enable: true, duration: 2000 }
});
range.appendTo('#element');
</code></td>
</tr>

<tr>
<td><b>Border for range navigator series</b></td>
<td>
Not Applicable
</td>
<td>
<b>Property</b>:<i>border</i>
</br>
</br>
<code>
let range: RangeNavigator = new RangeNavigator({
    series: [{{border:{ color: 'pink', width: 2}}}]
});
range.appendTo('#element');
</code></td>
</tr>

<tr>
<td><b>dataSource for range navigator</b></td>
<td>
<b>Property</b>:<i>series.dataSource</i>
</br>
</br>
<code>
$("#range").ejRangeNavigator({
   series: [{  dataSource: [{}] }]
});
</code>
</td>
<td>
<b>Property</b>:<i>series.dataSource</i>
</br>
</br>
<code>
let range: RangeNavigator = new RangeNavigator({
    series: [{ dataSource: [] }];
});
range.appendTo('#element');
</code></td>
</tr>

<tr>
<td><b>query for data source of range navigator</b></td>
<td>
Not Applicable
</td>
<td>
<b>Property</b>:<i>query</i>
</br>
</br>
<code>
let range: RangeNavigator = new RangeNavigator({
   series: [ { query: '' }]
});
range.appendTo('#element');
</code></td>
</tr>

<tr>
<td><b>series type for range navigator</b></td>
<td>
<b>Property</b>:<i>series.type</i>
</br>
</br>
<code>
$("#range").ejRangeNavigator({
   series: [{  type: '' }]
});
</code>
</td>
<td>
<b>Property</b>:<i>series.type</i>
</br>
</br>
<code>
let range: RangeNavigator = new RangeNavigator({
    series: [{type: '' }];
});
range.appendTo('#element');
</code></td>
</tr>

<tr>
<td><b>series xName for range navigator</b></td>
<td>
<b>Property</b>:<i>series.xName</i>
</br>
</br>
<code>
$("#range").ejRangeNavigator({
   series: [{  xName: '' }]
});
</code>
</td>
<td>
<b>Property</b>:<i>series.xName</i>
</br>
</br>
<code>
let range: RangeNavigator = new RangeNavigator({
    series: [{ xName: '' }];
});
range.appendTo('#element');
</code></td>
</tr>

<tr>
<td><b>series yName for range navigator</b></td>
<td>
<b>Property</b>:<i>series.yName</i>
</br>
</br>
<code>
$("#range").ejRangeNavigator({
   series: [{  yName: '' }]
});
</code>
</td>
<td>
<b>Property</b>:<i>series.yName</i>
</br>
</br>
<code>
let range: RangeNavigator = new RangeNavigator({
    series: [{ yName: '' }];
});
range.appendTo('#element');
</code></td>
</tr>

<tr>
<td><b>series fill color for range navigator</b></td>
<td>
<b>Property</b>:<i>series.fill</i>
</br>
</br>
<code>
$("#range").ejRangeNavigator({
   series: [{  fill: '' }]
});
</code>
</td>
<td>
<b>Property</b>:<i>series.fill</i>
</br>
</br>
<code>
let range: RangeNavigator = new RangeNavigator({
    series: [{ fill: '' }];
});
range.appendTo('#element');
</code></td>
</tr>

<tr>
<td><b>series width for range navigator</b></td>
<td>
<b>Property</b>:<i>series.width</i>
</br>
</br>
<code>
$("#range").ejRangeNavigator({
   series: [{  width: '' }]
});
</code>
</td>
<td>
<b>Property</b>:<i>series.width</i>
</br>
</br>
<code>
let range: RangeNavigator = new RangeNavigator({
    series: [{ width: '' }];
});
range.appendTo('#element');
</code></td>
</tr>

<tr>
<td><b>series dashArray for range navigator</b></td>
<td>
Not Applicable
</td>
<td>
<b>Property</b>:<i>series.dashArray</i>
</br>
</br>
<code>
let range: RangeNavigator = new RangeNavigator({
    series: [{ dashArray: '' }];
});
range.appendTo('#element');
</code></td>
</tr>

</table>

## StyleSettings

<!-- markdownlint-disable MD033 -->
<table>
<tr>
<td><b>Behaviour</b></td>
<td><b>API in Essential JS 1</b></td>
<td><b>API in Essential JS 2</b></td>
</tr>

<tr>
<td><b>Style settings of range navigator</b></td>
<td>
<b>Property</b>:<i>navigatorStyleSettings</i>
</br>
</br>
<code>
$("#range").ejRangeNavigator({
    navigatorStyleSettings: { }
});
</code>
</td>
<td>
<b>Property</b>:<i>styleSettings</i>
</br>
</br>
<code>
let range: RangeNavigator = new RangeNavigator({
    styleSettings: {}
    });
range.appendTo('#element');
</code></td>
</tr>

<tr>
<td><b>Selected region color of range navigator</b></td>
<td>
<b>Property</b>:<i>selectedRegionColor</i>
</br>
</br>
<code>
$("#range").ejRangeNavigator({
    navigatorStyleSettings: {
        selectedRegionColor: 'red'
     }
});
</code>
</td>
<td>
<b>Property</b>:<i>selectedRegionColor</i>
</br>
</br>
<code>
let range: RangeNavigator = new RangeNavigator({
    styleSettings: {
        selectedRegionColor: 'red'
    }
    });
range.appendTo('#element');
</code></td>
</tr>

<tr>
<td><b>UnSeleted region color of range navigator</b></td>
<td>
<b>Property</b>:<i>unselectedRegionColor</i>
</br>
</br>
<code>
$("#range").ejRangeNavigator({
    navigatorStyleSettings: {
        unselectedRegionColor: 'red'
     }
});
</code>
</td>
<td>
<b>Property</b>:<i>unselectedRegionColor</i>
</br>
</br>
<code>
let range: RangeNavigator = new RangeNavigator({
    styleSettings: {
        unselectedRegionColor: 'red'
    }
    });
range.appendTo('#element');
</code></td>
</tr>

<tr>
<td><b>Thumb color of range navigator</b></td>
<td>
<b>Property</b>:<i>navigatorStyleSettings</i>
</br>
</br>
<code>
$("#range").ejRangeNavigator({
    navigatorStyleSettings: {
        thumbColor: ''red'
     }
});
</code>
</td>
<td>
<b>Property</b>:<i>thumbSettings</i>
</br>
</br>
<code>
let range: RangeNavigator = new RangeNavigator({
    styleSettings: {
       thumbSettings: 'pink'
    }
    });
range.appendTo('#element');
</code></td>
</tr>

<tr>
<td><b>Thumb color of range navigator</b></td>
<td>
<b>Property</b>:<i>navigatorStyleSettings</i>
</br>
</br>
<code>
$("#range").ejRangeNavigator({
    navigatorStyleSettings: {
        thumbColor: ''red'
     }
});
</code>
</td>
<td>
<b>Property</b>:<i>thumbSettings</i>
</br>
</br>
<code>
let range: RangeNavigator = new RangeNavigator({
    styleSettings: {
       thumbSettings: 'pink'
    }
    });
range.appendTo('#element');
</code></td>
</tr>

<tr>
<td><b>Selected region opacity of range navigator</b></td>
<td>
<b>Property</b>:<i>selectedRegionOpacity</i>
</br>
</br>
<code>
$("#range").ejRangeNavigator({
    navigatorStyleSettings: {
        selectedRegionOpacity: 0.4
     }
});
</code>
</td>
<td>
Not Applicable
</td>
</tr>

<tr>
<td><b>Unselected region opacity of range navigator</b></td>
<td>
<b>Property</b>:<i>unselectedRegionOpacity</i>
</br>
</br>
<code>
$("#range").ejRangeNavigator({
    navigatorStyleSettings: {
        unselectedRegionOpacity: 0.4
     }
});
</code>
</td>
<td>
Not Applicable
</td>
</tr>

<tr>
<td><b>Background for thumb</b></td>
<td>
<b>Property</b>:<i>background</i>
</br>
</br>
<code>
$("#range").ejRangeNavigator({
    navigatorStyleSettings: {
        background: 'red'
     }
});
</code>
</td>
<td>
Not Applicable
</td>
</tr>

<tr>
<td><b>border for thumb</b></td>
<td>
<b>Property</b>:<i>border</i>
</br>
</br>
<code>
$("#range").ejRangeNavigator({
    navigatorStyleSettings: {
        border: { color: 'red', width: 2}
     }
});
</code>
</td>
<td>
Not Applicable
</td>
</tr>

<tr>
<td><b>Highlightsettings for range navigator</b></td>
<td>
<b>Property</b>:<i>highlightSettings</i>
</br>
</br>
<code>
$("#range").ejRangeNavigator({
    navigatorStyleSettings: {
        highlightSettings: { }
     }
});
</code>
</td>
<td>
Not Applicable
</td>
</tr>

<tr>
<td><b>Selected style settings for range navigator</b></td>
<td>
<b>Property</b>:<i>selectionSettings</i>
</br>
</br>
<code>
$("#range").ejRangeNavigator({
    navigatorStyleSettings: {
        selectionSettings: { }
     }
});
</code>
</td>
<td>
Not Applicable
</td>
</tr>

<tr>
<td><b>Left thumb template for range navigator</b></td>
<td>
<b>Property</b>:<i>leftThumbTemplate</i>
</br>
</br>
<code>
$("#range").ejRangeNavigator({
    navigatorStyleSettings: {
        leftThumbTemplate: ''
     }
});
</code>
</td>
<td>
Not Applicable
</td>
</tr>

<tr>
<td><b>Right thumb template for range navigator</b></td>
<td>
<b>Property</b>:<i>rightThumbTemplate</i>
</br>
</br>
<code>
$("#range").ejRangeNavigator({
    navigatorStyleSettings: {
        rightThumbTemplate: ''
     }
});
</code>
</td>
<td>
Not Applicable
</td>
</tr>
</table>

## Tooltip

<!-- markdownlint-disable MD033 -->
<table>
<tr>
<td><b>Behaviour</b></td>
<td><b>API in Essential JS 1</b></td>
<td><b>API in Essential JS 2</b></td>
</tr>

<tr>
<td><b>tooltip</b></td>
<td>
<b>Property</b>:<i>visible</i>
</br>
</br>
<code>
$("#range").ejRangeNavigator({
    tooltip: { visible: true }
});
</code>
</td>
<td>
<b>Property</b>:<i>enable</i>
</br>
</br>
<code>
let range: RangeNavigator = new RangeNavigator({
    tooltip: { enable: true }
});
range.appendTo('#element');
</code></td>
</tr>

<tr>
<td><b>background color of tooltip</b></td>
<td>
<b>Property</b>:<i>backgroundColor</i>
</br>
</br>
<code>
$("#range").ejRangeNavigator({
    tooltip: { backgroundColor: 'red' }
});
</code>
</td>
<td>
<b>Property</b>:<i>fill</i>
</br>
</br>
<code>
let range: RangeNavigator = new RangeNavigator({
    tooltip: { fill: 'pink' }
});
range.appendTo('#element');
</code></td>
</tr>

<tr>
<td><b>Font style of tooltip</b></td>
<td>
<b>Property</b>:<i>font</i>
</br>
</br>
<code>
$("#range").ejRangeNavigator({
    tooltip: { font: 'red' }
});
</code>
</td>
<td>
<b>Property</b>:<i>textStyle</i>
</br>
</br>
<code>
let range: RangeNavigator = new RangeNavigator({
    tooltip: { textStyle: 'pink' }
});
range.appendTo('#element');
</code></td>
</tr>

<tr>
<td><b>Label format of tooltip</b></td>
<td>
<b>Property</b>:<i>labelFormat</i>
</br>
</br>
<code>
$("#range").ejRangeNavigator({
    tooltip: { labelFormat: 'yMd' }
});
</code>
</td>
<td>
<b>Property</b>:<i>format</i>
</br>
</br>
<code>
let range: RangeNavigator = new RangeNavigator({
    tooltip: { format: 'yMd' }
});
range.appendTo('#element');
</code></td>
</tr>

<tr>
<td><b>Display mode of tooltip</b></td>
<td>
<b>Property</b>:<i>tooltipDisplayMode</i>
</br>
</br>
<code>
$("#range").ejRangeNavigator({
    tooltip: { tooltipDisplayMode: 'always' }
});
</code>
</td>
<td>
<b>Property</b>:<i>displayMode</i>
</br>
</br>
<code>
let range: RangeNavigator = new RangeNavigator({
    tooltip: { displayMode: 'Always' }
});
range.appendTo('#element');
</code></td>
</tr>

<tr>
<td><b>Template of tooltip</b></td>
<td>
Not Applicable
</td>
<td>
<b>Property</b>:<i>template</i>
</br>
</br>
<code>
let range: RangeNavigator = new RangeNavigator({
    tooltip: { template: '<div>Chart</div>' }
});
range.appendTo('#element');
</code></td>
</tr>

<tr>
<td><b>Border of tooltip</b></td>
<td>
Not Applicable
</td>
<td>
<b>Property</b>:<i>border</i>
</br>
</br>
<code>
let range: RangeNavigator = new RangeNavigator({
    tooltip: { border:  { color: 'red', width: 2} }
});
range.appendTo('#element');
</code></td>
</tr>

<tr>
<td><b>Opacity of tooltip</b></td>
<td>
Not Applicable
</td>
<td>
<b>Property</b>:<i>opacity</i>
</br>
</br>
<code>
let range: RangeNavigator = new RangeNavigator({
    tooltip: { opacity: 0.5 }
});
range.appendTo('#element');
</code></td>
</tr>
</table>

## Period Selector

<!-- markdownlint-disable MD033 -->
<table>
<tr>
<td><b>Behaviour</b></td>
<td><b>API in Essential JS 1</b></td>
<td><b>API in Essential JS 2</b></td>
</tr>

<tr>
<td><b>tooltip</b></td>
<td>
Not Applicable
</td>
<td>
<b>Property</b>:<i>enable</i>
</br>
</br>
<code>
let range: RangeNavigator = new RangeNavigator({
    periodSelector: {
        periods: [ {
            interval: 1, intervalType: 'Months', text: '1M'
        }],
        position: 'Top'
    }
});
range.appendTo('#element');
</code></td>
</tr>
</table>

## Methods

<!-- markdownlint-disable MD033 -->
<table>
<tr>
<td><b>Behaviour</b></td>
<td><b>API in Essential JS 1</b></td>
<td><b>API in Essential JS 2</b></td>
</tr>

<tr>
<td><b>Print</b></td>
<td>
Not Applicable
</td>
<td>
<b>Property</b>:<i>print()</i>
</br>
</br>
<code>
let range: RangeNavigator = new RangeNavigator({

});
range.print('chart');
</code>
</td>
</tr>

<tr>
<td><b>Export</b></td>
<td>
Not Applicable
</td>
<td>
<b>Property</b>:<i>export()</i>
</br>
</br>
<code>
let range: RangeNavigator = new RangeNavigator({

});
range.export('JPEG', 'chart');
</code>
</td>
</tr>
</table>

## Events

<!-- markdownlint-disable MD033 -->
<table>
<tr>
<td><b>Behaviour</b></td>
<td><b>API in Essential JS 1</b></td>
<td><b>API in Essential JS 2</b></td>
</tr>

<tr>
<td><b>Fires before loading the RangeNavigator.</b></td>
<td>
<b>Property</b>:<i>load</i>
</br>
</br>
<code>
$("#rangeNavigator").ejRangeNavigator({
    load: () {

    }
});
</code>
</td>
<td>
<b>Property</b>:<i>load</i>
</br>
</br>
<code>
let rangeNavigator: RangeNavigator = new RangeNavigator({
    load: () => {
    }
});
rangeNavigator.appendTo('#rangeNavigator');
</code>
</td>
</tr>

<tr>
<td><b>Fires before loading the RangeNavigator.</b></td>
<td>
<b>Property</b>:<i>loaded</i>
</br>
</br>
<code>
$("#rangeNavigator").ejRangeNavigator({
    loaded: () {

    }
});
</code>
</td>
<td>
<b>Property</b>:<i>loaded</i>
</br>
</br>
<code>
let rangeNavigator: RangeNavigator = new RangeNavigator({
    loaded: () => {
    }
});
rangeNavigator.appendTo('#rangeNavigator');
</code>
</td>
</tr>

<tr>
<td><b>Fires when  the value changes in range navigator.</b></td>
<td>
<b>Property</b>:<i>rangeChanged</i>
</br>
</br>
<code>
$("#rangeNavigator").ejRangeNavigator({
    rangeChanged: () {

    }
});
</code>
</td>
<td>
<b>Property</b>:<i>changed</i>
</br>
</br>
<code>
let rangeNavigator: RangeNavigator = new RangeNavigator({
    changed: () => {
    }
});
rangeNavigator.appendTo('#rangeNavigator');
</code>
</td>
</tr>

<tr>
<td><b>Fires before after the RangeNavigator.</b></td>
<td>
Not Applicable
</td>
<td>
<b>Property</b>:<i>changed</i>
</br>
</br>
<code>
let rangeNavigator: RangeNavigator = new RangeNavigator({
    resized: () => {
    }
});
rangeNavigator.appendTo('#rangeNavigator');
</code>
</td>
</tr>

<tr>
<td><b>Fires before tooltip the RangeNavigator.</b></td>
<td>
Not Applicable
</td>
<td>
<b>Property</b>:<i>tooltipRender</i>
</br>
</br>
<code>
let rangeNavigator: RangeNavigator = new RangeNavigator({
    tooltipRender: () => {
    }
});
rangeNavigator.appendTo('#rangeNavigator');
</code>
</td>
</tr>

<tr>
<td><b>Fires before period render in the RangeNavigator.</b></td>
<td>
Not Applicable
</td>
<td>
<b>Property</b>:<i>selectorRender</i>
</br>
</br>
<code>
let rangeNavigator: RangeNavigator = new RangeNavigator({
    selectorRender: () => {
    }
});
rangeNavigator.appendTo('#rangeNavigator');
</code>
</td>
</tr>

<tr>
<td><b>Fires when scrollStart the RangeNavigator.</b></td>
<td>
<b>Property</b>:<i>scrollStart</i>
</br>
</br>
<code>
$("#rangeNavigator").ejRangeNavigator({
    scrollStart: () {

    }
});
</code>
</td>
<td>
Not Applicable
</td>
</tr>

<tr>
<td><b>Fires when scrollEnd the RangeNavigator.</b></td>
<td>
<b>Property</b>:<i>scrollEnd</i>
</br>
</br>
<code>
$("#rangeNavigator").ejRangeNavigator({
    scrollEnd: () {

    }
});
</code>
</td>
<td>
Not Applicable
</td>
</tr>

<tr>
<td><b>Fires when selected range Start the RangeNavigator.</b></td>
<td>
<b>Property</b>:<i>selectedRangeStart</i>
</br>
</br>
<code>
$("#rangeNavigator").ejRangeNavigator({
    selectedRangeStart: () {

    }
});
</code>
</td>
<td>
Not Applicable
</td>
</tr>

<tr>
<td><b>Fires when selected range ends the RangeNavigator.</b></td>
<td>
<b>Property</b>:<i>selectedRangeEnd</i>
</br>
</br>
<code>
$("#rangeNavigator").ejRangeNavigator({
    selectedRangeEnd: () {

    }
});
</code>
</td>
<td>
Not Applicable
</td>
</tr>

<tr>
<td><b>Fires when scroll range changed in the RangeNavigator.</b></td>
<td>
<b>Property</b>:<i>scrollChanged</i>
</br>
</br>
<code>
$("#rangeNavigator").ejRangeNavigator({
    scrollChanged: () {

    }
});
</code>
</td>
<td>
Not Applicable
</td>
</tr>

<tr>
<td><b>Fires when  click in the RangeNavigator.</b></td>
<td>
<b>Property</b>:<i>click</i>
</br>
</br>
<code>
$("#rangeNavigator").ejRangeNavigator({
    click: () {

    }
});
</code>
</td>
<td>
Not Applicable
</td>
</tr>

<tr>
<td><b>Fires when  right click in the RangeNavigator.</b></td>
<td>
<b>Property</b>:<i>rightClick</i>
</br>
</br>
<code>
$("#rangeNavigator").ejRangeNavigator({
    rightClick: () {

    }
});
</code>
</td>
<td>
Not Applicable
</td>
</tr>

<tr>
<td><b>Fires when double click in the RangeNavigator.</b></td>
<td>
<b>Property</b>:<i>doubleClick</i>
</br>
</br>
<code>
$("#rangeNavigator").ejRangeNavigator({
    doubleClick: () {

    }
});
</code>
</td>
<td>
Not Applicable
</td>
</tr>

</table>