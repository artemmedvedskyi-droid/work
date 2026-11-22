# ГЗ 1.2 — HTTP-запити до магазину відеоігор (CRUD)

Запустіть програму; всі приклади нижче призначені для **Windows CMD**, коли поточна папка — корінь цього проєкту. JSON для POST/PUT знаходиться у `examples/`, тому нічого не потрібно екранувати в командному рядку.

## 1. Перегляд списку (200)
```cmd
curl.exe -i http://localhost:8080/api/games
```

## 2. Перегляд однієї гри (200) і помилка (404)
```cmd
curl.exe -i http://localhost:8080/api/games/1
curl.exe -i http://localhost:8080/api/games/999
```

## 3. Фільтр за жанром (200)
```cmd
curl.exe -i "http://localhost:8080/api/games?genre=RPG"
```

## 4. Створення гри (201)
```cmd
curl.exe -i -X POST http://localhost:8080/api/games -H "Content-Type: application/json" --data-binary "@examples/create-game.json"
```

ID нової гри повертається сервером, на початку це **6**. Якщо додано інші записи, ID буде іншим.

## 5. Оновлення (200; якщо ID відсутній — 404)
```cmd
curl.exe -i -X PUT http://localhost:8080/api/games/6 -H "Content-Type: application/json" --data-binary "@examples/update-game.json"
```

## 6. Видалення (204; повторне — 404)
```cmd
curl.exe -i -X DELETE http://localhost:8080/api/games/6
curl.exe -i -X DELETE http://localhost:8080/api/games/6
```

## Додатково: помилка перевірки даних (400)

Якщо надіслати порожню назву або від'ємну ціну, сервер поверне HTTP 400.

**Увага:** дані знаходяться у пам'яті; після перезапуску сервера зміни зникнуть.
