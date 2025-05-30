**Определение стабильного типа:**

- **Стабильный тип** гарантирует, что метод `equals()` всегда возвращает одинаковый результат для идентичных экземпляров.
- Все **публичные свойства** такого типа также должны быть стабильными.
- Простыми словами, тип считается стабильным, если Jetpack Compose может определить, изменилось ли его значение между рекомпозициями.

**Примеры стабильных типов:**

- Примитивные типы: `Int`, `Boolean`, `String`
- Другие неизменяемые (immutable) типы

**Иммутабельность:**

- Если создается пользовательский класс, где все поля объявлены как `val` (то есть неизменяемы), Jetpack Compose будет считать его стабильным, и рекомпозиция не произойдет при неизменном состоянии.
- Рекомендуется использовать `data class`, так как они автоматически генерируют корректные реализации `equals()`, `hashCode()` и `toString()`, что способствует стабильности.

**Аннотации для улучшения понимания стабильности:**

- Можно явно помечать пользовательские классы аннотациями `@Immutable` или `@Stable`, чтобы помочь Compose правильно обработать их при рекомпозициях.

**Почему не стоит использовать тип `Any`:

- - Использование типа `Any` небезопасно в контексте стабильности, так как Compose не может гарантировать, что все возможные реализации `Any` будут вести себя стабильно. Подробнее об этом можно почитать [[Kotlin/Interesting Questions/Почему не сделать каждый типа Any|здесь]].

Любой класс из другого модуля jetpack compose будет считать нестабильным, даже если он стабилен. Чтобы это фиксануть добавляй к классам аннотацию @Stable или @Immutable. 
- `@Stable` — когда класс может изменяться, но изменения отслеживаются (например, при использовании `mutableStateOf` внутри),
- `@Immutable` — когда класс действительно неизменяемый (all `val`-поля, и их типы тоже стабильные).

И это можно делать спокойно не только со своими классами, но и классами из чужих библиотек. Для этого нужно сделать свой отдельный факлик stability.conf и там будет список файлов (с пакетами которые по нашему мнению являются стабильными). Не забудь в gradle установить путь к этому пакету используя plugins:stabilityConfigurationPath

Таким образом, с помощью `stability.conf` и соответствующей настройки в Gradle можно спокойно объявлять стабильность сторонних классов и библиотек, что улучшает работу Jetpack Compose при рекомпозициях.