---
title: String.prototype.slice()
slug: Web/JavaScript/Reference/Global_Objects/String/slice
tags:
  - JavaScript
  - Method
  - Prototype
  - Reference
  - String
browser-compat: javascript.builtins.String.slice
---
{{JSRef}}

Метод **`slice()`** витягає частину рядка і повертає її новим рядком, не змінюючи початковий.

{{EmbedInteractiveExample("pages/js/string-slice.html", "taller")}}

## Синтаксис

```js
slice(beginIndex)
slice(beginIndex, endIndex)
```

### Параметри

- `beginIndex`

  - : Індекс (нумерація якого починається нулем), за яким почнеться вибирання частини рядка.

    Якщо значення `beginIndex` — від'ємне, метод `slice()` почне екстракцію з позиції за індексом `str.length + beginIndex`. (Наприклад, `"test".slice(-2)` повертає `"st"`)

    Якщо параметр `beginIndex` опущено, не визначено, або його неможливо перетворити на число (за допомогою {{jsxref('Number', 'Number(beginIndex)')}}), метод `slice()` почне вибирання символів з початку рядка. (Наприклад, `"test".slice()` повертає `"test"`)

    Якщо параметр `beginIndex` — більший за довжину рядка `str.length` або дорівнює їй, то буде повернено порожній рядок. (Наприклад, `"test".slice(4)` повертає `""`)

- `endIndex` {{optional_inline}}

  - : Індекс (нумерація якого починається нулем), _перед_ яким слід припинити вибирання рядка. Символ, який знаходиться за цим індексом, не буде включено до результату.

    Якщо параметр `endIndex` опущено, не визначено, або він не може бути перетворений на число (за допомогою {{jsxref('Number', 'Number(endIndex)')}}), метод `slice()` продовжить вибирати все до кінця рядка. (Наприклад, `"test".slice(2)` повертає `"st"`)

    Якщо параметр `endIndex` — більший за `str.length`, метод `slice()` також вибирає все до кінця рядка. (Наприклад, `"test".slice(2, 10)` повертає `"st"`)

    Якщо `endIndex` — від'ємне число, метод `slice()` сприйматиме його як `str.length + endIndex`. (Наприклад, якщо `endIndex` дорівнює `-2`, його значення вважатиметься рівним виразові `str.length - 2`, а виклик `"test".slice(1, -2)` поверне `"e"`).

    Якщо параметр `endIndex` вказує на позицію, яка знаходиться перед тією, що позначена у `startIndex`, метод `slice()` поверне `""`.
    (Наприклад, як `"test".slice(2, -10)`, `"test".slice(-1, -2)` або `"test".slice(3, 2)`).

### Повернене значення

Новий рядок, що містить вибрану частину рядка.

## Опис

Метод `slice()` витягає текст з початкового рядка і повертає його як новий рядок. Зміни в тексті одного рядка ніяк не впливають на інший.

Метод `slice()` витягає текст до позиції, вказаної у `endIndex`, проте не включає її. Наприклад, `str.slice(1, 4)` вибирає вміст від другого символу і до четвертого (символи з індексами `1`, `2`, і `3`).

Іще один приклад: виклик `str.slice(2, -1)` витягне частину тексту, починаючи третім символом рядка, і закінчуючи другим з кінця.

## Приклади

### Застосування `slice()` для створення нового рядка

Наступний приклад використовує метод `slice()` для створення нового рядка.

```js
let str1 = 'Світає, край неба палає...', // довжина рядка str1 дорівнює 26.
    str2 = str1.slice(1, 6),
    str3 = str1.slice(5, -3),
    str4 = str1.slice(8),
    str5 = str1.slice(30);
console.log(str2)  // ВИВІД: вітає
console.log(str3)  // ВИВІД: є, край неба палає
console.log(str4)  // ВИВІД: край неба палає...
console.log(str5)  // ВИВІД: ""
```

### Застосування `slice()` з від'ємними індексами

Наступний приклад використовує метод `slice()` з від'ємними індексами.

```js
let str = 'Світає, край неба палає...'
str.slice(-8)      // повертає 'палає...'
str.slice(-8, -3)  // повертає 'палає'
str.slice(0, -3)   // повертає 'Світає, край неба палає'
```

Наступний приклад рахує `17` позицій у зворотному напрямі від кінця рядка, аби знайти індекс початку, і потім прямує звідти вперед на позицію `15` від початку рядка, щоб знайти індекс кінця вибірки.

```js
console.log(str.slice(-17, 15)) // => "рай не"
```

Код далі – рахує `11` позицій вперед від початку, щоб знайти індекс старту вибірки, і далі перебирає `9` позицій з кінця рядка у зворотному порядку, де і завершує вибирання.

```js
console.log(str.slice(11, -9)) // => "й неба"
```

А такі аргументи змушують метод порахувати `6` позицій з кінця у зворотному напрямку для знаходження індексу початку вибірки, і іще `1` у зворотному напрямку з кінця рядка для знаходження кінцевого індексу вибірки.

```js
console.log(str.slice(-6, -1)) // => "лає.."
```

## Специфікації

{{Specifications}}

## Сумісність із браузерами

{{Compat}}

## Дивіться також

- {{jsxref("String.prototype.substr()")}}
- {{jsxref("String.prototype.substring()")}}
- {{jsxref("Array.prototype.slice()")}}
