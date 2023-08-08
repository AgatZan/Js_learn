Аргументы
- Строка, которая преобразуется в объект
- Функция, которая вызывается для каждой пары, ключ-значение


### Пример

```js
let schedule = `{
  "meetups": [
    {"title":"Conference","date":"2017-11-30T12:00:00.000Z"},
    {"title":"Birthday","date":"2017-04-18T12:00:00.000Z"}
  ]
}`;

schedule = JSON.parse(schedule, function(key, value) {
  if (key == 'date') return new Date(value);
  return value;
});

/* schedele :
1. 0: {title: 'Conference', date: Thu Nov 30 2017 15:00:00 GMT+0300 (Москва, стандартное время)}
2. 1: {title: 'Birthday', date: Tue Apr 18 2017 15:00:00 GMT+0300 (Москва, стандартное время)}
*/
```