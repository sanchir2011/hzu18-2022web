
## HaruulZangi U18 2022 Web challenge Writeups (Round 1)


> ### Cloud Engineer 
> Монгол инженерууд заримдаа тохиргоогоо буруу хийх юм тэ? flag.txt файлыг олоорой.
> Холбоос: [https://cloud-engineer.u18.haruulzangi.mn/](https://cloud-engineer.u18.haruulzangi.mn/)

Хэрэв тухайн холбоосоор орж үзвэл дараах үүлний зураг гарч ирэх болно.
![Cloud Engineer](https://user-images.githubusercontent.com/28390518/171184847-64e7ac52-566c-48af-add9-8527b8f67fcc.png)

Source code-г нь харж үзэхэд тухайн зураг нь [Google Cloud Storage](https://cloud.google.com/) дээр байрлаж байгаа нь харагдана.
![Source code of Cloud Engineer](https://user-images.githubusercontent.com/28390518/171185340-96733de3-2222-430d-a4be-db5d2b3ec507.png)

Тухайн зурагны холбоосоор ороод **clouds.jpeg** хасаад ороход тухайн folder доторх файлууд **XML**-р харагдах болно.
![Files in the folder](https://user-images.githubusercontent.com/28390518/171186606-e24f06d4-92d3-41b1-b85d-4e8d0c036a85.png)

Тэгвэл ард нь **flag.txt** нэмээд ороод үзэхэд flag гарч ирэх болно 😊

***HZU18{Cl00ud_St0r@g#_f3830d5c1b}***

> ### Donut Name System
> Наба DNS-ыг Donut Name System гэж боддог. Тэр системд нууцуудаа хадгалаж болох юм уу?
> Холбоос: [https://donut-name-system.u18.haruulzangi.mn/](https://donut-name-system.u18.haruulzangi.mn/)

Мэдээж дүрмийн дагуу тухайн холбоосоор орж үзнэ 😂

![Donuts](https://user-images.githubusercontent.com/28390518/171188191-3d3ee2cf-1a80-4a9e-aebf-7d0c6a99ffb0.png)

Өөдөөс маш амттай харагдаж буй donut гарч ирлээ. Гэхдээ энд donut ямар ч хамаагүй шүү 👌. Даалгаварын нэрийг харвал **DNS** юм байна гэдгийг ойлгож болно. Тэгвэл source code-н хараад үзье.
```html
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta http-equiv="X-UA-Compatible" content="IE=edge" />
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
<title>Donut Name System</title>
<meta name="flag" content="See: dns.u18.haruulzangi.mn" />
</head>
<body>
<img src="./keep-donuts-fresh.jpeg" />
</body>
</html>
```

Сайн харвал `<meta name="flag" content="See: dns.u18.haruulzangi.mn" />` хэсэг маш онцгойрч харагдана. **See:** гэдэг утгаас нь хархад биднийг энэ домэйн нэр дээрх DNS-г шалгаад үз гэсэн hint өгч байгаа мэт 🤔
Тухайн домэйн дээрх DNS-г шалгахын тулд бидэнд `dig`комманд хэрэг болно. Хэрэв суулгаагүй бол `sudo apt install dnsutils` гээд бичээд сулгах боломжтой.
За тэгвэл шалгаад үзье. `dig dns.u18.haruulzangi.mn` гэж бичихэд бидэнд хэрэгтэй мэдээлэл гарч ирсэнгүй. 
![image](https://user-images.githubusercontent.com/28390518/171190072-a27b5c6e-c83a-412a-8967-366302a60cf8.png)
Тэгвэл **flag** мань TXT record дээр байх магдлалтай гэж үзээд `dig dns.u18.haruulzangi.mn txt` гэж шалгаад үзье.
![image](https://user-images.githubusercontent.com/28390518/171190892-5c3f4e94-e582-47ff-b7cd-b18c2fa6348e.png)
Бидний хэрэгтэй **flag** гарч ирлээ 🤟

***HZU18{DNS_3v3rywh3r3_e7b5960100}***

> ### My customers
> Хасаа өөрийн гэсэн хувцасны брендийнхээ урьдчислан захиалга авах API хийжээ. Одоогоор 100 хэрэглэгч бүртгүүлээд байна. User-ын ID-г нэмэгддэг тоогоор хийх нь зөв үү?
> Холбоос: [https://my-customers.u18.haruulzangi.mn/user](https://my-customers.u18.haruulzangi.mn/user)

Тухайн холбоосоор орж үзэхэд доорх текст гарч ирнэ.

![image](https://user-images.githubusercontent.com/28390518/171192501-ca94f409-3939-4c6d-80e5-d11dadd2279d.png)

Эндээс харвал энгийн **User API** байх бөгөөд https://my-customers.u18.haruulzangi.mn/user/1 гээд үзэхэд *1* гэсэн *id*-тай хэрэглэгчийн мэдээллийг гаргах болно.
```json
{"id":1,"firstName":"Mekhi","lastName":"D'Amore","email":"Zachary_Kuhn53@hotmail.com","phone":"1-377-678-4096 x81626","address":"458 Wintheiser Place","city":"East Vitoberg","state":"Oklahoma","zip":"57905","company":"Emmerich and Sons","avatar":"https://cloudflare-ipfs.com/ipfs/Qmd3W5DuhgHirLHGVixi6V76LhCkZUz6pnFt5AJBiyvHye/avatar/496.jpg"}
```
Тэгвэл эхлээд 100 дээр шалгахад *User not found* гэсэн бичиг гарна. Үүн дээрээс харвал 0-ээс 99 хүртэл id-тай хэрэглэгчид байгаа гэсэн үг.
