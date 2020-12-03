---
title: "Initialize ButtonGroup using util function"
component: "ButtonGroup"
description: "ButtonGroup how to section, create ButtonGroup using util function, icons, form submit, show selected state on initial render."
---

# Initialize ButtonGroup using util function

Though, it is a CSS component for easy initialization of ButtonGroup `createButtonGroup` util function can be used.

To use `createButtonGroup` util function, [`SplitButton dependencies`](./../../split-button/getting-started#dependencies) should be configured and added in
`system.config.js` and it should also be imported in `script` file.

Using `createButtonGroup` method, the button options, selector, and cssClass is passed and the corresponding classes is added to the elements.

## Create basic ButtonGroup

To create a basic ButtonGroup, the target element along with the button elements should be created in `index.html` file.

## Create radio type ButtonGroup

To create a radio type ButtonGroup, the target element along with the input elements should be created with type `radio` in `index.html`.

## Create checkbox type ButtonGroup

Checkbox type ButtonGroup creation is similar to radio type ButtonGroup, instead the type of the input elements should be `checkbox`.

The following example illustrates how to create ButtonGroup using `createButtonGroup` function for basic, checkbox, and radio
type behaviors.

{% tab template= "button-group/basic-util", sourceFiles="app.ts,index.html,styles.css", es5Template="basic-util-template", isDefaultActive=true %}

```typescript

import { createButtonGroup } from '@syncfusion/ej2-splitbuttons';

// To create basic ButtonGroup.
createButtonGroup('#basic', {
    buttons: [
        { content: 'HTML' },
        { content: 'CSS' },
        { content: 'Javascript'}
    ]
});

// To create checkbox type ButtonGroup.
createButtonGroup('#checkbox', {
    buttons: [
        { content: 'Bold' },
        { content: 'Italic' },
        { content: 'Undeline'}
    ]
});

// To create radio type ButtonGroup.
createButtonGroup('#radio', {
    buttons: [
        { content: 'Left' },
        { content: 'Center' },
        { content: 'Right'}
    ]
});

```

{% endtab %}

> If null value is passed in button options, then that particular button will be skipped from processing in `createButtonGroup` util function.