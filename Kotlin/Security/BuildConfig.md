`BuildConfig` — это автоматически генерируемый класс во время сборки проекта, который содержит константы и параметры сборки.

**Назначение:**
- Содержит стандартные поля, такие как `DEBUG`, `APPLICATION_ID`, `BUILD_TYPE`, `VERSION_CODE` и `VERSION_NAME`.
- Позволяет добавлять пользовательские поля через `buildConfigField` в `build.gradle`, например, API-ключи из `local.properties`.