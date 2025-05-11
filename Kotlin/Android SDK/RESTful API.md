В Kotlin для работы с RESTful API часто используется библиотека Retrofit, которая в связке с OkHttp и конвертерами (например, Gson или Moshi) позволяет легко определять и вызывать HTTP-эндпоинты. Обычно процесс выглядит так:

1. **Определение интерфейса API:**  
    Вы описываете эндпоинты как функции в интерфейсе, аннотируя их HTTP-методами (например, @GET, @POST). При этом можно использовать поддержку корутин, объявляя функции с ключевым словом suspend.
2. **Настройка Retrofit:**  
    Создаёте экземпляр Retrofit, указывая базовый URL, конвертер JSON и при необходимости клиент OkHttp.
3. **Вызов API:**  
    Используя созданный интерфейс, выполняете запросы асинхронно (например, внутри корутин).
**Пример:**
interface ApiService {
    @GET("users")
    suspend fun getUsers(): List<User>
}

val retrofit = Retrofit.Builder()
    .baseUrl("https://example.com/api/")
    .addConverterFactory(GsonConverterFactory.create())
    .build()

val apiService = retrofit.create(ApiService::class.java)

lifecycleScope.launch {
    try {
        val users = apiService.getUsers()
    } catch (e: Exception) {
        // Обработка ошибок
    }
}

Такой подход позволяет интегрировать ваше Android-приложение с RESTful API для подключения к внутренним или внешним службам, делая код чистым, удобочитаемым и легко расширяемым.