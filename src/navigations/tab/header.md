---
title: "Tab Header"
component: "Tab"
description: "This section explains how to create the tab header with different styles in an Typescript application."
---

# Header

This section explains about modifying the style of Tab header, and configuring its icons and positions.

## Styles

You can customize header styles by adding predefined classes in the Tab root element. The pre-defined CSS class names are as follows:

* **e-fill**: The Selected Tab header background is set as solid fill.
* **e-background**: Tab header has a solid fill background, and the selected header has a highlighted border.
* **e-background e-accent**: Tab header has a solid fill background, and the selected header has a highlighted border with accent color.

> If the above custom style classes are not included in the root element, the default style is applied to the Tab items.

{% tab template="tab/tab-style", es5Template="es5_tab_style", sourceFiles="index.ts,index.html,index.css"%}

```typescript
    import { Tab } from '@syncfusion/ej2-navigations';
    import { DropDownList, ChangeEventArgs } from '@syncfusion/ej2-dropdowns';
    import { enableRipple } from '@syncfusion/ej2-base';

    enableRipple(true);
    let tabObj: Tab = new Tab({
        items: [
            {
                header: { 'text': 'Twitter' },
                content: 'Twitter is an online social networking service that enables users to send and read short 140-character ' +
                'messages called "tweets". Registered users can read and post tweets, but those who are unregistered can only read ' +
                'them. Users access Twitter through the website interface, SMS or mobile device app Twitter Inc. is based in San ' +
                'Francisco and has more than 25 offices around the world. Twitter was created in March 2006 by Jack Dorsey, ' +
                'Evan Williams, Biz Stone, and Noah Glass and launched in July 2006. The service rapidly gained worldwide popularity, ' +
                'with more than 100 million users posting 340 million tweets a day in 2012.The service also handled 1.6 billion ' +
                'search queries per day.'
            },
            {
                header: { 'text': 'Facebook' },
                content: 'Facebook is an online social networking service headquartered in Menlo Park, California. Its website was ' +
                'launched on February 4, 2004, by Mark Zuckerberg with his Harvard College roommates and fellow students Eduardo ' +
                'Saverin, Andrew McCollum, Dustin Moskovitz and Chris Hughes.The founders had initially limited the website\'\s ' +
                'membership to Harvard students, but later expanded it to colleges in the Boston area, the Ivy League, and Stanford ' +
                'University. It gradually added support for students at various other universities and later to high-school students.'
            },
            {
                header: { 'text': 'WhatsApp' },
                content: 'WhatsApp Messenger is a proprietary cross-platform instant messaging client for smartphones that operates ' +
                'under a subscription business model. It uses the Internet to send text messages, images, video, user location and ' +
                'audio media messages to other users using standard cellular mobile numbers. As of February 2016, WhatsApp had a user ' +
                'base of up to one billion,[10] making it the most globally popular messaging application. WhatsApp Inc., based in ' +
                'Mountain View, California, was acquired by Facebook Inc. on February 19, 2014, for approximately US$19.3 billion.'
            }
        ]
    });
    tabObj.appendTo('#element');
    let headerStyles: DropDownList = new DropDownList({
        width: '90%',
        change:()=>{ changeHeaderStyle();}
    });
    headerStyles.appendTo('#headerStyles');

    function changeHeaderStyle(e: ChangeEventArgs): void {
        removeStyleClass();
        if (headerStyles.value === 'fill') {
            tabObj.element.classList.add('e-fill');
        } else if (headerStyles.value === 'background') {
            tabObj.element.classList.add('e-background');
        } else if (headerStyles.value === 'accent') {
            tabObj.element.classList.add('e-background');
            tabObj.element.classList.add('e-accent');
        }
    }

    function removeStyleClass(): void {
        tabObj.element.classList.remove('e-fill');
        tabObj.element.classList.remove('e-background');
        tabObj.element.classList.remove('e-accent');
    }
```

{% endtab %}

## Icon positions

You can customize the position of the Tab header icons using the [`iconPosition`](../api/tab/header#iconposition) property.  This property depends on the header items [`iconCss`](../api/tab/header#iconcss) property.  By default, Tab header icon is placed on left position.  The position values are as follows:

* **Left**: Icon is placed on the left of the Tab header item.
* **Right**: Icon is placed on the right of the Tab header item.
* **Top**: Icon is placed on the top of the Tab header item.
* **Bottom**: Icon is placed on the bottom of the Tab header item.

{% tab template="tab/icon-position", es5Template="es5_icon_position", sourceFiles="index.ts,index.html,index.css"%}

```typescript
    import { Tab } from '@syncfusion/ej2-navigations';
    import { DropDownList, ChangeEventArgs } from '@syncfusion/ej2-dropdowns';
    import { enableRipple } from '@syncfusion/ej2-base';

    enableRipple(true);
    let tabObj: Tab = new Tab({
        items: [
            {
                header: { 'text': 'Twitter', 'iconCss': 'e-twitter' },
                content: 'Twitter is an online social networking service that enables users to send and read short 140-character ' +
                'messages called "tweets". Registered users can read and post tweets, but those who are unregistered can only read ' +
                'them. Users access Twitter through the website interface, SMS or mobile device app Twitter Inc. is based in San ' +
                'Francisco and has more than 25 offices around the world. Twitter was created in March 2006 by Jack Dorsey, ' +
                'Evan Williams, Biz Stone, and Noah Glass and launched in July 2006. The service rapidly gained worldwide popularity, ' +
                'with more than 100 million users posting 340 million tweets a day in 2012.The service also handled 1.6 billion ' +
                'search queries per day.'
            },
            {
                header: { 'text': 'Facebook', 'iconCss': 'e-facebook' },
                content: 'Facebook is an online social networking service headquartered in Menlo Park, California. Its website was ' +
                'launched on February 4, 2004, by Mark Zuckerberg with his Harvard College roommates and fellow students Eduardo ' +
                'Saverin, Andrew McCollum, Dustin Moskovitz and Chris Hughes.The founders had initially limited the website\'\s ' +
                'membership to Harvard students, but later expanded it to colleges in the Boston area, the Ivy League, and Stanford ' +
                'University. It gradually added support for students at various other universities and later to high-school students.'
            },
            {
                header: { 'text': 'WhatsApp', 'iconCss': 'e-whatsapp' },
                content: 'WhatsApp Messenger is a proprietary cross-platform instant messaging client for smartphones that operates ' +
                'under a subscription business model. It uses the Internet to send text messages, images, video, user location and ' +
                'audio media messages to other users using standard cellular mobile numbers. As of February 2016, WhatsApp had a user ' +
                'base of up to one billion,[10] making it the most globally popular messaging application. WhatsApp Inc., based in ' +
                'Mountain View, California, was acquired by Facebook Inc. on February 19, 2014, for approximately US$19.3 billion.'
            }
        ]
    });
    //Render initialized Tab component
    tabObj.appendTo('#element');
    let iconPosition: DropDownList = new DropDownList({
        width: '90%',
        change:()=>{ changeHeaderStyle();}
    });
    iconPosition.appendTo('#iconPosition');

    function changeHeaderStyle(e: ChangeEventArgs): void {
        let items: any = tabObj.items;
        for(let i: number = 0; i < items.length; i++) {
            tabObj.items[i].header.iconPosition = iconPosition.value;
        }
    }
```

{% endtab %}

## See Also

* [How to customize selected tab styles](./how-to/customize-selected-tab-styles)