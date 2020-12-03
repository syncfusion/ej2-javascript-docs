---
title: "Getting Started"
component: "Spinner"
description: "Helps to get started with the spinner component."
---

# Getting Started

Initialize the Spinner using `createSpinner` method and show/hide the spinner using `showSpinner` and `hideSpinner` methods accordingly. Set the target to the spinner to render it based on specific target.

```typescript
  createSpinner({
    target: document.getElementById('container')
  });
```

* Show and hide this spinner by using `showSpinner` and `hideSpinner` methods for loading in your page.

## Create the Spinner globally

The Spinner can be render globally in a page using public exported functions of the `ej.popups`.

{% tab template="spinner/intro",sourceFiles="app.ts,index.html,styles.css", es5Template="default" %}

```typescript

//createSpinner() method is used to create spinner

createSpinner({

  // Specify the target for the spinner to show

  target: document.getElementById('container')

});

//showSpinner() will make the spinner visible

ej.popups.showSpinner(document.getElementById('container'));

setInterval(function () {

  //hideSpinner() method used hide spinner

  ej.popups.hideSpinner(document.getElementById('container'))

}, 100000);

```

{% endtab %}