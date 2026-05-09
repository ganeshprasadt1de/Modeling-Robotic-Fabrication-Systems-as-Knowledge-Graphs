# Graph Notes

## System

The system is a robotic timber fabrication system.

It makes a simplified timber slab with a column. The element has two timber plates, one stronger reinforcement layer between the plates, and one timber column.

Robot 1 is a KUKA KR6 R900 robot with a drill.

Robot 2 is a KUKA KR6 R900 robot with a gripper. It also has axis 7, which is the rail between the two workstations.

Robot 3 is a KUKA KR6 R900 robot with a saw.

Softwood is used for the main plates and the column.

Beech LVL timber is used for the stronger reinforcement between the plates.

LVL means laminated veneer lumber. It is made from thin timber layers glued together, so it can be stronger and more stable than normal timber.

The robot shape is linked to the file `KUKA KR6 R900 sixx.stp`.

STEP is a CAD file format. CAD means computer-aided design, which is a 3D model used by design software.

## Main Nodes

A node is one object in the graph.

Main system node:

- System

Main robot nodes:

- Robot1
- Robot2
- Robot3

Main tool nodes:

- DrillTool
- GripperTool
- SawTool

Main material nodes:

- Softwood
- BeechLVL

Main product nodes:

- TimberSlabWithColumn
- BottomPlate
- TopPlate
- ReinforcementBetweenPlates
- TimberColumn

Main process nodes:

- DrillStep
- CutStep
- MovePlateStep
- MoveReinforcementStep
- PlaceColumnStep
- AssembleStep
- CheckStep

Main sensor nodes:

- Robot2ToolSensor
- Robot2GripSensor
- Robot2RailSensor

## Single Query

Query file:

```text
query_lift_capacity.sparql
```

Question:

```text
Can Robot 2 lift the timber parts it moves?
```

This query follows these paths:

```text
Robot 2 -> process -> moved component -> estimated weight
Robot 2 -> robot model -> max payload
Robot 2 -> sensor -> checked process
```

The query uses the sensor links. It only returns a sensor if the sensor checks the same movement process that Robot 2 performs.

## Inferred Knowledge

The query infers the lift decision.

```text
If component weight is less than or equal to robot payload,
then Robot 2 can lift the component.
```

Example:

```text
TimberColumn estimatedWeightKg 5.5
KUKA_KR6_R900_Model maxPayloadKg 6.0
Therefore Robot2 can lift TimberColumn
```

In simple words, the query checks whether Robot 2 can carry each part with the gripper before the system assembles the timber slab.
