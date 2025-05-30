# 🧩 Best Sneakers

**Best Sneakers** — это современное одностраничное веб-приложение интернет-магазина кроссовок, созданное на Vue 3 с использованием TailwindCSS и Vite. Это демонстрационный проект, показывающий лучшие практики построения e-commerce SPA на Vue.

## 🚀 Возможности

1. Просмотр каталога кроссовок
2. Добавление и удаление товаров из корзины
3. Избранные товары
4. Поиск и фильтрация по названию и цене
5. Оформление заказа (эмуляция)
6. Сохранение корзины в `localStorage`
7. REST API через [Mokky.dev](https://mokky.dev/)
8. Анимации элементов с [Auto Animate](https://formkit.com/essentials/auto-animate)


## 🛠️ Используемые технологии

- [Vue 3](https://vuejs.org/)
- [Vite](https://vitejs.dev/)
- [TailwindCSS](https://tailwindcss.com/)
- [Vue Router](https://router.vuejs.org/)
- [Axios](https://axios-http.com/)
- [Lodash.debounce](https://lodash.com/docs/4.17.15#debounce)
- [FormKit Auto Animate](https://formkit.com/essentials/auto-animate)


## 📂 Структура проекта

```bash
project-root/
├── .vscode/                  # Настройки редактора (опционально)
├── node_modules/             # Установленные зависимости (автоматически создаётся)
├── public/                   # Публичные файлы, доступные напрямую
│   ├── sneakers/             # Изображения кроссовок (если есть)
│   ├── *.svg, *.png, *.ico   # Иконки UI: корзина, стрелки, логотипы, эмодзи и т.д.
│   └── favicon.ico           # Иконка вкладки браузера
├── src/                      # Исходный код приложения
│   ├── assets/
│   │   └── main.css          # Стили с импортом TailwindCSS
│   ├── components/           # Повторно используемые Vue-компоненты
│   │   ├── CardComponent.vue       # Отображение одной карточки товара
│   │   ├── CardList.vue            # Список карточек товаров
│   │   ├── CartItem.vue            # Элемент корзины
│   │   ├── CartItemList.vue        # Список элементов корзины
│   │   ├── DrawerComponent.vue     # Выдвижная панель-корзина
│   │   ├── DrawerHead.vue          # Заголовок корзины
│   │   ├── HeaderComponent.vue     # Шапка сайта
│   │   └── InfoBlock.vue           # Информационный блок (пустая корзина, заказ оформлен)
│   ├── pages/                # Страницы, соответствующие маршрутам
│   │   ├── FavoritesPage.vue       # Страница избранного
│   │   └── HomePage.vue           # Главная страница (каталог товаров)
│   ├── App.vue               # Главный компонент приложения
│   └── main.js               # Точка входа в приложение
├── index.html                # Основной HTML-шаблон
├── package.json              # Скрипты, зависимости, метаинформация о проекте
├── vite.config.js            # Конфигурация Vite (включая Tailwind и Vue плагины)
├── .gitignore                # Файлы и папки, игнорируемые Git
└── README.md                 # Документация проекта
```

## 🌐 API

Приложение использует мок-сервер на базе [Mokky](https://mokky.dev):

**GET** /items — список всех кроссовок

**GET** /favorites — избранные товары

**POST** /orders — оформление заказа

*Пример адреса:*
```bash
https://7c1179b9d2e1c831.mokky.dev/items
```

## ⚙️ Установка и запуск

+ Установка зависимостей
```bash
npm install
```

+  Запуск проекта в dev-режиме
```bash
npm run dev
```

+ Сборка проекта
```bash
npm run build
```

+ Предпросмотр прод-сборки
```bash
npm run preview
```


## 📬 Автор

+ Ivan Kalugin
+ Телеграмм: https://t.me/Ivan_Anatolievich_Kalugin


## 📝 Лицензия

Этот проект лицензирован в соответствии с условиями лицензии **MIT License**. Смотрите файл [LICENSE](LICENSE) для получения подробной информации.
