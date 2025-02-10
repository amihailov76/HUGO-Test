## Установить перед развертыванием
- Git https://git-scm.com/downloads
- Node.js https://nodejs.org/en/download
- VSCode https://code.visualstudio.com/download

## Порядок действий
###В терминале VSCode:

1. Проверка установки git
```
git -v
```

2. Проверка установки NodeJS
```
node -v
```

3. Клонирование git репозитория
```
git clone https://github.com/amihailov76/HUGO-Test
```

4. Переход в директорию проекта
```
cd HUGO-Test
```

5. Установка npm зависимостей
```
npm i
```

6. запуск hugo сервера
```
npm run server
```

7. открыть ссылку в браузере
http://localhost:1313/

8. добавить новую страницу
- создать файл `content/docs/new-article.md`
```
---
title: New Article
---

Test content.
```

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
