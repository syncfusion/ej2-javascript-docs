---
title: "Rich text editor Markdown"
component: "Rich Text Editor"
description: "This section for Syncfusion JavaScript Rich Text Editor control explains the markdown editing and custom formatting."
---

# Markdown

When you format the word in Markdown format, you should add Markdown syntax to the word to indicate the words and phrases that looks different from each other.

Rich Text Editor supports markdown editing when the [`editorMode`](../api/rich-text-editor/#editormode) set as **markdown** and using both *keyboard interaction* and *toolbar action*, you can apply the formatting to text.

> To create Rich Text Editor with Markdown editing feature, inject the [MarkdownEditor](../api/rich-text-editor/#markdowneditor) module to the Rich Text Editor using the `RichTextEditor.Inject(MarkdownEditor)` method.

## Supported Commands

The Javascript Markdown editor supports the following commands to format the markdown content:

|Commands|Syntax| Description |
|--------|------------------------------------------|------------|
| Bold | Sample content for `**`bold text`**`. | For bold, add `**` or `__` to front and back of the text. | For order list, precede each line with a number. |
| Italic | Sample content for `*`Italic text`*`. | For Italic, add `*` or `_` to front and back of the text. |
| Bold and Italics | Sample content for `***`bold and Italic text`***`. | For bold and Italics, add `***` to the front and back of the text. |
| Heading 1 | `#` Heading 1 content | For heading 1, add `#` to start of the line. |
| Heading 2 | `##` Heading 2 content | For heading 2, add `##` to start of the line. |
| Heading 3 | `###` Heading 3 content | For heading 3, add `###` to start of the line. |
| Heading 4 | `####` Heading 4 content | For heading 4, add `####` to start of the line. |
| Heading 5 | `#####` Heading 5 content | For heading 5, add `#####` to start of the line. |
| Heading 6 | `######` Heading 6 content | For heading 6, add `######` to start of the line. |
| Line Break | First line `<br>`Second line | For line break, press enter two times (or) add `<br>` in between the first and the second line. |
| Blockquotes | `>` Blockquotes text | For blockquotes, add `>` to start of the line. |
| Strike Through | Sample content for `~~`strike through text`~~`. | For strike through, add `~~` to front and back of the text. |
| Code (Single line) | \`Single line code\` | For single line code, add \` to front and back of the text. |
| Code block (Multi Line) | \`\`\`<br>Multi line code text<br>Multi line code text<br>\`\`\` | For multiple line code, add \`\`\` in the new line before and after the content. |
| Subscript | `<sub>`Subscript text`</sub>` | For subscript, add `<sub>` to the front and `</sub>` to the back of the text. |
| Superscript | `<sup>`Superscript text`</sup>` | For superscript, add `<sup>` to the front and `</sup>` to the back of the text. |
| Ordered List | `1.` First<br>`1.` Second | For ordered list, preceding one or more lines of text with `1.` |
| Unordered List | `*` First<br>`*` second | For unordered list, preceding one or more lines of text with `*`. |
| Links | **Link text without title text**<br>`[` Link text `](`URL`)`<br> **Link text with title text**<br>`[` Link text `](`URL , “title text”`)` | Create an inline link by wrapping link text in brackets `[ ]`, and then wrapping the URL as first parameter and title as second parameter in the parentheses `()`.<br>**Note:** The title text is optional, if needed it can be given manually.|
| Table | `|` Heading 1 `|` Heading 2 `|`<br>`|---------|---------|`<br>`|` Col A1 `|` Col A2 `|`<br>`|` Col B1 `|` Col B2 `|` | Create a table using the pipes and underscores as given in the syntax to create 2 x 2 table. |
| Horizontal Line | `***` (three asterix in new line)<br>(or)<br>`___` (three underscores in new line) | For horizontal line, add `***` or `___` to the start of the new line. |
| Image | `![](`URL path`)` | Create an image by wrapping the image source in parentheses `()`. |
| Image with alternate text | `![` alternate text `](`URL path`)` | Create an image with alternate text by wrapping an alternative text in brackets `[]`, and then link of the image source in parentheses `()`.<br>**Note:** When inserting the image using toolbar, the alternate text cannot be provided that needs to be given manually. |
| Escape tick marks supported | Sample text content with `**`bold and `**`not bold`**` text can be in the same line.`**` | In the syntax, the whole content is made as bold where the content `not bold` can be made as normal text by adding the bold syntax to the start and end of the respective text. Likewise you can do the same for various inline commands. |
| Escape Character | `\(`any syntax`)` | Escape any markdown syntax by prefix `\` to the syntax.<br>Example:<br>`\**`Bold text`**`|
| HTML Entities | Copyright: &copy; - `&copy;` <br>Trade mark: &trade; - `&trade;`<br>Registered: &reg; - `&reg;`<br>Ampersand: &amp; - `&amp;`<br>Less than: &lt; - `&lt;`<br>Greater than: &gt; - `&gt;` | For HTML entities, add & and ; to the front and back of the respective entities. |

> The above listed commands alone are supported in Syncfusion Markdown editor. For other unsupported commands, you can achieve using the HTML tags in Markdown editor. The foot notes, definitions, math, and check list markdown syntax are also not supported.

## Markdown to HTML

The Rich Text Editor allows you to preview markdown changes immediately using preview. In this sample, the third-party library [`Marked`](https://marked.js.org/) is used to convert markdown into HTML content.

This sample demonstrates how to preview markdown changes in Rich Text Editor. Type or edit the display text, and apply format to view the preview of markdown. The [actionComplete](../api/rich-text-editor/#actioncomplete) event can be used to convert Markdown to HTML.

This sample demonstrates how to preview markdown changes in Rich Text Editor. Type or edit the display text and apply format to view the preview of markdown.

{% tab template="rich-text-editor/markdown", es5Template="basic" %}

```typescript

import { enableRipple } from '@syncfusion/ej2-base';
enableRipple(true);

import { RichTextEditor, Link, Image, MarkdownEditor, Toolbar, QuickToolbar } from '@syncfusion/ej2-richtexteditor';
import { createElement, KeyboardEventArgs, isNullOrUndefined, addClass, removeClass, Browser } from '@syncfusion/ej2-base';

RichTextEditor.Inject(Link, Image, MarkdownEditor, Toolbar, QuickToolbar);

let textArea: HTMLTextAreaElement;
let mdsource: HTMLElement;
let mdSplit: HTMLElement;
let htmlPreview: HTMLElement;

let defaultRTE: RichTextEditor = new RichTextEditor({
    height: 340, editorMode: 'Markdown',
    toolbarSettings: {
        items: ['Bold', 'Italic', 'StrikeThrough', '|', 'Formats', 'OrderedList', 'UnorderedList', '|', 'CreateLink', 'Image', '|',
            { tooltipText: 'Preview', template: '<button id="preview-code" class="e-tbar-btn e-control e-btn e-icon-btn">' +
                '<span class="e-btn-icon e-md-preview e-icons"></span></button>' }, '|', 'Undo', 'Redo']
    },
    created: () => {
        textArea = defaultRTE.contentModule.getEditPanel() as HTMLTextAreaElement;
        textArea.addEventListener('keyup', (e: KeyboardEventArgs) => { markDownConversion(); });
        let rteObj: RichTextEditor = defaultRTE;
        mdsource = document.getElementById('preview-code');
        mdsource.addEventListener('click', (e: MouseEvent) => {
            fullPreview({ mode: true, type: 'preview' });
            if ((e.currentTarget as HTMLElement).classList.contains('e-active')) {
                defaultRTE.disableToolbarItem(['Bold', 'Italic', 'StrikeThrough', '|',
                    'Formats', 'OrderedList', 'UnorderedList', '|',
                    'CreateLink', 'Image', 'Undo', 'Redo']);
            } else {
                defaultRTE.enableToolbarItem(['Bold', 'Italic', 'StrikeThrough', '|',
                    'Formats', 'OrderedList', 'UnorderedList', '|',
                    'CreateLink', 'Image', 'Undo', 'Redo']);
            }
        });
    },
});
defaultRTE.appendTo('#defaultRTE');
function markDownConversion(): void {
    if (mdsource.classList.contains('e-active')) {
        let id: string = defaultRTE.getID() + 'html-preview';
        let htmlPreview: HTMLElement = defaultRTE.element.querySelector('#' + id);
        let rteElement = defaultRTE.contentModule.getEditPanel() as HTMLTextAreaElement;
        let rteValue = rteElement.value;
        htmlPreview.innerHTML = marked((defaultRTE.contentModule.getEditPanel() as HTMLTextAreaElement).value);
    }
}
function fullPreview(e: { [key: string]: string | boolean }): void {
    let id: string = defaultRTE.getID() + 'html-preview';
    htmlPreview = defaultRTE.element.querySelector('#' + id);
    if (mdsource.classList.contains('e-active')) {
        mdsource.classList.remove('e-active');
        mdsource.parentElement.title = 'Preview';
        textArea.style.display = 'block';
        textArea.style.width = '100%';
        htmlPreview.style.display = 'none';
    } else {
        mdsource.classList.add('e-active');
        if (!htmlPreview) {
            htmlPreview = createElement('div', { className: 'e-content' });
            htmlPreview.id = id;
            textArea.parentNode.appendChild(htmlPreview);
        }
        if (e.type === 'preview') {
            textArea.style.display = 'none'; htmlPreview.classList.add('e-pre-source');
        } else {
            htmlPreview.classList.remove('e-pre-source');
            textArea.style.width = '50%';
        }
        htmlPreview.style.display = 'block';
        markDownConversion();
        mdsource.parentElement.title = 'Code View';
    }
}

```

{% endtab %}

## Table

Rich Text Editor allows to insert Markdown table in edit panel with 2 X 2 rows and columns along with the heading.
To use table tool, add the `CreateTable` item in toolbar items.

### Insert table

To insert the table in Rich Text Editor, click the `table` toolbar option to insert the table into Rich Text Editor content and this is the default way in all the devices.
Please refer the below sample and code snippets to add the table in Markdown editor

{% tab template="rich-text-editor/markdown", es5Template="table" %}

```typescript

import { enableRipple } from '@syncfusion/ej2-base';
enableRipple(true);

import { RichTextEditor, Link, Image, MarkdownEditor, Toolbar, QuickToolbar } from '@syncfusion/ej2-richtexteditor';
import { createElement, KeyboardEventArgs, isNullOrUndefined, addClass, removeClass, Browser } from '@syncfusion/ej2-base';

RichTextEditor.Inject(Link, Image, MarkdownEditor, Toolbar, QuickToolbar);

let textArea: HTMLTextAreaElement;
let mdsource: HTMLElement;
let mdSplit: HTMLElement;
let htmlPreview: HTMLElement;

let defaultRTE: RichTextEditor = new RichTextEditor({
    height: 340, editorMode: 'Markdown',
    toolbarSettings: {
        items: ['Bold', 'Italic', 'StrikeThrough', '|', 'Formats', 'OrderedList', 'UnorderedList', '|', 'CreateLink', 'Image', 'CreateTable', '|',
            { tooltipText: 'Preview', template: '<button id="preview-code" class="e-tbar-btn e-control e-btn e-icon-btn">' +
                '<span class="e-btn-icon e-md-preview e-icons"></span></button>' }, '|', 'Undo', 'Redo']
    },
    created: () => {
        textArea = defaultRTE.contentModule.getEditPanel() as HTMLTextAreaElement;
        textArea.addEventListener('keyup', (e: KeyboardEventArgs) => { markDownConversion(); });
        let rteObj: RichTextEditor = defaultRTE;
        mdsource = document.getElementById('preview-code');
        mdsource.addEventListener('click', (e: MouseEvent) => {
            fullPreview({ mode: true, type: 'preview' });
            if ((e.currentTarget as HTMLElement).classList.contains('e-active')) {
                defaultRTE.disableToolbarItem(['Bold', 'Italic', 'StrikeThrough', '|',
                    'Formats', 'OrderedList', 'UnorderedList', '|',
                    'CreateLink', 'Image', 'Undo', 'Redo', 'CreateTable']);
            } else {
                defaultRTE.enableToolbarItem(['Bold', 'Italic', 'StrikeThrough', '|',
                    'Formats', 'OrderedList', 'UnorderedList', '|',
                    'CreateLink', 'Image', 'Undo', 'Redo', 'CreateTable']);
            }
        });
    },
});
defaultRTE.appendTo('#defaultRTE');
function markDownConversion(): void {
    if (mdsource.classList.contains('e-active')) {
        let id: string = defaultRTE.getID() + 'html-preview';
        let htmlPreview: HTMLElement = defaultRTE.element.querySelector('#' + id);
        let rteElement = defaultRTE.contentModule.getEditPanel() as HTMLTextAreaElement;
        let rteValue = rteElement.value;
        htmlPreview.innerHTML = marked((defaultRTE.contentModule.getEditPanel() as HTMLTextAreaElement).value);
    }
}
function fullPreview(e: { [key: string]: string | boolean }): void {
    let id: string = defaultRTE.getID() + 'html-preview';
    htmlPreview = defaultRTE.element.querySelector('#' + id);
    if (mdsource.classList.contains('e-active')) {
        mdsource.classList.remove('e-active');
        mdsource.parentElement.title = 'Preview';
        textArea.style.display = 'block';
        textArea.style.width = '100%';
        htmlPreview.style.display = 'none';
    } else {
        mdsource.classList.add('e-active');
        if (!htmlPreview) {
            htmlPreview = createElement('div', { className: 'e-content' });
            htmlPreview.id = id;
            textArea.parentNode.appendChild(htmlPreview);
        }
        if (e.type === 'preview') {
            textArea.style.display = 'none'; htmlPreview.classList.add('e-pre-source');
        } else {
            htmlPreview.classList.remove('e-pre-source');
            textArea.style.width = '50%';
        }
        htmlPreview.style.display = 'block';
        markDownConversion();
        mdsource.parentElement.title = 'Code View';
    }
}

```

{% endtab %}

### Changing table constants

The Markdown table constants can be changed for the table heading and the column name.

{% tab template="rich-text-editor/markdown", es5Template="table-constants" %}

```typescript

import { enableRipple } from '@syncfusion/ej2-base';
enableRipple(true);

import { RichTextEditor, Link, Image, MarkdownEditor, Toolbar, QuickToolbar } from '@syncfusion/ej2-richtexteditor';
import { createElement, KeyboardEventArgs, isNullOrUndefined, addClass, removeClass, Browser } from '@syncfusion/ej2-base';
import { L10n } from '@syncfusion/ej2-base';
L10n.load({
    'en-US': {
        'richtexteditor': {
            'TableHeadingText': 'Header',
            'TableColText': 'Cell'
         }
     }
});

RichTextEditor.Inject(Link, Image, MarkdownEditor, Toolbar, QuickToolbar);

let textArea: HTMLTextAreaElement;
let mdsource: HTMLElement;
let mdSplit: HTMLElement;
let htmlPreview: HTMLElement;

let defaultRTE: RichTextEditor = new RichTextEditor({
    height: 340, editorMode: 'Markdown',
    toolbarSettings: {
        items: ['Bold', 'Italic', 'StrikeThrough', '|', 'Formats', 'OrderedList', 'UnorderedList', '|', 'CreateLink', 'Image', 'CreateTable', '|',
            { tooltipText: 'Preview', template: '<button id="preview-code" class="e-tbar-btn e-control e-btn e-icon-btn">' +
                '<span class="e-btn-icon e-md-preview e-icons"></span></button>' }, '|', 'Undo', 'Redo']
    },
    created: () => {
        textArea = defaultRTE.contentModule.getEditPanel() as HTMLTextAreaElement;
        textArea.addEventListener('keyup', (e: KeyboardEventArgs) => { markDownConversion(); });
        let rteObj: RichTextEditor = defaultRTE;
        mdsource = document.getElementById('preview-code');
        mdsource.addEventListener('click', (e: MouseEvent) => {
            fullPreview({ mode: true, type: 'preview' });
            if ((e.currentTarget as HTMLElement).classList.contains('e-active')) {
                defaultRTE.disableToolbarItem(['Bold', 'Italic', 'StrikeThrough', '|',
                    'Formats', 'OrderedList', 'UnorderedList', '|',
                    'CreateLink', 'Image', 'Undo', 'Redo', 'CreateTable']);
            } else {
                defaultRTE.enableToolbarItem(['Bold', 'Italic', 'StrikeThrough', '|',
                    'Formats', 'OrderedList', 'UnorderedList', '|',
                    'CreateLink', 'Image', 'Undo', 'Redo', 'CreateTable']);
            }
        });
    },
});
defaultRTE.appendTo('#defaultRTE');
function markDownConversion(): void {
    if (mdsource.classList.contains('e-active')) {
        let id: string = defaultRTE.getID() + 'html-preview';
        let htmlPreview: HTMLElement = defaultRTE.element.querySelector('#' + id);
        let rteElement = defaultRTE.contentModule.getEditPanel() as HTMLTextAreaElement;
        let rteValue = rteElement.value;
        htmlPreview.innerHTML = marked((defaultRTE.contentModule.getEditPanel() as HTMLTextAreaElement).value);
    }
}
function fullPreview(e: { [key: string]: string | boolean }): void {
    let id: string = defaultRTE.getID() + 'html-preview';
    htmlPreview = defaultRTE.element.querySelector('#' + id);
    if (mdsource.classList.contains('e-active')) {
        mdsource.classList.remove('e-active');
        mdsource.parentElement.title = 'Preview';
        textArea.style.display = 'block';
        textArea.style.width = '100%';
        htmlPreview.style.display = 'none';
    } else {
        mdsource.classList.add('e-active');
        if (!htmlPreview) {
            htmlPreview = createElement('div', { className: 'e-content' });
            htmlPreview.id = id;
            textArea.parentNode.appendChild(htmlPreview);
        }
        if (e.type === 'preview') {
            textArea.style.display = 'none'; htmlPreview.classList.add('e-pre-source');
        } else {
            htmlPreview.classList.remove('e-pre-source');
            textArea.style.width = '50%';
        }
        htmlPreview.style.display = 'block';
        markDownConversion();
        mdsource.parentElement.title = 'Code View';
    }
}

```

{% endtab %}

## Custom format

The Rich Text Editor allows you to customize the markdown syntax by overriding its default syntax. Configure the customized markdown syntax using the [`formatter`](../api/rich-text-editor/#formatter) property.

This sample demonstrates how to customize tags of markdown formatting.

For example, apply `+` to Unordered list, apply `1., 2., 3.` to Ordered list, for bold, `__`, and for italic `_`.

{% tab template="rich-text-editor/markdown", es5Template="customformation" %}

```typescript

import { RichTextEditor, Toolbar, Link, Image, MarkdownFormatter, MarkdownEditor, QuickToolbar } from '@syncfusion/ej2-richtexteditor';
RichTextEditor.Inject(Toolbar, Link, Image, MarkdownEditor, QuickToolbar);

let defaultRTE: RichTextEditor = new RichTextEditor({
    height: 340,
    toolbarSettings: {
        items: ['Bold', 'Italic', 'StrikeThrough', '|',
            'Formats', 'OrderedList', 'UnorderedList', '|',
            'CreateLink', 'Image', '|','Undo', 'Redo']
    },
    editorMode: 'Markdown',
    formatter: new MarkdownFormatter({
        listTags: { 'OL': '1., 2., 3.', 'UL': '+ ' },
        formatTags: {
            'Blockquote': '> '
        },
        selectionTags: {'Bold': '__',  'Italic': '_'}
    })
});
defaultRTE.appendTo('#defaultRTE');

```

{% endtab %}

## See Also

* [How to integrate the third party library](./third-party-integration/)
* [How to change the editor mode](./editor-modes/#markdown-editor)