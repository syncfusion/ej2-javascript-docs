# Localization

Localization library allows you to localize the text content of the Syncfusion JavaScript (ES5) control.

## Loading translations

To load translation object in your application use [`load`](../api/base/l10n#load) function of `L10n` class.

{% tab template="common/locale", es5Template="locale" %}

```javascript
import { L10n } from '@syncfusion/ej2-base';
import { Grid, Group, Page } from '@syncfusion/ej2-grids';
import { data } from './datasource.ts';

Grid.Inject(Group, Page);

L10n.load({
    'de-DE': {
        'grid': {
            'EmptyRecord': 'Keine Aufzeichnungen angezeigt',
            'GroupDropArea': 'Ziehen Sie einen Spaltenkopf hier, um die Gruppe ihre Spalte',
            'UnGroup': 'Klicken Sie hier, um die Gruppierung aufheben',
            'EmptyDataSourceError': 'DataSource darf bei der Erstauslastung nicht leer sein, da Spalten aus der dataSource im AutoGenerate Spaltenraster',
            'Item': 'Artikel',
            'Items': 'Artikel'
        },
        'pager': {
            'currentPageInfo': '{0} von {1} Seiten',
            'totalItemsInfo': '({0} Beiträge)',
            'firstPageTooltip': 'Zur ersten Seite',
            'lastPageTooltip': 'Zur letzten Seite',
            'nextPageTooltip': 'Zur nächsten Seite',
            'previousPageTooltip': 'Zurück zur letzten Seit',
            'nextPagerTooltip': 'Zum nächsten Pager',
            'previousPagerTooltip': 'Zum vorherigen Pager'
        }
    }
});

let grid: Grid = new Grid({
    dataSource: data,
    locale: 'de-DE',
    allowGrouping: true,
    allowPaging: true,
    pageSettings: { pageSize: 6 },
    columns: [
        { field: 'OrderID', headerText: 'Order ID', textAlign: 'Right', width: 120 },
        { field: 'CustomerID', headerText: 'Customer ID', width: 150 },
        { field: 'ShipCity', headerText: 'Ship City', width: 150 },
        { field: 'ShipName', headerText: 'Ship Name', width: 150 }
    ],
    height: 210
});
grid.appendTo('#Grid');

```
{% endtab %}

## Changing current locale

Current locale can be changed for all the Syncfusion JavaScript (ES5) controls in your application by invoking
 `setCulture` function with your desired culture name.

```javascript
ej.base.enableRipple(true);
var L10n  = new ej.base.L10n();
var setCulture = new ej.base.setCulture();

L10n.load({
    'fr-BE': {
       'Button': {
             'id': 'Numéro de commande',
             'date':'Date de commande'
         }
     }
});
setCulture('fr-BE');
```

> Note: Before changing a culture globally, ensure that locale text for the concerned culture is loaded through `L10n.load` function.
