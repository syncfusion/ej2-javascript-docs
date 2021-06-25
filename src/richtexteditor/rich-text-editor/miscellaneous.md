---
title: "Rich text editor Miscellaneous"
component: "Rich Text Editor"
description: "This section for Syncfusion JavaScript Rich Text Editor control explains on how to directly edit HTML code via `Source View` in the text area."
---

# Miscellaneous

## Placeholder

Specifies the placeholder for the Rich Text Editor’s content used when the Rich Text Editor body is empty through the [placeholder](../api/rich-text-editor/#placeholder) property.

Through the `e-rte-placeholder` class to define our custom font family, font color, and styles to the placeholder text.

```typescript

.e-richtexteditor .e-rte-placeholder {
    font-family: monospace;
}

```

The below sample demonstrates the placeholder option in Rich Text Editor.

{% tab template="rich-text-editor/getting-started", es5Template="placeholder" %}

```typescript

import { enableRipple } from '@syncfusion/ej2-base';
enableRipple(true);
/**
 * Rich Text Editor default sample
 */
import { RichTextEditor, Toolbar, Link, Image, HtmlEditor, QuickToolbar, Count } from '@syncfusion/ej2-richtexteditor';
RichTextEditor.Inject(Toolbar, Link, Image, HtmlEditor, QuickToolbar, Count);

let defaultRTE: RichTextEditor = new RichTextEditor({ placeholder:'Type Something' });
defaultRTE.appendTo('#defaultRTE');

```

{% endtab %}

## Character count

The Rich Text Editor automatically counts the number of characters in the content are while typing using the  [showCharCount](../api/rich-text-editor/#showcharcount) property. The characters count displayed at the bottom of the editor. You can limit the number of characters in your content using the [maxLength](../api/rich-text-editor/#maxlength) property. By default, the editor sets the characters limit value is infinity.

The character count color will be modified based on the characters in the Rich Text Editor.

| Status | Description |
|----------------|---------|
| normal | Till 70% of given maxLength count reach, character count color is black.|
| warning | Once the number of character count in the Rich Text Editor reached 70% of given maxLength count, the character count color will be orange, indicating that, the Rich Text Editor value going to reach the maximum count.|
| error | Once the number of character count in the Rich Text Editor reached 90% of given maxLength count, the character count color will be red, indicating that, the Rich Text Editor value reached the maximum count.|

To create Rich Text Editor with [showCharCount](../api/rich-text-editor/#showcharcount) feature, inject the Count module to the RTE using the `RichTextEditor.Inject(Count)` method.

{% tab template="rich-text-editor/getting-started", es5Template="count" %}

```typescript

import { enableRipple } from '@syncfusion/ej2-base';
enableRipple(true);
/**
 * Rich Text Editor default sample
 */
import { RichTextEditor, Toolbar, Link, Image, HtmlEditor, QuickToolbar, Count } from '@syncfusion/ej2-richtexteditor';
RichTextEditor.Inject(Toolbar, Link, Image, HtmlEditor, QuickToolbar, Count);

let defaultRTE: RichTextEditor = new RichTextEditor({ showCharCount: true, maxLength: 2000 });
defaultRTE.appendTo('#defaultRTE');

```

{% endtab %}

## Code view

Rich Text Editor includes the ability for users to directly edit HTML code via `Source View` in the text area. If you made any modification in Source view directly, the changes will be reflected in the Rich Text Editor's content. So, the users will have more flexibility over the content they have created.

{% tab template="rich-text-editor/code-mirror", es5Template="code-mirror" %}

```typescript

import { addClass, removeClass, Browser } from '@syncfusion/ej2-base';
import { RichTextEditor, Toolbar, Link, Image, Count, HtmlEditor, QuickToolbar } from '@syncfusion/ej2-richtexteditor';
RichTextEditor.Inject(Toolbar, Link, Image, Count, HtmlEditor, QuickToolbar);
import { createElement } from '@syncfusion/ej2-base';

let defaultRTE: RichTextEditor = new RichTextEditor({ toolbarSettings: {
  items: ['SourceCode']},
  showCharCount: true,
  actionComplete: actionCompleteHandler});
defaultRTE.appendTo('#defaultRTE');

let myCodeMirror: any;

function mirrorConversion(e?: any): void {
  let id: string = defaultRTE.getID() + 'mirror-view';
  let textArea: HTMLElement = defaultRTE.contentModule.getEditPanel() as HTMLElement;
  let mirrorView: HTMLElement = defaultRTE.element.querySelector('#' + id) as HTMLElement;
  let charCount: HTMLElement = defaultRTE.element.querySelector('.e-rte-character-count') as HTMLElement;
  if (e.targetItem === 'Preview') {
      textArea.style.display = 'block';
      mirrorView.style.display = 'none';
      textArea.innerHTML = myCodeMirror.getValue();
      charCount.style.display = 'block';
  } else {
      if (!mirrorView) {
          mirrorView = createElement('div', { className: 'e-content' });
          mirrorView.id = id;
          textArea.parentNode.appendChild(mirrorView);
      } else {
          mirrorView.innerHTML = '';
      }
      textArea.style.display = 'none';
      mirrorView.style.display = 'block';
      renderCodeMirror(mirrorView, defaultRTE.value);
      charCount.style.display = 'none';
  }
}

function renderCodeMirror(mirrorView: HTMLElement, content: string): void {
  myCodeMirror = CodeMirror(mirrorView, {
      value: content,
      lineNumbers: true,
      mode: 'text/html',
      lineWrapping: true,

  });
}

function actionCompleteHandler(e: any): void {
    if (e.targetItem && (e.targetItem === 'SourceCode' || e.targetItem === 'Preview')) {
        this.sourceCodeModule.getPanel().style.display = 'none';
        mirrorConversion(e);
    } else {
        setTimeout(() => { defaultRTE.toolbarModule.refreshToolbarOverflow(); }, 400);
    }
}

```

{% endtab %}

## Undo/Redo Manager

Undo and redo tools allow you to edit the text by disregard/cancel the recently made changes and restore it to previous state. It is a useful tool to restore the performed action which got changed by mistake. By default, upto 30 actions can be undo/redo in the editor.

To undo and redo operations, do one of the following:

* Press the undo/redo button on the toolbar
* Press the `Ctrl + Z`/`Ctrl + Y` combination on the keyboard

Customize the undo/redo step count using [`undoRedoSteps`](../api/rich-text-editor/#undoredosteps) property. By default, undo/redo actions take `300ms` time interval for store the action to the `undoRedoManager`. The time interval can be customized by using the  [`undoRedoTimer`](../api/rich-text-editor/#undoredotimer).

{% tab template="rich-text-editor/getting-started", es5Template="undo-redo" %}

```typescript

import { enableRipple } from '@syncfusion/ej2-base';
enableRipple(true);
/**
 * Rich Text Editor default sample
 */
import { RichTextEditor, Toolbar, Link, Image, HtmlEditor, QuickToolbar } from '@syncfusion/ej2-richtexteditor';
RichTextEditor.Inject(Toolbar, Link, Image, HtmlEditor, QuickToolbar);


let defaultRTE: RichTextEditor = new RichTextEditor({
    height: 340,
    toolbarSettings: {
        items: ['Undo', 'Redo']},
    undoRedoSteps: 50,
    undoRedoTimer: 400
});

defaultRTE.appendTo('#defaultRTE');

```

{% endtab %}

## Prevention of cross-site scripting (XSS)

The Rich Text Editor allows the users to edit the content with security by preventing cross-site
scripting (XSS). By default, provided built-in support to remove the elements from editor content, which cause XSS
attack. The editor removes the elements based on the attributes if it is possible to execute script.

In the following sample, removed `script` tag and `onmouseover` attribute from content of the Rich Text Editor.

{% tab template="rich-text-editor/xss-attack", es5Template="xss-attack" %}

```typescript

import { enableRipple } from '@syncfusion/ej2-base';
enableRipple(true);

/**
 * Prevention of XSS attack sample
 */
import { RichTextEditor, Toolbar, Link, Image, HtmlEditor, QuickToolbar } from '@syncfusion/ej2-richtexteditor';
RichTextEditor.Inject(Toolbar, Link, Image, HtmlEditor, QuickToolbar);

let rteValue: string = `<div onmouseover='javascript:alert(1)'>Prevention of Cross Sit Scripting (XSS) </div> <script>alert('hi')</script>`;

let defaultRTE: RichTextEditor = new RichTextEditor({
    value: rteValue
 });
defaultRTE.appendTo('#defaultRTE');

```

{% endtab %}

> It is only applicable to editorMode as HTML.

### Custom cross-site scripting

You can also filter the elements and attributes additionally, which cause the XSS attack through
[`beforeSanitizeHtml`](../api/rich-text-editor/#beforesanitizehtml) event. Return the value from the event argument `helper` function to apply in the editor. To prevent the built-in support and make own cross-site scripting rules, set `cancel` argument to true.

The following sample demonstrates how to filter `script` tag from value.

{% tab template="rich-text-editor/xss-attack-event", es5Template="xss-attack-event" %}

```typescript

import { enableRipple } from '@syncfusion/ej2-base';
enableRipple(true);

/**
 * Custom cross-site scripting sample
 */
import { RichTextEditor, Toolbar, Link, Image, HtmlEditor, QuickToolbar, BeforeSanitizeHtmlArgs } from '@syncfusion/ej2-richtexteditor';
import { detach } from '@syncfusion/ej2-base';
RichTextEditor.Inject(Toolbar, Link, Image, HtmlEditor, QuickToolbar);

let rteValue: string = `<div>Prevention of Cross Sit Scripting (XSS) </div> <script>alert('hi')</script>`;

let defaultRTE: RichTextEditor = new RichTextEditor({
    value: rteValue,
     beforeSanitizeHtml: (e: BeforeSanitizeHtmlArgs) => {
      e.helper = (value: string) => {
        e.cancel = true;
        let temp: HTMLElement = document.createElement('div');
        temp.innerHTML = value;
        let scriptTag: HTMLElement = temp.querySelector('script');
        if (scriptTag) {
            detach(scriptTag);
        }
        return temp.innerHTML;
      }
  }
 });
defaultRTE.appendTo('#defaultRTE');

```

{% endtab %}

## Resizable support

This feature allows the editor to be resized dynamically. The users can enable or disable this feature using the `enableResize` property in the Rich Text Editor. If `enableResize` is set to true, the Rich Text Editor component creates grip at the bottom right corner, which allows resizing the component in the diagonal direction. The following sample demonstrates the resizable feature.

### Enabling the resizable support

To render the Rich Text Editor in the resizable mode, set the `enableResize` property to true. The above feature is built as module and hence the `Resize` module needs to be included in your application.

{% tab template="rich-text-editor/toolbar", es5Template="resizable" %}

```typescript

import { RichTextEditor, Toolbar, Link, Image, HtmlEditor, QuickToolbar, Resize } from '@syncfusion/ej2-richtexteditor';
RichTextEditor.Inject(Toolbar, Link, Image, HtmlEditor, QuickToolbar, Resize);

let defaultRTE: RichTextEditor = new RichTextEditor({
    enableResize: true
});
defaultRTE.appendTo('#defaultRTE');

```

{% endtab %}

### Specifying the Minimum and Maximum width and height for Resize

To have a restricted resizable area for the Rich Text Editor, you need to specify the min-width, max-width, min-height, and max-height CSS properties for the control's wrapper element. By default, the control is capable of resizing upto the current viewport. The `e-richtexteditor` CSS class will be available in the component's wrapper and can be used for applying the above mentioned styles.

```CSS

.e-richtexteditor {
    min-width: 200px;
    max-width: 800px;
    min-height: 100px;
    max-height: 300px;
}

```

{% tab template="rich-text-editor/resizable", es5Template="resizable" %}

```typescript

import { RichTextEditor, Toolbar, Link, Image, HtmlEditor, QuickToolbar, Resize } from '@syncfusion/ej2-richtexteditor';
RichTextEditor.Inject(Toolbar, Link, Image, HtmlEditor, QuickToolbar, Resize);

let defaultRTE: RichTextEditor = new RichTextEditor({
    enableResize: true
});
defaultRTE.appendTo('#defaultRTE');

```

{% endtab %}

## Number and Bullet Format Lists

This feature allows the user to change the appearance of the Numbered and Bulleted lists. Users can also apply different numbering or bullet formats lists such as lowercase greek, upper Alpha, square and circles. You can also customize the style type of the lists to be populated in the dropdown from the toolbar by using the `numberFormatList` and `bulletFormatList` properties in the Rich Text Editor.

{% tab template="rich-text-editor/format-lists", es5Template="format-lists" %}

```typescript

import { enableRipple } from '@syncfusion/ej2-base';
enableRipple(true);
/**
 * Rich Text Editor default sample
 */
import { RichTextEditor, Toolbar, Link, Image, HtmlEditor, QuickToolbar } from '@syncfusion/ej2-richtexteditor';
RichTextEditor.Inject(Toolbar, Link, Image, HtmlEditor, QuickToolbar);


let defaultRTE: RichTextEditor = new RichTextEditor({
    toolbarSettings: {
        items: ['NumberFormatList', 'BulletFormatList']},
});

defaultRTE.appendTo('#defaultRTE');

```

{% endtab %}