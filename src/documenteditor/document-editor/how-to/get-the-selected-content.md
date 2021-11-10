---
title: "How to get the selected content as plain text or SFDT" 
component: "DocumentEditor" 
description: "Learn how to get the selected content from the Syncfusion JavaScript Document Editor component as plain text or SFDT (rich text)." 
---

# How to get the selected content in JavaScript Document Editor component

You can get the selected content from the JavaScript Document Editor component as plain text and SFDT (rich text).

## Get the selected content as plain text

You can use [`text`](../../api/document-editor/selection/#text-code-classlanguage-textstringcode) API to get the selected content as plain text from JavaScript Document Editor component.

The following example code illustrates how to add search in google option in context menu for the selected text.

```typescript
import { DocumentEditorContainer, Toolbar, CustomContentMenuEventArgs } from '@syncfusion/ej2-documenteditor';
import { MenuItemModel } from '@syncfusion/ej2-navigations';

DocumentEditorContainer.Inject(Toolbar);

let container: DocumentEditorContainer = new DocumentEditorContainer({ enableToolbar: true, height: '590px' });

container.serviceUrl = 'https://ej2services.syncfusion.com/production/web-services/api/documenteditor/';

container.appendTo('#container');

//Creating custom menu items
let menuItems: MenuItemModel[] = [
    {
        text: 'Search In Google',
        id: 'search_in_google',
        iconCss: 'e-icons e-de-ctnr-find'
    }];
//Adding custom options
container.documentEditor.contextMenu.addCustomMenu(menuItems, false);
//To handle contextmenu select event
container.documentEditor.customContextMenuSelect = (args: CustomContentMenuEventArgs): void => {
    let item: string = args.id;
    let id: string = container.documentEditor.element.id;
    switch (item) {
        case id + 'search_in_google':
            // To get the selected content as plain text
            let searchContent: string = container.documentEditor.selection.text;
            if (!container.documentEditor.selection.isEmpty && /\S/.test(searchContent)) {
                window.open('http://google.com/search?q=' + searchContent);
            }
            break;
    }
};
```

You can add the following custom options using this API,

* Save or export the selected text as text file.
* Search the selected text in Google or other search engines.
* Show synonyms for the selected word in context menu and replace with selected synonym using the setter method of same API.

## Get the selected content as SFDT (rich text)

You can use [`sfdt`](../../api/document-editor/selection/#sfdt-code-classlanguage-textstringcode) API to get the selected content as plain text from JavaScript Document Editor component.

The following example code illustrates how to get the content of a bookmark and export it as SFDT.

```typescript
import {  DocumentEditorContainer, Toolbar } from '@syncfusion/ej2-documenteditor';

DocumentEditorContainer.Inject(Toolbar);

let container: DocumentEditorContainer = new DocumentEditorContainer({ enableToolbar: true, height: '590px' });

container.serviceUrl = 'https://ej2services.syncfusion.com/production/web-services/api/documenteditor/';

container.appendTo('#container');

// To insert text in cursor position
container.documentEditor.editor.insertText('Document editor');
// To select all the content in document
container.documentEditor.selection.selectAll();
// Insert bookmark to selected content
container.documentEditor.editor.insertBookmark('Bookmark1');
//Select the bookmark
container.documentEditor.selection.selectBookmark('Bookmark1');
 // To get the selected content as sfdt
 let selectedContent: string = container.documentEditor.selection.sfdt;
 // Insert the sfdt content in cursor position using paste API
 container.documentEditor.editor.paste(selectedContent);

```

You can add the following custom options using this API,

* Save or export the selected content as SFDT file.
* Get the content of a bookmark in Word document as SFDT by selecting a bookmark using [`selectbookmark`](../../api/document-editor/editor/#selectbookmark) API.
* Create template content that can be inserted to multiple documents in cursor position using [`paste`](../../api/document-editor/editor/#paste) API.