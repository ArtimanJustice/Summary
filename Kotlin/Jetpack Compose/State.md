`remember` allows you to store a value inside a composable function. This value is retained across recompositions, meaning it won't reset to its initial value every time the composable function is re-executed. It's let you create value just one time after first composition.

`by` -> is used for property delegation, it delegates the getter and setter logic to a predefined delegate. For example, when used with Jetpack Compose’s `remember` or `mutableStateOf`, the state handling is delegated to the Compose framework.

**Without `by`:**
`val counterState = remember { mutableStateOf(0) } val counter = counterState.value`
**With `by`:**
`val counter by remember { mutableStateOf(0) }`