---
title: "Tab Content Height"
component: "Tab"
description: "This section explains how to customize the Syncfusion Essential JS 2 Tab content height based on different needs."
---

# Customize Tab content height

You can change the Tab content height by using the [`heightAdjustMode`](../../api/tab#heightadjustmode) property. By default, the Tab content [`heightAdjustMode`](../../api/tab#heightadjustmode) property is set to `Content` value.

* **None**: Each tab content height is set based on the Tab height. This value is used only the tab component having the [`height`](../../api/tab#height) property.
* **Auto**: Each tab content height will take the maximum height of all other tabs content.
* **Content**: Each tab content height is set based on their own content.
* **Fill**: Each tab content height is set based on the full height of Tabs parent element.

{% tab template="tab/tab-height", es5Template="es5_tab-height", sourceFiles="index.ts,index.html"%}

```typescript
    import { Tab } from '@syncfusion/ej2-navigations';
    import { DropDownList, ChangeEventArgs } from '@syncfusion/ej2-dropdowns';
    import { enableRipple } from '@syncfusion/ej2-base';

    enableRipple(true);
    let tabObj: Tab = new Tab({
        height: "400px",
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
    let heightValues: DropDownList = new DropDownList({
        width: '90%',
        index: 1,
        change:()=>{ changeHeightValue();}
    });
    heightValues.appendTo('#contentHeight');

    function changeHeightValue(e: ChangeEventArgs): void {
        tabObj.heightAdjustMode = heightValues.value;
    }

```

{% endtab %}