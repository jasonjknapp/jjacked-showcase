# Architecture

The phone and watch share training logic while presenting workout controls suited to each device. The app keeps workout history separate from the shared exercise library and supports optional integrations.

```mermaid
flowchart LR
    Phone[iPhone app] --> Core[Shared training logic]
    Watch[Watch app] --> Core
    Core --> History[Workout history]
    Core --> Library[Shared exercise library]
    Phone -. optional .-> Health[Apple Health]
    Phone -. optional .-> Calendar[Calendar]
    Phone -. optional .-> Files[Shared-folder edits]
```

This diagram is a simplified view of the full private application; it is not a runnable implementation.
