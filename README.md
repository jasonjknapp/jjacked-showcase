# JJacked

JJacked is a personal iPhone and Apple Watch workout app that adapts exercise selection to training needs, equipment and the current session. It combines workout logging, a shared exercise library, progression, and optional Health and calendar integrations. The project was developed with AI assistance.

This repository is a small portfolio sample, not the complete app. It contains an [architecture overview](architecture.md) and two excerpts from the app's source:

- [Rotation overlap](rotation-overlap.md) measures overlap with the previous exercise for use in ranking.
- [Settings change undo](settings-undo.md) avoids overwriting a newer setting when an earlier change is undone.

The excerpts rely on types and services from the full app and are not standalone build targets. The sample contains no personal workout history or production configuration. No software license is included.
