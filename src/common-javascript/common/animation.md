# Animation

The **Animation** library is used to perform animation effects on HTML elements by running sequence of frames.

## Animating a HTML Element

The [`animate`](../api/base/animation/#animate) method of `Animation` library
can be used to animate the HTML elements. This method can also take additional
[`AnimationModel`](../api/base/animationModel). Refer to the following code snippet
to animate a multiple DOM element.

{% tab template="common/animation-multiple", es5Template="animation-template1", isDefaultActive=true %}

```javascript
ej.base.enableRipple(true);
var animation  = new ej.base.Animation({duration: 5000 });
grid.animate('#element1', { name: 'FadeOut' });
grid.animate('#element1', { name: 'FadeOut' });
```

{% endtab %}