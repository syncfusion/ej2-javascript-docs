---
title: "Set custom animation"
component: "Tab"
description: "This example demonstrates how to set custom animation for both previous and next actions on Essential JS 2 Tab component when the tab select."
---

# Set custom animation

Tab supports custom animations for both previous and next actions from the provided animation option of `Animation` library. The [`animation`](../../api/tab#animation) property also allows you to set [`easing`](../../api/tab/tabActionSettings#easing), [`duration`](../../api/tab/tabActionSettings#duration), and various other [`effect`](../../api/tab/tabActionSettings#effect).

Default animation is given as `SlideLeftIn` for [`previous`](../../api/tab/tabAnimationSettings#previous) tab animation and `SlideRightIn` for [`next`](../../api/tab/tabAnimationSettings#next) tab animation. You can also disable the animation by setting the animation effect as none.

The sample demonstrates some types of animation that suits Tab. You can check all the animation effects here.

{% tab template="tab/tab-animation", es5Template="es5_tab_animation", sourceFiles="index.ts,index.html,datasource.ts" %}

```typescript

import { Tab, selectEventArgs } from '@syncfusion/ej2-navigations';
import { DropDownList } from '@syncfusion/ej2-dropdowns';

let tabObj: Tab = new Tab({
    items: [{
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
    let listObjPrevious: DropDownList = new DropDownList({
        index: 0,
        placeholder: 'Select a animate type',
        popupHeight: '150px',
        change: () => { valueChange();  }
    });
    listObjPrevious.appendTo('#previousAnimation');
    let listObjNext: DropDownList = new DropDownList({
        index: 1,
        placeholder: 'Select a animate type',
        popupHeight: '150px',
        change: () => { valueChange1();  }
    });
    listObjNext.appendTo('#nextAnimation');
    function valueChange(): void {
        tabObj.animation.previous.effect = listObjPrevious.value;
    }
    function valueChange1(): void {
        tabObj.animation.next.effect = listObjNext.value;
    }

```

{% endtab %}
