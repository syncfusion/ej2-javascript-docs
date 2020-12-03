---
title: "Button Types and Styles"
component: "Button"
description: "TypeScript Button component supports different types, predefined styles, sizes and also has support for icons."
---

# Types and Styles

This section explains the different styles and types of Buttons.

## Button styles

The Essential JS 2 Button has the following predefined styles that can be defined using the [`cssClass`](../api/button#cssclass) property.

| Class | Description |
| -------- | -------- |
| e-primary | Used to represent a primary action. |
| e-success | Used to represent a positive action. |
| e-info |  Used to represent an informative action. |
| e-warning | Used to represent an action with caution. |
| e-danger | Used to represent a negative action. |
| e-link |  Changes the appearance of the Button like a hyperlink. |

{% tab template= "button/button-style", sourceFiles="app.ts,index.html,styles.css",
es5Template="styles-template", isDefaultActive=true %}

```typescript
import { Button } from '@syncfusion/ej2-buttons';
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);

//Primary Button - Used to represent a primary action.
let button: Button = new Button({ cssClass: `e-primary`}, '#primarybtn');

//Success Button - Used to represent a positive action.
button = new Button({ cssClass: `e-success`}, '#successbtn');

//Info Button - Used to represent an informative action.
button = new Button({ cssClass: `e-info`}, '#infobtn');

//Warning Button - Used to represent an action with caution.
button = new Button({ cssClass: `e-warning`}, '#warningbtn');

//Danger Button - Used to represent a negative action.
button = new Button({ cssClass: `e-danger`}, '#dangerbtn');

//Link Button - Changes the appearance of the Button like a hyperlink.
button = new Button({ cssClass: `e-link`}, '#linkbtn');

```

{% endtab %}

> Predefined Button styles provide only the visual indication. So, Button content should define the Button style for the users of assistive technologies such as screen readers.
> Primary action button can also be achieved by setting [`isPrimary`](../api/button#isprimary) property as `true`.

## Button types

The types of Essential JS 2 Button are as follows:

* Basic types
* Flat Button
* Outline Button
* Round Button
* Toggle Button

### Basic types

The basic Button types are explained below.

| Type | Description |
| -------- | -------- |
| Button | Defines a click Button. |
| Submit | This Button submits the form data to the server. |
| Reset |  This Button resets all the controls in the form elements to their initial values. |

{% tab template= "button/basic-types", sourceFiles="app.ts,index.html,styles.css",
es5Template="basic-types-template" %}

```typescript
import { Button } from '@syncfusion/ej2-buttons';
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);

//Submit.
let button: Button = new Button();
button.appendTo('#submitbtn');

//Reset.
button = new Button();
button.appendTo('#resetbtn');
```

{% endtab %}

### Flat Button

The Flat Button is styled with no background color. To create a flat Button,
set the [`cssClass`](../api/button#cssclass) property to `e-flat`.

### Outline Button

An outline Button has a border with transparent background. To create an outline Button,
set the [`cssClass`](../api/button#cssclass) property to `e-outline`.

### Round Button

A round Button is shaped like a circle. Usually, it contains an icon representing its action. To create a round Button,
set the [`cssClass`](../api/button#cssclass) property to `e-round`.

{% tab template= "button/button-type", sourceFiles="app.ts,index.html,styles.css",
es5Template="btn-types-template" %}

```typescript
import { Button } from '@syncfusion/ej2-buttons';
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);

//Flat Button.
let button: Button = new Button({ cssClass: `e-flat`}, '#flatbtn');

//Outline Button.
button = new Button({ cssClass: `e-outline`}, '#outlinebtn');

//Round Button - Icon can be loaded by setting "e-icons e-plus-icon" in "iconCss" property.
//Use "e-icons" class name to load Essential JS 2 built-in icons.
//Use "e-plus-icon" class name to load plus icon that you can refer in "styles.css".
button = new Button({ cssClass: `e-round`, iconCss: 'e-icons e-plus-icon', isPrimary:true}, '#roundbtn');
```

{% endtab %}

### Toggle Button

A toggle Button allows you to change between the two states. The Button is active in toggled state and can be recognized through the `e-active` class.
The functionality of the toggle Button is handled by click event. To create a toggle Button,
set the [`isToggle`](../api/button#istoggle) property to `true`. In the following code snippet,
the toggle Button text changes to play/pause based on the state of the Button with the use of click event.

{% tab template= "button/toggle-button", sourceFiles="app.ts,index.html,styles.css",
es5Template="toggle-btn-template" %}

```typescript

//Button is active in toggled state.
import { Button } from '@syncfusion/ej2-buttons';
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);

let togglebtn: Button = new Button({cssClass: `e-flat`, iconCss: 'e-btn-sb-icon e-play-icon', isToggle: true, content:'Play'}, '#toggelbtn');

//Click Event.
document.getElementById('toggelbtn').onclick = (): void => {
        if (document.getElementById('toggelbtn').classList.contains('e-active')) {
            togglebtn.content = 'Pause';
            togglebtn.iconCss = 'e-btn-sb-icon e-pause-icon';
        } else {
            togglebtn.content = 'Play';
            togglebtn.iconCss = 'e-btn-sb-icon e-play-icon';
        }
    };
```

{% endtab %}

## Icons

### Button with font icons

The Button can have an icon to provide the visual representation of the action. To place the icon on a Button,
set the [`iconCss`](../api/button#iconcss) property with the required icon CSS. By default, the icon is positioned to the left side of the Button.
You can customize the icon's position by using the [`iconPosition`](../api/button#iconposition) property.

{% tab template= "button/icon", sourceFiles="app.ts,index.html,styles.css",
es5Template="icons-template" %}

```typescript
import { Button } from '@syncfusion/ej2-buttons';
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);

//To position the icon to the left of the text on a Button.
let button: Button = new Button({iconCss: 'e-btn-sb-icon e-prev-icon'}, '#iconbutton');

//To position the icon to the right of the text on a Button.
button = new Button({iconCss: 'e-btn-sb-icon e-stop-icon', iconPosition: 'Right'}, '#iconposbtn');

```

{% endtab %}

### Button with SVG image

SVG image can be added to the Button using [`iconCss`](../api/button#iconcss) property.

In the following example, SVG image is added using the iconCss class `e-search-icon` by setting `height` and `width`.

{% tab template= "button/svg", sourceFiles="app.ts,index.html",es5Template="icons-template" %}

```typescript
import { Button } from '@syncfusion/ej2-buttons';
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);

let button: Button = new Button({ iconCss: 'e-search-icon' }, '#iconbutton');

```

{% endtab %}

> The Essential JS 2 provides a set of icons that can be loaded by applying `e-icons` class name to the element.
You can also use third party icons on the Button using the [`iconCss`](../api/button#iconcss) property.

## Button size

The two types of Button sizes are default and small. To change the size of the default Button to small Button,
set the [`cssClass`](../api/button#cssclass) property to `e-small`.

{% tab template= "button/size", sourceFiles="app.ts,index.html,styles.css",
es5Template="size-template" %}

```typescript
import { Button } from '@syncfusion/ej2-buttons';
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);

//Small Button.
let button: Button = new Button({ cssClass: `e-small`}, '#smallbtn');

//Normal Button.
button = new Button();
button.appendTo('#normalbtn');
```

{% endtab %}

## See Also

* [Customize Button appearance](./how-to/customize-button-appearance)
* [How to create block button](./how-to/create-a-block-button)
* [How to create repeat button](./how-to/repeat-button)