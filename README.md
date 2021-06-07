# Hit-JavaScript-Best-Practice-Guide

# JS best practices


### 1. Избегать глобальные переменные

Названия переменных должны отражать тип значения и контекст, в котором они будут использоваться.
Названия функций должны отражать их назначение или получаемый результат.

``` js
//плохо
  const a = 10;
  const anotherString = '...';
  const human = true;
  const date = () => {
    const currentTime = new Date();
    return currentTime;
  }
// хорошо
   const length = 10;
  const thirdString = '...';
  const isHuman = true;
  const getDate = () => {
    const currentTime = new Date();
    return currentTime;
  } 
```

### 2. Объявление переменных

#### 2.1. Выбор имени

Выбирать простые, короткие и удобочитаемые имена переменных, функций и т.д.

```js
//плохо
let x1, incrementorForMainLoopWhichSpansFromTenToTwenty;
// хорошо
let age;
```
#### 2.1. Помещать объявление переменных сверху скрипта
Это делает код более чистым, позволяет увидеть неиспользуемые переменные, уменьшает возможность повторного объявления переменных
```js
// Объявление в начале
let firstName, lastName, price, discount, fullPrice;
// Используем после объявления
firstName = "John";
lastName = "Doe";
```
#### 2.2. Инициализировать переменные при объявлении
Это делает код более чистым, позволяет увидеть неиспользуемые переменные, уменьшает возможность повторного объявления переменных
```js
let firstName = "",
lastName = "",
price = 0;
```
### 3. Не объявлять переменные как объекты типов String, Number, Boolean
Обрабатывать числа, строки или логические значения как примитивные значения. Не как объекты.
Объявление этих типов как объектов снижает скорость выполнения и вызывает неприятные побочные эффекты:
```js
let x = "John";  // хорошо            
let y = new String("John"); // плохо
(x === y) // false, так как x - строка, а y - объект
var x = new String("John");             
var y = new String("John");
(x == y) // false, так как объекты не сравнимы

```
### 4. Не использовать new Object()
* {} вместо new Object()
* "" вместо new String()
* 0 вместо new Number()
* false вместо new Boolean()
* [] вместо new Array()
* /()/ вместо new RegExp()
* function (){} вместо new Function()
```css
let x1 = {};           // new object
let x2 = "";           // new primitive string
let x3 = 0;            // new primitive number
let x4 = false;        // new primitive boolean
let x5 = [];           // new array object
let x6 = /()/;         // new regexp object
let x7 = function(){}; // new function object
```

### 5. Избегать автоматического преобразования типов
Числа могут быть случайно преобразованы в строки или NaN (не число).
```css
let x = 5 + 7;       // x.valueOf() = 12,  typeof x - number
let x = 5 + "7";     // x.valueOf() = 57,  typeof x - string
let x = 5 - "7";     // x.valueOf() = -2,  typeof x - number
let x = 5 - "x";     // x.valueOf() = NaN, typeof x - number
```

### 6. Устанавливать параметры по-умолчанию
Иначе при отсутствие параметра при вызове устанавливается значение undefined
```css
function (a=1, b=1) { 
  /*function code*/
}
```

### 7. Использовать ===

При сравнении использовать === вместо ==

```css
[10] === 10    // is false
[10]  == 10    // is true
'10' == 10     // is true
'10' === 10    // is false
[]   == 0     // is true
[] ===  0     // is false
'' == false   // is true but true == "a" is false
'' ===   false // is false
```

### 8. Каждое новое свойство следует писать с новой строки

```js
// плохо
  const user = { firstName: "Olga", age: 23 }  

// хорошо
    const user = {                             
    firstName: "Olga",
    age: 23,
  }  
```

### 9. Размещать скрипты в конце страницы

script размещаем внутри тега body в конце
Это делает загрузку страницы максимально быстрой для пользователя
```css
<body>
  <!-- код страницы -->
  <script src="script.js"></script>
</body>
```

### 10. Завершите переключатели (switch) по умолчанию

```css
switch (new Date().getDay()) {
  case 0:
    day = "Sunday";
    break;
  case 1:
    day = "Monday";
    break;
  case 2:
    day = "Tuesday";
    break;
  case 3:
    day = "Wednesday";
    break;
  case 4:
    day = "Thursday";
    break;
  case 5:
    day = "Friday";
    break;
  case 6:
    day = "Saturday";
    break;
  default:
    day = "Unknown";
}
```
