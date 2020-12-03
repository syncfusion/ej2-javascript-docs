# Change animation settings

To change the animation of the ContextMenu, [`animationSettings`](../../api/context-menu/menuAnimationSettingsModel) property is used. The supported effects for ContextMenu are,

| Effect | Functionality |
| ------------ | ----------------------- |
| None | Specifies the sub menu transform with no animation effect. |
| SlideDown | Specifies the sub menu transform with slide down effect. |
| ZoomIn | Specifies the sub menu transform with zoom in effect. |
| FadeIn | Specifies the sub menu transform with fade in effect. |

The following sample illustrates how to open ContextMenu with `FadeIn` effect with the `duration` of `800ms`.

{% tab template= "context-menu/getting-started", sourceFiles="app.ts,index.html,styles.css",
es5Template="animation-template" %}

```typescript
import { ContextMenu, MenuItemModel, ContextMenuModel } from '@syncfusion/ej2-navigations';
import { enableRipple } from '@syncfusion/ej2-base';

enableRipple(true);

// Initialize menu items.
let menuItems: MenuItemModel[] = [
        {
            text: 'Show All Bookmarks',
        },
        {
            text: 'Bookmarks Toolbar',
            items: [
                {
                    text: 'Most Visited',
                    items: [
                    {
                        text: 'Google',
                    },
                    {
                        text: 'Gmail'
                    }]
                },
                {
                    text: 'Recently Added'
                }
            ]
        }];

// Initialize ContextMenu options.
let menuOptions: ContextMenuModel = {
        target: '#target',
        items: menuItems,
        animationSettings: {
            effect: 'FadeIn',
            duration: 800
        }
    };

// Initialize ContextMenu component.
let menuObj: ContextMenu = new ContextMenu(menuOptions, '#contextmenu');

```

{% endtab %}
