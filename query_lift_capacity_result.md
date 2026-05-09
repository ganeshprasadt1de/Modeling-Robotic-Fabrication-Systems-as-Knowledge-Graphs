# Query Result

Query file:

```text
query_lift_capacity.sparql
```

Question:

```text
Can Robot 2 lift the timber parts it moves?
```

Result:

| Component | Weight kg | Max payload kg | Sensor | Lift decision |
|---|---:|---:|---|---|
| Bottom plate | 4.2 | 6.0 | Grip sensor | can lift |
| Bottom plate | 4.2 | 6.0 | Robot 2 tool sensor | can lift |
| Reinforcement between plates | 2.8 | 6.0 | Grip sensor | can lift |
| Reinforcement between plates | 2.8 | 6.0 | Robot 2 tool sensor | can lift |
| Timber column | 5.5 | 6.0 | Grip sensor | can lift |
| Timber column | 5.5 | 6.0 | Robot 2 tool sensor | can lift |
| Top plate | 4.2 | 6.0 | Grip sensor | can lift |
| Top plate | 4.2 | 6.0 | Robot 2 tool sensor | can lift |

Inferred knowledge:

```text
Robot 2 can lift each timber part because each part weight is below the 6.0 kg payload.
```

Reasoning rule:

```text
If component weight is less than or equal to robot payload,
then Robot 2 can lift the component.
```
