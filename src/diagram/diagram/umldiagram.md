---
title: "Uml Diagram Shapes"
component: "Diagram"
description: "Class diagram describes the attributes and operations of a class and also the constraints imposed on the system"
---

# Uml Diagram Shapes

## Uml Class Diagram Shapes

Class diagram is used to represent the static view of an application. The class diagrams are widely used in the modelling of object oriented systems because they are the only UML diagrams which can be mapped directly with object-oriented languages.
Diagram supports to generate the class diagram shapes from business logic.

The UML class diagram shapes are explained as follows.

## Class

* A class describes a set of objects that shares the same specifications of features, constraints, and semantics. To define a class object, you should define the classifier as [`class`](../api/diagram/umlClassifierShapeModel#class).

* Also, define the [`name`](../api/diagram/umlClassModel#name), [`attributes`](../api/diagram/umlClassModel#attributes), and [`methods`](../api/diagram/umlClassModel#methods) of the class using the class property of node.

* The attribute’s [`name`](../api/diagram/umlClassAttributeModel#name), [`type`](../api/diagram/umlClassAttributeModel#type), and [`scope`](../api/diagram/umlClassAttributeModel#scope) properties allow you to define the name, data type, and visibility of the attribute.

* The method’s [`name`](../api/diagram/umlClassMethodModel#name), [`parameters`](../api/diagram/umlClassMethodModel#parameters), [`type`](../api/diagram/umlClassMethodModel#type), and [`scope`](../api/diagram/umlClassMethodModel#scope) properties allow you to define the name, parameter, return type, and visibility of the methods.

* The method parameters object properties allow you to define the name and type of the parameter.

* The following code example illustrates how to create a class.

{% tab template= "diagram/umldiagramshapes", es5Template="es5class" %}

```typescript
import {
  Diagram,
  NodeModel,
  UmlClassifierShapeModel
} from "@syncfusion/ej2-diagrams";

let node: NodeModel = {
    id: "Patient",
    //Position of the node
    offsetX: 200,
    offsetY: 200,
    shape: {
      type: "UmlClassifier",
      //Define class object
      class: {
        name: "Patient",
        //Define class attributes
        attributes: [{ name: "accepted", type: "Date" }],
        //Define class methods
        methods: [{ name: "getHistory", type: "getHistory" }]
      },
      classifier: "Class"
    } as UmlClassifierShapeModel
};

//Initializes diagram control
let diagram: Diagram = new Diagram({
  width: '100%',
  height: '600px',
  //Add node
  nodes: [node]
});
diagram.appendTo("#element");
```

{% endtab %}

## Interface

* An Interface is a kind of classifier that represents a declaration of a set of coherent public features and obligations. To create an interface, define the classifier property as [`interface`](../api/diagram/umlClassifierShapeModel#interface).

* Also, define the [`name`](../api/diagram/umlInterfaceModel#name), [`attributes`](../api/diagram/umlInterfaceModel#attributes), and [`methods`](../api/diagram/umlInterfaceModel#methods) of the interface using the interface property of the node.

* The attribute’s name, type, and scope properties allow you to define the name, data type, and visibility of the attribute.

* The method’s name, parameter, type, and scope properties allow you to define the name, parameter, return type, and visibility of the methods.

* The method parameter object properties of name and type allows you to define the name and type of the parameter.

* The following code example illustrates how to create an interface.

{% tab template= "diagram/umldiagramshapes", es5Template="es5interface" %}

```typescript
import {
  Diagram,
  NodeModel,
  UmlClassifierShapeModel
} from "@syncfusion/ej2-diagrams";

let node: NodeModel = {
    id: "Patient",
    //Position of the node
    offsetX: 200,
    offsetY: 200,
    shape: {
      type: "UmlClassifier",
      //Define interface object
      interface: {
        name: "Patient",
        //Define interface attributes
        attributes: [{ name: "owner", type: "String[*]" }],
        //Define interface methods
        methods: [
          {
            name: "deposit",
            parameters: [
              {
                name: "amount",
                type: "Dollars"
              }
            ]
          }
        ]
      },
      classifier: "Interface"
     } as UmlClassifierShapeModel
};
//Initializes diagram control
let diagram: Diagram = new Diagram({
  width: '100%',
  height: '600px',
  //Add node
  nodes: [node]
});
diagram.appendTo("#element");
```

{% endtab %}

## Enumeration

* To define an enumeration, define the classifier property of node as [`enumeration`](../api/diagram/umlClassifierShapeModel#enumeration). Also, define the name and members of the enumeration using the enumeration property of the node.

* You can set a name for the enumeration members collection using the name property of members collection.

* The following code example illustrates how to create an enumeration.

{% tab template= "diagram/umldiagramshapes", es5Template="es5enumeration" %}

```typescript
import {
  Diagram,
  NodeModel,
  UmlClassifierShapeModel
} from "@syncfusion/ej2-diagrams";

let node: NodeModel = {
    id: "Patient",
    offsetX: 200,
    offsetY: 200,
    shape: {
      type: "UmlClassifier",
      //Define enumeration object
      enumeration: {
        name: "AccountType",
        //set the members of enumeration
        members: [
          {
            name: "Checking Account",
          },
          {
            name: "Savings Account"
          },
          {
            name: "Credit Account"
          }
        ]
      },
      classifier: "Enumeration"
    } as UmlClassifierShapeModel
};
//Initializes diagram control
let diagram: Diagram = new Diagram({
  width: '100%',
  height: '600px',
  //Add node
  nodes: [node]
});
diagram.appendTo("#element");
```

{% endtab %}

## Connector shapes

* The connector shape property defines the role or meaning of the connector.

* The different types of connector shapes are BPMN, UmlClassifier, and UmlActivity and can render these shapes by setting the connector shape type property.

* The type of flow shapes in a BPMN process are sequence, association, and message.

## Relationships

* A relationship is a general term covering the specific types of logical connections found on class diagrams.

* The list of relationships are demonstrated as follows.

| Shape       | Image                                |
| ----------- | ------------------------------------ |
| Association | ![Association](images/Association.PNG) |
| Aggregation | ![Aggregation](images/Aggregation.PNG)  |
| Composition | ![Composition](images/Composition.PNG) |
| Inheritance | ![Inheritance](images/Inheritance.PNG)   |
| Dependency  | ![Dependency](images/Dependency.PNG) |

## Association

Association is basically a set of links that connects elements of an UML model. The type of association are as follows.

    1. Directional
    2. BiDirectional

The association property allows you to define the type of association. The default value of association is “Directional”. The following code example illustrates how to create an association.

{% tab template= "diagram/umldiagramshapes", es5Template="es5association" %}

```typescript
import {
  Diagram,
  ConnectorModel
} from "@syncfusion/ej2-diagrams";

let connector: ConnectorModel = {
    id: "connector",
    //Define connector start and end points
    sourcePoint: { x: 100, y: 100 },
    targetPoint: { x: 300, y: 300 },
    type: "Straight",
    shape: {
      type: "UmlClassifier",
      relationship: "Association",
      //Define type of association
      association: "BiDirectional"
    }
};

//Initializes diagram control
let diagram: Diagram = new Diagram({
  width: '100%',
  height: '600px',
  //Add connector
  connectors: [connector]
});
diagram.appendTo("#element");
```

{% endtab %}

## Aggregation

Aggregation is a binary association between a property and one or more composite objects which group together a set of instances.
Aggregation is decorated with a hollow diamond. To create an aggregation shape, define the relationship as “aggregation”.

The following code example illustrates how to create an aggregation.

{% tab template= "diagram/umldiagramshapes", es5Template="es5aggregation" %}

```typescript
import {
  Diagram,
  ConnectorModel
} from "@syncfusion/ej2-diagrams";

let connector: ConnectorModel = {
    id: "connector",
    //Define connector start and end points
    sourcePoint: { x: 100, y: 100 },
    targetPoint: { x: 300, y: 300 },
    type: "Straight",
    shape: {
      type: "UmlClassifier",
      //Set an relationship for connector
      relationship: "Aggregation"
    }
};
//Initializes diagram control
let diagram: Diagram = new Diagram({
  width: '100%',
  height: '600px',
  connectors: [connector]
});
diagram.appendTo("#element");
```

{% endtab %}

## Composition

Composition is a “strong” form of “aggregation”. Composition is decorated with a black diamond. To create a composition shape, define the relationship property of connector as “composition”.

The following code example illustrates how to create a composition.

{% tab template= "diagram/umldiagramshapes", es5Template="es5composition" %}

```typescript
import {
  Diagram,
  ConnectorModel
} from "@syncfusion/ej2-diagrams";

let connector: ConnectorModel = {
    id: "connector",
    //Define connector start and end points
    sourcePoint: { x: 100, y: 100 },
    targetPoint: { x: 300, y: 300 },
    type: "Straight",
    shape: {
      type: "UmlClassifier",
      //Set an relationship for connector
      relationship: "Composition"
    }
};
//Initializes diagram control
let diagram: Diagram = new Diagram({
  width: '100%',
  height: '600px',
  //Add connector
  connectors: [connector]
});
diagram.appendTo("#element");
```

{% endtab %}

## Dependency

Dependency is a directed relationship, which is used to show that some UML elements needs or depends on other model elements for specifications. Dependency is shown as dashed line with opened arrow.
To create a dependency, define the relationship property of connector as “dependency”.

The following code example illustrates how to create an dependency.

{% tab template= "diagram/umldiagramshapes", es5Template="es5dependency" %}

```typescript
import {
  Diagram,
  ConnectorModel,
} from "@syncfusion/ej2-diagrams";

let connector: ConnectorModel = {
    id: "connector",
    //Define connector start and end points
    sourcePoint: { x: 100, y: 100 },
    targetPoint: { x: 300, y: 300 },
    type: "Straight",
    shape: {
      type: "UmlClassifier",
      //Set relationship for connector
      relationship: "Dependency"
    }
  };
//Initializes diagram control
let diagram: Diagram = new Diagram({
  width: '100%',
  height: '600px',
  connectors: [connector]
});
diagram.appendTo("#element");
```

{% endtab %}

## Inheritance

Inheritance is also called as “generalization”. Inheritance is a binary taxonomic directed relationship between a more general classifier (super class) and a more specific classifier (subclass).
Inheritance is shown as a line with hollow triangle.

To create an inheritance, define the relationship as “inheritance”.

The following code example illustrates how to create an inheritance.

{% tab template= "diagram/umldiagramshapes", es5Template="es5inheritance" %}

```typescript
import {
  Diagram,
  ConnectorModel
} from "@syncfusion/ej2-diagrams";

let connector: ConnectorModel = {
    id: "connector",
    //Define connector start and end points
    sourcePoint: { x: 100, y: 100 },
    targetPoint: { x: 300, y: 300 },
    type: "Straight",
    shape: {
      type: "UmlClassifier",
      //set an relation of connector
      relationship: "Inheritance"
    }
};
//Initializes diagram control
let diagram: Diagram = new Diagram({
  width: '100%',
  height: '600px',
  connectors: [connector]
});
diagram.appendTo("#element");
```

{% endtab %}

## Multiplicity

Multiplicity is a definition of an inclusive interval of non-negative integers to specify the allowable number of instances of described element. The type of multiplicity are as follows.

    1. OneToOne
    2. ManyToOne
    3. OneToMany
    4. ManyToMany

* By default the multiplicity will be considered as “OneToOne”.

* The multiplicity property in UML allows you to specify large number of elements or some collection of elements.

* The shape multiplicity’s source property is used to set the source label to connector and the target property is used to set the target label to connector.

* To set an optionality or cardinality for the connector source label, use optional property.

* The [`lowerBounds`](../api/diagram/multiplicityLabelModel#lowerBounds) and [`upperBounds`](../api/diagram/multiplicityLabelModel#upperBounds) could be natural constants or constant expressions evaluated to natural (non negative) number. Upper bound could be also specified as asterisk ‘\*’ which denotes unlimited number of elements. Upper bound should be greater than or equal to the lower bound.

* The following code example illustrates how to customize the multiplicity.

{% tab template= "diagram/umldiagramshapes", es5Template="es5multiplicity" %}

```typescript
import {
  Diagram,
  ConnectorModel
} from "@syncfusion/ej2-diagrams";

let connector: ConnectorModel = {
    id: "connector",
    //Define connector start and end points
    sourcePoint: { x: 100, y: 100 },
    targetPoint: { x: 300, y: 300 },
    type: "Straight",
    shape: {
      type: "UmlClassifier",
      relationship: "Dependency",
      multiplicity: {
        //Set multiplicity type
        type: "OneToMany",
        //Set source label to connector
        source: {
          optional: true,
          lowerBounds: 89,
          upperBounds: 67
        },
        //Set target label to connector
        target: {
          optional: true,
          lowerBounds: 78,
          upperBounds: 90
        }
      }
    }
};
//Initializes diagram control
let diagram: Diagram = new Diagram({
  width: '100%',
  height: '600px',
  connectors: [connector]
});
diagram.appendTo("#element");
```

{% endtab %}

## UmlActivity diagram

Activity diagram is basically a flowchart to represent the flow from one activity to another. The activity can be described as an operation of the system.

The purpose of an activity diagram can be described as follows.

    1. Draw the activity flow of a system.

    2. Describe the sequence from one activity to another.

    3. Describe the parallel, branched, and concurrent flow of the system.

To create a UmlActivity, define type as "UmlActivity" and the list of built-in shapes as demonstrated as follows and it should be set in the "shape" property.

| Shape          | Image                                    |
| -------------- | ---------------------------------------- |
| Action         | ![Action](images/Action.PNG)          |
| Decision       | ![Decision](images/Decision.PNG)         |
| MergeNode      | ![MergeNode](images/MergeNode.PNG)       |
| InitialNode    | ![InitialNode](images/InitialNode.PNG)       |
| FinalNode      | ![FinalNode](images/FinalNode.PNG)      |
| ForkNode       | ![ForkNode](images/ForkNode.PNG)       |
| JoinNode       | ![JoinNode](images/JoinNode.PNG)       |
| TimeEvent      | ![TimeEvent](images/TimeEvent.PNG)      |
| AcceptingEvent | ![AcceptingEvent](images/AcceptingEvent.PNG) |
| SendSignal     | ![SendSignal](images/SendSignal.PNG)     |
| ReceiveSignal  | ![ReceiveSignal](images/ReceiveSignal.PNG)  |
| StructuredNode | ![StructuredNode](images/StructuredNode.PNG) |
| Note           | ![Note](images/Note.PNG)           |

The following code illustrates how to create a UmlActivity shapes.

{% tab template= "diagram/umldiagramshapes", es5Template="es5UmlActivity" %}

```typescript
import {
  Diagram,
  NodeModel,
  UmlClassifierShapeModel
} from "@syncfusion/ej2-diagrams";

let node: NodeModel = {
    id: "UmlDiagram",
    //Set node size
    width: 100,
    height: 100,
    //position the node
    offsetX: 200,
    offsetY: 200,
    shape: {
      type: "UmlActivity",
      //Define UmlActivity shape
      shape: "Action"
    }
};
//Initializes diagram control
let diagram: Diagram = new Diagram({
  width: '100%',
  height: '600px',
  nodes: [node]
});
diagram.appendTo("#element");
```

{% endtab %}

### UmlActivity connector

To create an UmlActivity connector, define the type as "UmlActivity" and flow as either "Exception" or "Control" or "Object".

The following code illustrates how to create a UmlActivity connector.

{% tab template= "diagram/umldiagramshapes", es5Template="es5UmlActivityConnector" %}

```typescript
import {
  Diagram,
  ConnectorModel,
  UmlClassifierShapeModel
} from "@syncfusion/ej2-diagrams";

let connector: ConnectorModel = {
     id: 'connector',
     type: 'Straight',
     //Define connector start and end points
     sourcePoint: { x: 100, y: 100 },
     targetPoint: { x: 200, y: 200 },
     shape: { type: 'UmlActivity', flow: 'Exception' }
};
//Initializes diagram control
let diagram: Diagram = new Diagram({
  width: '100%',
  height: '600px',
  connectors: [connector]
});
diagram.appendTo("#element");
```

{% endtab %}

### Editing

You can edit the name, attributes, and methods of the class diagram shapes just double clicking, similar to editing a node annotation.

The following image illustrates how the text editor looks in an edit mode.

![Editing Class Diagram](images/ClassEdit.PNG)
