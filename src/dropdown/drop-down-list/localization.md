---
title: "Drop-down list Localization"
component: "DropDownList"
description: "This section explains the localization support of the Syncfusion JavaScript drop-down list control."
---

# Localization

The Localization library allows you to localize static text content of the
[noRecordsTemplate](../api/drop-down-list/#norecordstemplate)
 and [actionFailureTemplate](../api/drop-down-list/#actionfailuretemplate)
&nbsp;properties according to the culture currently assigned to the DropDownList.

| Locale key | en-US (default)  |
|------|------|
| noRecordsTemplate |  No records found |
| actionFailureTemplate | The request failed |

## Loading translations

To load translation object to your application, use load function of the **L10n** class.

In the following sample, French culture is set to the DropDownList and no data is loaded. Hence, the [`noRecordsTemplate`](../api/drop-down-list/#norecordstemplate) property displays its text in French culture initially, and if the sample is run offline, the [`actionFailureTemplate`](../api/drop-down-list/#actionfailuretemplate) property displays its text appropriately.

{% tab template="dropdownlist/basic", es5Template="basic-locale" %}

```typescript

import { DropDownList } from '@syncfusion/ej2-dropdowns';
// import L10n class for load function
import { L10n, setCulture} from '@syncfusion/ej2-base';
import { DataManager, ODataV4Adaptor, Query } from '@syncfusion/ej2-data';

// bind remotedata to showcase actionFailureTemplate in offline.
let customerData: DataManager = new DataManager({
    url: 'https://services.odata.org/V4/Northwind/Northwind.svc/Customers',
    adaptor: new ODataV4Adaptor,
    crossDomain: true
});

let dropDownObj: DropDownList = new DropDownList({
    dataSource: customerData,
    // set locale culture to DropDownList
    locale: 'fr-BE',
    // map appropriate column
    fields: { text: 'ContactName', value: 'CustomerID' },
    // take 0 item to showcase noRecordsTemplate property.
    query: new Query().select(['ContactName', 'CustomerID']).take(0);
    // set placeholder to DropDownList input element
    placeholder: 'Sélectionnez un élément'
});
dropDownObj.appendTo('#ddlelement');

L10n.load({
    'fr-BE': {
       'dropdowns': {
             'noRecordsTemplate': "Aucun enregistrement trouvé",
             'actionFailureTemplate': "Modèle d'échec d'action"
         }
     }
});

```

{% endtab %}

## See Also

* [Accessibility](./accessibility)
* [How to bind the data to the combobox](./data-binding)