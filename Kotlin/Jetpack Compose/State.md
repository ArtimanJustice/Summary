`remember` allows you to store a value inside a composable function. This value is retained across recompositions, meaning it won't reset to its initial value every time the composable function is re-executed. It's let you create value just one time after first composition.

`by` -> is used for property delegation, it delegates the getter and setter logic to a predefined delegate. For example, when used with Jetpack Compose’s `remember` or `mutableStateOf`, the state handling is delegated to the Compose framework.

**Without `by`:**
`val counterState = remember { mutableStateOf(0) } val counter = counterState.value`
**With `by`:**
`val counter by remember { mutableStateOf(0) }`

**derivedStateOf**

As you know, we have three phases of rendering our UI in Jetpack Compose. When a Composable function, like `Text()`, uses state, the layout phase reruns each time the state changes. To prevent this, we can initialize our value outside of the function, but this approach still repeatedly triggers the Composition phase.

To resolve this, we use `derivedStateOf {}`. This function is useful when we only want to update a composable component selectively, not every time the state updates. For example, if we want a button to change position only after three clicks, `derivedStateOf {}` can help control when the UI updates.

**StateFlow**

`StateFlow` is a type of observable data holder in Kotlin that lets us manage and share UI state updates in a predictable way. In Jetpack Compose, it helps us handle state changes efficiently, especially for data that updates over time (like UI data in response to user actions or network calls).

**Why We Need It**  
In Compose, when we want our UI to react to changes in data, we can use `StateFlow`. It emits the latest value to any collectors (like a UI component) and automatically updates the UI when the data changes. This makes `StateFlow` a good choice for managing UI state in a clean, lifecycle-aware way.