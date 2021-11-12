---
title: "Customize the text search color"
component: "PDF Viewer"
description: "Learn how to customize the text search color programmatically for PDF Viewer control."
---

# Customize the text search color

The PDF Viewer library allows you to customize the color of the search text in the loaded PDF Document using the following properties of **TextSearchColorSettings** modules.

* [**searchColor**](https://ej2.syncfusion.com/javascript/documentation/api/pdfviewer/textSearchColorSettings/#searchcolor)
* [**searchHighlightColor**](https://ej2.syncfusion.com/javascript/documentation/api/pdfviewer/textSearchColorSettings/#searchhighlightcolor)

**Step 1:** Follow the steps provided in the [link](https://ej2.syncfusion.com/javascript/documentation/pdfviewer/getting-started/) to create simple PDF Viewer sample.

**Step 2:** Add the following code snippet to customize the text search color.

```html

<button id="search">SearchText</button>
<button id="searchNext">SearchNext</button>
<button id="searchPervious">searchPervious</button>
<button id="searchCancel">CancelSearch</button>

```

```javascript

    viewer.enableTextSearch = true;
    // customize the textSeach color
    viewer.textSearchColorSettings.searchColor = 'Blue';
    viewer.textSearchColorSettings.searchHighlightColor ='Red';
    document.getElementById('search').addEventListener('click', ()=> {
       viewer.textSearchModule.searchText('pdf',false);
    });
    document.getElementById('searchNext').addEventListener('click', ()=> {
       viewer.textSearchModule.searchNext();
    });
    document.getElementById('searchPervious').addEventListener('click', ()=> {
       viewer.textSearchModule.searchPrevious();
    });
    document.getElementById('searchCancel').addEventListener('click', ()=> {
       viewer.textSearchModule.cancelTextSearch();
    });

```

Find the Sample [how to customize the text search color](https://stackblitz.com/edit/glhn5g?devtoolsheight=33&file=index.js)