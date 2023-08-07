Формат записи данных.


В JS 2 метода 

- `JSON.stringify(value, replacer, space)` - преобразует в
	- value - какой объект
	- replacer - какие поля, прямое перечисление или функция отбора.
	- space - доп. отступы
- `JSON.parse` - преобразует из 


Пропускает:

- Свойства-функции (методы).
- Символьные ключи и значения.
- Свойства, содержащие `undefined`


Объекты могут при попытки преобразовать JSON, вызывают метод `.toJSON()`, поэтому его можно задать, 

**Важное ограничение: не должно быть циклических ссылок.**


```js
meetup.place = room;      
room.occupiedBy = meetup;
JSON.stringify(meetup) // ERROR!!! Попытка закодировать циклическую ссылку
```

С помощью параметра replacer, можно указать лишь те поля, которые будут закодированы, тем самым ошибки не будет


```js
let room = {
  number: 23
};

let meetup = {
  title: "Conference",
  participants: [{name: "John"}, {name: "Alice"}],
  place: room // meetup ссылается на room
};

room.occupiedBy = meetup; // room ссылается на meetup

alert( JSON.stringify(meetup, ['title', 'participants']) );
// {"title":"Conference","participants":[{},{}]}
```

Для того, чтобы грамотно преобразовать и объекты в participants, их имена также надо указать

```js
let room = {
  number: 23
};

let meetup = {
  title: "Conference",
  participants: [{name: "John"}, {name: "Alice"}],
  place: room // meetup ссылается на room
};

room.occupiedBy = meetup; // room ссылается на meetup

alert( JSON.stringify(meetup, ['title', 'participants', 'name', 'place', 'number']) );
// {"title":"Conference","participants":[{name: "John"}, {name: "Alice"}],"place":{"number":23}}
```