---
title: "globalization"
component: "Splitter"
description: "This section explains the localization support of Syncfusion Splitter component."
---

# Globalization

## RTL

Specifies the direction of the Splitter component using the enableRtl property. For writing systems that require it like Arabic, Hebrew, etc., the direction can be switched to right-to-left.

The following code shows how to enable RTL behavior.

{% tab template="splitter/rtl" sourceFiles="app.ts,index.html,styles.css" es5Template="rtl-splitter" %}

```typescript

import { Splitter } from '@syncfusion/ej2-layouts';

let splitObj: Splitter = new Splitter({
    paneSettings: [
       { content:'Left Pane' },
       { content:'Middle Pane' },
       { content:'Right Pane' }
    ],
    enableRtl : true,
    height: '250px'
});
splitObj.appendTo('#splitter');

```

{% endtab %}

## See Also

* [Migration from Essential JS 1](./ej1-api-migration)
