`java.util.LinkedList<E>` — готовая реализация двусвязного списка из Java Collections Framework, реализует интерфейсы `List` и `Deque`.

## Основные возможности

- Методы `add()`, `addFirst()`, `addLast()`, `remove()`, `get()`, `iterator()`.
    
- Эффективные вставка и удаление в начале и конце списка (O(1)).
    
- Доступ по индексу требует обхода списка (O(n)).
    
## Внутренняя реализация

```
static class Node<E> {
    E item;
    Node<E> next;
    Node<E> prev;
    Node(Node<E> prev, E element, Node<E> next) {
        this.item = element;
        this.next = next;
        this.prev = prev;
    }
}
```

[[Двунаправленный список]] — общий конспект о двусвязном списке