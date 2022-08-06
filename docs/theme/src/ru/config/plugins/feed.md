---
title: Конфиг плагина фида
icon: rss
order: 5
category:
  - Конфиг
tag:
  - Канал
  - Фид
  - Конфигурация плагина
  - Конфиг темы
---

## Введение <Badge text="включено по умолчанию" />

`vuepress-theme-hope` обеспечивает поддержку генерации каналов через плагин `vuepress-plugin-feed2`.

`vuepress-theme-hope` передает `plugins.feed` в параметрах темы в качестве параметров плагина для плагина `vuepress-plugin-feed2`.

Плагин `vuepress-plugin-feed2` может генерировать для вас файлы каналов в следующих трех форматах:

- Atom 1.0
- JSON 1.1
- RSS 2.0

Включите плагин, установив для `atom`, `json` или `rss` значение `true` в параметрах плагина в соответствии с форматом, который вы хотите сгенерировать.

::: tip

Atom и JSON предназначены для обеспечения дополнительной адаптации программного обеспечения Feed.

Если возможно, используйте RSS в качестве первого выбора.

:::

::: info

Подробнее смотрите в [документации плагина feed2][feed-config].

:::

## Опции плагина

### atom

- Тип: `boolean`
- По умолчанию: `false`

Выводить ли файлы синтаксиса Atom.

### json

- Тип: `boolean`
- По умолчанию: `false`

Выводить ли файлы синтаксиса JSON.

### rss

- Тип: `boolean`
- По умолчанию: `false`

Выводить ли файлы синтаксиса RSS.

### image

- Тип: `string`

Большое изображение/иконка ленты, вероятно, используемая в качестве баннера.

### icon

- Тип: `string`

Маленькая иконка ленты, вероятно, используемая в качестве фавиконки.

### count

- Тип: `number`
- По умолчанию: `1000`

Установите максимальное количество элементов в ленте. После того, как все страницы отсортированы, будут перехвачены первые элементы `count`.

Если на вашем сайте много статей, вы можете рассмотреть этот вариант, чтобы уменьшить размер файла фида.

### customElements

- Тип: `string[]`
- По умолчанию: `["ExternalLinkIcon"]`

Пользовательский элемент или компонент, который следует удалить из фида.

### filter

- Тип: `(page: Page)=> boolean`
- По умолчанию:

  ```ts
  ({ frontmatter, filePathRelative }: Page): boolean =>
    !(
      frontmatter.home ||
      !filePathRelative ||
      frontmatter.article === false ||
      frontmatter.feed === false
    );
  ```

Пользовательская функция фильтра, используемая для фильтрации элементов фида.

### sort

- Тип: `(pageA: Page, pageB: Page)=> number`

Пользовательская функция сортировки, используемая для сортировки элементов фида.

::: warning

Мы настоятельно рекомендуем вам установить этот параметр, иначе порядок элементов в потоке фида полностью определяется порядком страниц, выводимых VuePress.

Вы можете сортировать страницы на сайте в соответствии с вашими потребностями.

:::

### channel

Параметр `channel` используется для настройки _Каналов подачи_.

Доступные параметры см. в разделе [Конфигурация → Канал][feed-config-channel]

### atomOutputFilename

- Тип: `string`
- По умолчанию: `atom.xml`

Имя выходного файла синтаксиса Atom относительно выходного каталога.

### jsonOutputFilename

- Тип: `string`
- По умолчанию: `feed.json`

Имя выходного файла синтаксиса JSON относительно выходного каталога.

### rssOutputFilename

- Тип: `string`
- По умолчанию: `rss.xml`

Имя выходного файла синтаксиса RSS относительно выходного каталога.

### getter

Контроллер генерации фида.

::: tip

Плагин предоставляет разумный геттер по умолчанию, если вы хотите получить полный контроль над генерацией ленты, вы можете установить это поле.

:::

Подробности смотрите в разделе [Получатель фида][feed-config-getter].

### locales

- Тип: `Record<string, BaseFeedOptions>`
- Обязательный: Нет

Вы можете использовать его для определенных параметров для каждой локали.

Поддерживаются любые указанные выше параметры, кроме `hostname`.

[feed-config]: https://vuepress-theme-hope.github.io/v2/feed/config/
[feed-config-channel]: https://vuepress-theme-hope.github.io/v2/feed/config/channel.html
[feed-config-getter]: https://vuepress-theme-hope.github.io/v2/feed/config/getter.html