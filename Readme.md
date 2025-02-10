## Что это 

[Тестовый проект](https://github.com/amihailov76/HUGO-Test) для быстрого развертывания документационного HUGO-сайта на локальном компе под Windows 10.
Готов к использованию, уже содержит HUGO и шаблон сайта на теме [Hextra](http://localhost:1313/docs/#what-is-hextra)


## Что установить перед развертыванием проекта

- Git https://git-scm.com/downloads
- Node.js https://nodejs.org/en/download
- VSCode https://code.visualstudio.com/download

## Как создать сайт с документацией
В терминале VSCode:

1. Проверьте установку git
```
git -v
```

2. Проверьте установку NodeJS
```
node -v
```

3. Клонируйте git-репозиторий с шаблоном проекта
```
git clone https://github.com/amihailov76/HUGO-Test
```

4. Перейдите в каталог проекта
```
cd HUGO-Test
```

5. Установите npm-зависимости
```
npm i
```

6. Запустите сервер HUGO
```
npm run server
```

7. Откройте ссылку на сайт в браузере
http://localhost:1313/

Отобразится сайт с документацией. Его можно использовать для дальнейших экспериментов.

## Как добавлять и редактировать контент на сайте
Все действия ниже можно выполнять в VSCode или другом удобном инструменте. Не забывайте сохранять изменененные файлы. Сайт обновляется автоматически после каждого сохранения. Если изменения не отображаются на сайте, остановите в терминале сервер HUGO (CTRL+C), затем запустите сервер заново.
### Добавление новой страницы на сайт
1. Создайте файл `content/docs/new-article.md` со следующим содержанием:
```
---
title: Новый раздел
---

Test content.
```
2. Сохраните файл и посмотрите сайт в браузере.
Должна появиться страница **Новый раздел** на самой нижней позиции в главном меню сайта.

### Изменение положения страницы на сайте
1. В созданном файле `content/docs/new-article.md` добавьте строку `weight: 1`
```
---
title: New Article
weight: 1
---

Test content.
```
2. Сохраните файл и посмотрите сайт в браузере.
Страница **Новый раздел** переместится на верхнюю позицию в главном меню сайта.

### Добавление пункта меню в шапке сайта
1. В файл `config/_default/menus.yaml` добавьте следующий блок:
```
  - name: Example
    url: https://github.com/amihailov76/HUGO-Test
    weight: 6
```
2. Сохраните файл и посмотрите сайт в браузере.
В шапке сайта появится пункт меню **Example**.

### Добавление на страницу списка вложенных статей
1. В файл `layouts/docs/list.html` после `{{.Content}}` добавьте следующий блок: 

```
<ul>
  {{range .Pages }}
    <li>
      <a href={{.RelPermalink}}>{{.Title}}</a>
    </li>
  {{end}}
</ul>
```
2. Сохраните файл и посмотрите сайт в браузере.
На страницах, где есть вложенные страницы, появится блок ссылок на вложенные.


## Полезные ссылки

Дока Hugo:
- Контент https://gohugo.io/content-management/organization/#organization-of-content-source
- Конфигурация https://gohugo.io/getting-started/configuration/
- Меню https://gohugo.io/methods/site/menus/
- Шаблоны https://gohugo.io/templates/introduction/
- Shortcode https://gohugo.io/content-management/shortcodes/

Темы Hugo:
- Все темы для документации https://themes.gohugo.io/tags/docs/
- Hextra https://imfing.github.io/hextra/docs/getting-started/
- Lotus Docs https://lotusdocs.dev/docs/
