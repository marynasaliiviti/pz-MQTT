# Practical lesson pz-MQTT
# Розгортання та налаштування MQTT-брокера

> Розгортання MQTT-брокера EMQX у Docker та тестування через Postman.

---

## Що таке MQTT

MQTT — легкий протокол обміну повідомленнями за моделлю публікація/підписка.

Основні поняття:

- **Broker** — сервер який передає повідомлення між клієнтами
- **Topic** — назва каналу, наприклад `home/temperature`
- **Publish** — надіслати повідомлення в топік
- **Subscribe** — підписатись на топік щоб отримувати повідомлення
- **QoS** — рівень гарантії доставки (0, 1, 2)

---

## Структура

```
├── broker
│   └── docker-compose.yml
├── screenshots
├── .editorconfig
├── .gitignore
└── README.md
```

---

## Запуск

```bash
cd broker
docker compose up -d
```

Порти:
- `1883` — MQTT
- `8083` — WebSocket
- `18083` — веб-панель керування (логін: `admin`, пароль: `public`)

Зупинити:
```bash
docker compose down
```

---

## Тестування в Postman

1. New → MQTT
2. URL: `mqtt://localhost:1883` → Connect
3. Topics → додати `home/sensors` → Subscribe
4. Message → текст повідомлення → Topic: `home/sensors` → Send

Після надсилання повідомлення воно з'явиться у вкладці Messages.

---

## Скріншоти

Скріншоти знаходяться в папці `screenshots/`.

---

## Useful links

[EMQX Documentation](https://www.emqx.io/docs/en/latest/)

[MQTT with Postman](https://learning.postman.com/docs/sending-mqtt-messages/intro-to-mqtt/)
