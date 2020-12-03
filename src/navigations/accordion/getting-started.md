---
title: "Accordion Getting Started"
component: "Accordion"
description: "This section explains how to create Accordion component in an JavaScript(ES-5) application with its basic features."
---

# Getting Started  with JavaScript(ES5)

The Essential JS 2 for JavaScript (global script) is an ES5 formatted pure JavaScript framework which can be directly used in latest web browsers.

## Component Initialization

The Essential JS 2 JavaScript components can be initialized by using either of the following ways.

* Using local script and style references in a HTML page.
* Using CDN link for script and style reference.

### Using local script and style references in a HTML page

**Step 1:** Create an app folder `myapp` for Essential JS 2 JavaScript components.

**Step 2:** You can get the global scripts and styles from the [Essential Studio JavaScript (Essential JS 2)](https://www.syncfusion.com/downloads/essential-js2) build installed location.

**Syntax:**
> Script: `**(installed location)**/Syncfusion/Essential Studio/{RELEASE_VERSION}/Essential JS 2/{PACKAGE_NAME}/dist/global/{PACKAGE_NAME}.min.js`
>
> Styles: `**(installed location)**/Syncfusion/Essential Studio/{RELEASE_VERSION}/Essential JS 2/{PACKAGE_NAME}/styles/material.css`

**Example:**

> Script: `C:/Program Files (x86)/Syncfusion/Essential Studio/15.4.30/Essential JS 2/ej2-navigations/dist/global/ej2-navigations.min.js`
>
> Styles: `C:/Program Files (x86)/Syncfusion/Essential Studio/15.4.30/Essential JS 2/ej2-navigations/styles/material.css`

**Step 3:** Create a folder `myapp/resources` and copy/paste the global scripts and styles from the above installed location to `myapp/resources` location.

**Step 4:** Create a HTML page (index.html) in `myapp` location and add the Essentials JS 2 script and style references.

```html
<!DOCTYPE html>
  <html xmlns="http://www.w3.org/1999/xhtml">
       <head>
            <title>Essential JS 2</title>
            <!-- Essential JS 2 material theme -->
            <link href="resources/material.css" rel="stylesheet" type="text/css"/>

            <!-- Essential JS 2 Accordion's global script -->
            <script src="resources/ej2-navigations.min.js" type="text/javascript"></script>
       </head>
       <body>
       </body>
  </html>
```

**Step 5:** Now, add the `Accordion` element and initiate the `Essential JS 2 Accordion` component in the `index.html` by using following code

## Initialize the Accordion using JSON items collection

The Accordion can be rendered by defining an array of [`items`](../api/accordion#items).

```html
<!DOCTYPE html>
  <html xmlns="http://www.w3.org/1999/xhtml">
       <head>
            <title>Essential JS 2</title>
            <!-- Essential JS 2 material theme -->
            <link href="resources/material.css" rel="stylesheet" type="text/css"/>

            <!-- Essential JS 2 Accordion's global script -->
            <script src="resources/ej2-navigations.min.js" type="text/javascript"></script>
       </head>
       <body>
            <!-- Add the HTML <div> element  -->
             <div id="element"></div>
            <script>
//Initialize Accordion component

    var accordion = new ej.navigations.Accordion({
    items: [
        { header: 'ASP.NET', expanded: 'true', content: 'Microsoft ASP.NET is a set of technologies in the Microsoft .NET Framework for building Web applications and XML Web services.' },
        { header: 'ASP.NET MVC', content: 'The Model-View-Controller (MVC) architectural pattern separates an application into three main components: the model, the view, and the controller.' },
        { header: 'JavaScript', content: 'JavaScript (JS) is an interpreted computer programming language. It was originally implemented as part of web browsers so that client-side scripts could interact with the user, control the browser, communicate asynchronously, and alter the document content that was displayed.' },
    ]
    });

//Render initialized Accordion component
    accordion.appendTo('#element');

            </script>
       </body>
  </html>
```

**Step 6:** Now, run the `index.html` in web browser, it will render the **Essential JS 2 Accordion** component.

### Using CDN link for script and style reference

**Step 1:** Create an app folder `myapp` for the Essential JS 2 JavaScript components.

**Step 2:** The Essential JS 2 component's global scripts and styles are already hosted in the below CDN link formats.

**Syntax:**
> Script: `http://cdn.syncfusion.com/ej2/{PACKAGE_NAME}/dist/global/{PACKAGE_NAME}.min.js`
>
> Styles: `http://cdn.syncfusion.com/ej2/{PACKAGE_NAME}/styles/material.css`

**Example:**
> Script: [`http://cdn.syncfusion.com/ej2/ej2-navigations/dist/global/ej2-navigations.min.js`](http://cdn.syncfusion.com/ej2/ej2-navigations/dist/global/ej2-navigations.min.js)
>
> Styles: [`http://cdn.syncfusion.com/ej2/ej2-navigations/styles/material.css`](http://cdn.syncfusion.com/ej2/ej2-navigations/styles/material.css)

**Step 3:** Create a HTML page (index.html) in `myapp` location and add the CDN link references. Now, add the `Accordion` element and initiate the `Essential JS 2 Accordion` component in the index.html by using following code.

{% tab template="accordion/es5-getting-started",  sourceFiles="index.html" %}

```html
<!DOCTYPE html>
  <html xmlns="http://www.w3.org/1999/xhtml">
       <head>
            <title>Essential JS 2</title>
            <!-- Essential JS 2 material theme -->
            <link href="https://cdn.syncfusion.com/ej2/ej2-base/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="https://cdn.syncfusion.com/ej2/ej2-navigations/styles/material.css" rel="stylesheet" type="text/css"/>

            <!-- Essential JS 2 all script -->
            <script src="https://cdn.syncfusion.com/ej2/dist/ej2.min.js" type="text/javascript"></script>
       </head>
       <body>
           <!-- Add the HTML <div> element  -->
             <div id="element"></div>
            <script>

    var accordion = new ej.navigations.Accordion({
    items: [
        { header: 'ASP.NET', expanded: 'true', content: 'Microsoft ASP.NET is a set of technologies in the Microsoft .NET Framework for building Web applications and XML Web services.' },
        { header: 'ASP.NET MVC', content: 'The Model-View-Controller (MVC) architectural pattern separates an application into three main components: the model, the view, and the controller.' },
        { header: 'JavaScript', content: 'JavaScript (JS) is an interpreted computer programming language. It was originally implemented as part of web browsers so that client-side scripts could interact with the user, control the browser, communicate asynchronously, and alter the document content that was displayed.' },
    ]
    });

//Render initialized Accordion component
    accordion.appendTo('#element');
</script>
</body>
</html>
```

{% endtab %}

**Step 4:** Now, run the `index.html` in web browser, it will render the `Essential JS 2 Accordion` component.

## Initialize the Accordion using HTML elements

The Accordion component can be rendered based on the given HTML element using `id` as `target` property.
You need to follow the below structure of HTML elements to render the Accordion.

```html
  <div id='accordion_html_markup'>   --> Root Accordion Element
       <div>      --> Accordion Item Container
            <div>   --> Accordion Header Container
                <div> </div> --> Accordion Header
            </div>
            <div>  --> Accordion Panel Container
                <div> </div> --> Accordion Content
             </div>
        </div>
  </div>
```

{% tab template="accordion/accordion-template", es5Template="es5_accordion_template",  sourceFiles="index.html" %}

{% endtab %}

> You can add the custom class into Accordion component using [`cssClass`](../api/accordion/accordionItem#cssclass) property which is used to customize the Accordion component.

## See Also

* [How to load accordion items dynamically](./how-to/load-accordion-items-dynamically/)