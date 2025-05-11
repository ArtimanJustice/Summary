1.  [[Composition and Lifecycle|Composition]] Phase - what should be drawn? By building the data tree.
2.  Layout Phase - where components should be placed and how much space they should occupy. Compose aims to perform the layout phase in a single pass whenever possible. 
![[phases.png]]
3. Drawing Phase - how it should be drawn? Draw components within their bounds. 
**Skipping Phases:**
- You can **ignore the Composition and Drawing phases** if you are certain that a state change will not trigger recomposition. For example, using `.offset` with a lambda in a modifier will change the position without drawing a new component. In such cases, you can ignore the Drawing Phase and Composition Phase.
- Alternatively, you can **ignore the Layout and Drawing phases** and retain only the Composition Phase.
- Similarly, you can **ignore the [Composition](obsidian://open?vault=artilearning&file=Kotlin%2FJetpack%20Compose%2FComposition%20and%20Lifecycle) and Layout phases** and keep only the Drawing Phase.#
![[derivedStateOf.png]]