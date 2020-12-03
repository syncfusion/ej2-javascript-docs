---
title: "Query Builder JavaScript (es5) Getting Started"
component: "QueryBuilder"
description: "This section helps to learn how to create the query builder in HTML5 JavaScript (ECMAScript 5) application with its basic features in step-by-step procedure."
---

# Getting Started  with JavaScript(ES5)

The Essential JS 2 for JavaScript (global script) is an ES5 formatted pure JavaScript framework which can be directly used in latest web browsers.

## Control Initialization

The Essential JS 2 JavaScript controls can be initialized by using either of the following ways.

* Using local script and style references in a HTML page.
* Using CDN link for script and style reference.

### Using local script and style references in a HTML page

**Step 1:** Create an app folder `quickstart` for getting started.

**Step 2:** You can get the global scripts and styles from the [Essential Studio JavaScript (Essential JS 2)](https://www.syncfusion.com/downloads/essential-js2) build installed location.

**Syntax:**
> Script: `**(installed location)**/Syncfusion/Essential Studio/{RELEASE_VERSION}/Essential JS 2/{PACKAGE_NAME}/dist/global/{PACKAGE_NAME}.min.js`
>
> Style: `**(installed location)**/Syncfusion/Essential Studio/{RELEASE_VERSION}/Essential JS 2/{PACKAGE_NAME}/styles/material.css`

**Example:**
> Script: `C:/Program Files (x86)/Syncfusion/Essential Studio/16.3.29/Essential JS 2/ej2-query-builder/dist/global/ej2-querybuilder.min.js`
>
> style: `C:/Program Files (x86)/Syncfusion/Essential Studio/16.3.29/Essential JS 2/ej2-buttons/styles/material.css`

The [`Custom Resource Generator (CRG)`](https://crg.syncfusion.com/) is an online web tool, which can be used to generate the custom script and styles for a set of specific controls. This web tool is useful to combine the required control scripts and styles in a single file.

**Step 3:** Create a folder `~/quickstart/resources` and copy/paste the global scripts and styles from the above installed location to `~/quickstart/resources/package` corresponding package location.

**Step 4:** Create a HTML page (index.html) in `~/quickstart/index.html` and add the Essentials JS 2 script and style references.

```html
<!DOCTYPE html>
<html xmlns="http://www.w3.org/1999/xhtml">
    <head>
        <title>Essential JS 2</title>
         <!-- Essential JS 2 query-builder's dependency style -->
        <link href="resources/base/material.css" rel="stylesheet" type="text/css"/>
        <link href="resources/buttons/material.css" rel="stylesheet" type="text/css"/>
        <link href="resources/splitbuttons/material.css" rel="stylesheet" type="text/css"/>
        <link href="resources/dropdowns/material.css" rel="stylesheet" type="text/css"/>
        <link href="resources/inputs/material.css" rel="stylesheet" type="text/css"/>
        <link href="resources/calendars/material.css" rel="stylesheet" type="text/css"/>
         <link href="resources/popups/material.css" rel="stylesheet" type="text/css"/>
        <!-- Essential JS 2 query-builder material theme (Control Styles) -->
        <link href="resources/querybuilder/material.css" rel="stylesheet" type="text/css"/>

        <!-- Essential JS 2 query-builder's global script (Dependency Script) -->
        <script src="resources/base/ej2-base.min.js" type="text/javascript"></script>
        <script src="resources/buttons/ej2-buttons.min.js" type="text/javascript"></script>
        <script src="resources/splitbuttons/ej2-splitbuttons.min.js" type="text/javascript"></script>
        <script src="resources/dropdowns/ej2-dropdowns.min.js" type="text/javascript"></script>
        <script src="resources/inputs/ej2-inputs.min.js" type="text/javascript"></script>
        <script src="resources/calendars/ej2-calendars.min.js" type="text/javascript"></script>
         <script src="resources/popups/ej2-popups.min.js" type="text/javascript"></script>
        <!-- Essential JS 2 query-builder global script (Control Script) -->
        <script src="resources/querybuilder/ej2-querybuilder.min.js" type="text/javascript"></script>
    </head>
    <body>
    </body>
</html>
```

**Step 5:** Now, add the `Query Builder` and initiate the `Syncfusion JavaScript (ES5) Query Builder` control in the `~/quickstart/index.html` by using following code

```html
<!DOCTYPE html>
<html xmlns="http://www.w3.org/1999/xhtml">
    <head>
        <title>Essential JS 2</title>
         <!-- Essential JS 2 query-builder's dependency style -->
        <link href="resources/base/material.css" rel="stylesheet" type="text/css"/>
        <link href="resources/buttons/material.css" rel="stylesheet" type="text/css"/>
        <link href="resources/splitbuttons/material.css" rel="stylesheet" type="text/css"/>
        <link href="resources/dropdowns/material.css" rel="stylesheet" type="text/css"/>
        <link href="resources/inputs/material.css" rel="stylesheet" type="text/css"/>
        <link href="resources/calendars/material.css" rel="stylesheet" type="text/css"/>
         <link href="resources/popups/material.css" rel="stylesheet" type="text/css"/>
        <!-- Essential JS 2 query-builder material theme (Control Styles) -->
        <link href="resources/querybuilder/material.css" rel="stylesheet" type="text/css"/>

        <!-- Essential JS 2 query-builder's global script (Dependency Script) -->
        <script src="resources/base/ej2-base.min.js" type="text/javascript"></script>
        <script src="resources/buttons/ej2-buttons.min.js" type="text/javascript"></script>
        <script src="resources/splitbuttons/ej2-splitbuttons.min.js" type="text/javascript"></script>
        <script src="resources/dropdowns/ej2-dropdowns.min.js" type="text/javascript"></script>
        <script src="resources/inputs/ej2-inputs.min.js" type="text/javascript"></script>
        <script src="resources/calendars/ej2-calendars.min.js" type="text/javascript"></script>
        <script src="resources/popups/ej2-popups.min.js" type="text/javascript"></script>
        <!-- Essential JS 2 query-builder global script (Control Script) -->
        <script src="resources/querybuilder/ej2-querybuilder.min.js" type="text/javascript"></script>
    </head>
    <body>
        <!-- Add the HTML div element  -->
        <div id="querybuilder" class="row">
        <script>
        var columnData = [
            { field: 'EmployeeID', label: 'Employee ID', type: 'number' },
            { field: 'FirstName', label: 'First Name', type: 'string' },
            { field: 'TitleOfCourtesy', label: 'Title Of Courtesy', type: 'boolean', values: ['Mr.', 'Mrs.']},
            { field: 'Title', label: 'Title', type: 'string' },
            { field: 'HireDate', label: 'Hire Date', type: 'date', format: 'dd/MM/yyyy' },
            { field: 'Country', label: 'Country', type: 'string' },
            { field: 'City', label: 'City', type: 'string' }
        ];
        var qryBldrObj = new ej.querybuilder.QueryBuilder({
            width: '70%',
            columns: columnData,
        });
        qryBldrObj.appendTo('#querybuilder');
        </script>
    </body>
</html>
```

**Step 6:** Now, run the `index.html` in web browser, it will render the **Syncfusion JavaScript Query Builder** control.

### Using CDN link for script and style reference

**Step 1:** Create an app folder `quickstart` for getting started.

**Step 2:** The Essential JS 2 controls's global scripts and styles are already hosted in the below CDN link formats.

**Syntax:**
> Dependency Script: `http://cdn.syncfusion.com/ej2/{DEPENDENCY_PACKAGE_NAME}/dist/global/{PACKAGE_NAME}.min.js`
>
> Control Script: `http://cdn.syncfusion.com/ej2/{PACKAGE_NAME}/dist/global/{PACKAGE_NAME}.min.js`
>
> Dependency Styles: `http://cdn.syncfusion.com/ej2/{DEPENDENCY_PACKAGE_NAME}/styles/material.css`
>
> Control Styles: `http://cdn.syncfusion.com/ej2/{PACKAGE_NAME}/styles/material.css`

**Example:**
> Script: [`http://cdn.syncfusion.com/ej2/ej2-querybuilder/dist/global/ej2-querybuilder.min.js`](http://cdn.syncfusion.com/ej2/ej2-query-builder/dist/global/ej2-querybuilder.min.js)
>
> Styles: [`http://cdn.syncfusion.com/ej2/ej2-querybuilder/styles/material.css`](http://cdn.syncfusion.com/ej2/ej2-querybuilder/styles/material.css)

**Step 3:** Create a HTML page (index.html) in `~/quickstart/index.html` location and add the CDN link references. Now, add the `Query Builder` and initiate the `Syncfusion JavaScript (ES5) Query Builder` control in the index.html by using following code.

{% tab template="query-builder/es5-getting-started", sourceFiles="index.html", isDefaultActive=true %}

```html
<!DOCTYPE html>
  <html xmlns="http://www.w3.org/1999/xhtml">
       <head>
            <title>Essential JS 2</title>

             <!-- Essential JS 2 query-builder's dependency style -->
            <link href="https://cdn.syncfusion.com/ej2/ej2-base/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="https://cdn.syncfusion.com/ej2/ej2-buttons/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="https://cdn.syncfusion.com/ej2/ej2-splitbuttons/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="https://cdn.syncfusion.com/ej2/ej2-dropdowns/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="https://cdn.syncfusion.com/ej2/ej2-inputs/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="https://cdn.syncfusion.com/ej2/ej2-popups/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="https://cdn.syncfusion.com/ej2/ej2-calendars/styles/material.css" rel="stylesheet" type="text/css"/>
            <!-- Essential JS 2 query-builder material theme (Control Styles) -->
            <link href="https://cdn.syncfusion.com/ej2/ej2-querybuilder/styles/material.css" rel="stylesheet" type="text/css"/>

           <!-- Essential JS 2 query-builder's global script (Dependency Script) -->
            <script src="https://cdn.syncfusion.com/ej2/ej2-base/dist/global/ej2-base.min.js" type="text/javascript"></script>
            <script src="https://cdn.syncfusion.com/ej2/ej2-buttons/dist/global/ej2-buttons.min.js" type="text/javascript"></script>
            <script src="https://cdn.syncfusion.com/ej2/ej2-popups/dist/global/ej2-popups.min.js" type="text/javascript"></script>
            <script src="https://cdn.syncfusion.com/ej2/ej2-splitbuttons/dist/global/ej2-splitbuttons.min.js" type="text/javascript"></script>
            <script src="https://cdn.syncfusion.com/ej2/ej2-inputs/dist/global/ej2-inputs.min.js" type="text/javascript"></script>
            <script src="https://cdn.syncfusion.com/ej2/ej2-lists/dist/global/ej2-lists.min.js" type="text/javascript"></script>
            <script src="https://cdn.syncfusion.com/ej2/ej2-data/dist/global/ej2-data.min.js" type="text/javascript"></script>
            <script src="https://cdn.syncfusion.com/ej2/ej2-dropdowns/dist/global/ej2-dropdowns.min.js" type="text/javascript"></script>
             <script src="https://cdn.syncfusion.com/ej2/ej2-calendars/dist/global/ej2-calendars.min.js" type="text/javascript"></script>
            <!-- Essential JS 2 query-builder global script (Control Script) -->
            <script src="https://cdn.syncfusion.com/ej2/ej2-querybuilder/dist/global/ej2-querybuilder.min.js" type="text/javascript"></script>
       </head>
       <body>
           <!-- Add the HTML div element  -->
             <div id="querybuilder" class="row">
            <script>
                var columnData = [
                    { field: 'EmployeeID', label: 'Employee ID', type: 'number' },
                    { field: 'FirstName', label: 'First Name', type: 'string' },
                    { field: 'TitleOfCourtesy', label: 'Title Of Courtesy', type: 'boolean', values: ['Mr.', 'Mrs.']},
                    { field: 'Title', label: 'Title', type: 'string' },
                    { field: 'HireDate', label: 'Hire Date', type: 'date', format: 'dd/MM/yyyy' },
                    { field: 'Country', label: 'Country', type: 'string' },
                    { field: 'City', label: 'City', type: 'string' }
                ];
                var qryBldrObj = new ej.querybuilder.QueryBuilder({
                    width: '70%',
                    columns: columnData
                });
                qryBldrObj.appendTo('#querybuilder');
            </script>
       </body>
  </html>

```

{% endtab %}

**Step 4:** Now, run the `index.html` in web browser, it will render the `Syncfusion JavaScript Query Builder` control.

### Rendering with rule

Now, add the `Query Builder` and initiate the `Syncfusion JavaScript (ES5) Query Builder` control with rule in the `~/quickstart/index.html` by using following code

```html
<!DOCTYPE html>
<html xmlns="http://www.w3.org/1999/xhtml">
    <head>
        <title>Essential JS 2</title>
         <!-- Essential JS 2 query-builder's dependency style -->
        <link href="resources/base/material.css" rel="stylesheet" type="text/css"/>
        <link href="resources/buttons/material.css" rel="stylesheet" type="text/css"/>
        <link href="resources/splitbuttons/material.css" rel="stylesheet" type="text/css"/>
        <link href="resources/dropdowns/material.css" rel="stylesheet" type="text/css"/>
        <link href="resources/inputs/material.css" rel="stylesheet" type="text/css"/>
        <link href="resources/calendars/material.css" rel="stylesheet" type="text/css"/>
         <link href="resources/popups/material.css" rel="stylesheet" type="text/css"/>
        <!-- Essential JS 2 query-builder material theme (Control Styles) -->
        <link href="resources/querybuilder/material.css" rel="stylesheet" type="text/css"/>

        <!-- Essential JS 2 query-builder's global script (Dependency Script) -->
        <script src="resources/base/ej2-base.min.js" type="text/javascript"></script>
        <script src="resources/buttons/ej2-buttons.min.js" type="text/javascript"></script>
        <script src="resources/splitbuttons/ej2-splitbuttons.min.js" type="text/javascript"></script>
        <script src="resources/dropdowns/ej2-dropdowns.min.js" type="text/javascript"></script>
        <script src="resources/inputs/ej2-inputs.min.js" type="text/javascript"></script>
        <script src="resources/calendars/ej2-calendars.min.js" type="text/javascript"></script>
        <script src="resources/popups/ej2-popups.min.js" type="text/javascript"></script>
        <!-- Essential JS 2 query-builder global script (Control Script) -->
        <script src="resources/querybuilder/ej2-querybuilder.min.js" type="text/javascript"></script>
    </head>
    <body>
        <!-- Add the HTML div element  -->
        <div id="querybuilder" class="row">
        <script>
        var columnData = [
            { field: 'EmployeeID', label: 'Employee ID', type: 'number' },
            { field: 'FirstName', label: 'First Name', type: 'string' },
            { field: 'TitleOfCourtesy', label: 'Title Of Courtesy', type: 'boolean', values: ['Mr.', 'Mrs.']},
            { field: 'Title', label: 'Title', type: 'string' },
            { field: 'HireDate', label: 'Hire Date', type: 'date', format: 'dd/MM/yyyy' },
            { field: 'Country', label: 'Country', type: 'string' },
            { field: 'City', label: 'City', type: 'string' }
        ];
        var importRules = {
            'condition': 'and',
            'rules': [{
                    'label': 'Employee ID',
                    'field': 'EmployeeID',
                    'type': 'number',
                    'operator': 'equal',
                    'value': 1001
                },
                {
                    'label': 'Title',
                    'field': 'Title',
                    'type': 'string',
                    'operator': 'equal',
                    'value': 'Sales Manager'
                }
            ]
        };

        var employeeData = [{
      'EmployeeID': 1,
      'FirstName': 'Nancy',
      'Title': 'Sales Representative',
      'TitleOfCourtesy': 'Ms.',
      'HireDate': '22/07/2001',
      'City': 'Seattle',
      'Country': 'USA'
    },
    {
      'EmployeeID': 2,
      'FirstName': 'Andrew',
      'Title': 'Vice President',
      'TitleOfCourtesy': 'Dr.',
      'HireDate': '21/04/2003',
      'City': 'Tacoma',
      'Country': 'USA'
    },
    {
      'EmployeeID': 3,
      'FirstName': 'Janet',
      'Title': 'Sales Representative',
      'TitleOfCourtesy': 'Ms.',
      'HireDate': '22/07/2001',
      'City': 'Kirkland',
      'Country': 'USA'
    }];

        var qryBldrObj = new ej.querybuilder.QueryBuilder({
            width: '70%',
            dataSource: employeeData,
            columns: columnData,
            rule: importRules,
        });
        qryBldrObj.appendTo('#querybuilder');
        </script>
    </body>
</html>
```

Now, add the `Query Builder` and initiate the `Syncfusion JavaScript (ES5) Query Builder` control with rule in the index.html by using following code.

{% tab template="query-builder/es5-getting-started", sourceFiles="index.html", isDefaultActive=true %}

```html
<!DOCTYPE html>
  <html xmlns="http://www.w3.org/1999/xhtml">
       <head>
            <title>Essential JS 2</title>

             <!-- Essential JS 2 query-builder's dependency style -->
            <link href="https://cdn.syncfusion.com/ej2/ej2-base/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="https://cdn.syncfusion.com/ej2/ej2-buttons/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="https://cdn.syncfusion.com/ej2/ej2-splitbuttons/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="https://cdn.syncfusion.com/ej2/ej2-dropdowns/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="https://cdn.syncfusion.com/ej2/ej2-inputs/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="https://cdn.syncfusion.com/ej2/ej2-popups/styles/material.css" rel="stylesheet" type="text/css"/>
            <link href="https://cdn.syncfusion.com/ej2/ej2-calendars/styles/material.css" rel="stylesheet" type="text/css"/>
            <!-- Essential JS 2 query-builder material theme (Control Styles) -->
            <link href="https://cdn.syncfusion.com/ej2/ej2-querybuilder/styles/material.css" rel="stylesheet" type="text/css"/>

           <!-- Essential JS 2 query-builder's global script (Dependency Script) -->
            <script src="https://cdn.syncfusion.com/ej2/ej2-base/dist/global/ej2-base.min.js" type="text/javascript"></script>
            <script src="https://cdn.syncfusion.com/ej2/ej2-buttons/dist/global/ej2-buttons.min.js" type="text/javascript"></script>
            <script src="https://cdn.syncfusion.com/ej2/ej2-popups/dist/global/ej2-popups.min.js" type="text/javascript"></script>
            <script src="https://cdn.syncfusion.com/ej2/ej2-splitbuttons/dist/global/ej2-splitbuttons.min.js" type="text/javascript"></script>
            <script src="https://cdn.syncfusion.com/ej2/ej2-inputs/dist/global/ej2-inputs.min.js" type="text/javascript"></script>
            <script src="https://cdn.syncfusion.com/ej2/ej2-lists/dist/global/ej2-lists.min.js" type="text/javascript"></script>
            <script src="https://cdn.syncfusion.com/ej2/ej2-data/dist/global/ej2-data.min.js" type="text/javascript"></script>
            <script src="https://cdn.syncfusion.com/ej2/ej2-dropdowns/dist/global/ej2-dropdowns.min.js" type="text/javascript"></script>
            <script src="https://cdn.syncfusion.com/ej2/ej2-calendars/dist/global/ej2-calendars.min.js" type="text/javascript"></script>

            <!-- Essential JS 2 query-builder global script (Control Script) -->
            <script src="https://cdn.syncfusion.com/ej2/ej2-querybuilder/dist/global/ej2-querybuilder.min.js" type="text/javascript"></script>
       </head>
       <body>
           <!-- Add the HTML div element  -->
             <div id="querybuilder" class="row">
            <script>
                var columnData = [
                    { field: 'EmployeeID', label: 'Employee ID', type: 'number' },
                    { field: 'FirstName', label: 'First Name', type: 'string' },
                    { field: 'TitleOfCourtesy', label: 'Title Of Courtesy', type: 'boolean', values: ['Mr.', 'Mrs.']},
                    { field: 'Title', label: 'Title', type: 'string' },
                    { field: 'HireDate', label: 'Hire Date', type: 'date', format: 'dd/MM/yyyy' },
                    { field: 'Country', label: 'Country', type: 'string' },
                    { field: 'City', label: 'City', type: 'string' }
                ];
                var importRules = {
                    'condition': 'and',
                    'rules': [{
                            'label': 'Employee ID',
                            'field': 'EmployeeID',
                            'type': 'number',
                            'operator': 'equal',
                            'value': 1001
                        },
                        {
                            'label': 'Title',
                            'field': 'Title',
                            'type': 'string',
                            'operator': 'equal',
                            'value': 'Sales Manager'
                        }
                    ]
                };

                var employeeData = [{
      'EmployeeID': 1,
      'FirstName': 'Nancy',
      'Title': 'Sales Representative',
      'TitleOfCourtesy': 'Ms.',
      'HireDate': '22/07/2001',
      'City': 'Seattle',
      'Country': 'USA'
    },
    {
      'EmployeeID': 2,
      'FirstName': 'Andrew',
      'Title': 'Vice President',
      'TitleOfCourtesy': 'Dr.',
      'HireDate': '21/04/2003',
      'City': 'Tacoma',
      'Country': 'USA'
    },
    {
      'EmployeeID': 3,
      'FirstName': 'Janet',
      'Title': 'Sales Representative',
      'TitleOfCourtesy': 'Ms.',
      'HireDate': '22/07/2001',
      'City': 'Kirkland',
      'Country': 'USA'
    }];

var qryBldrObj = new ej.querybuilder.QueryBuilder({
                    width: '70%',
                    dataSource: employeeData,
                    columns: columnData,
                    rule: importRules,
                });
                qryBldrObj.appendTo('#querybuilder');
            </script>
       </body>
  </html>

```

{% endtab %}
