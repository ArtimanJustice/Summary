### Когда использовать ConstraintLayout?

- **Сложные макеты:** Если ваш UI требует сложного позиционирования элементов, особенно с зависимостями между ними (например, один элемент всегда ниже другого).
- **Динамические ограничения:** Когда элементы должны изменять свое положение в зависимости от других элементов или внешних условий.
### Подключение библиотеки

Для использования **ConstraintLayout** в Jetpack Compose нужно добавить отдельную зависимость в `build.gradle`:

`implementation "androidx.constraintlayout:constraintlayout-compose:1.0.1"`
### Поведение по умолчанию

Когда вы добавляете `Composable` элементы внутри `ConstraintLayout`, по умолчанию они размещаются в верхнем левом углу. Чтобы изменить их положение, нужно использовать **Constraints** через модификатор `Modifier.constrainAs()`.
### Создание ссылок

Для управления размещением элементов нужно создавать ссылки с помощью:

- **`createRef()`**: создает одну ссылку для привязки элемента.
- **`createRefs()`**: создает сразу несколько ссылок.
- **`createGuidelineFromStart`, `createGuidelineFromEnd`, `createGuidelineFromTop`, `createGuidelineFromBottom`**: создают направляющие для позиционирования.
### Что такое `parent`?

`parent` — это ссылка на сам `ConstraintLayout`. Вы можете использовать `parent` для привязки элементов к краям или центру `ConstraintLayout`. Например:

- `parent.start`: левая граница `ConstraintLayout`.
- `parent.end`: правая граница `ConstraintLayout`.
- `parent.top`: верхняя граница.
- `parent.bottom`: нижняя граница.
### Позиционирование элементов

Для указания положения используется метод `constrainAs(ref) { ... }`, где в блоке задаются ограничения, такие как расстояние от краев родителя (`parent`) или других элементов.
