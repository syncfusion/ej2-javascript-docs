# Chip Customization

This section explains the customization of styles, leading icons, avatar, and trailing icons in Chip control.

## Styles

The Chip control has the following predefined styles that can be defined using the `cssClass` property.

| Class | Description |
| -------- | -------- |
| e-primary | Represents a primary chip. |
| e-success | Represents a positive chip. |
| e-info |  Represents an informative chip. |
| e-warning | Represents a chip with caution. |
| e-danger | Represents a negative chip. |

{% tab template= "chips/customization", sourceFiles="app.ts,index.html,styles.css",
es5Template="es5-styles" isDefaultActive=true %}

```typescript

import { ChipList } from '@syncfusion/ej2-buttons';
new ChipList({chips:  [{
        "text": "Apple",
        "cssClass": "e-primary"
    },
    {
        "text": "Microsoft",
        "cssClass": "e-info"
    },
    {
        "text": "Google",
        "cssClass": "e-success"
    },
    {
        "text": "Tesla",
        "cssClass": "e-warning"
    },
    {
        "text": "Intel",
        "cssClass": "e-danger"
    }
] }, '#chip');

```

{% endtab %}

## Leading Icon

You can add and customize the leading icon of chip using the `leadingIconCss` property.

{% tab template= "chips/customization", sourceFiles="app.ts,index.html,styles.css",
es5Template="es5-leading" isDefaultActive=true %}

```typescript

import { ChipList } from '@syncfusion/ej2-buttons';
new ChipList({chips: [{
      "text": "Anne",
      "leadingIconCss": "andrew"
  },
  {
      "text": "Janet",
      "leadingIconCss": "janet"
  },
  {
      "text": "Laura",
      "leadingIconCss": "laura"
  },
  {
      "text": "Margaret",
      "leadingIconCss": "margaret"
  }
]}, '#chip');

```

{% endtab %}

## Avatar

You can add and customize the avatar of chip using the `avatarIconCss` property.

{% tab template= "chips/customization", sourceFiles="app.ts,index.html,styles.css",
es5Template="es5-avatar" isDefaultActive=true %}

```typescript

import { ChipList } from '@syncfusion/ej2-buttons';
new ChipList({chips: [{
      "text": "Anne",
      "avatarIconCss": "andrew"
  },
  {
      "text": "Janet",
      "avatarIconCss": "janet"
  },
  {
      "text": "Laura",
      "avatarIconCss": "laura"
  },
  {
      "text": "Margaret",
      "avatarIconCss": "margaret"
  }
]}, '#chip');

```

{% endtab %}

## Avatar Content

You can add and customize the avatar content of chip using the `avatarText` property.

{% tab template= "chips/customization", sourceFiles="app.ts,index.html,styles.css",
es5Template="es5-content" isDefaultActive=true %}

```typescript

import { ChipList } from '@syncfusion/ej2-buttons';
new ChipList({chips: [{
            "text": "Anne",
            "avatarText": "A"
        },
        {
            "text": "Janet",
            "avatarText": "J"
        },
        {
            "text": "Laura",
            "avatarText": "L"
        },
        {
            "text": "Margaret",
            "avatarText": "M"
        }
]}, '#chip');

```

{% endtab %}

## Trailing Icon

You can add and customize the trailing icon of chip using the `trailingIconCss` property.

{% tab template= "chips/customization", sourceFiles="app.ts,index.html,styles.css",
es5Template="es5-trailing" isDefaultActive=true %}

```typescript

import { ChipList } from '@syncfusion/ej2-buttons';
new ChipList({chips: [{
            "text": "Anne",
            "trailingIconCss": "e-dlt-btn"
        },
        {
            "text": "Janet",
            "trailingIconCss": "e-dlt-btn"
        },
        {
            "text": "Laura",
            "trailingIconCss": "e-dlt-btn"
        },
        {
            "text": "Margaret",
            "trailingIconCss": "e-dlt-btn"
        }
]}, '#chip');

```

{% endtab %}

## Outline Chip

Outline chip has the border with the background transparent. It can be set using the `cssClass` property.

{% tab template= "chips/customization", sourceFiles="app.ts,index.html,styles.css",
es5Template="es5-outline" isDefaultActive=true %}

```typescript

import { ChipList } from '@syncfusion/ej2-buttons';
new ChipList({chips: ['Chai', 'Chang', 'Aniseed Syrup ', 'Ikura'],
    cssClass: 'e-outline'}, '#chip');

```

{% endtab %}
