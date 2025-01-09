Для создания аннотации в Kotlin используется ключевое слово `annotation`.

- **`@Target`**: определяет, где можно использовать аннотацию (например, на классах, функциях, свойствах).
- **`@Retention`**: указывает, когда аннотация доступна (в исходном коде, в байткоде, или в runtime через рефлексию).
### Обработка аннотаций

#### 1. **Через рефлексию**

Рефлексия позволяет получить информацию об аннотациях во время выполнения.

Пример:

fun processAnnotations(target: Any) {
    val kClass = target::class
    kClass.annotations.forEach { annotation ->
        println("Found annotation: $annotation")
    }
}

@MyAnnotation("Example", priority = 5)
class ExampleClass

fun main() {
    processAnnotations(ExampleClass())
}

#### 2. **Через KAPT (Kotlin Annotation Processing Tool)**

KAPT автоматически обрабатывает аннотации и позволяет генерировать код или выполнять другую логику. Он работает под капотом через рефлексию.

Пример создания процессора аннотаций:

kotlin

Copy code

@SupportedAnnotationTypes("MyAnnotation")
@SupportedSourceVersion(SourceVersion.RELEASE_8)
class MyAnnotationProcessor : AbstractProcessor() {
    override fun process(annotations: MutableSet<out TypeElement>, roundEnv: RoundEnvironment): Boolean {
        val elements = roundEnv.getElementsAnnotatedWith(MyAnnotation::class.java)
        elements.forEach {
            processingEnv.messager.printMessage(Diagnostic.Kind.NOTE, "Found annotation on: $it")
        }
        return true
    }
}