---
title: "BPMN Shapes"
component: "Diagram"
description: "Diagram BPMN shapes allow you to graphically notate the internal business procedure."
---

# Shapes

BPMN shapes are used to represent the internal business procedure in a graphical notation and enable you to communicate the procedures in a standard manner. To create a BPMN shape, in the node property shape, type should be set as “bpmn” and its shape should be set as any one of the built-in shapes. The following code example illustrates how to create a simple business process.

>Note: If you want to use BPMN shapes in diagram, you need to inject BpmnDiagrams in the diagram.

{% tab template= "diagram/bpmnShapes", es5Template="es5bpmn" %}

```typescript

import { Diagram, NodeModel, BpmnShape, BpmnSubProcessModel, BpmnDiagrams, BpmnActivityModel, BpmnFlowModel } from '@syncfusion/ej2-diagrams';
Diagram.Inject(BpmnDiagrams);

// A node is created and stored in nodes array.
let node: NodeModel = {
    // Position of the node
    offsetX: 250,
    offsetY: 250,
    // Size of the node
    width: 100,
    height: 100,
    //Sets type as Bpmn and shape as Event
    shape: {
        type: 'Bpmn',
        shape: 'Event',
        // set the event type as End
        event: {
            event: 'End'
        }
    },
};

// initialize Diagram component

let diagram: Diagram = new Diagram({
    width: '100%',
    height: '600px',
    // Add node
    nodes: [node]
});
// render initialized Diagram
diagram.appendTo('#element');

```

{% endtab %}

>Note : The default value for the property `shape` is “event”.

The list of BPMN shapes are as follows:

| Shape | Image |
| -------- | -------- |
| Event | ![Event Shape](images/Event.png) |
| Gateway | ![Gateway Shape](images/Gateway.png) |
| Task | ![Task Shape](images/Task.png) |
| Message | ![Message Shape](images/Message.png) |
| DataSource | ![Datasource Shape](images/Datasource.png) |
| DataObject | ![Dataobject Shape](images/Dataobject.png) |
| Group | ![Group Shape](images/Group.png) |

The BPMN shapes and its types are explained as follows.

<!-- markdownlint-disable MD033 -->

## Event

An [`event`](../api/diagram/bpmnEvent) is notated with a circle and it represents an event in a business process. The type of events are as follows:

    * Start
    * End
    * Intermediate
The [`event`](../api/diagram/bpmnEvent#event-bpmnevents) property of the node allows you to define the type of the event. The default value of the event is **start**. The following code example illustrates how to create a BPMN event.

{% tab template= "diagram/bpmnShapes", es5Template="es5Event" %}

```typescript

import { Diagram, NodeModel, BpmnShape, BpmnSubProcessModel, BpmnDiagrams, BpmnActivityModel, BpmnFlowModel } from '@syncfusion/ej2-diagrams';
Diagram.Inject(BpmnDiagrams);

// A node is created and stored in nodes array.
let node: NodeModel = {
    // Position of the node
    offsetX: 250,
    offsetY: 250,
    // Size of the node
    width: 100,
    height: 100,
    //Sets type as Bpmn and shape as event
    shape: {
        type: 'Bpmn',
        shape: 'Event',
        // Sets event as End and trigger as None
        event: {
            event: 'End',
            trigger: 'None'
        }
    },
};

// initialize diagram component

let diagram: Diagram = new Diagram({
    width: '100%',
    height: '600px',
    // Add node
    nodes: [node]
});
// render initialized diagram
diagram.appendTo('#element');

```

{% endtab %}

Event triggers are notated as icons inside the circle and they represent the specific details of the process. The [`trigger`](../api/diagram/bpmnEvent#trigger-bpmntriggers) property of the node allows you to set the type of trigger and by default, it is set as **none**. The following table illustrates the type of event triggers.

| Triggers | Start | Non-Interrupting Start | Intermediate | Non-Interrupting Intermediate | Throwing Intermediate | End |
| -------- | -------- | -------- | -------- | -------- | -------- | -------- |
| None | ![None Trigger Start event BPMN Shape](images/None1.png)  | ![None Trigger Interupting event BPMN Shape](images/None2.png) | ![None Trigger Intermediate event  BPMN Shape](images/None3.png) | ![None Trigger NonInteruptingIntermediate BPMNShape](images/None4.png) | | ![None Trigger End event  event  BPMNShape](images/None5.png) |
| Message | ![Message Trigger Start Event BPMN Shape](images/Message1.png) | ![Message Trigger NonInterupting Event BPMN Shape](images/Message2.png) | ![Message Trigger Intermediate Event BPMN Shape](images/Message3.png) | ![Message Trigger NonInteruptingIntermediate Event BPMN Shape](images/Message4.png)
|![Message Trigger ThrowingIntermediate Event BPMNShape](images/Message5.png) | ![Message Trigger End Event BPMN EndShape](images/Message6.png) |
| Timer | ![Timer Trigger Start Event BPMNShape](images/Timer1.png) | ![Timer Trigger NonInterupting Event BPMN Shape](images/Timer2.png) | ![Timer Trigger Intermediate Event BPMN Shape](images/Timer3.png)|![Timer Trigger NonInteruptingIntermediate  Event BPMN Shape](images/Timer4.png) | | |
| Conditional | ![Conditional Trigger Start BPMN Shape](images/Conditional1.png) | ![Conditional Trigger NonInterupting BPMN Shape](images/Conditional2.png) | ![Conditional Trigger Intermediate BPMN Shape](images/Conditional3.png)
|![Conditional Trigger NonInteruptingIntermediateBPMNShape](images/Conditional4.png) | | |
| Link | | |![Link Trigger Intermediate Event BPMNShape](images/Link1.png) | | ![Link Trigger ThrowingIntermediate  Event BPMN Shape](images/Link2.png) | |
| Signal | ![Signal Trigger Start Event BPMN Shape](images/Signal1.png) | ![Signal Trigger NonInterrupting Event BPMN Shape](images/Signal2.png) | ![Signal Trigger Intermediate Event BPMN Shape](images/Signal3.png) | ![Signal Trigger NonInterrupting Event BPMN Shape](images/Signal4.png)
| ![SignalThrowing Trigger Intermediate  Event BPMN Shape](images/Signal5.png) | ![Signal Trigger End Event BPMN Shape](images/Signal6.png) |
| Error | ![Error Trigger Start Event BPMN Shape](images/Error1.png) | | ![Error Trigger Intermediate Event BPMN Shape](images/Error2.png)  | | | ![Error Trigger End Event BPMN Shape](images/Error3.png)|
| Escalation | ![Escalation Trigger Start Event BPMN Shape](images/Esclation1.png) | ![Escalation  Trigger  Non-Interrupting  Event BPMN Shape](images/Esclation2.png) | ![Escalation  Trigger  Intermediate  Event BPMN Shape](images/Esclation3.png)
| ![Escalation  Trigger Non-Interrupting  Event BPMN Shape](images/Esclation4.png)| ![Escalation  Trigger  Throwing Intermediate Event  BPMN Shape](images/Esclation5.png) |  ![Escalation  Trigger  End Event BPMN Shape](images/Esclation6.png)|
| Termination | | | | | | ![Termination Trigger End  Event BPMN Shape](images/Termination1.png)|
| Compensation |![Compensation  Trigger Start Event  BPMN Shape](images/Compensation1.png)  | | ![Compensation Trigger Intermediate  Event BPMN Shape](images/Compensation2.png) | | ![Compensation  Trigger  Throwing Intermediate Event  BPMN Shape](images/Compensation3.png)
|![Compensation  Trigger End BPMN  Event Shape](images/Compensation4.png) |
| Cancel | | | ![Cancel Trigger Intermediate  Event BPMN Shape](images/Cancel1.png) | | | ![Cancel Trigger End  Event BPMN Shape](images/Cancel2.png) |
| Multiple | ![Multiple Trigger Start  Event BPMN Shape](images/Multiple1.png) | ![Multiple Trigger Non-Interrupting  Event BPMN Shape](images/Multiple2.png)  | ![Multiple Trigger Intermediate BPMN Shape](images/Multiple3.png)
| ![Multiple Trigger Non-Interrupting Event BPMN Shape](images/Multiple4.png) | ![Multiple Trigger  Throwing Intermediate  Event BPMN Shape](images/Multiple5.png)  | ![Multiple Trigger End Event  BPMN Shape](images/Multiple6.png) |
| Parallel | ![Parallel Trigger Start  Event BPMN Shape](images/Parallel1.png) | ![Parallel Trigger Non-Interrupting Event  BPMN Shape](images/Parallel2.png) | ![Parallel Trigger Intermediate  Event BPMN Shape](images/Parallel3.png)
| ![Parallel Trigger End Event  BPMN Shape](images/Parallel4.png) | | |

## Gateway

Gateway is used to control the flow of a process and it is represented as a diamond shape. To create a gateway, the shape property of the node should be set as [`gateway`](../api/diagram/bpmnGateways) and the gateway property can be set with any of the appropriate gateways. The following code example illustrates how to create a BPMN Gateway.

{% tab template= "diagram/bpmnShapes", es5Template="es5Gateway" %}

```typescript

import { Diagram, NodeModel, BpmnShape, BpmnSubProcessModel, BpmnDiagrams, BpmnActivityModel, BpmnFlowModel, BpmnGatewayModel } from '@syncfusion/ej2-diagrams';
Diagram.Inject(BpmnDiagrams);

// A node is created and stored in nodes array.
let node: NodeModel = {
    // Position of the node
    offsetX: 250,
    offsetY: 250,
    // Size of the node
    width: 100,
    height: 100,
    //Sets type as Bpmn and shape as Gateway
    shape: {
        type: 'Bpmn',
        shape: 'Gateway',
        //Sets type of the gateway as None
        gateway: {
            type: 'None'
        }
        as BpmnGatewayModel
    },
};

// initialize diagram component

let diagram: Diagram = new Diagram({
    width: '100%',
    height: '600px',
    // Add node
    nodes: [node]
});
// render initialized diagram
diagram.appendTo('#element');

```

{% endtab %}

>Note: By default, the `gateway` will be set as **none**.

There are several types of gateways as tabulated:

| Shape | Image |
| -------- | -------- |
| Exclusive | ![Exclusive GateWay BPMN Shape](images/Exclusive.png) |
| Parallel | ![Parallel GateWay BPMN Shape](images/Parallel.png) |
| Inclusive | ![Inclusive GateWay BPMN Shape](images/Inclusive.png) |
| Complex | ![Complex GateWay BPMN Shape](images/Complex.png) |
| EventBased | ![EventBased GateWay BPMNShape](images/EventBased.png) |
| ExclusiveEventBased | ![Exclusive EventBased GateWay BPMN Shape](images/EEBased.png) |
| ParallelEventBased | ![Parallel EventBased GateWay BPMN Shape](images/PEBased.png) |

## Activity

The [`activity`](../api/diagram/bpmnActivity#BpmnActivity) is the task that is performed in a business process. It is represented by a rounded rectangle.

There are two types of activities. They are listed as follows:

* Task: Occurs within a process and it is not broken down to a finer level of detail.
* Subprocess: Occurs within a process and it is broken down to a finer level of detail.

To create a BPMN activity, set the shape as **activity**. You also need to set the type of the BPMN activity by using the activity property of the node. By default, the type of the activity is set as **task**. The following code example illustrates how to create an activity.

{% tab template= "diagram/bpmnShapes", es5Template="es5Activity" %}

```typescript

import { Diagram, NodeModel, BpmnShape, BpmnSubProcessModel, BpmnDiagrams, BpmnActivityModel, BpmnFlowModel, BpmnGatewayModel } from '@syncfusion/ej2-diagrams';
Diagram.Inject(BpmnDiagrams);

// A node is created and stored in nodes array.

let node: NodeModel = {
    // Position of the node
    offsetX: 250,
    offsetY: 250,
    // Size of the node
    width: 100,
    height: 100,
    //Sets type as Bpmn and shape as Activity
    shape: {
        type: 'Bpmn',
        shape: 'Activity',
        //Sets activity as Task
        activity: {
            activity: 'Task'
        },
    },
};

// initialize diagram component

let diagram: Diagram = new Diagram({
    width: '100%',
    height: '600px',
    // Add node
    nodes: [node]
});
// render initialized diagram
diagram.appendTo('#element');

```

{% endtab %}

The different activities of BPMN process are listed as follows.

## Tasks

The [`task`](../api/diagram/bpmnTask#BpmnTask) property of the node allows you to define the type of task such as sending, receiving, user based task, etc. By
default, the type property of task is set as **none**. The following code illustrates how to create different types of
BPMN tasks.
The [`type`](../api/diagram/bpmnTask#type) property of tasks allows to represent these results as an event attached to the task.

{% tab template= "diagram/bpmnShapes", es5Template="es5Task" %}

```typescript

import { Diagram, NodeModel, BpmnShape, BpmnSubProcessModel, BpmnDiagrams, BpmnActivityModel, BpmnFlowModel, BpmnGatewayModel } from '@syncfusion/ej2-diagrams';
Diagram.Inject(BpmnDiagrams);

// A node is created and stored in nodes array.
let node: NodeModel = {
    // Position of the node
    offsetX: 250,
    offsetY: 250,
    // Size of the node
    width: 100,
    height: 100,
    //Sets type as Bpmn and shape as activity
    shape: {
        type: 'Bpmn',
        shape: 'Activity',
        //Sets activity as Task
        activity: {
            activity: 'Task',
            //Sets the type of the task as Send
            task: {
                type: 'Send'
            }
        },
    },
};

// initialize diagram component

let diagram: Diagram = new Diagram({
    width: '100%',
    height: '600px',
    // Add node
    nodes: [node]
});
// render initialized diagram
diagram.appendTo('#element');

```

{% endtab %}

The various types of BPMN tasks are tabulated as follows.

| Shape | Image |
| -------- | -------- |
| Service | ![Service Task BPMN Shape](images/Service.png) |
| Send | ![Send Task BPMN Shape](images/Send.png) |
| Receive | ![Receive Task BPMN Shape](images/Receive.png) |
| Instantiating Receive | ![Instantiating Receive Task BPMN Shape](images/InsService.png) |
| Manual |![Manual Task BPMN Shape](images/Manual.png) |
| Business Rule | ![Business Rule  Task BPMN Shape](images/Bussiness.png) |
| User | ![User Task BPMN Shape](images/User.png) |
| Script | ![Script Task BPMN Shape](images/Script.png) |

## Subprocess

A [`sub-process`](../api/diagram/bpmnSubProcess) is a group of tasks, which is used to hide or reveal details of additional levels using the [`collapsed`](../api/diagram/bpmnSubProcess#collapsed-boolean) property.

{% tab template= "diagram/bpmnShapes", es5Template="es5Subprocess" %}

```typescript

import { Diagram, NodeModel, BpmnShape, BpmnSubProcessModel, BpmnDiagrams, BpmnActivityModel, BpmnFlowModel, BpmnGatewayModel } from '@syncfusion/ej2-diagrams';
Diagram.Inject(BpmnDiagrams);

// A node is created and stored in nodes array.
let node: NodeModel = {
    // Position of the node
    offsetX: 250,
    offsetY: 250,
    // Size of the node
    width: 100,
    height: 100,
    //Sets type as Bpmn and shape as Activity
    shape: {
        type: 'Bpmn',
        shape: 'Activity',
        //Sets activity as Subprocess and collapsed of subprocess as true
        activity: {
            activity: 'SubProcess',
            subProcess: {
                collapsed: true
            }
            as BpmnSubProcessModel
        }
    },
};

// initialize diagram component

let diagram: Diagram = new Diagram({
    width: '100%',
    height: '600px',
    // Add node
    nodes: [node]
});
// render initialized diagram
diagram.appendTo('#element');

```

{% endtab %}

The different types of subprocess are as follows:

    * Event subprocess
    * Transaction

## Event subprocess

A subprocess is defined as an event subprocess, when it is triggered by an event. An event subprocess is placed within another subprocess which is not part of the normal flow of its parent process. You can set event to a subprocess with the [`event`](../api/diagram/bpmnEvent##BpmnEvent) and [`trigger`](../api/diagram/bpmnEvent#trigger) property of the subprocess. The [`type`](../api/diagram/bpmnSubProcess#type) property of subprocess allows you to define the type of subprocess whether it should be event subprocess or transaction subprocess.

{% tab template= "diagram/bpmnShapes", es5Template="es5EventSub" %}

```typescript

import { Diagram, NodeModel, BpmnShape, BpmnSubProcessModel, BpmnDiagrams, BpmnActivityModel, BpmnFlowModel, BpmnGatewayModel } from '@syncfusion/ej2-diagrams';
Diagram.Inject(BpmnDiagrams);

// A node is created and stored in nodes array.
let node: NodeModel = {
    // Position of the node
    offsetX: 250,
    offsetY: 250,
    // Size of the node
    width: 100,
    height: 100,
    //Sets type as Bpmn and shape as activity
    shape: {
        type: 'Bpmn',
        shape: 'Activity',
        //Sets activity as SubProcess
        activity: {
            activity: 'SubProcess',
            //Sets the collapsed as true and type as Event
            subProcess: {
                collapsed: true,
                type: 'Event',
                //Sets event as Start and trigger as Message
                event: {
                    event: 'Start',
                    trigger: 'Message'
                }
            }
            as BpmnSubProcessModel
        },
    },
};

// initialize diagram component

let diagram: Diagram = new Diagram({
    width: '100%',
    height: '600px',
    // Add node
    nodes: [node]
});
// render initialized diagram
diagram.appendTo('#element');

```

{% endtab %}

## Transaction subprocess

* [`transaction`](../api/diagram/bpmnSubProcess#transaction-bpmntransactionsubprocessmodel) is a set of activities that logically belong together, in which all contained activities must complete their parts of the transaction; otherwise the process is undone. The execution result of a transaction is one of Successful Completion, Unsuccessful Completion (Cancel), and Hazard (Exception). The [`events`](../api/diagram/bpmnSubProcess#event-bpmnsubeventmodel) property of subprocess allows to represent these results as an event attached to the subprocess.

* The event object allows you to define the type of event by which the subprocess will be triggered. The name of the event can be defined to identify the event at runtime.

* The event’s offset property is used to set the fraction/ratio (relative to parent) that defines the position of the event shape.

* The trigger property defines the type of the event trigger.

* You can also use define ports and labels to subprocess events by using event’s ports and labels properties.

{% tab template= "diagram/bpmnShapes", es5Template="es5TransitionSub" %}

```typescript

import { Diagram, NodeModel, BpmnShape, BpmnSubProcessModel, BpmnDiagrams, BpmnActivityModel, BpmnFlowModel, BpmnGatewayModel } from '@syncfusion/ej2-diagrams';
Diagram.Inject(BpmnDiagrams);

// A node is created and stored in nodes array.
let node: NodeModel = {
    // Position of the node
    offsetX: 250,
    offsetY: 250,
    // Size of the node
    width: 100,
    height: 100,
    //Sets type as Bpmn and shape as activity
    shape: {
        type: 'Bpmn',
        shape: 'Activity',
        //Sets activity as SubProcess
        activity: {
            activity: 'SubProcess',
            //Sets collapsed as true and type as Transition
            subProcess: {
                collapsed: true,
                type: 'Transition',
                //Sets event as Intermediate and trigger as Cancel
                event: [{
                        event: 'Intermediate',
                        trigger: 'Cancel',
                        offset: {
                            x: 0.25,
                            y: 1
                        }
                    },
                    {
                        event: 'Intermediate',
                        trigger: 'Error',
                        offset: {
                            x: 0.25,
                            y: 1
                        }
                    },
                ]
            }
            as BpmnSubProcessModel
        },
    },
};

// initialize diagram component

let diagram: Diagram = new Diagram({
    width: '100%',
    height: '600px',
    // Add node
    nodes: [node]
});
// render initialized diagram
diagram.appendTo('#element');

```

{% endtab %}

## Process

Processes is an array collection that defines the children values for BPMN subprocess.

## Loop

[`Loop`](../api/diagram/bpmnTask#loop) is a task that is internally being looped. The loop property of task allows you to define the type of loop. The default value for `loop` is **none**.
You can define the loop property in subprocess BPMN shape as shown in the following code.

{% tab template= "diagram/bpmnShapes", es5Template="es5Loop" %}

```typescript

import { Diagram, NodeModel, BpmnShape, BpmnSubProcessModel, BpmnDiagrams, BpmnActivityModel, BpmnFlowModel, BpmnGatewayModel } from '@syncfusion/ej2-diagrams';
Diagram.Inject(BpmnDiagrams);

// A node is created and stored in nodes array.
let node: NodeModel = {
    // Position of the node
    offsetX: 100,
    offsetY: 100,
    // Size of the node
    width: 100,
    height: 100,
    //Sets type as Bpmn and shape as Activity
    shape: {
        type: 'Bpmn',
        shape: 'Activity',
        //Sets activity as Task
        activity: {
            activity: 'Task',
            //Sets loop of the task as Standard
            task: {
                loop: 'Standard'
            }
        },
    },
};

let node2: NodeModel = {
    // Position of the node
    offsetX: 300,
    offsetY: 100,
    // Size of the node
    width: 100,
    height: 100,
    //Sets type as Bpmn and shape as activity
    shape: {
        type: 'Bpmn',
        shape: 'Activity',
        //Sets Activity as SubProcess
        activity: {
            activity: 'SubProcess',
            //Sets collapsed as true and loop as Standard
            subProcess: {
                collapsed: true,
                loop: 'Standard'
            }
            as BpmnSubProcessModel
        },
    },
};

// initialize diagram component

let diagram: Diagram = new Diagram({
    width: '100%',
    height: '600px',
    // Add node
    nodes: [node, node2]
});
// render initialized diagram
diagram.appendTo('#element');

```

{% endtab %}

The following table contains various types of BPMN loops.

| Loops | Task | Subprocess |
| -------- | -------- | --------|
| Standard | ![Standard Task BPMN Shape](images/Standard1.png)  | ![Standard Subprocess BPMN Shape](images/Standard2.png) |
| SequenceMultiInstance | ![Sequence MultiInstance Task BPMN Shape](images/Sequence1.png) |  ![SequenceMultiInstance Subprocess BPMN Shape](images/Sequence2.png)|
| ParallelMultiInstance | ![ParallelMultiInstance Task BPMNShape](images/PMultiInstance1.png) | ![ParallelMultiInstance Subprocess BPMN Shape](images/PMultiInstance2.png) |

## Compensation

[`Compensation`](../api/diagram/bpmnTask#compensation-boolean) is triggered, when operation is partially failed and enabled it with the compensation property of the task and the subprocess.

{% tab template= "diagram/bpmnShapes", es5Template="es5Compensation" %}

```typescript

import { Diagram, NodeModel, BpmnShape, BpmnSubProcessModel, BpmnDiagrams, BpmnActivityModel, BpmnFlowModel, BpmnGatewayModel } from '@syncfusion/ej2-diagrams';
Diagram.Inject(BpmnDiagrams);

// A node is created and stored in nodes array.
let node: NodeModel = {
    // Position of the node
    offsetX: 100,
    offsetY: 100,
    // Size of the node
    width: 100,
    height: 100,
    //Sets type as Bpmn and shape as Activity
    shape: {
        type: 'Bpmn',
        shape: 'Activity',
        //Sets activity as Task
        activity: {
            activity: 'Task',
            //Sets compensation of the task as true
            task: {
                compensation: true
            }
        },
    },
};

let node2: NodeModel = {
    // Position of the node
    offsetX: 300,
    offsetY: 100,
    // Size of the node
    width: 100,
    height: 100,
    //Sets type as Bpmn and shape as Activity
    shape: {
        type: 'Bpmn',
        shape: 'Activity',
        //Sets activity as SubProcess
        activity: {
            activity: 'SubProcess',
            //Set the collapsed as true and compensation as true
            subProcess: {
                collapsed: true,
                compensation: true
            }
            as BpmnSubProcessModel
        },
    },
};

// initialize diagram component

let diagram: Diagram = new Diagram({
    width: '100%',
    height: '600px',
    // Add node
    nodes: [node, node2]
});
// render initialized diagram
diagram.appendTo('#element');

```

{% endtab %}

## Call

A [`call`](../api/diagram/bpmnTask#call-boolean) activity is a global subprocess that is reused at various points of the business flow and set it with the call property of the task.

{% tab template= "diagram/bpmnShapes", es5Template="es5Call" %}

```typescript

import { Diagram, NodeModel, BpmnShape, BpmnSubProcessModel, BpmnDiagrams, BpmnActivityModel, BpmnFlowModel, BpmnGatewayModel } from '@syncfusion/ej2-diagrams';
Diagram.Inject(BpmnDiagrams);

// A node is created and stored in nodes array.
let node: NodeModel = {
    // Position of the node
    offsetX: 250,
    offsetY: 250,
    // Size of the node
    width: 100,
    height: 100,
    //Sets type as Bpmn and shape as Activity
    shape: {
        type: 'Bpmn',
        shape: 'Activity',
        //Sets the activity as task
        activity: {
            activity: 'Task',
            //Sets the call of the task as true
            task: {
                call: true
            }
        },
    },
};

// initialize diagram component

let diagram: Diagram = new Diagram({
    width: '100%',
    height: '600px',
    // Add node
    nodes: [node]
});
// render initialized diagram
diagram.appendTo('#element');

```

{% endtab %}

## Adhoc

An adhoc subprocess is a group of tasks that are executed in any order or skipped in order to fulfill the end condition and set it with the [`adhoc`](../api/diagram/bpmnSubProcess#adhoc-boolean) property of subprocess.

{% tab template= "diagram/bpmnShapes", es5Template="es5Adhoc" %}

```typescript

import { Diagram, NodeModel, BpmnShape, BpmnSubProcessModel, BpmnDiagrams, BpmnActivityModel, BpmnFlowModel, BpmnGatewayModel } from '@syncfusion/ej2-diagrams';
Diagram.Inject(BpmnDiagrams);

// A node is created and stored in nodes array.
let node: NodeModel = {
    // Position of the node
    offsetX: 250,
    offsetY: 250,
    // Size of the node
    width: 100,
    height: 100,
    //Sets type as Bpmn and shape as Activity
    shape: {
        type: 'Bpmn',
        shape: 'Activity',
        //Sets activity as SubProcess
        activity: {
            activity: 'SubProcess',
            //Sets collapsed as true and adhoc as true
            subProcess: {
                collapsed: true,
                adhoc: true
            }
            as BpmnSubProcessModel
        },
    },
};

// initialize diagram component

let diagram: Diagram = new Diagram({
    width: '100%',
    height: '600px',
    // Add node
    nodes: [node]
});
// render initialized diagram
diagram.appendTo('#element');

```

{% endtab %}

## Boundary

Boundary represents the type of task that is being processed. The [`boundary`](../api/diagram/bpmnSubProcess#boundary-bpmnboundary) property of subprocess allows you to define the type of boundary. By default, it is set as **default**.

{% tab template= "diagram/bpmnShapes", es5Template="es5Boundary" %}

```typescript

import { Diagram, NodeModel, BpmnShape, BpmnSubProcessModel, BpmnDiagrams, BpmnActivityModel, BpmnFlowModel, BpmnGatewayModel } from '@syncfusion/ej2-diagrams';
Diagram.Inject(BpmnDiagrams);

// A node is created and stored in nodes array.
let node: NodeModel = {
    // Position of the node
    offsetX: 250,
    offsetY: 250,
    // Size of the node
    width: 100,
    height: 100,
    //Sets type as Bpmn and shape as Activity
    shape: {
        type: 'Bpmn',
        shape: 'Activity',
        //Sets activity as SubProcess
        activity: {
            activity: 'SubProcess',
            //Sets collapsed as true and boundary as Call
            subProcess: {
                collapsed: true,
                boundary: 'Call'
            }
            as BpmnSubProcessModel
        },
    },
};

// initialize diagram component

let diagram: Diagram = new Diagram({
    width: '100%',
    height: '600px',
    // Add node
    nodes: [node]
});
// render initialized diagram
diagram.appendTo('#element');

```

{% endtab %}

The following table contains various types of BPMN boundaries.

| Boundary | Image |
| -------- | -------- |
| Call | ![Call Boundary BPMN Shape](images/Call.png) |
| Event | ![Event Boundary BPMN Shape](images/Eventtask.png) |
| Default | ![Default Boundary BPMN Shape](images/DefaultBoundary.png) |

## Data

A data object represents information flowing through the process, such as data placed into the process, data resulting from the process, data that needs to be collected, or data that must be stored. To define a [`data object`](../api/diagram/bpmnDataObject), set the shape as **DataObject** and the type property defines whether data is an input or an output. You can create multiple instances of data object with the collection property of data.

{% tab template= "diagram/bpmnShapes", es5Template="es5Data" %}

```typescript

import { Diagram, NodeModel, BpmnShape, BpmnSubProcessModel, BpmnShapeModel, BpmnDiagrams, BpmnActivityModel, BpmnFlowModel, BpmnGatewayModel } from '@syncfusion/ej2-diagrams';
Diagram.Inject(BpmnDiagrams);

// A node is created and stored in nodes array.
let node: NodeModel = {
    // Position of the node
    offsetX: 250,
    offsetY: 250,
    // Size of the node
    width: 100,
    height: 100,
    //Sets type as Bpmn and shape as DataObject
    shape: {
        type: 'Bpmn',
        shape: 'DataObject',
        //Sets collection as true and type as Input
        dataObject: {
            collection: true,
            type: 'Input'
        }
    }
    as BpmnShapeModel,
};

// initialize diagram component

let diagram: Diagram = new Diagram({
    width: '100%',
    height: '600px',
    // Add node
    nodes: [node]
});
// render initialized diagram
diagram.appendTo('#element');

```

{% endtab %}

The following table contains various representation of BPMN data object.

| Boundary | Image |
| -------- | -------- |
| Collection Data Object | ![Collection Data BPMN Shape](images/Dataobject.png) |
| Data Input | ![Data Input BPMN Shape](images/DataInput.png) |
| Data Output | ![Data Output BPMN Shape](images/DataOutput.png) |

## Datasource

Datasource is used to store or access data associated with a business process. To create a datasource, set the shape as **datasource**. The following code example illustrates how to create a datasource.

{% tab template= "diagram/bpmnShapes", es5Template="es5Datasource" %}

```typescript

import { Diagram, NodeModel, BpmnShape, BpmnSubProcessModel, BpmnDiagrams, BpmnActivityModel, BpmnFlowModel, BpmnGatewayModel } from '@syncfusion/ej2-diagrams';
Diagram.Inject(BpmnDiagrams);

// A node is created and stored in nodes array.
let node: NodeModel = {
    // Position of the node
    offsetX: 250,
    offsetY: 250,
    // Size of the node
    width: 100,
    height: 100,
    //Sets type as Bpmn and shape as DataSource
    shape: {
        type: 'Bpmn',
        shape: 'DataSource',
    }
};

// initialize diagram component

let diagram: Diagram = new Diagram({
    width: '100%',
    height: '600px',
    // Add node
    nodes: [node]
});
// render initialized diagram
diagram.appendTo('#element');

```

{% endtab %}

## Artifact

Artifact is used to show additional information about a process in order to make it easier to understand. There are two types of artifacts in BPMN.

* Text annotation
* Group

## Text annotation

* A BPMN object can be associated with a text annotation which does not affect the flow but gives details about objects within a flow. The annotation property of the node is used to connect an annotation element to the BPMN node.

* The annotation element can be displaced into a different position interactively by dragging the annotation to a particular position.

* The annotation element can be switched from a BPMN node to another BPMN node simply by dragging the source end of the annotation connector into the other BPMN node.

* The annotation angle property is used to set the angle between the BPMN shape and the annotation.

* The annotation direction property is used to set the direction of the text annotation.

* To set the size for text annotation, use width and height properties.

* The annotation length property is used to set the distance between the BPMN shape and the annotation.

* The annotation text property defines the additional information about the flow object in a BPMN process.

{% tab template= "diagram/bpmnShapes", es5Template="es5Text" %}

```typescript

import { Diagram, NodeModel, BpmnShape, BpmnSubProcessModel, BpmnShapeModel,BpmnDiagrams, BpmnActivityModel, BpmnFlowModel, BpmnGatewayModel } from '@syncfusion/ej2-diagrams';
Diagram.Inject(BpmnDiagrams);

// A node is created and stored in nodes array.
let node: NodeModel = {
    // Position of the node
    offsetX: 100,
    offsetY: 100,
    // Size of the node
    width: 100,
    height: 100,
    //Sets type as Bpmn and shape as DataObject
    shape: {
        type: 'Bpmn',
        shape: 'DataObject',
        //Sets collection as true and type as Input
        dataObject: {
            collection: true,
            type: 'Input'
        },
        //Sets the id, angle, length and text for the annotation
        annotations: [{
            id: 'left',
            angle: 45,
            length: 150,
            text: 'Left',
        }]
    }
    as BpmnShapeModel,
};

// initialize diagram component

let diagram: Diagram = new Diagram({
    width: '100%',
    height: '600px',
    // Add node
    nodes: [node]
});
// render initialized diagram
diagram.appendTo('#element');

```

{% endtab %}

## Group

A group is used to frame a part of the diagram, shows that elements included in it are logically belong together and does not have any other semantics other than organizing elements. To create a group, the shape property of the node should be set as **group**. The following code example illustrates how to create a BPMN group.

{% tab template= "diagram/bpmnShapes", es5Template="es5Group" %}

```typescript

import { Diagram, NodeModel, BpmnShape, BpmnSubProcessModel, BpmnShapeModel,BpmnDiagrams, BpmnActivityModel, BpmnFlowModel, BpmnGatewayModel } from '@syncfusion/ej2-diagrams';
Diagram.Inject(BpmnDiagrams);

// A node is created and stored in nodes array.
let node: NodeModel = {
    // Position of the node
    offsetX: 250,
    offsetY: 250,
    // Size of the node
    width: 100,
    height: 100,
    //Sets type as Bpmn and shape as Group
    shape: {
        type: 'Bpmn',
        shape: 'Group',
    }
};

// initialize diagram component

let diagram: Diagram = new Diagram({
    width: '100%',
    height: '600px',
    // Add node
    nodes: [node]
});
// render initialized diagram
diagram.appendTo('#element');

```

{% endtab %}

## BPMN flows

[`BPMN Flows`](../api/diagram/bpmnFlow#BpmnFlow) are lines that connects BPMN flow objects.

## Association

[`BPMN Association`](../api/diagram/bpmnFlow#association) flow is used to link flow objects with its corresponding text or artifact. An association is represented as a dotted graphical line with opened arrow. The types of association are as follows:

* Directional
* BiDirectional
* Default

The `association` property allows you to define the type of association. The following code example illustrates how to create an association.

{% tab template= "diagram/bpmnShapes", es5Template="es5Association" %}

```typescript

import { Diagram, NodeModel, ConnectorModel, BpmnShape, BpmnSubProcessModel, BpmnShapeModel,BpmnDiagrams, BpmnActivityModel, BpmnFlowModel, BpmnGatewayModel } from '@syncfusion/ej2-diagrams';
Diagram.Inject(BpmnDiagrams);

// A node is created and stored in nodes array.
let connector: ConnectorModel = {
    // Position of the node
    sourcePoint: {
        x: 100,
        y: 200
    },
    targetPoint: {
        x: 300,
        y: 200
    },
    //Sets type of the connector as Orthogonal
    type: 'Orthogonal',
    //Sets type as Bpmn, shflowape as Association and association as BiDirectional
    shape: {
        type: 'Bpmn',
        flow: 'Association',
        association: 'BiDirectional'
    },
};

// initialize diagram component

let diagram: Diagram = new Diagram({
    width: '100%',
    height: '600px',
    // Add Connectors
    connectors: [connector]
});
// render initialized diagram
diagram.appendTo('#element');

```

{% endtab %}

The following table demonstrates the visual representation of association flows.

| Association | Image |
| -------- | -------- |
| Default | ![Default BPMN FlowShapes](images/Default1.png) |
| Directional | ![Directional BPMN FlowShapes](images/Directional1.png) |
| BiDirectional | ![BiDirectional BPMN FlowShapes](images/BiDirectional.png) |

>Note : The default value for the property `association` is **default**.

## Sequence

A [`sequence`](../api/diagram/bpmnFlow#sequence) flow shows the order in which the activities are performed in a BPMN process and is represented by a solid graphical line. The types of sequence are as follows:

* Normal
* Conditional
* Default

The sequence property allows you to define the type of sequence. The following code example illustrates how to create a sequence flow.

{% tab template= "diagram/bpmnShapes", es5Template="es5Sequence" %}

```typescript

import { Diagram, NodeModel, ConnectorModel, BpmnShape, BpmnSubProcessModel, BpmnShapeModel,BpmnDiagrams, BpmnActivityModel, BpmnFlowModel, BpmnGatewayModel } from '@syncfusion/ej2-diagrams';
Diagram.Inject(BpmnDiagrams);

// A node is created and stored in nodes array.
let connector: ConnectorModel = {
    // Position of the node
    sourcePoint: {
        x: 100,
        y: 200
    },
    targetPoint: {
        x: 300,
        y: 200
    },
    type: 'Orthogonal',
    //Sets type as Bpmn, flow as Sequence, and sequence as Conditional
    shape: {
        type: 'Bpmn',
        flow: 'Sequence',
        sequence: 'Conditional'
    },
};

// initialize diagram component

let diagram: Diagram = new Diagram({
    width: '100%',
    height: '600px',
    // Add node
    connectors: [connector]
});
// render initialized diagram
diagram.appendTo('#element');
```

{% endtab %}

The following table contains various representation of sequence flows.

| Sequence | Image |
| -------- | -------- |
| Default | ![Default Sequence BPMN Shpae](images/Default2.png) |
| Conditional | ![Conditional Sequence BPMN Shpae](images/Conditional.png) |
| Normal | ![Normal Sequence BPMN Shpae](images/Normal.png) |

> Note: The default value for the property `sequence` is **normal**.

## Message

A [`message`](../api/diagram/bpmnFlow#message) flow shows the flow of messages between two participants and is represented by dashed line. The types of message are as follows:

* InitiatingMessage
* NonInitiatingMessage
* Default

The message property allows you to define the type of message. The following code example illustrates how to define a message flow.

{% tab template= "diagram/bpmnShapes", es5Template="es5Message" %}

```typescript

import { Diagram, NodeModel, ConnectorModel, BpmnShape, BpmnSubProcessModel, BpmnShapeModel,BpmnDiagrams, BpmnActivityModel, BpmnFlowModel, BpmnGatewayModel } from '@syncfusion/ej2-diagrams';
Diagram.Inject(BpmnDiagrams);

// A node is created and stored in nodes array.
let connector: ConnectorModel = {
    // Position of the node
    sourcePoint: {
        x: 100,
        y: 200
    },
    targetPoint: {
        x: 300,
        y: 200
    },
    type: 'Orthogonal',
    //Sets type as Bpmn, flow as Message, and message as InitiatingMessage
    shape: {
        type: 'Bpmn',
        flow: 'Message',
        message: 'InitiatingMessage'
    },
};

// initialize diagram component

let diagram: Diagram = new Diagram({
    width: '100%',
    height: '600px',
    // Add node
    connectors: [connector]
});
// render initialized diagram
diagram.appendTo('#element');
```

{% endtab %}

The following table contains various representation of message flows.

| Message | Image |
| -------- | -------- |
| Default | ![Default Message BPMN Shape](images/Default1.png) |
| InitiatingMessage | ![InitiatingMessage Message BPMN Shape](images/IMessage.png) |
| NonInitiatingMessage | ![NonInitiatingMessage Message BPMN Shape](images/NIMessage.png) |

>Note: The default value for the property `message` is **default**.
