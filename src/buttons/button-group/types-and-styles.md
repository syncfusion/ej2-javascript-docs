---
title: "ButtonGroup Types and Styles"
component: "ButtonGroup"
description: "ButtonGroup CSS component supports outline type and predefined styles."
---

# Types and Styles

This section explains about different types and styles of ButtonGroup.

## ButtonGroup types

### Outline ButtonGroup

An Outline ButtonGroup has a border with transparent background. To create an Outline ButtonGroup, `e-outline` class should be added to the target element and also add `e-outline` and `e-btn` class to each button elements.

The following sample illustrates how to achieve an Outline ButtonGroup.
{% tab template= "button-group/types", sourceFiles="index.html,styles.css", isDefaultActive=true %}

{% endtab %}

> ButtonGroup does not have support for `flat` and `round` types.

## ButtonGroup styles

The Essential JS 2 ButtonGroup has the following predefined styles. This can be achieved by adding corresponding class name in each button elements.

| Class | Description |
| -------- | -------- |
| e-primary | Used to represent a primary action. |
| e-success | Used to represent a positive action. |
| e-info | Used to represent an informative action. |
| e-warning | Used to represent an action with caution. |
| e-danger | Used to represent a negative action. |

The following example illustrates how to achieve predefined styles in ButtonGroup.

{% tab template= "button-group/styles", sourceFiles="index.html,styles.css" %}

{% endtab %}

> Predefined ButtonGroup styles provide only the visual indication. So,
ButtonGroup content should define the ButtonGroup style for the users of assistive technologies such as screen readers.

## See Also

* [ButtonGroup with icons](./how-to/create-buttongroup-with-icons)
* [Create ButtonGroup with rounded corner](./how-to/create-buttongroup-with-rounded-corner)