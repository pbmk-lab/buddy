# Buddy — pixel AI-tamagotchi PWA

Карманный AI-питомец в ретро-стиле Claude Desktop Buddy, но как PWA для Android (и любого браузера). Подключается напрямую к Anthropic API.

![Buddy screenshot](icon-512.png)

## Запуск

PWA требует HTTPS. Самый быстрый способ — GitHub Pages:

1. Push в этот репо (см. ниже).
2. В **Settings → Pages → Source** выбери ветку `main`, папку `/ (root)`, **Save**.
3. Через минуту приложение будет доступно по адресу `https://pbmk-lab.github.io/buddy/`.
4. Открой ссылку в Chrome на Android → меню → **«Установить приложение»**.
5. В приложении нажми ⚙ → вставь `sk-ant-...` ключ. Без ключа работает демо-режим.

## Локальная разработка

```bash
python3 -m http.server 8000
# открой http://localhost:8000
```

Для теста API на `localhost` тоже работает (Chrome считает localhost безопасным).

## Что умеет Buddy

- **mood / fed / energy** — живые статы, тикают каждую минуту
- **feed / play / nap** — кнопки взаимодействия
- **chat** — общение с Claude (Haiku / Sonnet / Opus 4.6)
- **approved / denied** — Buddy сам решает по системному промпту
- **tokens / today** — реальный usage из API
- Тык в самого Buddy = поглаживание (+mood)
- Всё сохраняется в `localStorage`

## Структура

```
index.html      — единый файл со всем UI и логикой
manifest.json   — PWA-манифест
sw.js           — service worker (offline shell)
icon-192.png    — иконка приложения
icon-512.png    — большая иконка
```

## API-ключ

Ключ хранится только в `localStorage` твоего браузера. Запросы идут с телефона напрямую на `api.anthropic.com` с заголовком `anthropic-dangerous-direct-browser-access: true`.
