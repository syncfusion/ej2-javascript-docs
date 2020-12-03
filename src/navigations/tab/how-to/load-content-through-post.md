---
title: "Load content through Ajax"
component: "Tab"
description: "This example demonstrates how to load external content into the Essential JS 2 Tab component through an AJAX post."
---

# Load content through Ajax

The Tab supports to load external contents through AJAX library. Refer to the following steps.

* Import the Ajax module from ej2-base and initialize with URL path.

* Get the data from Ajax Success event, then initialize the Tab with retrieved external path data.

{% tab template="tab/tab-ajax", es5Template="es5_tab_ajax", sourceFiles="index.ts,index.html,ajax.html" %}

```typescript
import {Tab} from '@syncfusion/ej2-navigations';
import { enableRipple } from '@syncfusion/ej2-base';
import { Ajax } from '@syncfusion/ej2-base';

enableRipple(true);

let ajax: Ajax = new Ajax('./ajax.html', 'GET', true);
ajax.send().then();
ajax.onSuccess = (data: string): void => {
  let ctn2: string = data;
  let tabObj: Tab = new Tab({
        items: [
        { header: { 'text' : 'Facebook'},
        content: 'Facebook is an online social networking service headquartered in Menlo Park, California. Its website was ' +
        'launched on February 4, 2004, by Mark Zuckerberg with his Harvard College roommates and fellow students Eduardo ' +
        'Saverin, Andrew McCollum, Dustin Moskovitz and Chris Hughes.The founders had initially limited the website\'\s ' +
        'membership to Harvard students, but later expanded it to colleges in the Boston area, the Ivy League, and Stanford ' +
        'University. It gradually added support for students at various other universities and later to high-school students.'},
        { header: { 'text' : 'Whatsapp'},
        content: 'WhatsApp Messenger is a proprietary cross-platform instant messaging client for smartphones that operates ' +
        'under a subscription business model. It uses the Internet to send text messages, images, video, user location and ' +
        'audio media messages to other users using standard cellular mobile numbers. As of February 2016, WhatsApp had a user ' +
        'base of up to one billion,[10] making it the most globally popular messaging application. WhatsApp Inc., based in ' +
        'Mountain View, California, was acquired by Facebook Inc. on February 19, 2014, for approximately US$19.3 billion.' },
        { header: { 'text' : 'Twitter'}, content: ctn2 },
        ]
    });
  tabObj.appendTo('#element');
}

```

{% endtab %}
