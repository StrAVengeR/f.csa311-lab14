# Бие Даалт 14 — API Testing with Postman & Newman

## Оюутан
- Нэр: Батбаяр Билгүүн
- Хичээл: F.CSM311 Программ хангамжийн бүтээлт

## API
- JSONPlaceholder — https://jsonplaceholder.typicode.com
- Auth: Шаардахгүй

## Хавтасны бүтэц
f.csa311-lab14/
├── README.md
├── REFLECTION.md
├── partA/
│   ├── SETUP.md
│   └── screenshot.png
├── postman/
│   ├── collection.json
│   ├── env.dev.json
│   └── env.ci.json
├── .github/
│   └── workflows/
│       └── api-tests.yml
└── reports/
└── api.html

## Ажиллуулах заавар

### 1. Newman суулгах
```bash
npm install -g newman newman-reporter-htmlextra
```

### 2. Тест ажиллуулах
```bash
newman run postman/collection.json -e postman/env.dev.json
```

### 3. HTML report үүсгэх
```bash
newman run postman/collection.json -e postman/env.dev.json \
  --reporters cli,htmlextra \
  --reporter-htmlextra-export reports/api.html
```

## Тестийн товч мэдээлэл
- Нийт request: 8
- Нийт тест: 22
- Folder: Users, Posts, Errors