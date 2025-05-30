**`.invoke()`** вызывает (то есть выполняет) функцию или лямбду. В Kotlin функции являются объектами первого класса, и если у вас есть переменная, которая содержит функцию (например, лямбда-выражение), то вы можете вызвать её с помощью оператора `()`, что на самом деле является синтаксическим сахаром для вызова метода `.invoke()`. То есть запись `navIcon?.invoke()` эквивалентна записи `navIcon?.()` и означает: если `navIcon` не равен `null`, то выполнить его.

**`val`** -> immutable type

**`var`** -> mutable type

**`object`** -> used to create a **singleton**

**`annotation`** -> если хочешь сделать свою аннотацию просто можно пометить класс ключевым словом annotation

**`open`** -> значит от класса можно наследоваться, по дефолту в Котлин так нельзя.

**`open`** метод -> в kotlin означает, что метод может быть переопределен, потому что по умолчанию они не являются таковыми. Вместо этого в Java все методы могут быть переопределены по умолчанию

**`Any`** — это базовый класс для всех не-nullable типов в Kotlin, аналогичный `Object` в Java. Все классы в Kotlin неявно наследуются от `Any`. Он предоставляет три основных метода: `toString()`, `equals()` и `hashCode()`. Если необходимо, чтобы переменная могла принимать значение `null`, используется тип `Any?`

**`Unit`** — это специальный тип в Kotlin, который используется для обозначения отсутствия значимого значения. Он аналогичен `void` в Java, но имеет некоторые отличия, особенно в контексте 
функционального программирования и типов.

 **`Nothing`** - представляет тип, не имеющий значений, и используется для обозначения функций, которые никогда не возвращают значение, например, функций, всегда выбрасывающих исключения или содержащих бесконечные циклы. **`Nothing`** является подтипом всех типов, что позволяет использовать его в местах, где ожидается значение любого типа. Например, функция `error()` в стандартной библиотеке Kotlin имеет возвращаемый тип `Nothing`, поскольку она всегда выбрасывает исключение и никогда не возвращает значение.

**`out`** - используется для обозначения ковариантности в обобщённых типах (обычно в дженериках), что позволяет использовать обобщённый тип с подтипами там, где ожидается его суперкласс. Иными словами, позволяет использовать **подтипы** (`Cat` вместо `Animal`).

**`in`** - Позволяет использовать **суперклассы** (`Animal` вместо `Cat`).