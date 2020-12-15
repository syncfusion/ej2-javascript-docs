---
title: "Overview Control"
component: "Diagram"
description: "Overview control allows you to see a preview or an overall view of the entire content of a diagram."
---

# Overview Control

Overview control allows you to see a preview or an overall view of the entire content of a diagram. This helps you to look at the overall picture of a large diagram and also to navigate, pan, or zoom, on a particular position of the page.

When you work on a very large diagram, you may not know the part you are actually working on, or navigation from one part to another might be difficult. One solution for navigation is to zoom out the entire diagram and find where you are. Then, you can zoom in a particular area you want to. This solution is not suitable when you need some frequent navigation.

Overview control solves these problems by showing a preview, that is, an overall view of the entire diagram. A rectangle indicates viewport of the diagram. Navigation becomes easy by dragging this rectangle.

## Create overview

The `sourceID` property of overview should be set with the corresponding diagram ID for the overall view.

The `width` and `height` properties of the overview allow you to define the size of the overview.

The following code illustrates how to create overview.

### Zoom and Pan

In overview, the view port of the diagram is highlighted with a red colored rectangle. Diagram can be zoomed/panned by interacting with that. You can interact with overview as follows:

* Resize the rectangle: Zooms in/out the diagram.
* Drag the rectangle: Pans the diagram.
* Click at a position: Navigates to the clicked region.
* Choose a particular region by clicking and dragging: Navigates to the specified region.

The following image shows how the diagram is zoomed/panned with overview.

{% tab template= "diagram/overView", es5Template="es5Node" %}

```typescript

import {
    Diagram,
    ConnectorModel,
    Overview,
    OverviewModel
} from '@syncfusion/ej2-diagrams';
import {
    DataManager,
    Query
} from '@syncfusion/ej2-data';
import {
    TreeInfo,
    Node,
    StackPanel,
    ImageElement,
    Container,
    TextElement,
    DataBinding,
    HierarchicalTree
} from '@syncfusion/ej2-diagrams';
/**
 * Overview
 */
let diagram: Diagram;
let overview: Overview;

Diagram.Inject(DataBinding, HierarchicalTree);
let data: object[] = [{
        'Id': 'parent',
        'Name': 'Maria Anders',
        'Designation': 'Managing Director',
        'IsExpand': 'true',
        'RatingColor': '#C34444'
    },
    {
        'Id': 1,
        'Name': 'Ana Trujillo',
        'Designation': 'Project Manager',
        'IsExpand': 'false',
        'RatingColor': '#68C2DE',
        'ReportingPerson': 'parent'
    },
    {
        'Id': 2,
        'Name': 'Anto Moreno',
        'Designation': 'Project Lead',
        'IsExpand': 'false',
        'RatingColor': '#93B85A',
        'ReportingPerson': 'parent'
    },
    {
        'Id': 3,
        'Name': 'Thomas Hardy',
        'Designation': 'Senior S/w Engg',
        'IsExpand': 'false',
        'RatingColor': '#68C2DE',
        'ReportingPerson': 1
    },
    {
        'Id': 4,
        'Name': 'Christina kaff',
        'Designation': 'S/w Engg',
        'IsExpand': 'false',
        'RatingColor': '#93B85A',
        'ReportingPerson': 2
    },
    {
        'Id': 5,
        'Name': 'Hanna Moos',
        'Designation': 'Project Trainee',
        'IsExpand': 'true',
        'RatingColor': '#D46E89',
        'ReportingPerson': 2
    },
];

let items: DataManager = new DataManager(data as JSON[], new Query().take(7));
// Initializes the diagram control
diagram = new Diagram({
    snapSettings: {
        constraints: 0
    },
    layout: {
        type: 'OrganizationalChart',
        margin: {
            top: 20
        },
        getLayoutInfo: (node: Node, tree: TreeInfo) => {
            if (!tree.hasSubTree) {
                tree.orientation = 'Vertical';
                tree.type = 'Alternate';
            }
        }
    },
    dataSourceSettings: {
        id: 'Id',
        parentId: 'ReportingPerson',
        dataManager: items
    },
      getNodeDefaults: (node: NodeModel) => {
        node.height = 50;
        node.style.fill =  '#6BA5D7';
        node.style.borderColor = 'white';
        node.style.strokeColor =  'white';
        return  node;
    },
        getConnectorDefaults: (obj: ConnectorModel): ConnectorModel => {
        obj.style.strokeColor =  '#6BA5D7';
        obj.style.fill =  '#6BA5D7';
        obj.style.strokeWidth =  2;
        obj.targetDecorator.style.fill =  '#6BA5D7';
        obj.targetDecorator.style.strokeColor =  '#6BA5D7';
        obj.targetDecorator.shape = 'None';
        obj.type = 'Orthogonal';
        return  obj;
    },
    setNodeTemplate: (obj: Node, diagram: Diagram): Container => {
        let content: StackPanel = new StackPanel();
        content.id = obj.id + '_outerstack';
        content.style.strokeColor = 'darkgreen';
        content.style.fill = '#6BA5D7';
        content.orientation = 'Horizontal';
        content.padding = {
            left: 5,
            right: 10,
            top: 5,
            bottom: 5
        };
        let innerStack: StackPanel = new StackPanel();
        innerStack.style.strokeColor = 'none';
        innerStack.style.fill = '#6BA5D7';
        innerStack.margin = {
            left: 5,
            right: 0,
            top: 0,
            bottom: 0
        };
        innerStack.id = obj.id + '_innerstack';
        let text: TextElement = new TextElement();
        text.content = obj.data['Name'];
        text.style.color = 'white';
        text.style.strokeColor = 'none';
        text.style.fill = 'none';
        text.id = obj.id + '_text1';
        let desigText: TextElement = new TextElement();
        desigText.margin = {
            left: 0,
            right: 0,
            top: 5,
            bottom: 0
        };
        desigText.content = obj.data['Designation'];
        desigText.style.color = 'white';
        desigText.style.strokeColor = 'none';
        desigText.style.fill = 'none';
        desigText.style.textWrapping = 'Wrap';
        desigText.id = obj.id + '_desig';
        innerStack.children = [text, desigText];
        content.children = [innerStack];
        return content;
    }
});

diagram.appendTo('#element');
// Initializes the overview control
let options: OverviewModel = {};
// Relates diagram with overview
options.sourceID = 'element';
overview = new Overview(options);
overview.appendTo('#overview');

```

{% endtab %}
