
**См. также:** [[Basis]]

1. **Первый запрос**:
    ```
    ViewModelProvider(this).get(MyViewModel::class.java)
    ```
	создаёт и сохраняет `MyViewModel` в `ViewModelStore`.

2. **Поворот экрана**:
	- Android уничтожает старую Activity и создаёт новую;
    - но `ViewModelStore` остаётся во внутреннем механизме фреймворка.

3. **Повторный запрос**: новая Activity снова вызывает `get(MyViewModel::class.java)` и получает **тот же** экземпляр.

4. **Окончательное уничтожение**: при вызове `finish()` или «назад» фреймворк очищает `ViewModelStore` и вызывает `onCleared()` у сохранённых `ViewModel`.