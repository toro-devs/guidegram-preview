<div align="center">
  <img src="logo guidegram.png" alt="Guidegram Logo" width="120" />

  # Guidegram

  ### Telegram-бот для продажи цифровых продуктов

  [![Made with grammY](https://img.shields.io/badge/Made%20with-grammY-00BFFF?logo=telegram)](https://grammy.dev)
  [![TypeScript](https://img.shields.io/badge/TypeScript-strict-3178C6?logo=typescript&logoColor=white)](https://www.typescriptlang.org)
  [![Payments Ready](https://img.shields.io/badge/Оплата-YooKassa%20%7C%20Robokassa-brightgreen)](https://yookassa.ru)
  [![CI/CD](https://img.shields.io/badge/CI%2FCD-автоматизирован-blue)](https://github.com)

  <img src="https://www.evilsocket.net/images/human-coded.png" height="30px" alt="This project is 100% made by humans."/>

  *Сделан в одиночку. Запущен в продакшн. Полный ownership.*

</div>

---

## Что это такое

Guidegram позволяет авторам продавать гайды, чек-листы, курсы и любые цифровые файлы прямо в Telegram — без сайта, без сторонних платформ, с полным контролем над платежами.

- Покупатели выбирают продукт, оплачивают и получают файл — всё внутри Telegram
- Полноценный paywall: ссылка на оплату → подтверждение через webhook → выдача контента
- Система скидок и сегментированные рассылки для владельца бота

> Это превью-репозиторий. Основной код проекта закрытый.

---

## Техническое устройство

**Платёжная интеграция**
Полная логика paywall поверх API YooKassa и Robokassa:
- Генерация ссылок на оплату для каждого заказа
- Обработка асинхронных webhook-уведомлений
- Выдача контента только после подтверждения оплаты

**Система рассылок**
Сегментированные рассылки — всем пользователям или покупателям конкретного продукта. Реализовано на BullMQ для надёжной асинхронной обработки задач.

**Инфраструктура**
Полностью self-hosted. Автоматизированный CI/CD — провижининг сервера, сборка, настройка домена, деплой без даунтайма.

---

## Стек

| Слой | Технология |
|---|---|
| Bot framework | grammY |
| Язык | TypeScript |
| API слой | Hono |
| База данных | PostgreSQL |
| Кэш / очереди | Redis + BullMQ |
| Деплой | CI/CD, VPS |

---

## Архитектура

```
Пользователь (Telegram)
      │
      ▼
  grammY Bot
      │
      ├── Каталог продуктов
      ├── Платёжный флоу ──► YooKassa / Robokassa
      │         │
      │         └── Webhook handler ──► Проверка ──► Выдача продукта
      │
      ├── Движок скидок
      └── Система рассылок ──► BullMQ ──► Сегментированная доставка
```

---

<div align="center">

Разработано [Алексеем Быковским](https://www.linkedin.com/in/aybykovskii/) — архитектура, реализация, инфраструктура и деплой.

</div>
