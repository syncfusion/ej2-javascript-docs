---
title: "Rich text editor KeyBoard interaction"
component: "Rich Text Editor"
description: "This section for Syncfusion JavaScript Rich Text Editor control explains keyboard accessibility that includes shortcuts to interact with the component."
---

# Keyboard support

The editor has full keyboard accessibility that includes shortcuts to open and other actions with toolbar items, drop-down lists, and dialogs.

## HTML formation shortcut key

You can use the following key shortcuts when the Rich Text Editor renders with `HTML` [`editMode`](../api/rich-text-editor/#editormode).

| Actions | Keyboard shortcuts |
|----------------|---------|
| Toolbar focus | <kbd>alt</kbd> + <kbd>f10</kbd> |
| Insert link | <kbd>ctrl</kbd> + <kbd>k</kbd> |
| Insert image | <kbd>ctrl</kbd> + <kbd>shift</kbd> + <kbd>i</kbd> |
| Insert table | <kbd>ctrl</kbd> + <kbd>shift</kbd> + <kbd>e</kbd> |
| Undo | <kbd>ctrl</kbd> + <kbd>z</kbd> |
| Redo | <kbd>ctrl</kbd> + <kbd>y</kbd> |
| Copy | <kbd>ctrl</kbd> + <kbd>c</kbd> |
| Cut | <kbd>ctrl</kbd> + <kbd>x</kbd> |
| Paste| <kbd>ctrl</kbd> + <kbd>v</kbd> |
| Bold| <kbd>ctrl</kbd> + <kbd>b</kbd> |
| Italic| <kbd>ctrl</kbd> + <kbd>i</kbd> |
| Underline| <kbd>ctrl</kbd> + <kbd>u</kbd> |
| Strikethrough| <kbd>ctrl</kbd> + <kbd>shift</kbd> + <kbd>s</kbd> |
| Uppercase| <kbd>ctrl</kbd> + <kbd>shift</kbd> + <kbd>u</kbd> |
| Lowercase| <kbd>ctrl</kbd> + <kbd>shift</kbd> + <kbd>l</kbd> |
| Superscript| <kbd>ctrl</kbd> + <kbd>shift</kbd> + <kbd>=</kbd> |
| Subscript| <kbd>ctrl</kbd> + <kbd>=</kbd> |
| Indents| <kbd>ctrl</kbd> + <kbd>]</kbd> |
| Outdents| <kbd>ctrl</kbd> + <kbd>[</kbd> |
| HTML source | <kbd>ctrl</kbd> + <kbd>shift</kbd> + <kbd>h</kbd> |
| Fullscreen| <kbd>ctrl</kbd> + <kbd>shift</kbd> + <kbd>f</kbd> |
| Justify center| <kbd>ctrl</kbd> + <kbd>e</kbd> |
| Justify full | <kbd>ctrl</kbd> + <kbd>j</kbd> |
| Justify left | <kbd>ctrl</kbd> + <kbd>l</kbd> |
| Justify right | <kbd>ctrl</kbd> + <kbd>r</kbd> |
| Clear format | <kbd>ctrl</kbd> + <kbd>shift</kbd> + <kbd>r</kbd> |
| Ordered list | <kbd>ctrl</kbd> + <kbd>shift</kbd> + <kbd>o</kbd> |
| Unordered list | <kbd>ctrl</kbd> + <kbd>alt</kbd> + <kbd>o</kbd> |

{% tab template="rich-text-editor/getting-started", es5Template="keyConfig" %}

```typescript

import { RichTextEditor, Toolbar, HtmlEditor } from '@syncfusion/ej2-richtexteditor';

RichTextEditor.Inject(Toolbar, HtmlEditor);

let defaultRTE: RichTextEditor = new RichTextEditor({
    toolbarSettings: {
        items: ['Bold', 'Italic', 'Underline', 'StrikeThrough',
        'FontName', 'FontSize', 'FontColor', 'BackgroundColor',
        'LowerCase', 'UpperCase', '|',
        'Formats', 'Alignments', 'OrderedList', 'UnorderedList',
        'Outdent', 'Indent', '|',
        'CreateLink', 'Image', '|', 'ClearFormat', 'Print',
        'SourceCode', 'FullScreen', '|', 'Undo', 'Redo']
    }});
defaultRTE.appendTo('#defaultRTE');

document.onkeyup = function (e) {
    if (e.altKey && e.keyCode === 84 /* t */) {
        // press alt+t to focus the component.
        defaultRTE.focusIn();
    }
};

```

{% endtab %}

## Markdown formation shortcut key

You can use the following key shortcuts when the Rich Text Editor renders with `Markdown` [editMode](../api/rich-text-editor/#editormode).

| Actions | Keyboard shortcuts |
|----------------|---------|
| Toolbar focus| <kbd>alt</kbd> + <kbd>f10</kbd> |
| Insert link| <kbd>ctrl</kbd> + <kbd>k</kbd> |
| Insert image| <kbd>ctrl</kbd> + <kbd>shift</kbd> + <kbd>i</kbd> |
| Insert table| <kbd>ctrl</kbd> + <kbd>shift</kbd> + <kbd>e</kbd> |
| Undo| <kbd>ctrl</kbd> + <kbd>z</kbd> |
| Redo| <kbd>ctrl</kbd> + <kbd>y</kbd> |
| Copy| <kbd>ctrl</kbd> + <kbd>c</kbd> |
| Cut| <kbd>ctrl</kbd> + <kbd>x</kbd> |
| Paste| <kbd>ctrl</kbd> + <kbd>v</kbd> |
| Bold| <kbd>ctrl</kbd> + <kbd>b</kbd> |
| Italic| <kbd>ctrl</kbd> + <kbd>i</kbd> |
| Strikethrough| <kbd>ctrl</kbd> + <kbd>shift</kbd> + <kbd>s</kbd> |
| Uppercase| <kbd>ctrl</kbd> + <kbd>shift</kbd> + <kbd>u</kbd> |
| Lowercase| <kbd>ctrl</kbd> + <kbd>shift</kbd> + <kbd>l</kbd> |
| Superscript| <kbd>ctrl</kbd> + <kbd>shift</kbd> + <kbd>=</kbd> |
| Subscript| <kbd>ctrl</kbd> + <kbd>=</kbd> |
| Fullscreen| <kbd>ctrl</kbd> + <kbd>shift</kbd> + <kbd>f</kbd> |
| Ordered list| <kbd>ctrl</kbd> + <kbd>shift</kbd> + <kbd>o</kbd> |
| Unordered list| <kbd>ctrl</kbd> + <kbd>alt</kbd> + <kbd>o</kbd> |

{% tab template="rich-text-editor/markdown", es5Template="markdown-keyConfig" %}

```typescript

import { RichTextEditor, Toolbar, MarkdownEditor } from '@syncfusion/ej2-richtexteditor';

RichTextEditor.Inject(Toolbar, MarkdownEditor);

let defaultRTE: RichTextEditor = new RichTextEditor({
    editorMode: 'Markdown',
    toolbarSettings: {
        items: ['Bold', 'Italic', 'StrikeThrough', '|',
            'Formats', 'OrderedList', 'UnorderedList', '|',
            'CreateLink', 'Image', '|','Undo', 'Redo']
    }});
defaultRTE.appendTo('#defaultRTE');

document.onkeyup = function (e) {
    if (e.altKey && e.keyCode === 84 /* t */) {
        // press alt+t to focus the component.
        defaultRTE.focusIn();
    }
};

```

{% endtab %}

## Custom key config

Customize the key config for the keyboard interaction of Rich Text Editor, using the [`keyConfig`](../api/rich-text-editor/#keyconfig) property.

In the following sample, customize the cut, copy, paste toolbar action with `ctrl+1`, `ctrl+2`, `ctrl+3`, respectively.

{% tab template="rich-text-editor/getting-started", es5Template="custom-keyconfig" %}

```typescript

import { RichTextEditor, Toolbar, HtmlEditor } from '@syncfusion/ej2-richtexteditor';

RichTextEditor.Inject(Toolbar, HtmlEditor);

let defaultRTE: RichTextEditor = new RichTextEditor({
    toolbarSettings: {
        items: ['Bold', 'Italic', 'Underline', 'StrikeThrough',
        'FontName', 'FontSize', 'FontColor', 'BackgroundColor',
        'LowerCase', 'UpperCase', '|',
        'Formats', 'Alignments', 'OrderedList', 'UnorderedList',
        'Outdent', 'Indent', '|',
        'CreateLink', 'Image', '|', 'ClearFormat', 'Print',
        'SourceCode', 'FullScreen', '|', 'Undo', 'Redo']
    },
    keyConfig:{
        'copy': 'ctrl+1',
        'cut': 'ctrl+2',
        'paste': 'ctrl+3'
    }
});
defaultRTE.appendTo('#defaultRTE');

document.onkeyup = function (e) {
    if (e.altKey && e.keyCode === 84 /* t */) {
        // press alt+t to focus the component.
        defaultRTE.focusIn();
    }
};

```

{% endtab %}

## See Also

* [Globalization](./globalization/)
* [Accessibility](./accessibility/)
* [How to customize the toolbar items shortcut key](./how-to/shortcut-key/)
* [How to customize the saving operation](./how-to/save/)