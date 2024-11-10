In Jetpack Compose, `CompositionLocal` provides an implicit way of passing data through the composition tree without needing to pass it explicitly as parameters.

A common example is `LocalContext.current`, which allows us to access the current `Context` (typically the Activity context) from within a `@Composable` function. We often use `LocalContext.current` because we know our composable functions are part of an Activity, and accessing the context can be useful for tasks like starting a new Activity, accessing resources, or using system services.

This approach is efficient for sharing data within a composition hierarchy, as shown in your diagram, where various UI components access data implicitly through the composition.
![[CompositionLocal.png]]