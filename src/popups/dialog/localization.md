---
title: "Localization"
component: "Dialog"
description: "Explains how to localize the static text (built-in text) content of the dialog control such as close button's tooltip text."
---

# Localization

`Localization` library allows to localize the default text content of
Dialog. In Dialog, The close button's tooltip text alone will be localize based on culture.
By using [locale](../api/dialog/#locale) property you can the culture dynamically in dialog component.

| Locale key | en-US (default)  |
|------|------|
| close |  Close |

## Loading translations

To load translation object in an application use `load` function of `L10n` class.

In the below sample, `French` culture is set to Dialog and change the close button's tooltip
text.

{% tab template="dialog/locale",sourceFiles="app.ts,index.html,styles.css", es5Template="locale-template" %}

```typescript
import { Dialog } from '@syncfusion/ej2-popups';
import { L10n, setCulture } from '@syncfusion/ej2-base';
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);

// Load French culture for Dialog close button tooltip text
L10n.load({
    'fr-BE': {
       'dialog': {
             'close': "Fermer"
         }
     }
});

// Initialization of Dialog component
let dialog = new Dialog({
    // Set the locale culture
    locale: 'fr-BE',
    // Enables the header
    header: 'Dialogue',
    // Enables the close icon button in header
    showCloseIcon: true,
    // Dialog content
    content: 'Dialogue avec la culture française',
    // The Dialog shows within the target element
    target: document.getElementById("container"),
    // Dialog width
    width: '250px',
});

// Sample level code to handle the button click action
document.getElementById('targetButton').onclick = (): void => {
    // Call the show method to open the Dialog
     dialog.show();
}
// Render initialized Dialog
dialog.appendTo('#dialog');
```

{% endtab %}
