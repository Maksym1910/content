---
title: position
slug: Web/CSS/position
tags:
  - CSS
  - CSS Positioning
  - CSS Property
  - Reference
  - recipe:css-property
browser-compat: css.properties.position
---

{{CSSRef}}

Властивість [CSS](/uk/docs/Web/CSS) **`position`** вказує на те, як елемент розміщується в документі. Властивості {{Cssxref("top")}}, {{Cssxref("right")}}, {{Cssxref("bottom")}} та {{Cssxref("left")}} визначають остаточне місцеположення розміщених елементів.

{{EmbedInteractiveExample("pages/css/position.html")}}

## Синтаксис

```css
position: static;
position: relative;
position: absolute;
position: fixed;
position: sticky;

/* Глобальні значення */
position: inherit;
position: initial;
position: revert;
position: unset;
```

### Значення

- `static` (статичне)
  - : Елемент позиціонується згідно зі звичайним плином документа. Властивості {{cssxref("top")}}, {{cssxref("right")}}, {{cssxref("bottom")}}, {{cssxref("left")}} та {{cssxref("z-index")}} _не діють_. Таке значення є усталеним.
- `relative` (відносне)

  - : Елемент позиціонується згідно зі звичайним плином документа, а тоді відступає вбік _відносно початкового положення_ на основі значень `top`, `right`, `bottom` та `left`. Відступ жодним чином не впливає на розміщення інших елементів; таким чином, простір, виділений для елемента у макеті сторінки, залишається таким самим, як був би, якби його `position` мала значення `static`.

    Це значення створює новий [контекст нагромадження](/uk/docs/Web/CSS/CSS_Positioning/Understanding_z_index/The_stacking_context), коли значення `z-index` відмінне від `auto`. Його вплив на елементи `table-*-group`, `table-row`, `table-column`, `table-cell` та `table-caption` є невизначеним.

- `absolute` (абсолютне)

  - : Елемент зникає зі звичайного плину документа, і для нього не виділяється жодного простору у макеті сторінки. Він позиціонується відносно до свого найближчого позиціонованого предка, якщо такий є; інакше – він розміщується відносно початкового [контейнерного блока](/uk/docs/Web/CSS/Containing_block). Його остаточна позиція визначена значеннями властивостей `top`, `right`, `bottom` та `left`.

    Це значення створює новий [контекст нагромадження](/uk/docs/Web/CSS/CSS_Positioning/Understanding_z_index/The_stacking_context), коли значення `z-index` відмінне від `auto`. Зовнішні поля абсолютно позиціонованих елементів не [перекриваються](/uk/docs/Web/CSS/CSS_Box_Model/Mastering_margin_collapsing) з іншими зовнішніми полями.

- `fixed` (фіксоване)

  - : Елемент зникає зі звичайного плину документа, і для нього не виділяється жодного простору у макеті сторінки. Він позиціонується відносно до початкового [контейнерного блока](/uk/docs/Web/CSS/Containing_block), утвореного від {{glossary("viewport")}}, крім випадків, коли один з предків елемента має властивість `transform`, `perspective` або `filter`, значення котрої відмінне від `none` (дивіться також [Специфікацію трансформацій CSS](https://www.w3.org/TR/css-transforms-1/#propdef-transform)), – у таких випадках предок з однією з вищезгаданих властивостей поводиться як контейнерний блок. (Зверніть увагу: існує неузгодженість браузерів щодо впливу властивостей `perspective` та `filter` на формування контейнерного блоку.) Остаточна позиція елемента визначена значеннями властивостей `top`, `right`, `bottom` та `left`.

    Це значення завжди створює новий [контекст нагромадження](/uk/docs/Web/CSS/CSS_Positioning/Understanding_z_index/The_stacking_context). При друкові документа такий елемент друкується на одній позиції на _кожній сторінці_.

- `sticky` (липкий)

  - : Елемент позиціонується згідно зі звичайним плином документа, і далі зміщується відносно до свого _найближчого предка з прокручуванням_ та [контейнерного блока](/uk/docs/Web/CSS/Containing_block) (найближчого предка блокового рівня), включно з елементами таблиць, на основі значень властивостей `top`, `right`, `bottom` та `left`. Відступ не впливає на позицію інших елементів.

    Це значення завжди створює новий [контекст нагромадження](/uk/docs/Web/CSS/CSS_Positioning/Understanding_z_index/The_stacking_context). Зверніть увагу, що липкий елемент "прилипає" до свого найближчого предка, який має "механізм прокручування" (утворений встановленням властивості `overflow` у значення `hidden`, `scroll`, `auto` чи `overlay`), навіть коли такий предок не є найближчим справді прокручуваним предком. Це практично перешкоджає будь-якій "липкій" поведінці (дивіться [GitHub-проблему W3C CSSWG](https://github.com/w3c/csswg-drafts/issues/865)).

## Опис

### Типи позиціонування

- **Позиціонований елемент** – елемент, в котрого [обчислене](/uk/docs/Web/CSS/computed_value) значення `position` – одне з наступних: `relative`, `absolute`, `fixed`, `sticky`. (Інакше кажучи, що завгодно, окрім `static`.)
- **Відносно позиціонований елемент** – елемент, в котрого [обчислене](/uk/docs/Web/CSS/computed_value) значення `position` – `relative`. Властивості {{Cssxref("top")}} та {{Cssxref("bottom")}} вказують вертикальний відступ від його звичайної позиції; властивості {{Cssxref("left")}} та {{Cssxref("right")}} вказують горизонтальний відступ.
- **Абсолютно позиціонований елемент** – елемент, в котрого [обчислене](/uk/docs/Web/CSS/computed_value) значення `position` – `absolute` або `fixed`. Властивості {{Cssxref("top")}}, {{Cssxref("right")}}, {{Cssxref("bottom")}} та {{Cssxref("left")}} вказують відступи від країв [контейнерного блока](/uk/docs/Web/CSS/Containing_block) елемента. (Контейнерний блок – то предок, відносно якого позиціонується елемент.) Якщо елемент має зовнішні поля, то вони додаються до відступів. Елемент утворює новий [блоковий контекст форматування](/uk/docs/Web/Guide/CSS/Block_formatting_context) (БКФ) для свого вмісту.
- **Липко позиціонований елемент** – елемент, в котрого [обчислене](/uk/docs/Web/CSS/computed_value) значення `position` – `sticky`. Він розглядається як відносно позиціонований, поки його [контейнерний блок](/uk/docs/Web/CSS/Containing_block) не перетне встановлений поріг (встановлений, наприклад, значенням властивості {{Cssxref("top")}}, відмінним від `auto`) всередині свого кореня плину (чи контейнера, всередині якого він прокручується), після чого буде вважатись "застряглим", поки не зустріне протилежний край свого [контейнерного блоку](/uk/docs/Web/CSS/Containing_block).

Переважну більшість часу абсолютно позиціоновані елементи, що мають {{Cssxref("height")}} та {{Cssxref("width")}} зі значенням `auto`, мають розмір, відповідний їх вмістові. Втім, не [заміщені](/uk/docs/Web/CSS/Replaced_element), абсолютно позиціоновані елементи можуть бути змушені заповнювати увесь доступний простір по вертикалі шляхом вказання {{Cssxref("top")}} та {{Cssxref("bottom")}} і залишення {{Cssxref("height")}} невказаною (тобто `auto`). Вони можуть аналогічно бути змушені заповнювати ввесь доступний простір по горизонталі шляхом встановлення {{Cssxref("left")}} та {{Cssxref("right")}} і залишення {{Cssxref("width")}} – `auto`.

Окрім вищеописаного випадку (абсолютно позиціонованих елементів, що заповнюють доступний простір):

- Якщо як `top`, так `bottom` – вказані (або, точніше кажучи, їх значення відмінне від `auto`), `top` перемагає.
- Якщо як `left`, так `right` – вказані, то `left` перемагає, коли {{Cssxref("direction")}} – `ltr` (англійська, горизонтальна японська тощо), а `right` перемагає, коли {{Cssxref("direction")}} – `rtl` (перська, арабська, іврит тощо).

## Занепокоєння щодо доступності

Пересвідчіться, що елементи, позиціоновані як `absolute` чи `fixed`, не затуляють решту змісту, коли збільшують зображення сторінки чи розмір тексту.

- [MDN – Розуміння WCAG, пояснення Директиви 1.4](/uk/docs/Web/Accessibility/Understanding_WCAG/Perceivable#guideline_1.4_make_it_easier_for_users_to_see_and_hear_content_including_separating_foreground_from_background)
- [Візуальна презентація: розуміння SC 1.4.8 | Розуміння WCAG 2.0](https://www.w3.org/TR/UNDERSTANDING-WCAG20/visual-audio-contrast-visual-presentation.html)

### Швидкодія та доступність

Прокручування елементів, що мають вміст, позиційований як `fixed` чи `sticky`, може призводити до проблем зі швидкодією та доступністю. Поки користувач прокручує, браузер мусить перемальовувати липкий чи фіксований вміст у новому місці. Залежно від вмісту, що треба перемальовувати, швидкодії браузера та швидкості роботи пристрою, браузер може не мати змоги підтримувати рівень перемальовування 60 кадрів на секунду, що веде до занепокоєння відносно людей з особливими потребами та до провисань для геть усіх. Одне з рішень – додати {{cssxref("will-change", "will-change: transform")}} до позиціонованих елементів, аби відмальовувати елемент у власному шарі, підвищивши швидкість перемальовування та, таким чином, покращити швидкодію та доступність.

## Формальне визначення

{{cssinfo}}

## Формальний синтаксис

{{csssyntax}}

## Приклади

### Відносне позиціонування

Відносно позиціоновані елементи мають заданий відступ від звичайної позиції в документі, але, втім, їх відступ не впливає на інші елементи. У прикладі нижче зверніть увагу: інші елементи розміщені так, неначе блок "Два" займає місце у своєму звичайному положенні.

#### HTML

```html
<div class="box" id="one">Один</div>
<div class="box" id="two">Два</div>
<div class="box" id="three">Три</div>
<div class="box" id="four">Чотири</div>
```

#### CSS

```css
* {
  box-sizing: border-box;
}

.box {
  display: inline-block;
  width: 100px;
  height: 100px;
  background: red;
  color: white;
}

#two {
  position: relative;
  top: 20px;
  left: 20px;
  background: blue;
}
```

{{EmbedLiveSample('Relative_positioning', '', '200px')}}

### Абсолютне позиціонування

Елементи, що є відносно позиціонованими, залишаються у звичайному плині документа. На відміну від них, абсолютно позиціонований елемент виймається із плину; таким чином, інші елементи розміщуються так, ніби його не існує. Абсолютно позиціонований елемент позиціонується відносно до свого _найближчого позиціонованого предка_ (наприклад, найближчого предка, що не є `static`). Якщо позиціонований предок не існує, елемент позиціонується відносно ПКБ (початкового контейнерного блока – дивіться також [визначення W3C](https://www.w3.org/TR/CSS2/visudet.html#containing-block-details)), котрий є контейнерним блоком кореневого елемента документа.

#### HTML

```html
<h1>Абсолютне позиціонування</h1>

<p>
  Я є базовим елементом блокового рівня. Сусідні до мене елементи блокового
  рівня сидять на нових рядках нижче від мене.
</p>

<p class="positioned">
  Усталено ми займаємо 100% ширини свого батьківського елемента, і є настільки
  високими, наскільки високим є наш дочірній вміст. Наші підсумкові ширина та
  висота – це сума наших вмісту, внутрішніх відступів та ширини чи висоти меж.
</p>

<p>
  Ми розділені своїми зовнішніми полями. Завдяки перекриттю зовнішніх полів ми
  розділені шириною одного зовнішнього поля, а не двох.
</p>

<p>
  рядкові елементи, <span>як-от цей</span> та <span>цей</span>, сидять на одному
  й тому ж рядку, вкупі із суміжними текстовими вузлами, якщо на тому самому
  рядку є місце. Рядкові елементи з переповненням
  <span>завертають на новий рядок, якщо це можливо, як-от цей, із текстом</span
  >, або просто переходять на новий рядок, якщо це неможливо, як-ось це
  зображення: <img src="long.jpg" />
</p>
```

#### CSS

```css
* {
  box-sizing: border-box;
}

body {
  width: 500px;
  margin: 0 auto;
}

p {
  background: aqua;
  border: 3px solid blue;
  padding: 10px;
  margin: 10px;
}

span {
  background: red;
  border: 1px solid black;
}

.positioned {
  position: absolute;
  background: yellow;
  top: 30px;
  left: 30px;
}
```

#### Результат

{{EmbedLiveSample('Absolute_positioning', '', '420px')}}

### Фіксоване позиціонування

Фіксоване позиціонування є подібним до абсолютного позиціонування, за виключенням того, що [контейнерний блок](/uk/docs/Web/CSS/Containing_block) елемента є початковим контейнерним блоком, утвореним _областю перегляду_, якщо жоден предок не має властивості `transform`, `perspective` чи `filter` зі значенням, відмінним від `none` (дивіться [Специфікацію CSS перетворень](https://www.w3.org/TR/css-transforms-1/#propdef-transform)), що змусило б такого предка замінити елементові його [контейнерний блок](/uk/docs/Web/CSS/Containing_block). Це може бути використано для створення "плавучого" елемента, що залишається на одній позиції, незалежно від прокручування. У прикладі нижче елемент "Один" зафіксований на відстані 80 пікселів від верху сторінки, і 10 пікселів від лівого краю.

#### HTML

```html
<div class="outer">
  <p>
    Але щоб ви зрозуміли, звідки виникає це хибне уявлення людей, цуратись
    насолоди і вихваляти страждання, я розкрию перед вами всю картину і
    роз’ясню, що саме говорив цей чоловік, який відкрив істину, якого я б назвав
    зодчим щасливого життя. Дійсно, ніхто не відкидає, не зневажає, не уникає
    насолод тільки через те, що це насолоди, але лише через те, що тих, хто не
    вміє розумно вдаватися насолоді, осягають великі страждання. Так само як
    немає нікого, хто полюбивши, вважав за краще і зажадав би саме страждання
    тільки за те, що це страждання, а не тому, що інший раз виникають такі
    обставини, коли страждання і біль приносять якесь і чималу насолоду. Якщо
    скористатися найпростішим прикладом, то хто з нас став би займатися якими б
    то не було тяжкими фізичними вправами, якщо б це не приносило з собою якоїсь
    користі? І хто міг би по справедливості дорікнути прагнення до насолоди, яке
    не несло б з собою ніяких неприємностей, або того, хто уникав би такого
    страждання, яке не приносило б з собою ніякої насолоди?
  </p>
  <p>
    Але ми цураємось і вважаємо, що заслуговують справедливого обурення ті, хто,
    піддався звабі і розбещеним спокусам, які дають їм насолоду, і без тями від
    пристрасті не передбачили, яких страждань і які нещастя на них чекають. Вони
    винні так само, як і ті, хто через душевну слабкість, тобто через бажання
    уникнути страждань і болю відмовляється від виконання свого обов’язку. Втім,
    тут дуже легко і просто провести відмінності, тому що, коли ми вільні і нам
    надана повна можливість вибору бажаного, коли ніщо не заважає нам робити те,
    що нам більше подобається, будь яку насолоду слід визнати бажаним, а
    будь-яке страждання огидним. Але при деяких обставинах – або на вимогу
    боргу, або в силу якоїсь необхідності часто доводиться забувати про насолоди
    і не втікати від тягарів. Тому мудрець дотримується в цьому випадку
    наступного принципу вибору – або, відмовляючись від задоволення, він отримує
    якісь інші і навіть великі насолоди, або, зазнаючи страждання, він
    позбавляється від більш жорстоких.
  </p>
  <div class="box" id="one">Один</div>
</div>
```

#### CSS

```css
* {
  box-sizing: border-box;
}

.box {
  width: 100px;
  height: 100px;
  background: red;
  color: white;
}

#one {
  position: fixed;
  top: 80px;
  left: 10px;
  background: blue;
}

.outer {
  width: 500px;
  height: 300px;
  overflow: scroll;
  padding-left: 150px;
}
```

#### Результат

{{EmbedLiveSample('Fixed_positioning', '', '300px')}}

### Липке позиціонування

Липке позиціонування може вважатись гібридом відносного та фіксованого позиціонування. Липко позиціонований елемент обробляється як відносно позиціонований, поки не перетне визначений поріг, після чого обробляється як фіксований, поки не досягне межі свого предка. Наприклад...

```css
#one {
  position: sticky;
  top: 10px;
}
```

...позиціонувало б елемент з атрибутом `id="one"` відносно, поки область перегляду прокручувалась би, а елемент був би менш ніж за 10 пікселів од верху. Пройшовши цей поріг, елемент був би зафіксований за 10 пікселів од верху.

Загальноприйняте використання липкого позиціонування – заголовки списку, відсортованого за алфавітом. Заголовок "Б" з‘явиться зразу після пунктів, що починаються з "А", поки вони прокручуються поза екраном. Замість вислизання за межі екрану разом з рештою вмісту, заголовок "Б" залишиться зафіксованим згори області перегляду, поки всі пункти "Б" не будуть прокручені поза екран, після чого буде перекритим заголовком "В", і так далі.

Обов‘язково слід вказувати поріг в одній з властивостей: `top`, `right`, `bottom` чи `left`, щоб липке позиціонування поводилось як очікується.

#### HTML

```html
<dl>
  <div>
    <dt>А</dt>
    <dd>Абу-Касимові Капці</dd>
    <dd>Аква-Віта</dd>
    <dd>Андерсон</dd>
    <dd>Астарта</dd>
    <dd>АтмАсфера</dd>
  </div>
  <div>
    <dt>В</dt>
    <dd>Вагоновожатые</dd>
    <dd>Вежа хмар</dd>
    <dd>Вій</dd>
    <dd>Воплі Відоплясова</dd>
    <dd>Вхід у змінному взутті</dd>
  </div>
  <div>
    <dt>Ґ</dt>
    <dd>Ґринджоли</dd>
  </div>
  <div>
    <dt>П</dt>
    <dd>Перкалаба</dd>
    <dd>Пирятин</dd>
    <dd>Піккардійська терція</dd>
    <dd>Пісні наших днів</dd>
    <dd>Плач Єремії</dd>
  </div>
</dl>
```

#### CSS

```css
* {
  box-sizing: border-box;
}

dl > div {
  background: #fff;
  padding: 24px 0 0 0;
}

dt {
  background: #b8c1c8;
  border-bottom: 1px solid #989ea4;
  border-top: 1px solid #717d85;
  color: #fff;
  font: bold 18px/21px Helvetica, Arial, sans-serif;
  margin: 0;
  padding: 2px 0 0 12px;
  position: -webkit-sticky;
  position: sticky;
  top: -1px;
}

dd {
  font: bold 20px/45px Helvetica, Arial, sans-serif;
  margin: 0;
  padding: 0 0 0 12px;
  white-space: nowrap;
}

dd + dd {
  border-top: 1px solid #ccc;
}
```

#### Результат

{{EmbedLiveSample('Sticky_positioning', '', '300px')}}

## Специфікації

{{Specifications}}

## Сумісність із браузерами

{{Compat}}

## Дивіться також

- [Вивчаймо CSS: позиціонування](/uk/docs/Learn/CSS/CSS_layout/Positioning)