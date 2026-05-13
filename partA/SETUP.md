# Бие даалт 14 — Setup (Part A)

## Сонгосон API
- API нэр: DummyJSON
- Документаци: https://dummyjson.com/docs
- Base URL: `https://dummyjson.com`
- Auth: `POST /auth/login` endpoint-оос token авч, `Authorization: Bearer <token>` хэлбэрээр ашиглана.

## Яагаад DummyJSON сонгосон бэ?
- Read + write endpoint-ууд (GET/POST/PUT/DELETE) бүгд дэмждэг.
- Auth flow (login -> token -> protected route) байгаа тул request chaining хийхэд тохиромжтой.
- Тестийн хувьд status, schema/property, response time, business rule зэрэг бүх төрлийг хийхэд хялбар.

## Анхны шалгалт
- Эхний амжилттай request: `GET {{baseUrl}}/users?limit=5`
- Хүлээгдэж буй үр дүн: `200 OK`, `users` массив буцаж ирнэ.

## Screenshot
- `partA/screenshot.png` файлд эхний амжилттай request-ийн зургаа оруулна.
