---
title: "Pane Content"
component: "Splitter"
description: "This section explains about user can feed content to pane as plain text content or HTML markup or integrate other JavaScript UI controls."
---

# Pane Content

This section explains how to provide plain text content or HTML markup or integrate other JavaScript UI controls as content of splitter.

## HTML Markup

Splitter is a layout based container control. You can render the pane contents from existing HTML markups. Converting HTML markup as splitter pane is easy way to add the panes content dynamically.

{% tab template="splitter/htmlmarkup" sourceFiles="app.ts,index.html,styles.css" es5Template="htmlmarkup" %}

```typescript
import { Splitter } from '@syncfusion/ej2-layouts';

let splitObj: Splitter = new Splitter({
    height: '200px',
    paneSettings: [
        { size: '200px',
        content: '<div class="content"><h3 class="h3">PARIS </h3>Paris, the city of lights and love - this short guide is full of ideas for how to make the most of the romanticism...</div>'
        },
        { size: '200px',
        content: '<div class="content"><h3 class="h3">CAMEMBERT </h3>The village in the Orne département of Normandy where the famous French cheese is originated from.</div>'
        },
        { size: '200px',
        content: '<div class="content"><h3 class="h3">GRENOBLE </h3>The capital city of the French Alps and a major scientific center surrounded by many ski resorts, host of the Winter Olympics in 1968.</div>'
        }
    ],
    width: '600px'
});
splitObj.appendTo('#splitter');

```

{% endtab %}

Also, you can provide the pane content inner HTML.

{% tab template="splitter/innerhtml" sourceFiles="app.ts,index.html,styles.css" es5Template="innerhtml" %}

```typescript
import { Splitter } from '@syncfusion/ej2-layouts';

let splitObj: Splitter = new Splitter({
    height: '200px',
    paneSettings: [
        { size: '200px' },
        { size: '200px' },
        { size: '200px' }
    ],
    width: '600px'
});
splitObj.appendTo('#splitter');

```

{% endtab %}

## JavaScript UI controls

You can render any JavaScript UI controls along with their native and control events within splitter as pane content.

You can refer [Accordion within splitter](https://ej2.syncfusion.com/demos/#/material/splitter/accordion-navigation-menu.html) and [Listview within splitter](https://ej2.syncfusion.com/demos/#/material/splitter/details-view.html) examples.

## Plain content

You can add the plain text as a pane contents using either inner HTML or [`content`](../api/splitter/panePropertiesModel/#content) API

{% tab template="splitter/plaincontent" sourceFiles="app.ts,index.html,styles.css" es5Template="plaincontent" %}

```typescript
import { Splitter } from '@syncfusion/ej2-layouts';

let splitObj: Splitter = new Splitter({
    height: '200px',
    paneSettings: [
        { size: '200px', content: 'Left pane'
        },
        { size: '200px', content: 'Middle pane'
        },
        { size: '200px', content: 'Right pane'
        }
    ],
    width: '600px'
});
splitObj.appendTo('#splitter');

```

{% endtab %}

## Pane content using selector

You can set HTML element as pane [`content`](../api/splitter/panePropertiesModel/#content) using the query selectors such as ID or CSS class selectors.

The following code demonstrates how to fetch an element from the document and load it to pane using its ID.

{% tab template="splitter/selectorcontent" sourceFiles="app.ts,index.html,styles.css" es5Template="selectorcontent" %}

```typescript
import { Splitter } from '@syncfusion/ej2-layouts';

/**
 *  Splitter pane content as html element using ID selector
 */

let splitObj1: Splitter = new Splitter({
    height: '200px',
    paneSettings: [
        { size: '25%', min: '60px', content: '#left-pane-content' },
        { size: '50%', min: '60px', content: '#middle-pane-content' },
        { size: '25%', min: '60px', content: '#last-pane-content' }
    ],
    width: '100%',
    separatorSize: 4
});
splitObj1.appendTo('#horizontal');

```

{% endtab %}