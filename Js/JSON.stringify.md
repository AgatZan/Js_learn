Преобразует в формат json. `JSON.stringify(value, replacer, space)`

Имеется ограничение, на циклические ссылки, то есть в объекте не может содержаться объект ссылающийся на него, это вызовет ошибку.

Для ее предотвращения, существует параметр replacer, который указывает, какие именно [[Преобразование объекта в массив|пары]], попадут.

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