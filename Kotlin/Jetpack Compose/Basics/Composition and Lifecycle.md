In Jetpack Compose, if a value on the screen changes, the composable function is re-executed. However, during recomposition, only the part of the UI that changed is updated, while the rest remains the same.

Composable functions are not a tree of objects; they are functions. So, `@Composable` functions describe the UI's composition but are not the composition itself.

**Lifecycle:**
- **Enter** → `@Composable` function runs
- **Recomposition** → 0 to N times as values change
- **Leave** → Composable function exits when no longer needed