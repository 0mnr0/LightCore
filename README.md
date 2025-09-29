# 📚 LightCore.js — документация

Минималистичная JS-библиотека для упрощённой работы с DOM, анимациями, стилями, локальным хранилищем и переводами.
---

## 🚀 Быстрый старт

```html
<script src="lightcore.js" defer></script>
```

После подключения доступны глобальные утилиты, расширенные прототипы `HTMLElement` и вспомогательные объекты.

---

## 🔍 Основные утилиты

| Функция              | Описание                                            | Пример                           |
| -------------------- | --------------------------------------------------- | -------------------------------- |
| `find(selector)`     | Возвращает первый элемент по селектору.             | `find("h1").textContent`         |
| `findAll(selector)`  | Возвращает список всех элементов по селектору.      | `findAll("p")`                   |
| `findById(id)`       | Возвращает элемент по ID.                           | `findById("app")`                |
| `print`, `log`       | Синонимы `console.log`.                             | `print("Hello")`                 |
| `warn`               | Синоним `console.warn`.                             | `warn("Warning!")`               |
| `sleep(ms)`          | Промис-задержка.                                    | `await sleep(1000)`              |
| `random(min,max)`    | Случайное число от `min` до `max`.                  | `random(1,10)`                   |
| `runLater(fun,time)` | Выполнить функцию с задержкой (дважды ждет `time`). | `runLater(()=>alert("Hi"),1000)` |

---

## 🎨 Работа со стилями

### Создание и удаление CSS

* `CreateStyle(id, cssText)` — создать стиль и добавить его после `<body>`.
* `RemoveStyle(id)` — удалить стиль по ID.

```js
CreateStyle("redBorder", "div { border: 1px solid red; }");
RemoveStyle("redBorder");
```

---

## 🧩 Расширения `HTMLElement`

### Поиск и события

* `el.find(selector)` — поиск внутри элемента.
* `el.findAll(selector)` — все элементы внутри.
* `el.onEvent(type, listener)` — добавить обработчик события (синонимы: `listen`, `addEvent`).

### Прозрачность

* `el.setAlpha(a)` / `el.getAlpha()` — установка/чтение прозрачности.
* `el.alpha` — геттер/сеттер (от 0 до 1).

### Размеры

* `el.realWidth`, `el.realHeight` — реальные размеры (scroll).
* `el.cornerRadius` — радиус скругления (px).

### Жизненный цикл

* `el.destroy()` — удалить элемент.
* `el.phantom = true/false` — временно скрыть элемент (позиция `absolute`, `opacity=0`, `zIndex=-100`).

### Анимации

* `el.disableAnimations(property, unlockTime)` — временно отключить CSS transition.
* `el.makeZeroAnimation(animationFn, attrs, wait)` — отключить анимации для указанных свойств, применить изменения, вернуть анимации.
* `el.makeLater(fn,time)` / `el.executeLater(fn,time)` — выполнить функцию позже.

### Текстовые эффекты

* `el.animateByWords(speed, name)` — оборачивает слова в `<span>` с CSS-анимацией.
* `el.showByWords(speed, fontSize, fontFamily)` — поочередное появление слов.
* `el.splitBySymbols()` — разбивает текст на символы (возвращает список `<span>`).

---

## 🛠️ Debug-утилиты

```js
debug.hits();         // показать рамки вокруг элементов
debug.outlinedHits(); // показать outline вокруг элементов
debug.videoControls(); // включать/выключать controls у <video>
```

---

## 🏗️ Создание элементов

```js
createElementWith("div", {
  background: "red",
  scale: "1.2",
  transition: "all .2s"
});
```

Возвращает `<div>` с заданными стилями.

---

## 💾 LocalStorage API

Доступно через `window.LocalStorage`:

| Метод                            | Описание                           |
| -------------------------------- | ---------------------------------- |
| `save(key, val)`                 | Сохранить строку.                  |
| `get(key)`                       | Получить строку.                   |
| `getInt(key)`                    | Получить число.                    |
| `getFloat(key)`                  | Получить число с плавающей точкой. |
| `getBool(key)`                   | Получить булево значение.          |
| `getString(key)`                 | Получить строку.                   |
| `isKeyExists(key)`               | Проверить существование ключа.     |
| `remove(key)` / `removeKey(key)` | Удалить запись.                    |

---

## 🌍 TranslateAssistant (i18n)

Глобальный объект `window.TranslateAssistant` для работы с переводами.

### Инициализация

```js
TranslateAssistant.init("en", {
  en: { hello: "Hello" },
  ru: { hello: "Привет" },
  by: "ru" // alias языка
});
```

### Методы

* `TranslateAssistant.isLangAvailable(lang)` — проверка языка.
* `TranslateAssistant.defaultLocale(lang)` — получить/установить язык по умолчанию.
* `TranslateAssistant.dict(dict?)` — получить/заменить словарь.
* `TranslateAssistant.getAvailableLanguages()` — список доступных языков.

### Переводы

* `getString(key)` — глобальная функция для получения перевода.
* `TranslateAssistant.translate.get(key)` — получить строку.
* `TranslateAssistant.translate.all()` — перевести все элементы с `data-i18n`.
* `TranslateAssistant.translate.key(key)` — синоним `get(key)`.

```html
<p data-i18n="hello">Default</p>
<script>
  TranslateAssistant.translate.all(); // заменит текст на перевод
</script>
```

---

## 📌 Константы

| Константа              | Значение     |
| ---------------------- | ------------ |
| `absolute`             | `"absolute"` |
| `relative`             | `"relative"` |
| `PRC`                  | `"100%"`     |
| `center`               | `"center"`   |
| `scale`                | `"scale"`    |
| `none`, `None`, `NONE` | `"none"`     |

---

## 📖 Пример

```js
const box = createElementWith("div", { 
  background: "blue", 
  width: "100px", 
  height: "100px" 
});

document.body.appendChild(box);

box.alpha = 0.5;
box.makeLater(() => box.alpha = 1, 1000);
```

---
