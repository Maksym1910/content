---
title: Arrow function expressions
slug: Web/JavaScript/Reference/Functions/Arrow_functions
tags:
  - ECMAScript 2015
  - Functions
  - Intermediate
  - JavaScript
  - Language feature
  - Reference
browser-compat: javascript.functions.arrow_functions
---

{{jsSidebar("Functions")}}

**Вираз стрілкової функції** — це компактна альтернатива традиційному [виразові функції](/uk/docs/Web/JavaScript/Reference/Operators/function), яку, проте, через певні обмеження можна використовувати не у всіх випадках.

Існують відмінності між _стрілковими функціями_ й _традиційними функціями_, а також певні обмеження:

- Стрілкові функції не мають власної прив'язки до [`this`](/uk/docs/Web/JavaScript/Reference/Operators/this), [`arguments`](/en-US/docs/Web/JavaScript/Reference/Functions/arguments) та [`super`](/uk/docs/Web/JavaScript/Reference/Operators/super),
  і не повинні вживатися як [методи](/uk/docs/Glossary/Method).
- Стрілкові функції не мають доступу до ключового слова [`new.target`](/uk/docs/Web/JavaScript/Reference/Operators/new.target).
- Стрілкові функції не підходять для виклику методів [`call`](/uk/docs/Web/JavaScript/Reference/Global_Objects/Function/call), [`apply`](/uk/docs/Web/JavaScript/Reference/Global_Objects/Function/apply) та [`bind`](/uk/docs/Web/JavaScript/Reference/Global_Objects/Function/bind), які залежать від встановлення [контексту](/uk/docs/Glossary/Scope).
- Стрілкові функції не можуть використовуватись як [конструктори](/uk/docs/Glossary/Constructor).
- Стрілкові функції не можуть використовувати всередині свого тіла [`yield`](/uk/docs/Web/JavaScript/Reference/Operators/yield).

{{EmbedInteractiveExample("pages/js/functions-arrow.html")}}

### Порівняння традиційних і стрілкових функцій

Давайте крок за кроком розкладемо "традиційну анонімну функцію" до найпростішої "стрілкової функції":

> **Примітка:** Кожний крок спрощення залишається коректною "стрілковою функцією".

```js
// Традиційна анонімна функція
function (a){
  return a + 100;
}

// Спрощення стрілкової функції

// 1. Приберемо слово "function" і додамо стрілку між аргументом і дужкою початку тіла функції
(a) => {
  return a + 100;
}

// 2. Приберемо дужки навколо тіла функції і слово "return": так зване неявне повернення результату.
(a) => a + 100;

// 3. Приберемо дужки навколо аргумента
a => a + 100;
```

Фігурні `{}` та круглі `()` дужки, а також слово "return" — в деяких випадках обов'язкові.

Для прикладу, якщо є **декілька аргументів** чи **аргументів немає** взагалі, то дужки навколо аргументів доведеться повернути на місце:

```js
// Традиційна анонімна функція
function (a, b){
  return a + b + 100;
}

// Стрілкова функція
(a, b) => a + b + 100;

// Традиційна анонімна функція (без аргументів)
let a = 4;
let b = 2;
function (){
  return a + b + 100;
}

// Стрілкова функція (без аргументів)
let a = 4;
let b = 2;
() => a + b + 100;
```

Аналогічно, якщо в тілі функції потрібно **більше рядків** логіки, доведеться повернути на місце дужки, **А ТАКОЖ "return"** (стрілкові функції не вгадують якимось магічним чином, що саме потрібно повернути, або коли):

```js
// Традиційна анонімна функція
function (a, b){
  let chuck = 42;
  return a + b + chuck;
}

// Стрілкова функція
(a, b) => {
  let chuck = 42;
  return a + b + chuck;
}
```

І насамкінець, для створення **іменованих функцій** слід вважати стрілкові вирази просто змінними:

```js
// Традиційна функція
function bob(a) {
  return a + 100;
}

// Стрілкова функція
let bob = (a) => a + 100;
```

## Синтаксис

### Основний синтаксис

Єдиний аргумент. З простим виразом явний `return` не потрібен:

```js
(param) => expression;
```

Наявність декількох параметрів вимагає дужок. З простим виразом явний `return` не потрібен:

```js
(param1, paramN) => expression;
```

Наявність декількох рядків інструкцій потребує дужок навколо тіла функції та явного `return`:

```js
(param) => {
  let a = 1;
  return a + param;
};
```

Наявність декількох параметрів вимагає дужок, а декілька рядків інструкцій потребують дужок навколо тіла функції та явного `return`:

```js
(param1, paramN) => {
  let a = 1;
  return a + param1 + paramN;
};
```

### Поглиблений синтаксис

Щоб повернути об'єкт, літеральний вираз потребує дужок:

```js
(params) => ({ foo: 'a' }); // повертає об'єкт {foo: "a"}
```

Підтримуються [залишкові параметри](/uk/docs/Web/JavaScript/Reference/Functions/rest_parameters), причому в такому випадку обов‘язкові дужки:

```js
(a, b, ...r) => expression;
```

Підтримуються [усталені параметри](/uk/docs/Web/JavaScript/Reference/Functions/Default_parameters), причому в такому випадку обов‘язкові дужки:

```js
(a = 400, b = 20, c) => expression;
```

Підтримується [деструктуризація](/uk/docs/Web/JavaScript/Reference/Operators/Destructuring_assignment) всередині параметрів, причому в такому випадку обов‘язкові дужки:

```js
([a, b] = [10, 20]) => a + b; // результатом є 30
({ a, b } = { a: 10, b: 20 }) => a + b; // результатом є 30
```

## Опис

### Застосування стрілкових функцій як методів

Як було зауважено раніше, вирази стрілкових функцій найкраще підходять для функцій, які не є методами. Погляньмо, що трапиться, якщо все ж таки використати таку функцію як метод:

```js
'use strict';

var obj = {
  // не створює нового контексту
  i: 10,
  b: () => console.log(this.i, this),
  c: function () {
    console.log(this.i, this);
  },
};

obj.b(); // друкує undefined, Window {...} (або глобальний об'єкт)
obj.c(); // друкує 10, Object {...}
```

Стрілкові функції не мають свого власного `this`. Ось іще один приклад, цього разу із застосуванням {{jsxref("Object.defineProperty()")}}:

```js
'use strict';

var obj = {
  a: 10,
};

Object.defineProperty(obj, 'b', {
  get: () => {
    console.log(this.a, typeof this.a, this); // undefined 'undefined' Window {...} (або глобальний об'єкт)
    return this.a + 10; // звертається до глобального об'єкту 'Window', а отже – 'this.a' поверне 'undefined'
  },
});
```

### Функції `call`, `apply` та `bind`

Методи [`call`](/uk/docs/Web/JavaScript/Reference/Global_Objects/Function/call), [`apply`](/uk/docs/Web/JavaScript/Reference/Global_Objects/Function/apply) та [`bind`](/uk/docs/Web/JavaScript/Reference/Global_Objects/Function/bind) **не підходять** для стрілкових функцій. Адже вони були розроблені, щоб дозволити виконувати методи всередині різних контекстів, а **стрілкові функції визначають "this" на основі контексту, всередині якого стрілкова функція була оголошена.**

Наприклад, [`call`](/uk/docs/Web/JavaScript/Reference/Global_Objects/Function/call), [`apply`](/uk/docs/Web/JavaScript/Reference/Global_Objects/Function/apply) та [`bind`](/uk/docs/Web/JavaScript/Reference/Global_Objects/Function/bind) працюють так, як від них очікується, з традиційними функціями, оскільки для кожного з методів встановлюється контекст:

```js
// ----------------------
// Традиційний приклад
// ----------------------
// Приклад простого об'єкту зі своїм власним "this".
var obj = {
  num: 100,
};

// Встановлення "num" на об'єкті window, щоб проілюструвати, що це значення НЕ використовується.
window.num = 2020; // йой!

// Проста традиційна функція, яка оперує "this"
var add = function (a, b, c) {
  return this.num + a + b + c;
};

// call
var result = add.call(obj, 1, 2, 3); // встановлює "obj" як контекст виконання функції
console.log(result); // результат — 106

// apply
const arr = [1, 2, 3];
var result = add.apply(obj, arr); // встановлює "obj" як контекст виконання функції
console.log(result); // результат — 106

// bind
var result = add.bind(obj); // встановлює "obj" як контекст виконання функції
console.log(result(1, 2, 3)); // результат — 106
```

Якщо створити `add` як стрілкову функцію, то оскільки вона створена в контексті об'єкта `window` (глобальному контексті), вона вважатиме, що `this` і є `window`.

```js
// ----------------------
// Приклад зі стрілковою функцією
// ----------------------

// Приклад простого об'єкту зі своїм власним "this".
var obj = {
  num: 100,
};

// Встановлення "num" на об'єкті window, щоб проілюструвати, як це значення підхоплюється під час виконання.
window.num = 2020; // йой!

// Стрілкова функція
var add = (a, b, c) => this.num + a + b + c;

// call
console.log(add.call(obj, 1, 2, 3)); // результат — 2026

// apply
const arr = [1, 2, 3];
console.log(add.apply(obj, arr)); // результат — 2026

// bind
const bound = add.bind(obj);
console.log(bound(1, 2, 3)); // результат — 2026
```

Можливо, найбільшу користь стрілкові функції приносять під час використання їх з методами {{domxref("setTimeout()")}} й {{domxref("EventTarget/addEventListener()", "EventTarget.addEventListener()")}}, що часто потребує певного замикання, методу `call`, `apply` чи `bind`, щоб пересвідчитись, що функція виконується в правильному контексті.

#### Приклад з традиційною функцією

```js
var obj = {
  count: 10,
  doSomethingLater: function () {
    setTimeout(function () {
      // Функція виконується в контексті об'єкта window
      this.count++;
      console.log(this.count);
    }, 300);
  },
};

obj.doSomethingLater(); // консоль друкує "NaN", оскільки властивість "count" знаходиться не у контексті об'єкта window.
```

#### Приклад зі стрілковою функцією

```js
var obj = {
  count: 10,
  doSomethingLater: function () {
    // Традиційна функція прив'язує "this" до контексту об'єкта "obj".
    setTimeout(() => {
      // Оскільки стрілкова функція не має власної прив'язки, і
      // setTimeout (як виклик функції) не створює такої прив'язки
      // сам, то всередині буде використано контекст "obj" з
      // традиційної функції.
      this.count++;
      console.log(this.count);
    }, 300);
  },
};

obj.doSomethingLater();
```

### Відсутність прив'язки `arguments`

Стрілкові функції не мають власного [об'єкта `arguments`](/uk/docs/Web/JavaScript/Reference/Functions/arguments). Тому в наступному прикладі `arguments` посилається на аргументи зовнішнього контексту:

```js
var arguments = [1, 2, 3];
var arr = () => arguments[0];

arr(); // 1

function foo(n) {
  var f = () => arguments[0] + n; // неявна прив'язка до аргументів функції foo. arguments[0] дорівнює n
  return f();
}

foo(3); // 3 + 3 = 6
```

В більшості випадків застосування [залишкових параметрів](/uk/docs/Web/JavaScript/Reference/Functions/rest_parameters) є доброю альтернативою використанню об'єкта `arguments`.

```js
function foo(n) {
  var f = (...args) => args[0] + n;
  return f(10);
}

foo(1); // 11
```

### Використання з оператором `new`

Стрілкові функції не можна використовувати як конструктор, вживання їх з оператором `new` викине помилку.

```js
var Foo = () => {};
var foo = new Foo(); // TypeError: Foo is not a constructor
```

### Використання властивості `prototype`

Стрілкові функції не мають властивості `prototype`.

```js
var Foo = () => {};
console.log(Foo.prototype); // undefined
```

### Вживання з ключовим словом `yield`

Ключове слово [`yield`](/uk/docs/Web/JavaScript/Reference/Operators/yield) не можна використовувати всередині тіла стрілкової функції (окрім як всередині вкладених в неї звичайних функцій). Як наслідок, стрілкові функції не можуть бути генераторами.

### Тіло функції

Стрілкові функції можуть мати або "скорочене тіло", або звичне "блокове тіло функції".

В скороченому тілі вказується лише вираз, який стає неявним поверненим значенням. В блоці тіла функції необхідно вказати інструкцію `return` явно.

```js
var func = (x) => x * x;
// скорочений запис тіла, неявне повернення значення

var func = (x, y) => {
  return x + y;
};
// всередині блокового тіла необхідно вказувати "return" явно
```

### Повернення об'єктних літералів

Слід мати на увазі, що повернення об'єктних літералів в скороченому записі тіла функції `params => {object:literal}` не працюватиме так, як очікується.

```js
var func = () => { foo: 1 };
// Виклик func() поверне undefined!

var func = () => { foo: function() {} };
// SyntaxError: function statement requires a name
```

Так відбувається через те, що код всередині фігурних дужок ({}) читається як набір інструкцій (тобто `foo` вважається міткою, а не ключем значення в об'єктному літералі).

Необхідно обгортати об'єктний літерал в круглі дужки:

```js
var func = () => ({ foo: 1 });
```

### Розриви рядка

Стрілкова функція не може містити розрив рядка між параметрами і її стрілкою.

```js
var func = (a, b, c)
  => 1;
// SyntaxError: Unexpected token '=>'
```

Однак це можна обійти шляхом додавання розриву рядка після стрілки, або вживання круглих і фігурних дужок так, як показано нижче. Це дасть можливість зберегти код гарним і легким. Можна також переривати рядок між аргументами функції.

```js
var func = (a, b, c) => 1;

var func = (a, b, c) => 1;

var func = (a, b, c) => {
  return 1;
};

var func = (a, b, c) => 1;

// помилки SyntaxError не буде
```

### Порядок розбору

Хоча стрілка в стрілковій функції не є оператором, ці функції мають особливі правила парсингу, які по-іншому взаємодіють з [пріоритетом операторів](/uk/docs/Web/JavaScript/Reference/Operators/Operator_Precedence) у порівнянні зі звичайними функціями.

```js
let callback;

callback = callback || function() {}; // добре

callback = callback || () => {};
// SyntaxError: invalid arrow-function arguments

callback = callback || (() => {});    // добре
```

## Приклади

### Базове використання

```js
// Порожня стрілкова функція повертає undefined
let empty = () => {};

(() => 'foobar')();
// Повертає "foobar"
// (це називається Вираз одразу викликаної функції)

var simple = (a) => (a > 15 ? 15 : a);
simple(16); // 15
simple(10); // 10

let max = (a, b) => (a > b ? a : b);

// Проста фільтрація, перебирання масиву, тощо...

var arr = [5, 6, 13, 0, 1, 18, 23];

var sum = arr.reduce((a, b) => a + b);
// 66

var even = arr.filter((v) => v % 2 == 0);
// [6, 0, 18]

var double = arr.map((v) => v * 2);
// [10, 12, 26, 0, 2, 36, 46]

// Більш лаконічні ланцюги промісів
promise
  .then((a) => {
    // ...
  })
  .then((b) => {
    // ...
  });

// Безпараметрові стрілкові функції, які простіше розібрати візуально
setTimeout(() => {
  console.log('Я відбудусь раніше');
  setTimeout(() => {
    // Глибший код
    console.log('Я відбудусь пізніше');
  }, 1);
}, 1);
```

## Специфікації

{{Specifications}}

## Сумісність із браузерами

{{Compat}}

## Дивіться також

- ["Поглиблено про ES6: Стрілкові функції" на hacks.mozilla.org (англ.)](https://hacks.mozilla.org/2015/06/es6-in-depth-arrow-functions/)
