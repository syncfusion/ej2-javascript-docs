# Navigation Lines

The navigation lines are used to denote the path between two locations. This feature can be used to draw flight or sea routes. Navigation lines are enabled by setting the [`visible`](../api/maps/navigationLineSettingsModel/#visible) property of the [`navigationLineSettings`](../api/maps/navigationLineSettingsModel) property to **true**.

## Customization

The following properties are available in [`navigationLineSettings`](../api/maps/navigationLineSettingsModel/) property to customize the navigation line of the Maps component.

* [`color`](../api/maps/navigationLineSettingsModel/#color) - To apply the color for navigation lines in Maps.
* [`dashArray`](../api/maps/navigationLineSettingsModel/#dasharray) - To define the pattern of dashes and gaps that is applied to the outline of the navigation lines.
* [`width`](../api/maps/navigationLineSettingsModel/#width) - To customize the width of the navigation lines.
* [`angle`](../api/maps/navigationLineSettingsModel/#angle) - To customize the angle of the navigation lines.
* [`highlightSettings`](../api/maps/navigationLineSettingsModel/#highlightsettings) - To customize the highlight settings of the navigation line.
* [`selectionSettings`](../api/maps/navigationLineSettingsModel/#selectionsettings) - To customize the selection settings of the navigation line.

{% tab template= "maps/default-map", es5Template="navigation" %}

{% endtab %}

## Enabling the arrows

To enable the arrow in the navigation line, set the [`showArrow`](../api/maps/arrowModel/#showarrow) property of [`arrowSettings`](../api/maps/navigationLineSettingsModel/#arrowsettings) property to **true**. The following properties are available in [`arrowSettings`](../api/maps/navigationLineSettingsModel/#arrowsettings) property to customize the arrow of the navigation lines.

* [`color`](../api/maps/arrowModel/#color) - To apply the color for arrow of the navigation line.
* [`offset`](../api/maps/arrowModel/#offset) - To customize the offset position of the arrow of the navigation line.
* [`position`](../api/maps/arrowModel/#position) - To customize the position of the arrow in navigation line. The possible values can be **Start** and **End**.
* [`size`](../api/maps/arrowModel/#size) - To customize the size of the arrow in pixels.

{% tab template= "maps/default-map", es5Template="arrowSettings" %}

{% endtab %}