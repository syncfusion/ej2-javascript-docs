---
title: "Frequently Asked Questions"
component: "Schedule"
description: "Listed out frequently asked questions and corresponding solutions for scheduler "
---

# Frequently asked questions

In this article, you can find some frequently asked questions and corresponding solutions while getting hands-on experience with scheduler control.

## Grouping with empty resources

Grouping without providing any resource data will throw the following problems.

* Normal(vertical) views are rendered, but you are not able to perform CRUD operations
* Timeline views not at all render and shows empty scheduler table

So, we suggest to avoid grouping with empty resources in the scheduler.

## Not providing e-field in editor template

**Error:** While using editor template, value of  `e-field` is missing in editor window.

**Solution:** `e-field` value is mandatory, we need to add it. Please refer [here](https://ej2.syncfusion.com/javascript/documentation/schedule/editor-template/#customizing-event-editor-using-template) for more info.

## Missing CSS reference

**Error Image:**

  ![Missing CSS reference](images/missing-css-reference.png)

**Solution:**

The above problem occurs when missing CSS references for the scheduler in a project. You can resolve this issue by providing proper CSS for the scheduler.

```html
<html>
<head>
    <title>Syncfusion Javascript Sample</title>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=no" />
    <meta http-equiv="x-ua-compatible" content="ie=edge">
    <meta name="author" content="Syncfusion" />

      <! –– scheduler CSS is referred from this link ––>
    <link href="https://cdn.syncfusion.com/ej2/material.css" rel="stylesheet">

</head>

<body class="material">
    <div id='sample'>
</body>
</html>
```

## QuickInfoTemplate at bottom

When using the `quickInfoTemplate` in scheduler, sometimes quickinfo popup not shown fully at the bottom area of scheduler. You can resolve this by using `cellClick` and `eventClick` events and below code snippet.

```javascript

var eventAdded = false;

var scheduleObj = new ej.schedule.Schedule({
    .
    .
  cellClick: onClick,
  eventClick: onClick
});

scheduleObj.appendTo('#Schedule');

function onClick(args) {
  if (!this.eventAdded) {
    let popupInstance = document.querySelector('.e-quick-popup-wrapper').ej2_instances[0];
    popupInstance.open = () => {
      popupInstance.refreshPosition();
    };
    this.eventAdded = true;
  }
}
```

## Not processing culture files while using localization

**Error Image:**

![Locale import issue](images/locale-import-issue.png)

 While using [`locale`](https://ej2.syncfusion.com/javascript/documentation/schedule/localization/) in scheduler, not processing the `loadCultureFiles` properly throws the problem.

**Solution:** Properly add the culture files(numberingSystems, timeZoneNames, loadCldr, L10n etc.,) and `loadCultureFiles` method in your project will resolve the problem.

```javascript

loadCultureFiles();
var localeTexts;
var localeAjax = new ej.base.Ajax('./locale.json', 'GET', false);
localeAjax.onSuccess = function (value) {
  localeTexts = value;
};
localeAjax.send();
ej.base.L10n.load(JSON.parse(localeTexts));

function loadCultureFiles() {
  // Processing culture files
  var files = ['ca-gregorian.json', 'numbers.json', 'numberingSystems.json', 'timeZoneNames.json'];
  var loader = ej.base.loadCldr;
  var loadCulture = function (prop) {
    var val, ajax;
    ajax = new ej.base.Ajax('./' + files[prop], 'GET', false);
    ajax.onSuccess = function (value) {
      val = value;
    };
    ajax.send();
    loader(JSON.parse(val));
  };
  for (var prop = 0; prop < files.length; prop++) {
    loadCulture(prop);
  }
}

var scheduleObj = new ej.schedule.Schedule({
  width: '100%',
  height: '550px',
  locale: 'fr-CH',
}
});
scheduleObj.appendTo('#Schedule');

```
