---
title: "Working with Paragraph Formatting"
component: "DocumentEditor"
description: "Learn paragraph formatting supported in JavaScript document editor and how to apply it for selected contents."
---

# Working with Paragraph Formatting

Document Editor supports various paragraph formatting options such as text alignment, indentation, paragraph spacing, and more.

## Indentation

You can modify the left or right indentation of selected paragraphs using the following sample code.

```typescript
documenteditor.selection.paragraphFormat.leftIndent = 24;
documenteditor.selection.paragraphFormat.rightIndent = 24;
```

## Special indentation

You can define special indent for first line of the paragraph using the following sample code.

```typescript
documenteditor.selection.paragraphFormat.firstLineIndent = 24;
```

## Increase indent

You can increase the left indent of selected paragraphs by a factor of 36 points using the following sample code.

```typescript
documenteditor.editor.increaseIndent()
```

## Decrease indent

You can decrease the left indent of selected paragraphs by a factor of 36 points using the following sample code.

```typescript
documenteditor.editor.decreaseIndent()
```

## Text alignment

You can get or set the text alignment of selected paragraphs using the following sample code.

```typescript
documenteditor.selection.paragraphFormat.textAlignment = 'Center' | 'Left' | 'Right' | 'Justify';
```

You can toggle the text alignment of selected paragraphs by specifying a value using the following sample code.

```typescript
documenteditor.editor.toggleTextAlignment('Center' | 'Left' | 'Right' | 'Justify');
```

## Line spacing and its type

You can define the line spacing and its type for selected paragraphs using the following sample code.

```typescript
documenteditor.selection.paragraphFormat.lineSpacingType = 'AtLeast';
documenteditor.selection.paragraphFormat.lineSpacing = 6;
```

## Paragraph spacing

You can define the spacing before or after the paragraph by using the following sample code.

```typescript
documenteditor.selection.paragraphFormat.beforeSpacing = 24;
documenteditor.selection.paragraphFormat.afterSpacing = 24;
```

## Pagination properties

You can enable or disable the following pagination properties for the paragraphs in a Word document.

* Widow/Orphan control - whether the first and last lines of the paragraph are to remain on the same page as the rest of the paragraph when paginating the document.
* Keep with next - whether the specified paragraph remains on the same page as the paragraph that follows it while paginating the document.
* Keep lines together - whether all lines in the specified paragraphs remain on the same page while paginating the document.

The following example code illustrates how to enable or disable these pagination properties for the selected paragraphs.

```typescript
documenteditor.selection.paragraphFormat.widowControl = false;
documenteditor.selection.paragraphFormat.keepWithNext = true;
documenteditor.selection.paragraphFormat.keepLinesTogether = true;
```

## Toolbar with paragraph formatting options

The following sample demonstrates the paragraph formatting options using a toolbar.

{% tab template="document-editor/paragraph-format",es5Template="paragraph" , sourceFiles="index.ts,index.html" %}

```typescript
import { DocumentEditor, Editor, Selection, EditorHistory, SfdtExport, ContextMenu } from '@syncfusion/ej2-documenteditor';
import { Toolbar } from '@syncfusion/ej2-navigations';
import { ItemModel, DropDownButton } from '@syncfusion/ej2-splitbuttons';

//Inject the require module
DocumentEditor.Inject(Editor, Selection, EditorHistory, SfdtExport, ContextMenu);

let documenteditor: DocumentEditor = new DocumentEditor({
    height: '370px', isReadOnly: false, enableSelection: true, enableEditorHistory: true, enableEditor: true, enableContextMenu: true, enableSfdtExport: true
});

function toolbarButtonClick(arg) {
    switch (arg.item.id) {
        case 'AlignLeft':
            //Toggle the Left alignment for selected or current paragraph
            documenteditor.editor.toggleTextAlignment('Left');
            break;
        case 'AlignRight':
            //Toggle the Right alignment for selected or current paragraph
            documenteditor.editor.toggleTextAlignment('Right');
            break;
        case 'AlignCenter':
            //Toggle the Center alignment for selected or current paragraph
            documenteditor.editor.toggleTextAlignment('Center');
            break;
        case 'Justify':
            //Toggle the Justify alignment for selected or current paragraph
            documenteditor.editor.toggleTextAlignment('Justify');
            break;
        case 'IncreaseIndent':
            //Increase the left indent of selected or current paragraph
            documenteditor.editor.increaseIndent();
            break;
        case 'DecreaseIndent':
            //Decrease the left indent of selected or current paragraph
            documenteditor.editor.decreaseIndent();
            break;
        case 'ClearFormat':
            //Clear all formattiing of the selected paragraph or content.
            documenteditor.editor.clearFormatting();
            break;
    }
}
//Change the line spacing of selected or current paragraph
function lineSpacingAction(args: any) {
    let text: string = args.item.text;
    switch (text) {
        case 'Single':
            documenteditor.selection.paragraphFormat.lineSpacing = 1;
            break;
        case '1.15':
            documenteditor.selection.paragraphFormat.lineSpacing = 1.15;
            break;
        case '1.5':
            documenteditor.selection.paragraphFormat.lineSpacing = 1.5;
            break;
        case 'Double':
            documenteditor.selection.paragraphFormat.lineSpacing = 2;
            break;
    }
    setTimeout((): void => {
        documenteditor.focusIn();
    }, 30);
}
documenteditor.selectionChange = () => {
    setTimeout(() => {
        onSelectionChange();
    }, 20);
};
// Selection change to retrieve formatting
function onSelectionChange() {
    if (documenteditor.selection) {
        var paragraphFormat = documenteditor.selection.paragraphFormat;
        var toggleBtnId = ['AlignLeft', 'AlignCenter', 'AlignRight', 'Justify'];
        for (var i = 0; i < toggleBtnId.length; i++) {
            let toggleBtn: HTMLElement = document.getElementById(toggleBtnId[i]);
            //Remove toggle state.
            toggleBtn.classList.remove('e-btn-toggle');
        }
        //Add toggle state based on selection paragraph format.
        if (paragraphFormat.textAlignment === 'Left') {
            document.getElementById('AlignLeft').classList.add('e-btn-toggle');
        } else if (paragraphFormat.textAlignment === 'Right') {
            document.getElementById('AlignRight').classList.add('e-btn-toggle');
        } else if (paragraphFormat.textAlignment === 'Center') {
            document.getElementById('AlignCenter').classList.add('e-btn-toggle');
        } else {
            document.getElementById('Justify').classList.add('e-btn-toggle');
        }
        // #endregion
    }
}
//Toolbar configuration to add paragraph formatting options
let toolBar: Toolbar = new Toolbar({
    clicked: toolbarButtonClick,
    items: [
        {
            prefixIcon: 'e-de-ctnr-alignleft e-icons',
            tooltipText: 'Align Left',
            id: 'AlignLeft',
        },
        {
            prefixIcon: 'e-de-ctnr-aligncenter e-icons',
            tooltipText: 'Align Center',
            id: 'AlignCenter',
        },
        {
            prefixIcon: 'e-de-ctnr-alignright e-icons',
            tooltipText: 'Align Right',
            id: 'AlignRight',
        },
        {
            prefixIcon: 'e-de-ctnr-justify e-icons',
            tooltipText: 'Justify',
            id: 'Justify',
        },
        {
            prefixIcon: 'e-de-ctnr-increaseindent e-icons',
            tooltipText: 'Increase Indent',
            id: 'IncreaseIndent',
        },
        {
            prefixIcon: 'e-de-ctnr-decreaseindent e-icons',
            tooltipText: 'Decrease Indent',
            id: 'DecreaseIndent',
        },
        {
            type: 'Separator'
        },
        {
            id: 'lineSpacing'
        },
        {
            prefixIcon: 'e-de-ctnr-clearall e-icons',
            tooltipText: 'ClearFormatting',
            id: 'ClearFormat',
        }
    ],
});
toolBar.appendTo('#toolbar');
let items: ItemModel[] = [
    {
        text: 'Single',
    },
    {
        text: '1.15',
    },
    {
        text: '1.5',
    },
    {
        text: 'Double',
    },
];
let dropdown = new DropDownButton({
    items: items,
    iconCss: 'e-de-ctnr-linespacing e-icons',
    select: lineSpacingAction,
});
dropdown.appendTo('#lineSpacing');

documenteditor.appendTo('#DocumentEditor');

```

{% endtab %}

## See Also

* [Feature modules](../document-editor/feature-module/)
* [Paragraph dialog](../document-editor/dialog#paragraph-dialog/)
* [Keyboard shortcuts](../document-editor/keyboard-shortcut#paragraph-formatting/)