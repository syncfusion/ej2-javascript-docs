---
title: "Rich text editor Third Party Integration"
component: "Rich Text Editor"
description: "This section for Syncfusion JavaScript Rich Text Editor control explains how to integrate additional third-party libraries to enhance the content."
---

# Third Party Integration

The Rich Text Editor can be integrated with third-party to suite the application scenario.

## Code-Mirror Integration

Rich Text Editor comes with a basic HTML source editor through view-source property. [`Code mirror`](https://codemirror.net/) plugin can be used to highlight the syntax of HTML. CodeMirror plugin for Rich Text Editor makes editing of HTML source code with a pleasant experience.

Import necessary CSS and JS files of CodeMirror to the HTML page.

Required JS files of code mirror.

```typescript
 <script src="scripts/CodeMirror/codemirror.js" type="text/javascript"></script>
 <script src="scripts/CodeMirror/javascript.js" type="text/javascript"></script>
 <script src="scripts/CodeMirror/css.js" type="text/javascript"></script>
 <script src="scripts/CodeMirror/htmlmixed.js" type="text/javascript"></script>

```

Required CSS file of code mirror.

```typescript
 <link href="scripts/CodeMirror/codemirror.min.css" rel="stylesheet" />

```

Add a custom icon for HTML source editor in the toolbar of Rich Text Editor using template option of [`toolbarSettings`](../api/rich-text-editor/#toolbarsettings) and define the code mirror plugins, and then pass the Rich Text Editor content as argument in [`actionComplete`](../api/rich-text-editor/#actioncomplete) event.

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
  let textArea: HTMLElement = defaultRTE.contentModule.getEditPanel() as HTMLElement;
  let id: string = defaultRTE.getID() + 'mirror-view';
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

## At.js Integration

Rich Text Editor can easily be integrated with [`At.js`](https://github.com/ichord/At.js) library. To display the autocomplete list, type ‘@’.

Include `At.JS` style.

```typescript

 <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/at.js/1.4.0/css/jquery.atwho.min.css">

```

Include At.JS javascript.

```typescript

<script type="text/javascript" src="https://cdnjs.cloudflare.com/ajax/libs/at.js/1.4.0/js/jquery.atwho.min.js"></script>

```

Define the `At.js` configuration

> In below configuration, email id of employees list - email id of employees from the data source.

```typescript

var config = {
    at: "@",
    data: [email id of employees list],
    displayTpl: '<li>${name} <small>${email}</small></li>',
    limit: 200
  }

```

Populate the employee’s email id from local or remote data and set the result to the data of `At.js` configuration.

{% tab template="rich-text-editor/how-to-at-integration", es5Template="at-who" %}

```typescript

import { RichTextEditor, Toolbar, Link, Image, Count, HtmlEditor, QuickToolbar } from '@syncfusion/ej2-richtexteditor';
  RichTextEditor.Inject(Toolbar, Link, Image, Count, HtmlEditor, QuickToolbar);

  // Build data to be used in At.JS config.
  let employeeList: { [key: string]: Object }[] = [
      { id: 'emp01', name: 'Jacob', email: 'jacob@mail.com' },
      { id: 'emp02', name: 'Isabella', email: 'isabella@mail.com' },
      { id: 'emp03', name: 'Ethan', email: 'ethan@mail.com' },
      { id: 'emp04', name: 'Emma', email: 'emma@mail.com' },
      { id: 'emp05', name: 'Michael', email: 'michael@mail.com' },
      { id: 'emp06', name: 'Olivia', email: 'olivia@mail.com' },
      { id: 'emp07', name: 'Jeniffer', email: 'jeniffer@mail.com' }
  ];

  let config: Object = {
      at: "@",
      callbacks: {
        beforeReposition: function (offset) {
            offset.left = this.rect().left - (leftBarWdith + leftPadding);
        }
      },
      data: employeeList,
      displayTpl: '<li>${name} <small>${email}</small></li>',
      limit: 200
  };
let leftBarWdith : number = window.parent.document.getElementById('doc-left-toc').offsetWidth;
let leftPadding : number = +getComputedStyle(window.parent.document.getElementById('md-cnt')).paddingRight.match(/\d/g).join('');
  let defaultRTE: RichTextEditor = new RichTextEditor({
      toolbarSettings: {
          items: ['|', 'Undo', 'Redo', '|',
              'Bold', 'Italic', 'Underline', 'StrikeThrough', '|',
              'FontName', 'FontSize', 'FontColor', 'BackgroundColor', '|',
              'SubScript', 'SuperScript', '|',
              'LowerCase', 'UpperCase', '|',
              'Formats', 'Alignments', '|', 'OrderedList', 'UnorderedList', '|',
              'Outdent', 'Indent', '|', 'CreateLink', '|', 'Image', '|', 'SourceCode']
      },
      placeholder:"Type @ to get the e-mail list",
      created: (args: any) => {
          let textArea: HTMLElement = defaultRTE.contentModule.getEditPanel() as HTMLElement;
          $(textArea).atwho(config); // to get the popup of the email list
          $(textArea).on('keydown', function(e) {
            if(e.keyCode == 13 && $(textArea).atwho('isSelecting'))
              return false
          })
      }
  });
  defaultRTE.appendTo('#defaultRTE');

```

{% endtab %}

## Embed.ly Integration

Rich Text Editor easily integrate with [`Embed.ly`](https://embed.ly/) which is probably the best service when it comes to embed the rich content such as Twitter, Facebook, Instagram and lots of other publishing platform embeds.

```typescript

<script src="https://cdn.embedly.com/widgets/platform.js" charset="UTF-8"></script>

```

In the following sample, the `Embed.ly` class `embedly-card` has been added to `<a>` tag in [`actionComplete`](../api/rich-text-editor/#actioncomplete) event.

{% tab template="rich-text-editor/how-to-embedly-integration", es5Template="embedly" %}

```typescript

import { RichTextEditor, Toolbar, Link, Image, Count, HtmlEditor, QuickToolbar } from '@syncfusion/ej2-richtexteditor';
  RichTextEditor.Inject(Toolbar, Link, Image, Count, HtmlEditor, QuickToolbar);

let defaultRTE: RichTextEditor = new RichTextEditor({
    placeholder:"Click link icon in toolbar to add the desired link",
    toolbarSettings: {
        items: ['createLink']},
        actionComplete: function(args){
          if (<String>args.requestType === 'Links') {
            if (args.elements[0].parentNode && (<Element>args.elements[0].parentNode).tagName === 'A'){
              var emberEle=document.createElement('blockquote'); // to add the link
              emberEle.setAttribute('class', 'embedly-card'); // to add the class
              emberEle.appendChild(args.elements[0].parentElement);
              emberEle.appendChild(document.createElement('p'));
              args.range.insertNode(emberEle); // add the link  description to the rte content
            }
        }

        }
});
defaultRTE.appendTo('#defaultRTE');

```

{% endtab %}
