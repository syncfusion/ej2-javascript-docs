---
title: "API Migration"
component: "HeatMap Chart"
description: "This article describes the API migration process of heat map component from Essential JS 1 to Essential JS 2"
---

# Migration from Essential JS 1

This article describes the API migration process of heat map component from Essential JS 1 to Essential JS 2.

## Members

<!-- markdownlint-disable MD033 -->
<table>
<tr>
<td><b>Behaviour</b></td>
<td><b>API in Essential JS 1</b></td>
<td><b>API in Essential JS 2</b></td>
</tr>

<tr>
<td><b>Specifies the width of the heat map</b></td>
<td>
<b>Property</b>:<i>width</i>
</br>
</br>
<code>
$("#heatmap").ejHeatMap({
    width: "300"
});
</code>
</td>
<td>
<b>Property</b>:<i>width</i>
</br>
</br>
<code>
var heatmap = new ej.heatmap.HeatMap({
    width: '650px'
});
heatmap.appendTo('#heatmap');
</code></td>
</tr>

<tr>
<td><b>Specifies the height of the heat map</b></td>
<td>
<b>Property</b>:<i>height</i>
</br>
</br>
<code>
$("#heatmap").ejHeatMap({
    height: "300"
});
</code>
</td>
<td>
<b>Property</b>:<i>height</i>
</br>
</br>
<code>
var heatmap = new ej.heatmap.HeatMap({
    height: '650px'
});
heatmap.appendTo('#heatmap');
</code></td>
</tr>

<tr>
<td><b>Enables or disables tooltip of heat map</b></td>
<td>
<b>Property</b>:<i>showtooltip</i>
</br>
</br>
<code>
$("#heatmap").ejHeatMap({
    showtooltip: true
});
</code>
</td>
<td>
<b>Property</b>:<i>showTooltip</i>
</br>
</br>
<code>
var heatmap = new ej.heatmap.HeatMap({
    showTooltip: true
});
heatmap.appendTo('#heatmap');
</code></td>
</tr>

<tr>
<td><b>Defines the tooltip that should be shown when the mouse hovers over cells.</b></td>
<td>
<b>Property</b>:<i>toolTipSettings.templateId</i>
</br>
</br>
<code>
$("#heatmap").ejHeatMap({
    toolTipSettings: {
        templateId:"mouseovertoolTipId"
    }
});
</code>
</td>
<td>
<b>Property</b>:<i>tooltipRender</i>
</br>
</br>
<code>
var heatmap = new ej.heatmap.HeatMap({
    tooltipRender: function (args) {
            args.content = [args.yLabel + ' | ' + args.xLabel + ' : ' + args.value ];
    }
});
heatmap.appendTo('#heatmap');
</code></td>
</tr>

<tr>
<td><b>Specifies the source data of the heat map.</b></td>
<td>
<b>Property</b>:<i>itemsSource</i>
</br>
</br>
<code>
$("#heatmap").ejHeatMap({
    itemsSource: []
});
</code>
</td>
<td>
<b>Property</b>:<i>dataSource</i>
</br>
</br>
<code>
var heatmap = new ej.heatmap.HeatMap({
    dataSource: []
});
heatmap.appendTo('#heatmap');
</code></td>
</tr>

<tr>
<td><b>Specifies whether the cell content can be visible or not.</b></td>
<td>
<b>Property</b>:<i>heatmapCell.showContent</i>
</br>
</br>
<code>
$("#heatmap").ejHeatMap({
        heatmapCell: { showContent: ej.HeatMap.CellVisibility.Hidden }
});
</code>
</td>
<td>
<b>Property</b>:<i>cellSettings.showLabel</i>
</br>
</br>
<code>
var heatmap = new ej.heatmap.HeatMap({
    cellSettings: {
          showLabel: false
        },
});
heatmap.appendTo('#heatmap');
</code></td>
</tr>

<tr>
<td><b>Specifies the color of the heat map column data.</b></td>
<td>
<b>Property</b>:<i>colorMappingCollection.color</i>
</br>
</br>
<code>
$("#heatmap").ejHeatMap({
    colorMappingCollection: [
        { color: "#8ec8f8" },
        { color: "#0d47a1" }
    ]
});
</code>
</td>
<td>
<b>Property</b>:<i>paletteSettings.palette.color</i>
</br>
</br>
<code>
var heatmap = new ej.heatmap.HeatMap({
    paletteSettings: {
                palette: [
                { color: '#C06C84'},
            ]
        }
});
heatmap.appendTo('#heatmap');
</code></td>
</tr>

<tr>
<td><b>Specifies the color values of the heat map column data.</b></td>
<td>
<b>Property</b>:<i>colorMappingCollection.value</i>
</br>
</br>
<code>
$("#heatmap").ejHeatMap({
    colorMappingCollection: [
        { value: 0 },
        { value: 100 }
    ]
});
</code>
</td>
<td>
<b>Property</b>:<i>paletteSettings.palette.value</i>
</br>
</br>
<code>
var heatmap = new ej.heatmap.HeatMap({
    paletteSettings: {
                palette: [
                { value: 50 },
                { value: 100 }
            ]
        }
});
heatmap.appendTo('#heatmap');
</code></td>
</tr>

<tr>
<td><b>Specifies the label text of the heat map color.</b></td>
<td>
<b>Property</b>:<i>colorMappingCollection.label.text</i>
</br>
</br>
<code>
$("#heatmap").ejHeatMap({
    colorMappingCollection: [
        { label: { text: "Low" } },
        { label: { text: "Moderate" } }
    ]
});
</code>
</td>
<td>
<b>Property</b>:<i>paletteSettings.palette.label</i>
</br>
</br>
<code>
var heatmap = new ej.heatmap.HeatMap({
    paletteSettings: {
                palette: [
                { label:'Low' },
                { label:'Moderate' }
            ]
        }
});
heatmap.appendTo('#heatmap');
</code></td>
</tr>

<tr>
<td><b>Specifies the style of the heat map color label.</b></td>
<td>
<b>Property</b>:<i>colorMappingCollection.label.bold</i>
<b>Property</b>:<i>colorMappingCollection.label.italic</i>
</br>
</br>
<code>
$("#heatmap").ejHeatMap({
    colorMappingCollection: [
        { label: { bold: true } },
        { label: { italic: true } },
    ]
});
</code>
</td>
<td>
<b>Property</b>:<i>legendSettings.textStyle.fontStyle</i>
</br>
</br>
<code>
var heatmap = new ej.heatmap.HeatMap({
    legendSettings: {
        textStyle: { fontStyle:'bold' }
    }
});
heatmap.appendTo('#heatmap');
</code></td>
</tr>

<tr>
<td><b>Specifies the font size of the heat map label.</b></td>
<td>
<b>Property</b>:<i>colorMappingCollection.label.fontSize</i>
</br>
</br>
<code>
$("#heatmap").ejHeatMap({
    colorMappingCollection: [
        { label: { fontSize: 18 } }
    ]
});
</code>
</td>
<td>
<b>Property</b>:<i>legendSettings.textStyle.size</i>
</br>
</br>
<code>
var heatmap = new ej.heatmap.HeatMap({
    legendSettings: {
        textStyle: { size: 18 }
    }
});
heatmap.appendTo('#heatmap');
</code></td>
</tr>

<tr>
<td><b>Specifies the font family of the heat map label.</b></td>
<td>
<b>Property</b>:<i>colorMappingCollection.label.fontFamily</i>
</br>
</br>
<code>
$("#heatmap").ejHeatMap({
    colorMappingCollection: [
        { label: { fontFamily: "Arial" } }
    ]
});
</code>
</td>
<td>
<b>Property</b>:<i>legendSettings.textStyle.fontFamily</i>
</br>
</br>
<code>
var heatmap = new ej.heatmap.HeatMap({
    legendSettings: {
        textStyle: { fontFamily: 'Arial' }
    }
});
heatmap.appendTo('#heatmap');
</code></td>
</tr>

<tr>
<td><b>Specifies the font color of the heat map label.</b></td>
<td>
<b>Property</b>:<i>colorMappingCollection.label.fontColor</i>
</br>
</br>
<code>
$("#heatmap").ejHeatMap({
    colorMappingCollection: [
        { label: { fontColor: "red" } }
    ]
});
</code>
</td>
<td>
<b>Property</b>:<i>legendSettings.textStyle.fontFamily</i>
</br>
</br>
<code>
var heatmap = new ej.heatmap.HeatMap({
    legendSettings: {
        textStyle: { color: 'red' }
    }
});
heatmap.appendTo('#heatmap');
</code></td>
</tr>

<tr>
<td><b>Specifies the mapping name of the column.</b></td>
<td>
<b>Property</b>:<i>itemsMapping.column.propertyName</i>
</br>
</br>
<code>
$("#heatmap").ejHeatMap({
    itemsMapping: {
        column: { "propertyName": "ProductName" }
    }
});
</code>
</td>
<td>
<b>Property</b>:<i>dataSource.yDataMapping</i>
</br>
</br>
<code>
var heatmap = new ej.heatmap.HeatMap({
    dataSource: heatmapData,
    dataSourceSettings: {
            yDataMapping: 'columnid'
        }
});
heatmap.appendTo('#heatmap');
</code></td>
</tr>

<tr>
<td><b>Specifies the mapping name of the row.</b></td>
<td>
<b>Property</b>:<i>itemsMapping.row.propertyName</i>
</br>
</br>
<code>
$("#heatmap").ejHeatMap({
    itemsMapping: {
        row: { "displayName": "Product Name" }
    }
});
</code>
</td>
<td>
<b>Property</b>:<i>dataSource.xDataMapping</i>
</br>
</br>
<code>
var heatmap = new ej.heatmap.HeatMap({
    dataSource: heatmapData,
    dataSourceSettings: {
            xDataMapping: 'rowid'
        }
});
heatmap.appendTo('#heatmap');
</code></td>
</tr>

<tr>
<td><b>Specifies the mapping name of the row.</b></td>
<td>
<b>Property</b>:<i>itemsMapping.value.displayName</i>
</br>
</br>
<code>
$("#heatmap").ejHeatMap({
    itemsMapping: {
        value: { "displayName": "Product Name" }
    }
});
</code>
</td>
<td>
<b>Property</b>:<i>dataSource.valueMapping</i>
</br>
</br>
<code>
var heatmap = new ej.heatmap.HeatMap({
    dataSource: heatmapData,
    dataSourceSettings: {
            valueMapping: 'value'
        }
});
heatmap.appendTo('#heatmap');
</code></td>
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
<td><b>Triggered when the cell get clicked.</b></td>
<td>
<b>Property</b>:<i>cellSelected</i>
</br>
</br>
<code>
$("#heatmap").ejHeatMap({
    cellSelected: function(args) {}
});
</code>
</td>
<td>
<b>Property</b>:<i>cellClick</i>
</br>
</br>
<code>
var heatmap = new ej.heatmap.HeatMap({
    cellClick: function (args) {},
});
heatmap.appendTo('#heatmap');
</code></td>
</tr>
</table>
