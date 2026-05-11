# REFLECTION — Бие Даалт 14

## 1. Хамгийн үнэ цэнэтэй assertion
Schema validation буюу property болон type шалгах assertion хамгийн 
үнэ цэнэтэй санагдсан. Учир нь status 200 буцаасан ч response body 
доторх өгөгдлийн бүтэц өөрчлөгдвөл application эвдрэнэ. Жишээ нь 
`pm.expect(d).to.have.property("email")` гэсэн тест нь API-ийн 
contract-ийг баталгаажуулдаг.

## 2. Negative test
GET /users/999999 → 404 шалгах тест хамгийн сонирхолтой байсан. 
Зөвхөн "хэвийн ажиллах" тохиолдлыг шалгах нь хангалтгүй — алдааны 
тохиолдол ч бас API-ийн contract-ийн нэг хэсэг. Байхгүй ID явуулахад 
404 буцаах ёстой гэдэг нь тодорхой дүрэм бөгөөд энэ тестээр 
баталгаажуулсан.

## 3. Postman vs Newman ялгаа
Postman дотор {{baseUrl}} зөв ажиллаж байсан ч Newman-д env.json 
файлд baseUrl утга хоосон байсан учраас "Invalid URI" алдаа гарсан. 
Энэ нь environment export хийхдээ current value биш initial value 
экспортлогддогтой холбоотой байсан. env.json файлыг гараар засаж 
шийдсэн.

## 4. Token болон secret зохицуулалт
JSONPlaceholder auth шаардахгүй учраас token асуудал гараагүй. Гэхдээ 
env.dev.json болон env.ci.json файлд placeholder ашиглах дадлага хийсэн. 
Бодит токен commit хийхгүй байх нь маш чухал — GitHub дээр олон нийтэд 
харагдах учраас.

## 5. API өөрчлөгдвөл хамгийн эмзэг хэсэг
Schema validation тестүүд хамгийн эхэнд эвдрэнэ. Жишээ нь 
`pm.expect(d).to.have.property("email")` гэсэн тест нь API response-д 
"email" field-ийн нэр өөрчлөгдвөл шууд fail болно. Үүнийг бууруулахын 
тулд field нэрийг hardcode хийхгүйгээр environment variable ашиглах 
эсвэл schema validation library ашиглах нь зүйтэй.