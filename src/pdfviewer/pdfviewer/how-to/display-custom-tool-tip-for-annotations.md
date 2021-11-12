---
title: "Display custom tooltip for annotations using Mouse over event"
component: "PDF Viewer"
description: "Learn how to display custom tooltip for annotations using Mouse over event programmatically for PDF Viewer control."
---

# Display custom tooltip for annotations using Mouse over event

The PDF Viewer library allows you to customize the tooltip display for the annotations using the **annotationMouseover** and **annotationMouseLeave** events.

**Step 1:** Follow the steps provided in the [link](https://ej2.syncfusion.com/javascript/documentation/pdfviewer/getting-started/) to create simple PDF Viewer sample.

**Step 2:** Add the following code snippet to display custom tooltip for the annotations.

```javascript

    viewer.annotationSettings.author = "syncfusion";
    var tooltip = new ej.popups.Tooltip({
        mouseTrail: true,
        opensOn: "Custom"
    });
    viewer.annotationMouseover = function (args) {
        tooltip.appendTo("#pdfViewer_pageDiv_" + (viewer.currentPageNumber - 1));
        tooltip.content = args.annotation.author;
        tooltip.open();
        var ele = document.getElementsByClassName("e-tooltip-wrap")[0];
        ele.style.top = args.Y + 100 + "px";
        ele.style.left = args.X + "px";
    };
    viewer.annotationMouseLeave = function (args) {
        tooltip.close();
    };

```

Find the Sample [how to display custom tooltip for annotations using Mouse over event](https://stackblitz.com/edit/ztmvjx?file=index.js)