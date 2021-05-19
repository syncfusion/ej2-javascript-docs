---
title: "Kanban Globalization"
component: "Kanban"
description: "This section explains how to apply localization (l10n) based on culture file and right-to-left (RTL) in Kanban board."
---

# Globalization

The localization library allows you to localize the default text content of the Kanban to different cultures using the `locale` property.

In Kanban, total count and min or max count text alone will be localized based on culture.

| Locale key | en-US (default)  |
|------|------|
| items |  items |
| min |  Min |
| max |  Max |
| cardsSelected | Cards Selected |
| addTitle | Add New Card |
| editTitle | Edit Card Details |
| deleteTitle | Delete Card |
| deleteContent | Are you sure you want to delete this card? |
| save | Save |
| delete | Delete |
| cancel | Cancel |
| yes | Yes |
| no | No |
| close | Close |
| noCard | No cards to display |
| unassigned | Unassigned |

## Loading translations

To load translation object in an application, use `load` function of `L10n` class.

The following example demonstrates the Kanban in `Deutsch` culture.

{% tab template="kanban/locale", es5Template="locale", sourceFiles="index.ts,index.html,datasource.ts"%}

```typescript
import { Kanban } from '@syncfusion/ej2-kanban';
import { L10n } from '@syncfusion/ej2-base';
import { kanbanData } from './datasource.ts';

L10n.load({
    'de': {
        'kanban': {
            'items': 'Artikel',
            'min': 'Min',
            'max': 'Max',
            'cardsSelected': 'Karten ausgewählt',
            'addTitle': 'Neue Karte hinzufügen',
            'editTitle': 'Kartendetails bearbeiten',
            'deleteTitle': 'Karte löschen',
            'deleteContent': 'Möchten Sie diese Karte wirklich löschen?',
            'save': 'speichern',
            'delete': 'Löschen',
            'cancel': 'Stornieren',
            'yes': 'Ja',
            'no': 'Nein',
            'close': 'Schließen',
            'noCard': 'Keine Karten zum Anzeigen',
            'unassigned': 'nicht zugewiesen'
        }
    }
});

let kanbanObj: Kanban = new Kanban({
    dataSource: kanbanData,
    keyField: 'Status',
    locale: 'de',
    columns: [
        { headerText: 'Backlog', keyField: 'Open', showItemCount: true, minCount: 6 },
        { headerText: 'In Progress', keyField: 'InProgress', showItemCount: true, maxCount: 3 },
        { headerText: 'Done', keyField: 'Close', showItemCount: true }
    ],
    cardSettings: {
        contentField: 'Summary',
        headerField: 'Id'
    },
    swimlaneSettings: {
        keyField: 'Assignee'
    },
});
kanbanObj.appendTo('#Kanban');
```

{% endtab %}

## Right to left (RTL)

The Kanban provides an option to switch its text direction and layout from right to left. It improves the user experiences and accessibility for users who use right-to-left languages (Arabic, Farsi, Urdu, etc.). To enable right-to-left mode in Kanban, set the `enableRtl` to true.

{% tab template="kanban/rtl", es5Template="rtl", sourceFiles="index.ts,index.html,datasource.ts"%}

```typescript
import { Kanban } from '@syncfusion/ej2-kanban';
import { L10n, enableRtl} from '@syncfusion/ej2-base';
import { kanbanData } from './datasource.ts';

L10n.load({
    'ar': {
        'kanban': {
            'items': 'العناصر',
            'min': 'أنا',
            'max': 'ماكس',
            'cardsSelected': 'تم تحديد البطاقات',
            'addTitle': 'إضافة بطاقة جديدة',
            'editTitle': 'تحرير تفاصيل البطاقة',
            'deleteTitle': 'حذف البطاقة',
            'deleteContent': 'هل أنت متأكد أنك تريد حذف هذه البطاقة؟',
            'save': 'حفظ',
            'delete': 'حذف',
            'cancel': 'إلغاء',
            'yes': 'نعم',
            'no': 'لا',
            'close': 'قريب',
            'noCard': 'لا توجد بطاقات لعرضها',
            'unassigned': 'غير معين'
        }
    }
});

let kanbanObj: Kanban = new Kanban({
    dataSource: kanbanData,
    keyField: 'Status',
    enableRtl: true,
    locale: 'ar',
    columns: [
        { headerText: 'Backlog', keyField: 'Open', showItemCount: true, minCount: 2 },
        { headerText: 'In Progress', keyField: 'InProgress', showItemCount: true, maxCount: 3 },
        { headerText: 'Done', keyField: 'Close', showItemCount: true }
    ],
    cardSettings: {
        contentField: 'Summary',
        headerField: 'Id'
    },
    swimlaneSettings: {
        keyField: 'Assignee'
    }
});
kanbanObj.appendTo('#Kanban');
```

{% endtab %}
