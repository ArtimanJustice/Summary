Why should we use `LazyColumn`() to display lists instead of a simple `@Composable fun Column()`? Imagine you're showing a scrollable list with 100+ items on the screen. Users will see a different number of elements based on their display size, but not all 100 at once.

If you use `Column()`, Android will attempt to compose all 100 elements at the same time. In contrast, `LazyColumn` only composes the elements currently visible on the screen.

Think of `LazyColumn` like [[RecyclerView]] + Adapter in xml. Only the visible items are added to the composition, and off-screen items are cached.