Блочная область видимости.
```js
function name(params…){
body_fuction;
return something;
}
```

параметрами могут быть любые [[Типы данных| типы данных]], включая [[callback функции]] 

```js
function showMessage ( from, text = anotherFunction() ){
// anotherFunction() выполнится только если не передан text
// результатом будет значение text
}
```