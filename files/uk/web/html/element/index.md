---
title: Довідник елементів HTML
slug: Web/HTML/Element
tags:
  - Basic
  - Element
  - HTML
  - Reference
  - Web
  - l10n:priority
---

{{HTMLSidebar("Elements")}}

Ця сторінка перелічує всі {{Glossary("Element","елементи")}} {{Glossary("HTML")}}, котрі можна створити за допомогою {{Glossary("Tag", "тегів")}}.

Вони згруповані за функціями, щоб допомогти структурувати їх розуміння. Алфавітний список усіх елементів доступний у боковій панелі на сторінці кожного елемента, як і на цій.

> **Примітка:** Для отримання докладної інформації про основи елементів та атрибутів HTML дивіться [розділ про елементи у статті Вступ до HTML](/uk/docs/Learn/HTML/Introduction_to_HTML#elementy-osnovni-budmaterialy).

## Головний корінь

{{HTMLRefTable("HTML Root Element")}}

## Метадані документа

Метадані містять інформацію про сторінку. Вона включає інформацію про стилі, сценарії та дані, що допомагають програмам ({{Glossary("search engine", "пошуковим системам")}}, {{Glossary("Browser","браузерам")}} тощо) у використанні та візуалізації сторінки. Метадані стилів та сценаріїв можуть бути визначені у сторінці або посилатись на інший файл, що містить інформацію.

{{HTMLRefTable("HTML Document Metadata")}}

## Розділовий корінь

{{HTMLRefTable("Sectioning Root Element")}}

## Розділення вмісту

Елементи розділення вмісту дають змогу впорядкувати вміст документа у логічних частинах. Для створення грубого нарису вмісту сторінки, включно із верхньою та нижньою навігацією, а також елементами заголовків для розпізнання розділів вмісту, слід використовувати розділові елементи.

{{HTMLRefTable("HTML Sections")}}

## Текстовий вміст

Для впорядкування блоків чи розділів вмісту, розташованого між початковим {{HTMLElement("body")}} та завершальним `</body>` тегами, слід використовувати елементи текстового вмісту. Що важливо для {{Glossary("accessibility", "доступності")}} та {{Glossary("SEO")}}, ці елементи дають змогу розпізнати призначення або структуру такого вмісту

{{HTMLRefTable("HTML Grouping Content")}}

## Семантичні текстові елементи

Для оголошення значення, структури чи стилю слова, рядка або будь-якого довільного шматка тексту слід використовувати семантичні текстові елементи.

{{HTMLRefTable("HTML Text-Level Semantics")}}

## Зображення та мультимедіа

HTML підтримує різноманітні мультимедійні ресурси, наприклад, зображення, аудіо та відео.

{{HTMLRefTable("multimedia")}}

## Вбудований вміст

На додачу до звичайного мультимедійного вмісту, HTML може включати розмаїття іншого вмісту, навіть якщо з ним не завжди легко взаємодіяти.

{{HTMLRefTable({"include":["HTML embedded content"], "exclude":["multimedia"]})}}

## SVG та MathML

Можна вбудовувати [SVG](/uk/docs/Web/SVG) та [MathML](/uk/docs/Web/MathML) вміст в HTML документи за допомогою елементів {{SVGElement("svg")}} і {{MathMLElement("math")}}.

<table class="no-markdown">
  <thead>
    <tr>
      <th scope="col">Елемент</th>
      <th scope="col">Опис</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>{{SVGElement("svg")}}</td>
      <td>
        Елемент <code>svg</code> – контейнер, що оголошує нову систему координат та
        <a href="/uk/docs/Web/SVG/Attribute/viewBox">область перегляду</a>. Він використовується як крайній зовнішній елемент документів SVG, але також може використовуватись для вбудовування фрагмента SVG у документ SVG або HTML.
      </td>
    </tr>
    <tr>
      <td>{{MathMLElement("math")}}</td>
      <td>
        Елемент верхнього рівня у MathML – <code>&#x3C;math></code>. Кожен дійсний екземпляр MathML мусить бути загорнутий у теги <code>&#x3C;math></code>. На додачу – не можна вкладати один елемент <code>&#x3C;math></code> в інший, але можна мати довільне число інших нащадків у такому елементі.
      </td>
    </tr>
  </tbody>
</table>

## Сценарії

Для створення динамічного вмісту та вебзастосунків HTML підтримує використання мов сценаріїв, перш за все – JavaScript. Певні елементи слугують для підтримки такої функціональності.

{{HTMLRefTable("HTML Scripting")}}

## Розмежування редагувань

Ці елементи вказують на те, що певні частини тексту були змінені

{{HTMLRefTable("HTML Edits")}}

## Табличний вміст

Тут – елементи, що використовуються для створення та керування табличними даними.

{{HTMLRefTable("HTML tabular data")}}

## Форми

HTML надає низку елементів, що можуть разом використовуватись для створення форм, котрі користувач може заповнювати та надсилати вебсайтові або застосункові. Є купа докладнішої інформації про це, доступної у [Настановах з форм HTML](/uk/docs/Learn/Forms).

{{HTMLRefTable({"include": ["HTML forms"], "exclude":["Deprecated"]})}}

## Інтерактивні елементи

HTML пропонує палітру елементів, що допоміжні у створенні інтерактивних об‘єктів користувацького інтерфейсу.

{{HTMLRefTable("HTML interactive elements")}}

## Вебкомпоненти

Вебкомпоненти – пов‘язана із HTML технологія, що дає змогу, по суті, створювати та використовувати користувацькі елементи так, ніби вони є звичайним HTML. На додачу – можна створювати користувацькі версії стандартних елементів HTML.

{{HTMLRefTable({"include":["Web Components"],"exclude":["Deprecated", "Obsolete"]})}}

## Невживані та нерекомендовані елементи

> **Зауваження:** Це старі елементи HTML, що не повинні використовуватися. **Їх ніколи не слід використовувати у нових проєктах, а також слід заміняти у старих проєктах настільки скоро, наскільки можливо.** Вони перелічені виключно заради повноти інформації.

{{HTMLRefTable({"include":["Deprecated","Obsolete"]})}}
