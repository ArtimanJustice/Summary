Ключевое слово `by` в Kotlin сигнализирует компилятору: «вместо меня эту работу выполняет другой объект». Проще говоря, вы делегируете какую-то функцию или работу по чтению/записи свойства стороннему объекту.

См. также:  
- [[Делегирование Свойств]]  
- [[Стандартные делегаты]]
## 1. Без делегата

```kotlin
interface Greeter {
    fun greet(): String
}

class EnglishGreeter : Greeter {
    override fun greet() = "Hello!"
}

class MyService(private val greeter: Greeter) : Greeter {
    override fun greet() = greeter.greet()
}

fun main() {
    val service = MyService(EnglishGreeter())
    println(service.greet())  // Hello!
} ```

## 2. С делегатом через `by`

```kotlin
interface Greeter {
    fun greet(): String
}

class EnglishGreeter : Greeter {
    override fun greet() = "Hello!"
}

// Здесь вся реализация Greeter делегируется переданному объекту greeter
class MyService(greeter: Greeter) : Greeter by greeter

fun main() {
    val service = MyService(EnglishGreeter())
    println(service.greet())  // Hello!
} ```

