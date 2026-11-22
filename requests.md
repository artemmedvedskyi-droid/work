# ГЗ 1.1 — HTTP-запити до магазину відеоігор

У командному рядку Windows (`cmd.exe`) після запуску Spring Boot:

```cmd
curl.exe -i http://localhost:8080/api/games
curl.exe -i http://localhost:8080/api/games/1
curl.exe -i http://localhost:8080/api/games/999
```

Очікувано: список із 5 карток (200), детальна інформація про одну гру (200), відсутня гра (404).
Усі записи створені у `GameSeeder` під час старту застосунку.
