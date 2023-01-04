# JavaScript-ga kirish

Keling, JavaScript-ning nimasi o'ziga xosligini, u bilan nimaga erishishimiz mumkinligini va u bilan qanday boshqa texnologiyalar yaxshi o'ynashini ko'rib chiqaylik.

## JavaScript nima?

*JavaScript* dastlab "veb-sahifalarni jonli qilish" uchun yaratilgan.

Bu tildagi dasturlar skriptlar deb ataladi . Ular to'g'ridan-to'g'ri veb-sahifaning HTML-da yozilishi va sahifa yuklanganda avtomatik ravishda ishga tushishi mumkin.

Skriptlar oddiy matn sifatida taqdim etiladi va bajariladi. Ularni ishga tushirish uchun maxsus tayyorgarlik yoki kompilyatsiya kerak emas.

Bu jihatdan JavaScript Java deb nomlangan boshqa tildan juda farq qiladi . [Java](https://en.wikipedia.org/wiki/Java_(programming_language)).

```smart header="Nima uchun u <u>Java</u>Script deb ataladi?"
JavaScript yaratilganda, u dastlab boshqa nomga ega edi: "LiveScript". Ammo o'sha paytda Java juda mashhur edi, shuning uchun yangi tilni Java tilining "kenja ukasi" sifatida joylashtirish yordam berishiga qaror qilindi.

Ammo rivojlanish jarayonida JavaScript o'zining [ECMAScript](http://en.wikipedia.org/wiki/ECMAScript), deb nomlangan spetsifikatsiyasiga ega bo'lgan to'liq mustaqil tilga aylandi va endi uning Java bilan umuman aloqasi yo'q.
```

Bugungi kunda JavaScript nafaqat brauzerda, balki serverda yoki aslida JavaScript dvigateli deb nomlangan maxsus dasturga ega bo'lgan har qanday qurilmada ham ishlashi mumkin . [the JavaScript engine](https://en.wikipedia.org/wiki/JavaScript_engine).

Brauzerda ba'zan "JavaScript virtual mashinasi" deb ataladigan o'rnatilgan dvigatel mavjud.

Turli dvigatellarda turli xil "kod nomlari" mavjud. Masalan:

- [V8](https://en.wikipedia.org/wiki/V8_(JavaScript_engine)) -- Chrome, Opera va Edge-da.
- [SpiderMonkey](https://en.wikipedia.org/wiki/SpiderMonkey) -- Firefox-da.
- …IE uchun “Chakra”, “JavaScriptCore”, “Nitro” va Safari uchun “SquirrelFish” kabi boshqa kod nomlari mavjud.

Yuqoridagi shartlarni eslab qolish yaxshidir, chunki ular Internetdagi ishlab chiquvchilar maqolalarida qo'llaniladi. Biz ham ulardan foydalanamiz. Misol uchun, agar "X xususiyati V8 tomonidan qo'llab-quvvatlansa", u ehtimol Chrome, Opera va Edge'da ishlaydi.

```smart header="Dvigatellar qanday ishlaydi?"

Dvigatellar murakkab. Lekin asoslar oson.

1. Dvigatel (agar u brauzer bo'lsa, o'rnatilgan) skriptni o'qiydi ("tahlillaydi").
2. Keyin u skriptni mashina kodiga o'zgartiradi ("kompilyatsiya qiladi").
3. Va keyin mashina kodi juda tez ishlaydi.

Dvigatel jarayonning har bir bosqichida optimallashtirishni qo'llaydi. U hatto tuzilgan skriptni ishlayotganini kuzatib boradi, u orqali o'tadigan ma'lumotlarni tahlil qiladi va shu bilimlar asosida mashina kodini yanada optimallashtiradi.
```

## Brauzer ichidagi JavaScript nima qila oladi?

Zamonaviy JavaScript - bu "xavfsiz" dasturlash tili. U xotira yoki protsessorga past darajadagi kirishni ta'minlamaydi, chunki u dastlab buni talab qilmaydigan brauzerlar uchun yaratilgan.

JavaScript-ning imkoniyatlari ko'p jihatdan u ishlayotgan muhitga bog'liq. Masalan, [Node.js](https://wikipedia.org/wiki/Node.js) JavaScript-ga ixtiyoriy fayllarni o'qish/yozish, tarmoq so'rovlarini bajarish va h.k. imkonini beruvchi funksiyalarni qo'llab-quvvatlaydi.

In-brauzer JavaScript veb-sahifani manipulyatsiya qilish, foydalanuvchi va veb-server bilan o'zaro aloqa qilish bilan bog'liq hamma narsani qila oladi.

Misol uchun, brauzerda JavaScript quyidagilarga qodir:

- Sahifaga yangi HTML qo'shing, mavjud tarkibni o'zgartiring, uslublarni o'zgartiring.
- Foydalanuvchi harakatlariga munosabat bildiring, sichqonchani bosish, kursor harakati, tugmachalarni bosish orqali ishga tushirish.
- Tarmoq orqali masofaviy serverlarga so'rovlar yuboring, fayllarni yuklab oling va yuklang ( [AJAX](https://en.wikipedia.org/wiki/Ajax_(programming)) va [COMET](https://en.wikipedia.org/wiki/Comet_(programming)) texnologiyalari deb ataladi).
- Cookie-fayllarni oling va o'rnating, tashrif buyuruvchiga savollar bering, xabarlarni ko'rsating.
- Mijoz tomonidagi ma'lumotlarni eslab qoling ("mahalliy saqlash").

## Brauzerda JavaScript nima qila olmaydi?

JavaScript-ning brauzerdagi imkoniyatlari foydalanuvchi xavfsizligini himoya qilish uchun cheklangan. Maqsad, yomon veb-sahifaning shaxsiy ma'lumotlarga kirishini yoki foydalanuvchi ma'lumotlariga zarar etkazishining oldini olishdir 

Bunday cheklovlarga misollar:

- Veb-sahifadagi JavaScript qattiq diskdagi ixtiyoriy fayllarni o'qimasligi/yozmasligi, ularni nusxalashi yoki dasturlarni bajara olmasligi mumkin. U OS funktsiyalariga to'g'ridan-to'g'ri kirish imkoniga ega emas.

    Zamonaviy brauzerlar unga fayllar bilan ishlashga imkon beradi, lekin kirish cheklangan va faqat foydalanuvchi ma'lum amallarni bajarsa, masalan, faylni brauzer oynasiga "tashlab qo'yish" yoki uni <input>teg orqali tanlash bilan ta'minlanadi.

    Kamera/mikrofon va boshqa qurilmalar bilan o'zaro aloqa qilish usullari mavjud, ammo ular foydalanuvchining aniq ruxsatini talab qiladi. So a JavaScript-enabled page may not sneakily enable a web-camera, observe the surroundings and send the information to the [NSA](https://en.wikipedia.org/wiki/National_Security_Agency).
- Turli yorliqlar/oynalar odatda bir-biri haqida bilishmaydi. Ba'zan ular, masalan, bir oyna ikkinchisini ochish uchun JavaScript-dan foydalansa. Ammo bu holatda ham, bir sahifadagi JavaScript boshqa saytlardan (boshqa domen, protokol yoki portdan) kelgan bo'lsa, boshqa sahifaga kira olmasligi mumkin.

    Bu "Bir xil kelib chiqish siyosati" deb ataladi. Buni hal qilish uchun ikkala sahifa ham ma'lumotlar almashinuviga rozi bo'lishi va uni boshqaradigan maxsus JavaScript kodini o'z ichiga olishi kerak. Biz buni o'quv qo'llanmasida ko'rib chiqamiz.

Bu cheklov, yana, foydalanuvchi xavfsizligi uchun. http://anysite.comFoydalanuvchi ochgan sahifa, http://gmail.commasalan, URL manzili bo'lgan boshqa brauzer yorlig'iga kira olmasligi va u yerdan ma'lumotlarni o'g'irlamasligi kerak.

JavaScript tarmoq orqali joriy sahifa kelgan server bilan osongina bog'lanishi mumkin. Ammo uning boshqa saytlardan/domenlardan ma'lumotlarni olish qobiliyati zaif. Mumkin bo'lsa-da, bu uzoq tomondan aniq kelishuvni (HTTP sarlavhalarida ifodalangan) talab qiladi. Yana bir bor, bu xavfsizlik chegarasi.


![](limitations.svg)

JavaScript brauzerdan tashqarida, masalan, serverda ishlatilsa, bunday cheklovlar mavjud emas. Zamonaviy brauzerlar kengaytirilgan ruxsatnomalarni so'rashi mumkin bo'lgan plaginlar/kengaytmalarga ham ruxsat beradi.


## JavaScript-ni nima noyob qiladi?

JavaScript haqida kamida uchta ajoyib narsa bor:


```compare
+ HTML/CSS bilan to'liq integratsiya.
+ Oddiy narsalar oddiygina bajariladi.
+ Barcha asosiy brauzerlar tomonidan qo'llab-quvvatlanadi va sukut bo'yicha yoqilgan.

```
JavaScript bu uch narsani birlashtirgan yagona brauzer texnologiyasidir.

Bu JavaScript-ni noyob qiladi. Shuning uchun u brauzer interfeyslarini yaratish uchun eng keng tarqalgan vositadir.

Ya'ni, JavaScript serverlar, mobil ilovalar va boshqalarni yaratish uchun ishlatilishi mumkin.

## Tillar JavaScript-ni "ustidan"

JavaScript sintaksisi hammaning ehtiyojlariga mos kelmaydi. Turli odamlar turli xil xususiyatlarni xohlashadi.

Buni kutish mumkin, chunki loyihalar va talablar hamma uchun har xil.

Shunday qilib, yaqinda ko'plab yangi tillar paydo bo'ldi, ular brauzerda ishga tushirilgunga qadar JavaScript-ga ko'chiriladi (o'zgartiriladi).

Zamonaviy vositalar transpilyatsiyani juda tez va shaffof qiladi, aslida ishlab chiquvchilarga boshqa tilda kodlash va uni "qopqoq ostida" avtomatik ravishda aylantirish imkonini beradi.

Bunday tillarga misollar:

- [CoffeeScript](https://coffeescript.org/) -JavaScript uchun "sintaktik shakar". U qisqaroq sintaksisni taqdim etadi, bu bizga aniqroq va aniqroq kod yozish imkonini beradi. Odatda, Ruby ishlab chiqaruvchilariga yoqadi.
- [TypeScript](https://www.typescriptlang.org/) murakkab tizimlarni ishlab chiqish va qo'llab-quvvatlashni soddalashtirish uchun "qat'iy ma'lumotlarni yozish" ni qo'shishga qaratilgan. U Microsoft tomonidan ishlab chiqilgan.
- [Flow](https://flow.org/) shuningdek, ma'lumotlarni yozishni qo'shadi, ammo boshqacha tarzda. Facebook tomonidan ishlab chiqilgan.
- [Dart](https://www.dartlang.org/) mustaqil til bo'lib, u o'z dvigateliga ega bo'lib, u brauzerdan tashqari muhitlarda (masalan, mobil ilovalar)
- [Brython](https://brython.info/) JavaScript-ga Python-transpiler bo'lib, JavaScript-ni ishlatmasdan sof Python-da ilovalar yozish imkonini beradi.
- [Kotlin](https://kotlinlang.org/docs/reference/js-overview.html) zamonaviy, ixcham va xavfsiz dasturlash tili bo'lib, u brauzer yoki tugunni nishonga olishi mumkin.

Yana bor. Albatta, biz ushbu transpilyatsiya qilingan tillardan birini ishlatsak ham, nima qilayotganimizni tushunish uchun JavaScript-ni ham bilishimiz kerak.

## Xulosa

- JavaScript dastlab faqat brauzer tili sifatida yaratilgan, ammo hozir u ko'plab boshqa muhitlarda ham qo'llaniladi.
- Bugungi kunda JavaScript HTML/CSS bilan to'liq integratsiyalashgan eng keng tarqalgan brauzer tili sifatida o'ziga xos mavqega ega.
- JavaScript-ga "ko'chiriladigan" va ma'lum xususiyatlarni ta'minlaydigan ko'plab tillar mavjud. JavaScript-ni o'zlashtirgandan so'ng, ularni hech bo'lmaganda qisqacha ko'rib chiqish tavsiya etiladi.
