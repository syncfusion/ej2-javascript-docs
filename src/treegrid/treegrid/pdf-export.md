---
title: "PDF Export"
component: "TreeGrid"
description: "Documentation on exporting TreeGrid content to PDF format and customizing the exported document with headers and footers, and file name changes."
---

# PDF Export

PDF export allows exporting TreeGrid data to PDF document. You need to use the
 [`pdfExport`](../api/treegrid/#pdfexport) method for exporting. To enable PDF export in the treegrid, set the [`allowPdfExport`](../api/treegrid/#allowpdfexport) as true.

To use PDF export, inject the `PdfExport` module in treegrid.

{% tab template="treegrid/pdfexport",es5Template="pdfexport" %}

```typescript

import { TreeGrid, Page, Toolbar, PdfExport } from '@syncfusion/ej2-treegrid';
import { sampleData } from './datasource.ts';

TreeGrid.Inject(Page, Toolbar, PdfExport);

let treeGridObj: TreeGrid = new TreeGrid({
    dataSource: sampleData,
    childMapping: 'subtasks',
    allowPdfExport: true,
    allowPaging: true,
    height: 220,
    pageSettings: {pageSize: 7},
    toolbar: ['PdfExport'],
    treeColumnIndex: 1,
    columns: [
            { field: 'taskID', headerText: 'Task ID', width: 90, textAlign: 'Right' },
            { field: 'taskName', headerText: 'Task Name', width: 180, textAlign: 'Left' },
            {
                field: 'startDate', headerText: 'Start Date', width: 90, textAlign: 'Right', type: 'date', format: 'yMd'
            },
            { field: 'duration', headerText: 'Duration', width: 80, textAlign: 'Right' }
    ]
});

treeGridObj.appendTo('#TreeGrid');
treeGridObj.toolbarClick = (args: Object) => {
if (args['item'].text === 'PDF Export') {
        treeGridObj.pdfExport();
    }

}

```

{% endtab %}

<!-- Multiple exporting

PDF export provides an option for exporting multiple treegrids to same file. In this exported document, each treegrid will be exported to new page of document in same file.

{% tab template="treegrid/multiplepdfexport",es5Template="multiexport" %}

```typescript

import { TreeGrid, Page, Toolbar, PdfExport } from '@syncfusion/ej2-treegrid';
import { sampleData, projectData } from './datasource.ts';

TreeGrid.Inject(Page, Toolbar, PdfExport);

let firstTreeGrid: TreeGrid = new TreeGrid({
    dataSource: sampleData,
    childMapping: 'subtasks',
    allowPaging: true,
    height: 220,
    pageSettings: {pageSize: 7},
    allowPdfExport: true,
    toolbar: ['PdfExport'],
    treeColumnIndex: 1,
    columns: [
            { field: 'taskID', headerText: 'Task ID', width: 90, textAlign: 'Right' },
            { field: 'taskName', headerText: 'Task Name', width: 180, textAlign: 'Left' },
            {
                field: 'startDate', headerText: 'Start Date', width: 90, textAlign: 'Right', type: 'date', format: 'yMd'
            },
            { field: 'duration', headerText: 'Duration', width: 80, textAlign: 'Right' }
    ]
});

firstTreeGrid.appendTo('#TreeGrid');
let secondTreeGrid: TreeGrid = new TreeGrid({
    dataSource: projectData,
    idMapping: 'TaskID',
    parentIdMapping: 'parentID',
    allowPdfExport: true,
    allowPaging: true,
    height: 220,
    treeColumnIndex: 1,
    pageSettings: {pageSize: 7},
    columns: [
            { field: 'TaskID', headerText: 'Task ID', width: 90, textAlign: 'Right' },
            { field: 'TaskName', headerText: 'Task Name', width: 180 },
            {
                field: 'StartDate', headerText: 'Start Date', width: 90, textAlign: 'Right', type: 'date',format: 'yMd'
            },
            { field: 'Duration', headerText: 'Duration', width: 80, textAlign: 'Right' }
    ]
});
secondTreeGrid.appendTo('#TreeGrid2');
firstTreeGrid.toolbarClick = (args: Object) => {
if (args['item'].text === 'PDF Export') {
    let firstGridPdfExport: Promise<Object> = firstTreeGrid.pdfExport({}, true);
        firstGridPdfExport.then((pdfData: Object) => {
            secondTreeGrid.pdfExport({}, false, pdfData);
            });
        });
    }
}

```

{% endtab %} -->

## To customize PDF export

PDF export provides an option to customize mapping of treegrid to exported PDF document.

### File Name for Exported document

You can assign the file name for the exported document by defining `fileName` property in `PdfExportProperties`.

{% tab template="treegrid/pdfexport",es5Template="pdfexportfile" %}

```typescript

import { TreeGrid, Page, Toolbar, PdfExport, PdfExportProperties } from '@syncfusion/ej2-treegrid';
import { sampleData } from './datasource.ts';

TreeGrid.Inject(Page, Toolbar, PdfExport);

let treeGridObj: TreeGrid = new TreeGrid({
    dataSource: sampleData,
    childMapping: 'subtasks',
    allowPdfExport: true,
    allowPaging: true,
    height: 220,
    pageSettings: {pageSize: 7},
    toolbar: ['PdfExport'],
    treeColumnIndex: 1,
    columns: [
            { field: 'taskID', headerText: 'Task ID', width: 90, textAlign: 'Right' },
            { field: 'taskName', headerText: 'Task Name', width: 180, textAlign: 'Left' },
            {
                field: 'startDate', headerText: 'Start Date', width: 90, textAlign: 'Right', type: 'date', format: 'yMd'
            },
            { field: 'duration', headerText: 'Duration', width: 80, textAlign: 'Right' }
    ]
});

treeGridObj.appendTo('#TreeGrid');
treeGridObj.toolbarClick = (args: Object) => {
if (args['item'].text === 'PDF Export') {
        let exportProperties: PdfExportProperties = {
           fileName:"new.xlsx"
        };
        treeGridObj.pdfExport(exportProperties);
    }

}

```

{% endtab %}

### Default Fonts for PDF exporting

By default, treegrid uses `Helvetica` font in the exported document. You can change the default font by using `pdfExportProperties.theme` property. The available default fonts are,

* Helvetica
* TimesRoman
* Courier
* Symbol
* ZapfDingbats

The code example for changing default font,

```typescript

    import { PdfStandardFont, PdfFontFamily, PdfFontStyle } from '@syncfusion/ej2-pdf-export';

    ...

    let pdfExportProperties: PdfExportProperties = {
        theme: {
            header: {font:  new PdfStandardFont(PdfFontFamily.TimesRoman, 11, PdfFontStyle.Bold),
            record: { font: new PdfStandardFont(PdfFontFamily.TimesRoman, 10) }
        }
    };

```

### Add Custom Font for PDF exporting

You can change the default font of TreeGrid header, content and caption cells in the exported document by using `pdfExportProperties.theme` property.

In the following example, we have used Advent Pro font to export the treegrid with Hungarian fonts.

{% tab template="treegrid/pdfexport", sourceFiles="index.ts,index.html,datasource.ts", es5Template="customfont" %}

```typescript

import { TreeGrid, Page, Toolbar, PdfExport, PdfExportProperties } from '@syncfusion/ej2-treegrid';
import { sampleData, adventProFont } from './datasource.ts';
import { PdfTrueTypeFont } from '@syncfusion/ej2-pdf-export';

TreeGrid.Inject(Page, Toolbar, PdfExport);

let treeGridObj: TreeGrid = new TreeGrid({
    dataSource: sampleData,
    childMapping: 'subtasks',
    allowPdfExport: true,
    allowPaging: true,
    height: 220,
    pageSettings: {pageSize: 7},
    toolbar: ['PdfExport'],
    treeColumnIndex: 1,
    columns: [
            { field: 'taskID', headerText: 'Task ID', width: 90, textAlign: 'Right' },
            { field: 'taskName', headerText: 'Task Name', width: 180, textAlign: 'Left' },
            {
                field: 'startDate', headerText: 'Start Date', width: 90, textAlign: 'Right', type: 'date', format: 'yMd'
            },
            { field: 'duration', headerText: 'Duration', width: 80, textAlign: 'Right' }
    ]
});

treeGridObj.appendTo('#TreeGrid');
treeGridObj.toolbarClick = (args: Object) => {
if (args['item'].text === 'PDF Export') {
        let exportProperties: PdfExportProperties = {
           theme: {
                header: {font:  new PdfTrueTypeFont(adventProFont, 12) },
                record: { font: new PdfTrueTypeFont(adventProFont, 9) }
            }
        };
        treeGridObj.pdfExport(exportProperties);
    }

}

```

{% endtab %}

> `PdfTrueTypeFont` accepts base 64 format of the Custom Font.

### To add header and footer

You can customize text, page number, line, page size and changing orientation in header and footer.

#### How to write a text in header/footer

You can add text either in Header or Footer of exported PDF document.

```typescript

let exportProperties: PdfExportProperties = {
    header: {
        fromTop: 0,
        height: 130,
        contents: [
            {
                type: 'Text',
                value: "Task Details",
                position: { x: 0, y: 50 },
                style: { textBrushColor: '#000000', fontSize: 13 }
            },

        ]
    }

```

#### How to draw a line in header/footer

you can add line either in Header or Footer of the exported PDF document.

Supported line styles:

* dash
* dot
* dashdot
* dashdotdot
* solid

```typescript

let exportProperties: PdfExportProperties = {
    header: {
        fromTop: 0,
        height: 130,
        contents: [
            {
                type: 'Line',
                style: { penColor: '#000080', penSize: 2, dashStyle: 'Solid' },
                points: { x1: 0, y1: 4, x2: 685, y2: 4 }
            }
        ]
    }
}

```

#### Add page number in header/footer

you can add page number either in Header or Footer of exported PDF document.

Supported page number types:

* LowerLatin - a, b, c,
* UpperLatin - A, B, C,
* LowerRoman - i, ii, iii,
* UpperRoman - I, II, III,
* Number - 1,2,3.

```typescript

 let exportProperties: PdfExportProperties = {
    header: {
        fromTop: 0,
        height: 130,
        contents: [
            {
                type: 'PageNumber',
                pageNumberType: 'Arabic',
                format: 'Page {$current} of {$total}', //optional
                position: { x: 0, y: 25 },
                style: { textBrushColor: '#ffff80', fontSize: 15, hAlign: 'Center' }
            }
        ]
    }
}

```

#### Insert an image in header/footer

Image (Base64 string) can be added in the exported document in header/footer using the `exportProperties`.

```typescript

let exportProperties: PdfExportProperties = {
    header: {
        fromTop: 0,
        height: 130,
        contents: [
            {
                type: 'Image',
                src: image,
                position: { x: 40, y: 10 },
                size: { height: 100, width: 250 },
            }
        ]
    }
}

```

The below code illustrates the pdf export customization.

{% tab template="treegrid/pdfexport",es5Template="imagepdf" %}

```typescript

import { TreeGrid, Page, Toolbar, PdfExport, PdfExportProperties } from '@syncfusion/ej2-treegrid';
import { sampleData } from './datasource.ts';
import { image } from './image.ts';

TreeGrid.Inject(Page, Toolbar, PdfExport);

let treeGridObj: TreeGrid = new TreeGrid({
    dataSource: sampleData,
    childMapping: 'subtasks',
    allowPdfExport: true,
    allowPaging: true,
    height: 220,
    pageSettings: {pageSize: 7},
    toolbar: ['PdfExport'],
    treeColumnIndex: 1,
    columns: [
            { field: 'taskID', headerText: 'Task ID', width: 90, textAlign: 'Right' },
            { field: 'taskName', headerText: 'Task Name', width: 180, textAlign: 'Left' },
            {
                field: 'startDate', headerText: 'Start Date', width: 90, textAlign: 'Right', type: 'date', format: 'yMd'
            },
            { field: 'duration', headerText: 'Duration', width: 80, textAlign: 'Right' }
    ]
});

treeGridObj.appendTo('#TreeGrid');
treeGridObj.toolbarClick = (args: Object) => {
    if (args['item'].text === 'PDF Export') {
        let pdfExportProperties: PdfExportProperties = {
            header: {
                fromTop: 0,
                height: 130,
                contents: [
                    {
                        type: 'Image',
                        src: image,
                        position: { x: 40, y: 10 },
                        size: { height: 100, width: 250 },
                    }
                ]
            },
            footer: {
                fromBottom: 160,
                height: 150,
                contents: [
                    {
                        type: 'PageNumber',
                        pageNumberType: 'Arabic',
                        format: 'Page {$current} of {$total}',
                        position: { x: 0, y: 25 },
                        style: { textBrushColor: '#ffff80', fontSize: 15 }
                    }
                ]
            }
        };
        treeGridObj.pdfExport(pdfExportProperties);
    }
}

```

{% endtab %}

### How to change page orientation

Page orientation can be changed Landscape(Default Portrait) for the exported document using the `exportProperties`.

{% tab template="treegrid/pdfexport",es5Template="pageorientation" %}

```typescript

import { TreeGrid, Page, Toolbar, PdfExport, PdfExportProperties } from '@syncfusion/ej2-treegrid';
import { sampleData } from './datasource.ts';

TreeGrid.Inject(Page, Toolbar, PdfExport);

let treeGridObj: TreeGrid = new TreeGrid({
    dataSource: sampleData,
    childMapping: 'subtasks',
    allowPdfExport: true,
    allowPaging: true,
    height: 220,
    pageSettings: {pageSize: 7},
    toolbar: ['PdfExport'],
    treeColumnIndex: 1,
    columns: [
            { field: 'taskID', headerText: 'Task ID', width: 90, textAlign: 'Right' },
            { field: 'taskName', headerText: 'Task Name', width: 180, textAlign: 'Left' },
            {
                field: 'startDate', headerText: 'Start Date', width: 90, textAlign: 'Right', type: 'date', format: 'yMd'
            },
            { field: 'duration', headerText: 'Duration', width: 80, textAlign: 'Right' }
    ]
});

treeGridObj.appendTo('#TreeGrid');
treeGridObj.toolbarClick = (args: Object) => {
    if (args['item'].text === 'PDF Export') {
        let exportProperties: PdfExportProperties = {
            pageOrientation: 'Landscape',
        };
        treeGridObj.pdfExport(exportProperties);
    }
}

```

{% endtab %}

### How to change page size

Page size can be customized for the exported document using the `exportProperties`.
Supported page sizes are:

* Letter
* Note
* Legal
* A0
* A1
* A2
* A3
* A5
* A6
* A7
* A8
* A9
* B0
* B1
* B2
* B3
* B4
* B5
* Archa
* Archb
* Archc
* Archd
* Arche
* Flsa
* HalfLetter
* Letter11x17
* Ledger

{% tab template="treegrid/pdfexport" ,es5Template="pagesize" %}

```typescript

import { TreeGrid, Page, Toolbar, PdfExport, PdfExportProperties } from '@syncfusion/ej2-treegrid';
import { sampleData } from './datasource.ts';

TreeGrid.Inject(Page, Toolbar, PdfExport);

let treeGridObj: TreeGrid = new TreeGrid({
    dataSource: sampleData,
    childMapping: 'subtasks',
    allowPdfExport: true,
    allowPaging: true,
    height: 220,
    pageSettings: {pageSize: 7},
    toolbar: ['PdfExport'],
    treeColumnIndex: 1,
    columns: [
            { field: 'taskID', headerText: 'Task ID', width: 90, textAlign: 'Right' },
            { field: 'taskName', headerText: 'Task Name', width: 180, textAlign: 'Left' },
            {
                field: 'startDate', headerText: 'Start Date', width: 90, textAlign: 'Right', type: 'date', format: 'yMd'
            },
            { field: 'duration', headerText: 'Duration', width: 80, textAlign: 'Right' }
    ]
});

treeGridObj.appendTo('#TreeGrid');
treeGridObj.toolbarClick = (args: Object) => {
if (args['item'].text === 'PDF Export') {
        let exportProperties: PdfExportProperties = {
            pageSize: 'Letter'
        };
        treeGridObj.pdfExport(exportProperties);
    }
}

```

{% endtab %}

<!--  Export current page

PDF export provides an option to export the current page into PDF. To export current page, define the `exportType` to `CurrentPage`.

{% tab template="treegrid/pdfexport",es5Template="exportpage" %}

```typescript

import { TreeGrid, Page, Toolbar, PdfExport, PdfExportProperties } from '@syncfusion/ej2-treegrid';
import { sampleData } from './datasource.ts';

TreeGrid.Inject(Page, Toolbar, PdfExport);

let treeGridObj: TreeGrid = new TreeGrid({
    dataSource: sampleData,
    childMapping: 'subtasks',
    allowPdfExport: true,
    allowPaging: true,
    height: 220,
    pageSettings: {pageSize: 7},
    toolbar: ['PdfExport'],
    treeColumnIndex: 1,
    columns: [
            { field: 'taskID', headerText: 'Task ID', width: 90, textAlign: 'Right' },
            { field: 'taskName', headerText: 'Task Name', width: 180, textAlign: 'Left' },
            {
                field: 'startDate', headerText: 'Start Date', width: 90, textAlign: 'Right', type: 'date', format: 'yMd'
            },
            { field: 'duration', headerText: 'Duration', width: 80, textAlign: 'Right' }
    ]
});

treeGridObj.appendTo('#TreeGrid');
treeGridObj.toolbarClick = (args: Object) => {
	if (args['item'].text === 'PDF Export') {
        let exportProperties: PdfExportProperties = {
            exportType: 'CurrentPage'
        };
        treeGridObj.pdfExport(exportProperties);
    }
}

```

{% endtab %} -->

### Export hidden columns

PDF export provides an option to export hidden columns of TreeGrid by defining the `includeHiddenColumn` as `true`.

{% tab template="treegrid/pdfexport",es5Template="exporthidden" %}

```typescript

import { TreeGrid, Page, Toolbar, PdfExport, PdfExportProperties } from '@syncfusion/ej2-treegrid';
import { sampleData } from './datasource.ts';

TreeGrid.Inject(Page, Toolbar, PdfExport);

let treeGridObj: TreeGrid = new TreeGrid({
    dataSource: sampleData,
    childMapping: 'subtasks',
    allowPdfExport: true,
    allowPaging: true,
    height: 220,
    pageSettings: {pageSize: 7},
    toolbar: ['PdfExport'],
    treeColumnIndex: 1,
    columns: [
            { field: 'taskID', headerText: 'Task ID', width: 90, textAlign: 'Right' },
            { field: 'taskName', headerText: 'Task Name', width: 180, textAlign: 'Left' },
            {
                field: 'startDate', headerText: 'Start Date', width: 90, textAlign: 'Right', type: 'date', format: 'yMd'
            },
            { field: 'duration', headerText: 'Duration', visible: false, width: 80, textAlign: 'Right' }
    ]
});

treeGridObj.appendTo('#TreeGrid');
treeGridObj.toolbarClick = (args: Object) => {
if (args['item'].text === 'PDF Export') {
        let exportProperties: PdfExportProperties = {
            includeHiddenColumn: true
        };
        treeGridObj.pdfExport(exportProperties);
    }
}

```

{% endtab %}

### Show or Hide columns on Exported PDF

You can show a hidden column or hide a visible column while exporting the treegrid using [`toolbarClick`](../api/treegrid#toolbarclick) and [`pdfExportComplete`](../api/treegrid#pdfExportComplete) events.

In the `toolbarClick` event, based on `args.item.text` as `PDF Export`. We can show or hide columns by setting `column.visible` property to `true` or `false` respectively.

In the pdfExportComplete event, We have reversed the state back to the previous state.

In the below example, we have `Duration` as a hidden column in the treegrid. While exporting, we have changed `Duration` to visible column and `StartDate` as hidden column.

{% tab template="treegrid/pdfexport",es5Template="show-hide-pdf" %}

```typescript

import { TreeGrid, Page, Toolbar, PdfExport, PdfExportProperties } from '@syncfusion/ej2-treegrid';
import { Column }  from '@syncfusion/ej2-grids';
import { sampleData } from './datasource.ts';

TreeGrid.Inject(Page, Toolbar, PdfExport);

let treeGridObj: TreeGrid = new TreeGrid({
    dataSource: sampleData,
    childMapping: 'subtasks',
    allowPdfExport: true,
    allowPaging: true,
    height: 220,
    pageSettings: {pageSize: 7},
    toolbar: ['PdfExport'],
    treeColumnIndex: 1,
    columns: [
            { field: 'taskID', headerText: 'Task ID', width: 90, textAlign: 'Right' },
            { field: 'taskName', headerText: 'Task Name', width: 180, textAlign: 'Left' },
            {
                field: 'startDate', headerText: 'Start Date', width: 90, textAlign: 'Right', type: 'date', format: 'yMd'
            },
            { field: 'duration', headerText: 'Duration', visible: false, width: 80, textAlign: 'Right' }
    ]
});

treeGridObj.appendTo('#TreeGrid');
treeGridObj.toolbarClick = (args: Object) => {
if (args['item'].text === 'PDF Export') {
        let cols: Column[] = treeGridObj.grid.columns;
        cols[2].visible = false;
        cols[3].visible = true;
        treeGridObj.pdfExport();
    }
}
treeGridObj.pdfExportComplete = () => {
        let cols: Column[] = treeGridObj.grid.columns;
        cols[3].visible = false;
        cols[2].visible = true;
    }

```

{% endtab %}

### Conditional Cell Formatting

TreeGrid cells in the exported PDF can be customized or formatted using [`pdfQueryCellInfo`](../api/treegrid#pdfQueryCellInfo) event. In this event, we can format the treegrid cells of exported PDF document based on the column cell value.

In the below sample, we have set the background color for `Duration` column in the exported document by `args.cell` and `backgroundColor` property.

{% tab template="treegrid/pdfexport",es5Template="padfexport" %}

```typescript

import { TreeGrid, Page, Toolbar, PdfExport, PdfExportProperties, RowDataBoundEventArgs, PdfQueryCellInfoEventArgs } from '@syncfusion/ej2-treegrid';
import { sampleData } from './datasource.ts';

TreeGrid.Inject(Page, Toolbar, PdfExport);

let treeGridObj: TreeGrid = new TreeGrid({
    dataSource: sampleData,
    childMapping: 'subtasks',
    allowPdfExport: true,
    allowPaging: true,
    height: 220,
    pageSettings: {pageSize: 7},
    toolbar: ['PdfExport'],
    treeColumnIndex: 1,
    columns: [
            { field: 'taskID', headerText: 'Task ID', width: 90, textAlign: 'Right' },
            { field: 'taskName', headerText: 'Task Name', width: 180, textAlign: 'Left' },
            {
                field: 'startDate', headerText: 'Start Date', width: 90, textAlign: 'Right', type: 'date', format: 'yMd'
            },
            { field: 'duration', headerText: 'Duration', width: 80, textAlign: 'Right' }
    ]
});

treeGridObj.appendTo('#TreeGrid');
treeGridObj.toolbarClick = (args: Object) => {
if (args['item'].text === 'PDF Export') {
        treeGridObj.pdfExport();
    }
}
treeGridObj.pdfQueryCellInfo = (args: PdfQueryCellInfoEventArgs) => {
        if(args.column.field == 'duration'){
            if(+args.value === 0 || args.value === "") {
                args.style = {backgroundColor: '#336c12'};
            }
            else if(args.value < 3) {
                args.style = {backgroundColor: '#7b2b1d'};
            }
        }
    }
treeGridObj.queryCellInfo = (args: RowDataBoundEventArgs) => {
    if (args.data['duration'] == 0 && args.column.field === 'duration' ) {
        args.cell.style.background= '#336c12';
    } else if (args.data['duration'] < 3 && args.column.field === 'duration') {
        args.cell.style.background= '#7b2b1d';
    }
}

```

{% endtab %}

### Theme

PDF export provides an option to include theme for exported PDF document.

To apply theme in exported PDF, define the `theme` in `exportProperties` .

{% tab template="treegrid/pdfexport",es5Template="exporttheme" %}

```typescript

import { TreeGrid, Page, Toolbar, PdfExportProperties, PdfExport } from '@syncfusion/ej2-treegrid';
import { sampleData } from './datasource.ts';

TreeGrid.Inject(Page, Toolbar, PdfExport);

let treeGridObj: TreeGrid = new TreeGrid({
    dataSource: sampleData,
    childMapping: 'subtasks',
    allowPdfExport: true,
    allowPaging: true,
    height: 220,
    pageSettings: {pageSize: 7},
    toolbar: ['PdfExport'],
    treeColumnIndex: 1,
    columns: [
            { field: 'taskID', headerText: 'Task ID', width: 90, textAlign: 'Right' },
            { field: 'taskName', headerText: 'Task Name', width: 180, textAlign: 'Left' },
            {
                field: 'startDate', headerText: 'Start Date', width: 90, textAlign: 'Right', type: 'date', format: 'yMd'
            },
            { field: 'duration', headerText: 'Duration', width: 80, textAlign: 'Right' }
    ]
});

treeGridObj.appendTo('#TreeGrid');
treeGridObj.toolbarClick = (args: Object) => {
if (args['item'].text === 'PDF Export') {
        let exportProperties: PdfExportProperties = {
            theme: {
                header: {
                    fontColor: '#64FA50', fontName: 'Calibri', fontSize: 17, bold: true, border: { color: '#64FA50', lineStyle: 'Thin' }
                },
                record: {
                    fontColor: '#64FA50', fontName: 'Calibri', fontSize: 17, bold: true
                }
            }
        };
        treeGridObj.pdfExport(exportProperties);
    }
}

```

{% endtab %}

> By default, material theme is applied to exported PDF document.

## Custom data source

PDF export provides an option to define datasource dynamically before exporting. To export data dynamically, define the `dataSource` in `exportProperties`

{% tab template="treegrid/pdfexport",es5Template="exportcustom" %}

```typescript

import { TreeGrid, Page, Toolbar, PdfExport, PdfExportProperties } from '@syncfusion/ej2-treegrid';
import { sampleData } from './datasource.ts';

TreeGrid.Inject(Page, Toolbar, PdfExport);

let treeGridObj: TreeGrid = new TreeGrid({
    dataSource: sampleData,
    childMapping: 'subtasks',
    allowPdfExport: true,
    allowPaging: true,
    height: 220,
    pageSettings: {pageSize: 7},
    toolbar: ['PdfExport'],
    treeColumnIndex: 1,
    columns: [
            { field: 'taskID', headerText: 'Task ID', width: 90, textAlign: 'Right' },
            { field: 'taskName', headerText: 'Task Name', width: 180, textAlign: 'Left' },
            {
                field: 'startDate', headerText: 'Start Date', width: 90, textAlign: 'Right', type: 'date', format: 'yMd'
            },
            { field: 'duration', headerText: 'Duration', width: 80, textAlign: 'Right' }
    ]
});

treeGridObj.appendTo('#TreeGrid');
treeGridObj.toolbarClick = (args: Object) => {
if (args['item'].text === 'PDF Export') {
        let exportProperties: PdfExportProperties = {
            dataSource: sampleData,
        };
        treeGridObj.pdfExport(exportProperties);
    }
}


```

{% endtab %}

> You can refer to our [`JavaScript Tree Grid`](https://www.syncfusion.com/javascript-ui-controls/js-tree-grid) feature tour page for its groundbreaking feature representations. You can also explore our JavaScript Tree Grid example [`JavaScript Tree Grid example`](https://ej2.syncfusion.com/demos/#/material/tree-grid/treegrid-overview.html) to knows how to present and manipulate data.