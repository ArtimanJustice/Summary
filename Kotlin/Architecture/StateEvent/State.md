
[[Event]] • [[State and Event]]
## Определение
Модель данных, хранящая «снимок» интерфейса или бизнес-логики в любой момент времени.
## Составляющие
- **Loading:** индикатор ожидания  
- **Data:** основные данные (список, объект, текст)  
- **Error:** состояние ошибки (сообщение, код)  
- **UI-флаги:** вспомогательные булевы (`isEditMode`, `isRefreshing`)
## Пример

```kotlin
sealed class ProfileState {
  object Loading : ProfileState()
  data class Success(val user: UserEntity) : ProfileState()
  data class Error(val message: String) : ProfileState()
}