# test task

**Framework:** [Nuxt 3](https://nuxt.com/)

**Среда выполнения:** [NodeJS версия 22+](https://nodejs.org)

**Менеджер пакетов:**  [npm](https://www.npmjs.com/)

**Для деплоя установлен:** [pm 2 + ecosystem.config.cjs](https://pm2.keymetrics.io/) 

## Технический стек

- **Nuxt 3** - прогрессивный фреймворк для создания современных веб-приложений
- **Vue 3** - прогрессивный JavaScript-фреймворк
- **Pinia** - управление состоянием приложения
- **TypeScript** - для типизации и повышения надежности кода

## Структура проекта

- `app/` - основной исходный код приложения
  - `assets/` - статические ресурсы (CSS, изображения)
  - `layouts/` - шаблоны страниц
  - `nuxt-config/` - настройки конфигов для модулей накста
  - `plugins/` - плагины для подключения vue библиотек и внешних сервисов
  - `public/` - публичные файлы
- `composables/` - переиспользуемые композаблы
- `entities/` - модель данных и хранилища
- `features/` - Фичи
- `pages/` - компоненты страниц приложения
- `shared/` - переиспользуемые функции и компоненты
- `widgets/` - Виджеты
- `.nuxt/` - сгенерированные файлы Nuxt
- `.output/` - скомпилированные файлы для production

## Архитектура приложения

Приложение следует принципам Feature-Sliced Design:
- **App** содержит настройки приложения и конфигурации проекта, статичные файлы и стили, используемые на всём проекте
- **Entities** - содержат модели данных и хранилища
- **Features** - реализация бизнес-логики
- **Widgets** - композиция компонентов для конкретных задач
- **Pages** - компоненты страниц приложения
- **Shared** - переиспользуемые функции и компоненты

## Development

1. Установка зависимостей:

```bash
npm install
```

2. Необходимо запустить конфигурацию husky, для корректной работы pre-commit хуков

```bash
npm run prepare-husky
```

3. Скопируйте файл `.env.example` в `.env` и настройте переменные окружения:
  ```bash
  cp .env.example .env
  ```

4. Заполните следующие переменные в файле `.env`:
  - NUXT_BASE_URL - эндпоинт апи
  - NUXT_IMAGE_BASE_DOMAIN - внешний домен, на котором хостятся изображения проекта

5. Запуск devServer on `http://localhost:3000`:

```bash
npm run dev
```

6. Для запуска локально в докере:
```bash
cd ../
make rebuild
make up
npm install
npm run dev
```

## Production

Для сборки и запуска в production:

Сборка контейнера

```bash
make rebuild
```

Запуск контейнера

```bash
make up
```

```bash
make bash-nuxt // Зайти в контейнер
npm install --production=false // Установить зависимости в контейнере
npm run deploy // Выполнить команду для обновления сборки и перезапуска pm2
```

Ознакомьтесь с [Deployment documentation Nuxt 3](https://nuxt.com/docs/getting-started/deployment) для получения дополнительной информации.
Ознакомьтесь с [Deployment System PM 2](https://pm2.keymetrics.io/docs/usage/deployment/) для получения дополнительной информации.
