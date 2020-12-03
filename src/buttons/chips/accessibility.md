# Accessibility

## Keyboard interaction

The following shortcut keys are used to access the Chip control without any interruption.

| Keyboard shortcuts | Actions |
|------------|-------------------|
| <kbd>Enter</kbd> | Selects the targeted chip from the ChipList/ChipCollection. |
| <kbd>Delete</kbd> | Deletes the targeted chip from the ChipList/ChipCollection. |

{% tab template= "chips/accessibility", sourceFiles="app.ts,index.html,styles.css",
es5Template="es5-accessibility" isDefaultActive=true %}

```typescript
import { ChipList } from '@syncfusion/ej2-buttons';

// Initialize and Render Chip control

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
    ],
 enableDelete: true }, '#chip');
```

{% endtab %}