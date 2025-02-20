---
title: String.prototype.at()
slug: Web/JavaScript/Reference/Global_Objects/String/at
tags:
  - String
  - JavaScript
  - Method
  - Prototype
  - Reference
  - polyfill
  - at
  - Experimental
browser-compat: javascript.builtins.String.at
---
{{JSRef}}

Метод **`at()`** приймає ціле число і повертає новий {{jsxref('String', 'рядок')}}, що складається з однієї кодової одиниці UTF-16, розміщеної за вказаною позицією. Цей метод приймає як додатні, так і від'ємні цілі числа. Від'ємні числа позначають номер позиції у зворотному напрямку, від останнього символу рядка.

{{EmbedInteractiveExample("pages/js/string-at.html")}}

## Синтаксис

```js
at(index)
```

### Параметри

- `index`
  - : Індекс (позиція) символу рядка, який потрібно отримати. Дає змогу також обирати позицію з кінця рядка, якщо передати від'ємне значення. Іншими словами, якщо вжито від'ємне число, цільовий символ буде знайдено шляхом перебирання позицій у зворотному напрямку, з кінця сторінки.

### Повернене значення

{{jsxref('String', 'Рядок')}}, який містить єдину кодову одиницю UTF-16, взяту за вказаною позицією. Повертає {{jsxref('undefined')}}, якщо за переданим індексом нічого не знайдено.

## Приклади

### Повернення останнього символу рядка

Наступний приклад демонструє функцію, яка повертає останній символ, знайдений у вказаному рядку.

```js
// Функція, яка повертає останній символ переданого рядка
function returnLast(arr) {
  return arr.at(-1);
}

let invoiceRef = 'мійІнвойс01';

console.log( returnLast(invoiceRef) );
// Друкує: '1'

invoiceRef = 'мійІнвойс02';

console.log( returnLast(invoiceRef) );
// Друкує: '2'
```

### Порівняння методів

Нижче наведено порівняння різних способів отримання передостаннього символу {{jsxref('String', 'рядка')}}. Позаяк всі наведені далі методи — коректні, з-поміж них виділяється лаконічність і чіткість саме методу `at()`.

```js
const myString = 'Всякий зелений автобус їде швидко.';

// Використання властивості "length" і методу charAt()
const lengthWay = myString.charAt(myString.length-2);
console.log(lengthWay); // Друкує: 'о'

// За допомогою методу slice()
const sliceWay = myString.slice(-2, -1);
console.log(sliceWay); // Друкує: 'о'

// Шляхом застосування методу at()
const atWay = myString.at(-2);
console.log(atWay); // Друкує: 'о'
```

## Специфікації

{{Specifications}}

## Сумісність із браузерами

{{Compat}}

## Дивіться також

- Поліфіл методу `String.prototype.at` також доступний у [`core-js`](https://github.com/zloirock/core-js#ecmascript-string-and-regexp)
- [Поліфіл методу "at()"](https://github.com/tc39/proposal-relative-indexing-method#polyfill).
- {{jsxref("String.prototype.indexOf()")}}
- {{jsxref("String.prototype.lastIndexOf()")}}
- {{jsxref("String.prototype.charCodeAt()")}}
- {{jsxref("String.prototype.codePointAt()")}}
- {{jsxref("String.prototype.split()")}}
