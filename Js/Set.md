#структура 
Объект [`Set`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Set) – это особый вид коллекции: «множество» значений (без ключей), где каждое значение может появляться только один раз.

- `new Set(iterObj)` - конструктор, если передан [[Протоколы перебора| итерируемый объект]], то копирует его
- `.add(value)` - добавляет если нет, **возвращает себя** 
- `.delete(value)` - удаляет value, если удалила, то вернет true.
- `.has(value)` - находится или нет?
- `.clear()` - деструктор (удаляет все, но не объект)
- `.size` - всего элементов

### Перебор

[[Протоколы перебора|Итераторы]]

- `.keys()` - в цикле [[for of]] перебирает значения
- `.values()` - обратная совместимость с [[Map]]
- `.entries()` - [значение, значение], так же обратная совместимость с [[Map]]