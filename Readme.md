## Что это 
Тестовый проект для быстрого развертывания документационного HUGO-сайта на локальном компе под Windows 10.
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

Отобразится сайт с документацией. Его можно использовать для дальнейших эекспериментов.

## Как добавлять и редактировать контент на сайте
Все действия ниже можно выполнять в VSCode или другом удобном инструменте. 
### Добавление новой страницы
Создайте файл `content/docs/new-article.md` со следующим содержанием:
```
---
title: New Article
---

Test content.
```
Сохраните файл и посмотрите сайт в браузере. Должна появиться пустая страница **New Article**.

9. добавить новую страницу
- создать файл `content/docs/new-article.md`
```
---
title: New Article
weight: 1
---

Test content.
```

10. Добавить пункт меню
- добавить в файл `config/_default/menus.yaml`
```
  - name: Example
    url: https://github.com/amihailov76/HUGO-Test
    weight: 6
```

11. Шаблон - добавить листинг статей
- добавить в файл `layouts/docs/list.html`
- после {{.Content}}

```
<ul>
  {{range .Pages }}
    <li>
      <a href={{.RelPermalink}}>{{.Title}}</a>
    </li>
  {{end}}
</ul>
```

12. Shortcode callout
- создать файл `layouts/shortcodes/callout.html`

```
{{ $type := .Get "type" | default "default" }}

<div class="callout {{ $type }}">
      {{ .Inner | markdownify }}
</div>
```

13. Использование callout
- добавить в `content/docs/guide/shortcodes/callout.md`

```
{{< callout type="info" >}}
Please visit GitHub to see the latest releases.
{{< /callout >}}
```

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
