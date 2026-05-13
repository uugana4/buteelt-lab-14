# bie-daalt-14

Integration & API Testing лабораторийн ажил (Postman + Newman + GitHub Actions).

## Ашигласан хувилбар
- Сонголт: **Хувилбар 1 (Public API)**
- API: **DummyJSON** (`https://dummyjson.com`)

## Repository бүтэц
- `.github/workflows/api-tests.yml` — GitHub Actions workflow
- `partA/SETUP.md` — Setup тайлбар
- `partA/screenshot.png` — Эхний амжилттай request-ийн зураг (гараар нэмнэ)
- `postman/collection.json` — Collection (8 request)
- `postman/env.dev.json` — Dev environment
- `postman/env.ci.json` — CI environment
- `reports/api.html` — Newman HTML report (эхний файл нь placeholder)
- `REFLECTION.md` — Эргэцүүлэл (5 асуултын хариулт)

## Хэрхэн ажиллуулах вэ
1. Postman дээр `postman/collection.json`, `postman/env.dev.json` import хийнэ.
2. Environment-ийг `dev` болгож сонгоно.
3. Request-үүдийг дарааллаар нь ажиллуулна:
   - `Auth/Login`
   - `Auth/Get My Profile`
   - `Users/...`
   - `Posts/...`
4. Бүх тест pass байгаа эсэхийг Postman Test Results дээр шалгана.

## Newman local run
```bash
npm install -g newman newman-reporter-htmlextra
newman run postman/collection.json -e postman/env.dev.json
newman run postman/collection.json \
  -e postman/env.dev.json \
  --reporters cli,htmlextra \
  --reporter-htmlextra-export reports/api.html
```

## CI (GitHub Actions)
Workflow файл: `.github/workflows/api-tests.yml`

Хэрэв login credential-ийг secrets-ээр өгөх бол repo дээр дараах secrets нэмнэ:
- `CI_USERNAME`
- `CI_PASSWORD`

> Тэмдэглэл: `postman/env.ci.json` дотор placeholder байгаа. Workflow нь secrets байвал runtime дээр орлуулна.

## Анхаарах зүйлс
- Secret/token-оо commit хийхгүй.
- `{{baseUrl}}`-г бүх request дээр ашигласан байх.
- `partA/screenshot.png`-г өөрийн эхний амжилттай request-ийн зургаар заавал солино.
- `reports/api.html`-г өөрийн Newman run-ий бодит report-оор заавал солино.
